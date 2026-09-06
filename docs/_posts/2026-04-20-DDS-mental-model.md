---
layout: single
title: "DDS Mental Model - A reference"
date: 2026-04-20
categories:
    - robotics
    - research-notes
tags:
    - networks
    - systems
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
    subgraph AppLayer["Application Layer"]
        PUB["Publisher\npublish(sensor_data)\nTopic: /sensor\nQoS: reliable"]
        SUB_L["Subscriber (local)\non_data(callback)\nTopic: /sensor"]
        SUB_R["Subscriber (remote)\non_data(callback)\nTopic: /sensor"]
    end

    subgraph Discovery["Discovery Phase (TCP + UDP)"]
        D1["TCP handshake → .176:7499"]
        D2["UDP: DATA(p) → loopback + .157\n(SPDP: announce participant)"]
        D3["TCP: 642B → discovery server\n(forward DATA(p))"]
        D4["TCP: 138B ← server\n(ACK)"]
        D5["TCP: 690B ← server\n(peer registry: endpoints + QoS)"]
        D6["SEDP match: topic + type + QoS\n(inside TCP tunnel)"]
    end

    subgraph Reliability["Reliability Init (UDP)"]
        R1["UDP: HEARTBEAT x6 → loopback + .157\n(writer: here are my sequence numbers)"]
        R2["UDP: ACKNACK x14 ← loopback + .157\n(readers: missing seqN, resend)\n2 bursts 11ms apart — NACK storm"]
        R3["UDP: retransmit DATA(m)\n(storm resolved)"]
    end

    subgraph TopicExchange["Topic Data Exchange (UDP)"]
        T1["UDP: DATA(m) → .157\n(remote subscriber receives sample)"]
        T2["UDP: DATA(m) → loopback\n(local subscriber receives sample)"]
        T3["UDP: DATA(m) + HEARTBEAT → loopback + .157\n(piggybacked: data + reliability check)"]
        T4["UDP: ACKNACK ← loopback + .157\n(readers confirm — no missing samples)"]
    end

    subgraph Steady["Steady State every 100ms"]
        S1["UDP: DATA(p) → loopback + .157\n(SPDP keepalive)"]
        S2["TCP: 642B → discovery server"]
        S3["TCP: 138B + 690B ← server"]
        S4["UDP: DATA(p) → loopback only\n(2nd local participant)"]
    end

    PUB -->|"DDS match via SEDP"| SUB_L
    PUB -->|"DDS match via SEDP"| SUB_R

    PUB --> D1 --> D2 --> D3 --> D4 --> D5 --> D6

    D6 --> R1 --> R2 --> R3

    R3 --> T1
    R3 --> T2
    T1 & T2 --> T3
    T3 -->|"readers ACK"| T4

    T4 --> S1 --> S2 --> S3
    S3 --> T3
    S1 --> S4
</div>


## Packet Level

```text
── Discovery Phase ───────────────────────────────────────────────────────────────────────
[TCP]  192.168.2.13  →  172.28.16.176:7499   SYN / SYN-ACK / ACK          (handshake)
[TCP]  192.168.2.13  →  172.28.16.176:7499   68B each way                  (session init)
[RTPS] 192.168.2.13  →  loopback + .157       DATA(p)                       (SPDP: announce participant)
[TCP]  192.168.2.13  →  172.28.16.176:7499   642B                           (forward DATA(p) to server)
[TCP]  172.28.16.176 →  192.168.2.13          138B                           (server ACK)
[TCP]  172.28.16.176 →  192.168.2.13          690B                           (peer registry: endpoints + QoS)
[TCP]  <inside tunnel>                         DATA(w) / DATA(r)             (SEDP: topic + type + QoS match)

── Reliability Init ──────────────────────────────────────────────────────────────────────
[RTPS] 192.168.2.13  →  loopback + .157       HEARTBEAT x6                  (writer: here are my sequence numbers)
[RTPS] 192.168.2.13  →  loopback + .157       ACKNACK x14 in 2 bursts       (readers: missing seqN — NACK storm)
[RTPS] 192.168.2.13  →  loopback + .157       DATA(m) retransmit            (storm resolved)

── Topic Data Exchange ───────────────────────────────────────────────────────────────────
[RTPS] 192.168.2.13  →  172.28.16.157         DATA(m)                       (remote subscriber: sample delivered)
[RTPS] 192.168.2.13  →  192.168.2.13          DATA(m)                       (local subscriber: sample delivered)
[RTPS] 192.168.2.13  →  loopback + .157       DATA(m) + HEARTBEAT           (piggybacked: data + reliability check)
[RTPS] loopback + .157 → 192.168.2.13         ACKNACK                       (readers confirm — no missing samples)

── Steady State (every 100ms) ────────────────────────────────────────────────────────────
[RTPS] 192.168.2.13  →  loopback + .157       DATA(p)                       (SPDP keepalive)
[TCP]  192.168.2.13  →  172.28.16.176:7499   642B                           (forward to server)
[TCP]  172.28.16.176 →  192.168.2.13          138B + 690B                   (server response)
[RTPS] 192.168.2.13  →  loopback + .157       DATA(m) + HEARTBEAT           (topic data + reliability)
[RTPS] loopback + .157 → 192.168.2.13         ACKNACK                       (readers confirm)
[RTPS] 192.168.2.13  →  loopback only         DATA(p)                       (2nd local participant)
```

## References

- [Fast-DDS RTPS Layer](https://fast-dds.docs.eprosima.com/en/latest/fastdds/rtps_layer/rtps_layer.html)
- [RTPS Specification v2.5](https://www.omg.org/spec/DDSI-RTPS/2.5/About-DDSI-RTPS)
