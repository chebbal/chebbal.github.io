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
