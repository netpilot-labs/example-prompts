# Open Source Routing Lab — FRRouting BGP + OSPF

A 4-router lab built entirely on FRRouting (FRR) — eBGP between autonomous systems over an OSPF-backed core. No commercial images, no licenses: the full open-source routing stack in one prompt.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a 4-router open source routing lab using FRRouting on every node. R1 and R2 are both in AS 65001 and run OSPF area 0 between them over 10.0.12.0/30 (R1 = .1, R2 = .2), each advertising a loopback into OSPF (R1 = 1.1.1.1/32, R2 = 2.2.2.2/32). R3 is in AS 65002 and R4 is in AS 65003 — both external eBGP peers: R2 peers with R3 over 10.0.23.0/30 and R1 peers with R4 over 10.0.14.0/30. Redistribute the OSPF loopbacks into BGP, advertise 203.0.113.0/24 from R3 and 198.51.100.0/24 from R4, and verify the R1–R2 OSPF adjacency, full BGP convergence, and that R3 and R4 can reach each other's prefixes through AS 65001.

## What You'll Build

- 4 FRRouting routers — zero commercial images, zero licenses
- An OSPF area-0 core inside AS 65001 (the IGP)
- eBGP to two external autonomous systems (AS 65002, AS 65003)
- OSPF → BGP redistribution and end-to-end reachability across the AS boundaries

## Concepts Demonstrated

- Running BGP and OSPF together on the open-source FRR stack (`bgpd` + `ospfd` under one `vtysh`)
- IGP-as-core, eBGP-at-edge — the canonical enterprise/service-provider routing shape
- Route redistribution and next-hop resolution across protocols
- That a complete multi-protocol routing lab needs no proprietary NOS — FRRouting alone covers it

## Vendors Used

- FRRouting (all four routers) — open source, no license required, no BYOI needed

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Add a second OSPF area and make R2 an ABR"
- "Replace the eBGP edges with an iBGP route-reflector design inside AS 65001"
- "Swap OSPF for IS-IS as the IGP core"
- "Inject 5% packet loss with tc netem on the R1–R2 link and watch OSPF and BGP reconverge"

## Related Resources

- [NetPilot blog: FRRouting Cloud Lab — AI-Built BGP & OSPF](https://www.netpilot.io/blog/frr-cloud-lab-guide)
- [NetPilot: Open Networking Research Lab — SONiC, FRR & SR Linux](https://www.netpilot.io/network-research-lab/open-networking)
- [NetPilot blog: OSPF vs BGP](https://www.netpilot.io/blog/ospf-vs-bgp)
- [RFC 4271 — A Border Gateway Protocol 4 (BGP-4)](https://datatracker.ietf.org/doc/html/rfc4271)
- [RFC 2328 — OSPF Version 2](https://datatracker.ietf.org/doc/html/rfc2328)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
