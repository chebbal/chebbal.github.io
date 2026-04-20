---
layout: single
title: "DDS Mental Model - A reference"
date: 2026-04-20
categories: 
  - robotics
tags:
  - networks
---

## Mental Model

<pre>
┌─────────────────────────────────────┐
│           YOUR APPLICATION          │
│   publisher.publish(sensor_data)    │
│   subscriber.on_data(callback)      │
├─────────────────────────────────────┤
│              DDS LAYER              │
│  - Topic naming & type system       │
│  - QoS enforcement                  │
│  - History / durability cache       │
│  - Liveliness monitoring            │
│  - Content filtering                │
├─────────────────────────────────────┤
│             RTPS LAYER              │
│  - Wire encoding of messages        │
│  - HEARTBEAT / ACKNACK reliability  │
│  - SPDP / SEDP discovery            │
│  - Sequence numbers                 │
│  - Vendor extensions (Unknown[80])  │
├─────────────────────────────────────┤
│           UDP / TCP                 │
└─────────────────────────────────────┘
</pre>

## Example setup - RTPS over TCP for discovery, data over UDP

{% include mermaid.html %}

<div class="mermaid">
flowchart TD
    APP["Your Application\npublisher.publish()\nsubscriber.on_data()"]
    DDS["DDS Layer\nTopic / QoS / History / Liveliness"]
    RTPS["RTPS Layer\nDATA · HEARTBEAT · ACKNACK · SPDP · SEDP"]
    NET["UDP / TCP"]

    APP --> DDS --> RTPS --> NET

    subgraph Nodes
        A["192.168.2.13\n(local node)"]
        B["172.28.16.157\n(peer node)"]
        C["172.28.16.176:7499\n(Fast DDS Discovery Server)"]
        L["192.168.2.13\n(2nd local participant)"]
    end

    subgraph Discovery["Discovery Phase"]
        D1["TCP handshake → .176:7499"]
        D2["DATA(p) → loopback + .157\n(SPDP announce)"]
        D3["642B → discovery server\n(forward DATA(p))"]
        D4["138B + 690B ← server\n(peer registry)"]
    end

    subgraph Reliability["Reliability Init"]
        R1["HEARTBEAT x6 → loopback + .157"]
        R2["DATA(m) → loopback + .157\n(first topic data)"]
        R3["ACKNACK x14 in 2 bursts\n(NACK storm, resolved)"]
    end

    subgraph Steady["Steady State (every 100ms)"]
        S1["DATA(p) → loopback + .157\n(SPDP keepalive)"]
        S2["642B → discovery server"]
        S3["138B + 690B ← server"]
        S4["DATA(m) + HEARTBEAT\n(piggybacked)"]
        S5["DATA(p) → loopback only\n(2nd local participant)"]
    end

    A -->|TCP| D1
    A -->|RTPS/UDP| D2
    A -->|TCP| D3
    C -->|TCP| D4

    D4 --> R1 --> R2 --> R3

    R3 --> S1
    S1 --> S2
    C -->|TCP| S3
    S3 --> S4
    L -->|RTPS/UDP| S5
</div>

## Packet Level

```text
[TCP]  192.168.2.13  →  172.28.16.176:7499   SYN / SYN-ACK / ACK          (handshake)
[TCP]  192.168.2.13  →  172.28.16.176:7499   68B each way                  (session init)
[RTPS] 192.168.2.13  →  loopback + .157       DATA(p)                       (SPDP: announce self)
[TCP]  192.168.2.13  →  172.28.16.176:7499   642B                           (DATA(p) → discovery server)
[TCP]  172.28.16.176 →  192.168.2.13          138B + 690B                   (server: peer registry)
[RTPS] 192.168.2.13  →  loopback + .157       HEARTBEAT x6                  (reliability init)
[RTPS] 192.168.2.13  →  loopback + .157       DATA(m)                       (first topic data)
[RTPS] 192.168.2.13  →  loopback + .157       ACKNACK x14 (2 bursts/11ms)   (NACK storm, resolved)
── steady state every 100ms ──────────────────────────────────────────────────────────────
[RTPS] 192.168.2.13  →  loopback + .157       DATA(p)                       (SPDP keepalive)
[TCP]  192.168.2.13  →  172.28.16.176:7499   642B                           (forward to server)
[TCP]  172.28.16.176 →  192.168.2.13          138B + 690B                   (server response)
[RTPS] 192.168.2.13  →  loopback + .157       DATA(m) [+HEARTBEAT piggyback](topic data)
[RTPS] 192.168.2.13  →  loopback only         DATA(p)                       (2nd local participant)
```

## References

- [Fast-DDS RTPS Layer](https://fast-dds.docs.eprosima.com/en/latest/fastdds/rtps_layer/rtps_layer.html)
- [RTPS Specification v2.5](https://www.omg.org/spec/DDSI-RTPS/2.5/About-DDSI-RTPS)
