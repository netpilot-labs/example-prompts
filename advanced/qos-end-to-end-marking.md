# QoS End-to-End Marking and Queuing

A multi-router lab demonstrating end-to-end QoS: classification at the edge, DSCP marking, trust boundaries, queuing in the core, and policing at egress — the full DiffServ pipeline.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a 4-router QoS lab with Cisco IOL in a line topology (R1-R2-R3-R4). R1 is the ingress edge, R4 is the egress edge, R2-R3 form the core. Configure classification on R1's ingress: voice traffic (UDP 16384-32767) marked DSCP EF (46), video traffic (TCP 1935, 5004) marked DSCP AF41 (34), web traffic (TCP 80, 443) marked DSCP AF21 (18), default DSCP 0. Trust the DSCP markings on R2 and R3 (trust boundary is R1). Configure queuing on all egress interfaces with priority queue for EF (voice), bandwidth-guaranteed queues for AF41 and AF21, and best-effort for the rest. Police any voice traffic exceeding 256 Kbps. Place 3 hosts on R1 (one per traffic class) and a server on R4. Generate traffic and verify marking is preserved end-to-end, confirm queue drops under congestion happen in best-effort first, and test that excess voice is policed.

## What You'll Build

- 4 Cisco IOL routers in a line topology
- 3 client hosts (voice, video, web) + 1 server
- Full DiffServ pipeline (classify, mark, queue, police)
- 4 traffic classes with different priority/bandwidth guarantees

## Concepts Demonstrated

- DiffServ model (classification + marking once, forwarding behavior everywhere)
- DSCP markings: EF (Expedited Forwarding) vs AF (Assured Forwarding) vs BE (Best Effort)
- Trust boundaries — where you trust upstream markings vs re-classify
- Priority queuing for voice (bounded latency)
- Weighted queuing for video/web (bandwidth guarantees)
- Policing vs shaping at the edge

## Vendors Used

- Cisco IOL (all 4 routers)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Add WRED to the web queue to demonstrate random early drops"
- "Replace the line topology with a ring to test QoS under path failure"
- "Add DSCP-to-MPLS-EXP mapping at the SP edge (for QoS across an MPLS core)"
- "Test QoS behavior across a Cisco-Juniper boundary to observe vendor interop"

## Related Resources

- [RFC 2474 — Definition of the Differentiated Services Field (DS Field)](https://datatracker.ietf.org/doc/html/rfc2474)
- [RFC 2597 — Assured Forwarding PHB Group](https://datatracker.ietf.org/doc/html/rfc2597)
- [RFC 3246 — An Expedited Forwarding PHB](https://datatracker.ietf.org/doc/html/rfc3246)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
