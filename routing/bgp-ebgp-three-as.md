# eBGP Three-AS Multi-Vendor Lab

A 3-router eBGP topology spanning Cisco, Juniper, and Arista — perfect for understanding cross-vendor BGP behavior.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a 3-router eBGP lab with Cisco IOL as R1 in AS 65001, Juniper cRPD as R2 in AS 65002, and Arista cEOS as R3 in AS 65003. R1 connects to R2 via 10.1.2.0/30 (R1 = .1, R2 = .2). R2 connects to R3 via 10.2.3.0/30 (R2 = .1, R3 = .2). Each router has a loopback advertised into BGP: R1 = 1.1.1.1/32, R2 = 2.2.2.2/32, R3 = 3.3.3.3/32. Verify full reachability between all loopbacks and confirm BGP next-hop behavior across vendor boundaries.

## What You'll Build

- 3 routers, 3 different vendors (Cisco, Juniper, Arista)
- Point-to-point eBGP peering between each adjacent pair
- Loopback advertisement and propagation
- Cross-vendor route exchange

## Concepts Demonstrated

- eBGP fundamentals — peering, AS path, next-hop
- How each vendor handles BGP configuration syntax (very different across Cisco/Juniper/Arista)
- Default behaviors that differ: route filtering, eBGP multihop, next-hop-self
- Real interop testing — your skills shouldn't be vendor-locked

## Vendors Used

- Cisco IOL (R1)
- Juniper cRPD (R2)
- Arista cEOS (R3)

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Add an iBGP session between R1 loopback and R3 loopback (transit through R2 with eBGP multihop)"
- "Add an inbound prefix-list/policy on R2 to filter R1's loopback"
- "Replace eBGP with iBGP and add a route reflector on R2"
- "Add MED and LOCAL_PREF manipulation between R1 and R3"

## Related Resources

- [NetPilot blog: BGP Multi-Vendor Lab](https://netpilot.io/blog/bgp-multi-vendor-lab)
- [NetPilot blog: BGP Basics Lab](https://netpilot.io/blog/bgp-basics-lab)
- [RFC 4271 — A Border Gateway Protocol 4 (BGP-4)](https://datatracker.ietf.org/doc/html/rfc4271)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
