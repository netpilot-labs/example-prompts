# OSPF ↔ BGP Redistribution

Classic dual-protocol design: OSPF internally, eBGP externally, with controlled redistribution at the boundary — a CCNP/CCIE staple and real-world enterprise pattern.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build an OSPF + BGP redistribution lab with 4 Cisco IOL routers in AS 65000. R1 and R2 form the internal OSPF domain (area 0) with loopbacks 1.1.1.1/32 and 2.2.2.2/32. R3 is a border router running both OSPF area 0 (internal) and eBGP to AS 65100 (external via R4, a Cisco IOL in AS 65100 advertising 100.64.0.0/16). Configure R3 to redistribute OSPF routes into BGP with a route-map that ONLY permits loopback /32 prefixes (deny everything else). Configure R3 to redistribute BGP into OSPF as external type-2 LSAs, filtering to permit only 100.64.0.0/16 (no bogons, no defaults). Verify (1) AS 65100 learns R1 and R2 loopbacks via BGP, (2) R1 and R2 see 100.64.0.0/16 as OSPF external type-2, (3) no routing loops form, (4) the route-maps correctly filter unwanted prefixes.

## What You'll Build

- 4 Cisco IOL routers across 2 ASes
- OSPF area 0 internal + eBGP external
- Two-way redistribution with route-maps
- Type 2 external LSAs visible

## Concepts Demonstrated

- Why redistribution is dangerous without filters (routing loops, suboptimal paths)
- Route-map filtering (permit/deny logic)
- OSPF external LSA types (E1 vs E2 — cost handling difference)
- Administrative distance interplay
- Common ENCOR/ENARSI exam scenario

## Vendors Used

- Cisco IOL (all 4 routers)

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Add R5 as a second boundary router — now you have a redistribution loop to prevent"
- "Replace route-map with prefix-list filtering and compare"
- "Configure route tagging to prevent re-redistribution loops"
- "Redistribute into OSPF as E1 instead of E2 and compare path selection"

## Related Resources

- [NetPilot blog: BGP Basics Lab](https://netpilot.io/blog/bgp-basics-lab)
- [NetPilot blog: OSPF Configuration Lab Guide](https://netpilot.io/blog/ospf-configuration-lab-guide)
- [Related: OSPF Multi-Area with ABR](ospf-multi-area-with-abr.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
