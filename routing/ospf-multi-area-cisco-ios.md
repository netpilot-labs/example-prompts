# OSPF Multi-Area on Cisco IOS: Four Routers, Three Areas

The multi-area OSPF lab from NetPilot labs episode 3, built from a Claude chat: two core routers in the area 0 backbone, one edge router in area 1, one in area 2, a Linux host behind each edge. The design a CCNA or CCNP candidate draws on paper, running on real Cisco IOS in a few minutes.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io), or into Claude with the NetPilot connector switched on:

> Build me a multi-area OSPF lab on Cisco IOS routers: CORE-RTR-01 and CORE-RTR-02 in area 0, EDGE-RTR-01 in area 1 behind CORE-RTR-01, EDGE-RTR-02 in area 2 behind CORE-RTR-02, one Linux host behind each edge router, RFC 5737 addressing and placeholder passwords only. Design it fresh, do not reuse any saved design. Show me the topology and the IP plan as a table, deploy it on my lab VM, and tell me when every OSPF neighbor is FULL and the two hosts can ping each other.

## What You'll Build

- 4 Cisco IOL routers and 2 Linux hosts
- Area 0 backbone between the core routers, area 1 and area 2 behind each core router
- Point-to-point router links from 192.0.2.0/24, host LANs on 198.51.100.0/24 and 203.0.113.0/24 (RFC 5737 documentation ranges)
- Both core routers acting as Area Border Routers
- Host-to-host reachability across three areas

## Concepts Demonstrated

- Why every non-backbone area attaches to area 0
- What an ABR does with Type 3 summary LSAs, and how an edge router learns the far host network as an inter-area (O IA) route
- Point-to-point OSPF network type on router links and passive interfaces on host LANs
- Reading the proof on the real CLI: `show ip ospf neighbor`, `show ip route ospf`, `show ip ospf border-routers`

## Vendors Used

- Cisco IOL (all 4 routers)
- Linux (the two hosts)

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Make area 1 a stub area and area 2 a totally stubby area, then compare the edge routers' routing tables"
- "Raise the OSPF cost on the CORE-RTR-01 to EDGE-RTR-01 link to 500 and show me the before and after routing table on EDGE-RTR-01"
- "Replace EDGE-RTR-02 with an Arista cEOS switch and keep the same areas"
- "Add a loopback per router and summarize the area 1 loopbacks on CORE-RTR-01 with area range"

## Watch It Built

- [How to Connect NetPilot in Claude and Build a Real Cisco OSPF Lab From the Chat](https://www.youtube.com/watch?v=y3QlwAFSBM0): this prompt, typed in Claude, built and verified on the CLI (5 minutes)
- [The written walkthrough with the IP plan, the frames and the lab files](https://www.netpilot.io/blog/netpilot-in-claude)

## Related Resources

- [OSPF Multi-Area with ABR](ospf-multi-area-with-abr.md): the five-router version with LSA types in focus
- [OSPF Single Area — Three Router Lab](ospf-single-area-three-routers.md): the single-area starting point
- [NetPilot blog: OSPF Configuration Lab Guide](https://www.netpilot.io/blog/ospf-configuration-lab-guide)
- [Connect NetPilot in Claude, ChatGPT or Meta Muse](https://www.netpilot.io/docs/agent-route)
- [RFC 2328, OSPF Version 2](https://datatracker.ietf.org/doc/html/rfc2328)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
