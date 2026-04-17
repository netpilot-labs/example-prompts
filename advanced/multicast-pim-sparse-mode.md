# Multicast PIM Sparse Mode

A PIM sparse-mode multicast topology with rendezvous point, IGMP joins, and source-tree switchover — foundational multicast design tested in CCNP/CCIE and used in enterprise video/IPTV networks.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a 4-router PIM sparse-mode multicast lab with Cisco IOL. R1, R2, R3, R4 connected in a partial mesh (R1↔R2, R2↔R3, R3↔R4, R1↔R4). Use OSPF as unicast IGP. Enable PIM sparse-mode on all router interfaces. R2 is the Rendezvous Point (RP) with RP address 2.2.2.2 advertised via Auto-RP (or BSR). A multicast source sits off R1 sending to group 239.1.1.1. A multicast receiver sits off R4, joining group 239.1.1.1 via IGMP. Verify the shared tree (RPT) is built from R4 to R2 (RP), the source-tree (SPT) is built from R4 to R1 after SPT switchover threshold, the receiver joins successfully, and traffic flows through the RP initially then switches to the optimal path.

## What You'll Build

- 4 Cisco IOL routers in a partial mesh
- OSPF unicast underlay
- PIM sparse-mode everywhere
- 1 RP (rendezvous point)
- 1 multicast source + 1 receiver
- Group 239.1.1.1 traffic flow

## Concepts Demonstrated

- Shared tree (RPT) vs source tree (SPT) — and the SPT switchover threshold
- RP discovery methods: static, Auto-RP, BSR
- (*, G) vs (S, G) state
- IGMP (host-to-router) vs PIM (router-to-router)
- Why sparse mode replaced dense mode for most deployments

## Vendors Used

- Cisco IOL (all 4 routers)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Add a second RP with Anycast RP for redundancy"
- "Replace PIM-SM with PIM Bidirectional (Bidir-PIM) and compare"
- "Add MSDP between RPs in different ASes for inter-domain multicast"
- "Test MVPN (multicast VPN) by layering this inside an MPLS L3VPN"

## Related Resources

- [RFC 7761 — Protocol Independent Multicast - Sparse Mode (PIM-SM)](https://datatracker.ietf.org/doc/html/rfc7761)
- [NetPilot blog: Multicast GRE Tunnel Testing](https://netpilot.io/blog/multicast-gre-tunnel-testing)
- [Related: OSPF Multi-Area with ABR](../routing/ospf-multi-area-with-abr.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
