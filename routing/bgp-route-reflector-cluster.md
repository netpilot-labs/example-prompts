# BGP Route Reflector Cluster

An iBGP design using route reflectors to scale beyond full-mesh limitations — production-grade pattern used in every large enterprise and SP backbone.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build an iBGP route reflector cluster with 6 Cisco IOL routers, all in AS 65000. R1 and R2 are route reflectors (cluster ID 1.1.1.1). R3, R4, R5, and R6 are route reflector clients. Each client has an iBGP session to BOTH R1 and R2 for redundancy. R1 and R2 have an iBGP session between themselves. All routers have loopbacks (1.1.1.1/32 through 6.6.6.6/32) advertised into BGP. Use OSPF area 0 as the IGP across all router-to-router links (10.0.0.0/30 series). R3 has an additional eBGP session to an external AS 65100 advertising prefix 100.64.0.0/24. Verify route reflection works (R3's external prefix reaches R6 via R1 and R2), confirm cluster-list attribute prevents loops, and check BGP best path selection.

## What You'll Build

- 6-router topology, all Cisco IOL
- 2 route reflectors with redundancy
- 4 route reflector clients
- OSPF underlay
- One eBGP edge for external prefix injection

## Concepts Demonstrated

- Why iBGP requires full-mesh by default and what RRs solve
- Cluster ID, originator ID, and cluster-list BGP attributes
- Loop prevention in iBGP RR designs
- Redundant RR design (two clusters or one cluster with two RRs)
- BGP best-path selection with reflected routes

## Vendors Used

- Cisco IOL (all 6 routers)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Add a third route reflector for extra redundancy and observe cluster-list growth"
- "Replace OSPF with IS-IS as the IGP"
- "Add BGP confederation to compare with route reflection"
- "Add a second AS via eBGP and test route filtering policies"

## Related Resources

- [RFC 4456 — BGP Route Reflection](https://datatracker.ietf.org/doc/html/rfc4456)
- [NetPilot blog: BGP Multi-Vendor Lab](https://netpilot.io/blog/bgp-multi-vendor-lab)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
