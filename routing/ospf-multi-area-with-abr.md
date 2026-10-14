# OSPF Multi-Area with Area Border Router

A classic OSPF design with three areas (backbone + two non-backbone areas) and an ABR, essential for CCNP and real-world enterprise networks.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build an OSPF multi-area lab with 5 Cisco IOL routers. R1 and R2 are in Area 1 (10.1.0.0/16). R3 is the Area Border Router connected to R1 (Area 1) and to R4 (Area 0 backbone). R4 is in Area 0. R4 also connects to R5 in Area 2 (10.2.0.0/16) via a second ABR role. Use 10.0.0.0/30 series for inter-router point-to-point links. Each router has a loopback (1.1.1.1/32 through 5.5.5.5/32). Verify OSPF neighbor adjacencies, confirm Type 1, 2, 3, and 4 LSA generation, and ensure full IP reachability across all three areas.

## What You'll Build

- 5 Cisco IOL routers
- 3 OSPF areas (Area 0 backbone + Area 1 + Area 2)
- Two ABR functions
- Inter-area route summarization opportunities
- Multiple LSA types observable

## Concepts Demonstrated

- Why OSPF requires a backbone area (Area 0)
- ABR responsibilities: translating LSAs across area boundaries
- LSA types: Router (1), Network (2), Summary (3), ASBR Summary (4)
- How Type 3 LSAs propagate inter-area routes
- Area design principles for scaling OSPF

## Vendors Used

- Cisco IOL (all 5 routers)

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Make Area 1 a stub area and Area 2 a totally stubby area to compare LSA reduction"
- "Add an external route via redistribution from EIGRP or static and observe Type 5/7 LSAs"
- "Replace R5 with a Juniper cRPD to test OSPF interop"
- "Configure manual area-range summarization on the ABRs"

## From Claude

The same lab from a Claude chat: connect NetPilot from the composer (the + menu, Connectors, the directory, NetPilot) and paste this prompt. Claude starts your lab VM, designs the topology and the IP plan, writes every router config, deploys it and reports when every OSPF neighbor is FULL. Open the lab viewer link it returns and run the show commands yourself.

> Build me a multi-area OSPF lab on Cisco IOS routers: CORE-RTR-01 and CORE-RTR-02 in area 0, EDGE-RTR-01 in area 1 behind CORE-RTR-01, EDGE-RTR-02 in area 2 behind CORE-RTR-02, one Linux host behind each edge router, RFC 5737 addressing and placeholder passwords only. Design it fresh, do not reuse any saved design. Show me the topology and the IP plan as a table, deploy it on my lab VM, and tell me when every OSPF neighbor is FULL and the two hosts can ping each other.

Four routers instead of five, each area behind its own backbone router and a Linux host per edge area, so the inter-area routes and the end-to-end ping are the proof. Watch it built: [the episode](https://www.youtube.com/watch?v=y3QlwAFSBM0) and the tutorial post below.

## Related Resources

- [NetPilot blog: How to Connect NetPilot in Claude and Build a Real Cisco OSPF Lab From the Chat](https://www.netpilot.io/blog/netpilot-in-claude)
- [NetPilot docs: connect NetPilot in Claude, ChatGPT and Meta Muse](https://www.netpilot.io/docs/agent-route)
- [NetPilot blog: OSPF Configuration Lab Guide](https://www.netpilot.io/blog/ospf-configuration-lab-guide)
- [NetPilot blog: OSPF Multi-Vendor Lab](https://www.netpilot.io/blog/ospf-multi-vendor-lab)
- [RFC 2328, OSPF Version 2](https://datatracker.ietf.org/doc/html/rfc2328)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
