# BGP Confederation

An alternative to route reflection for scaling iBGP — splits a large AS into sub-ASes with eBGP-like relationships between them. Common in service providers and large enterprises with multi-region networks.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a BGP confederation with 6 Cisco IOL routers inside confederation AS 65000. Split into 3 sub-ASes: sub-AS 65001 (routers R1, R2), sub-AS 65002 (routers R3, R4), sub-AS 65003 (routers R5, R6). Within each sub-AS, run iBGP full-mesh. Between sub-ASes, run "intra-confederation eBGP" (R2↔R3, R4↔R5, R6↔R1). Use OSPF as the IGP across all devices. R1 has an additional eBGP session to an external AS 65100 advertising 100.64.0.0/24. Each router has a loopback (1.1.1.1/32 through 6.6.6.6/32). Verify that external AS 65100 sees ONLY confederation AS 65000 (not the sub-ASes), confirm AS_CONFED_SEQUENCE is used internally, and test that R5 in sub-AS 65003 can reach the external prefix through the confederation.

## What You'll Build

- 6-router BGP confederation
- 3 sub-ASes, each with internal iBGP full-mesh
- Intra-confederation eBGP between sub-ASes
- OSPF IGP across all routers
- 1 external eBGP peer (AS 65100)

## Concepts Demonstrated

- Why confederation exists (iBGP full-mesh scaling alternative)
- AS_CONFED_SEQUENCE vs AS_SEQUENCE — internal to confederation, stripped at boundary
- How external peers see only the confederation ID, not sub-ASes
- Confederation vs route reflection tradeoffs
- Why most providers choose RR, but some choose confederation (operational boundaries)

## Vendors Used

- Cisco IOL (all 6 routers)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Combine confederation with route reflection — use RRs inside each sub-AS"
- "Replace OSPF with IS-IS as the IGP"
- "Add a second external AS on the other side of the confederation and observe path selection"
- "Migrate this confederation to a pure RR design to compare"

## Related Resources

- [RFC 5065 — Autonomous System Confederations for BGP](https://datatracker.ietf.org/doc/html/rfc5065)
- [Related: BGP Route Reflector Cluster](bgp-route-reflector-cluster.md)
- [Related: eBGP Three-AS Multi-Vendor](bgp-ebgp-three-as.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
