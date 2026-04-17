# MPLS L3VPN — Basic Provider Network

A classic MPLS L3VPN topology with two PE routers, one P router, and two CE sites — the foundation of every service provider network.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build an MPLS L3VPN topology with 5 Cisco IOL routers. The provider core has PE1, P1, and PE2 in AS 65000 running OSPF area 0 as the IGP and LDP for label distribution. CE1 and CE2 are customer edge routers in customer VRF "CUSTOMER-A". CE1 connects to PE1 (eBGP, customer AS 65001), CE2 connects to PE2 (eBGP, customer AS 65002). The PE routers run MP-BGP VPNv4 to exchange customer routes through the core. Use loopbacks for MP-BGP peering between PE1 and PE2 (10.0.0.1 and 10.0.0.2). Customer LANs: CE1 advertises 192.168.1.0/24, CE2 advertises 192.168.2.0/24. Verify CE1 can reach CE2's LAN through the MPLS core, confirm VPN labels in the data path, and observe MP-BGP route exchange.

## What You'll Build

- 5-router service provider topology (2 PE + 1 P + 2 CE)
- OSPF + LDP in the provider core
- MP-BGP VPNv4 between PE routers
- Customer VRF isolation
- End-to-end VPN service across MPLS

## Concepts Demonstrated

- The role of PE, P, and CE routers in an MPLS network
- IGP + LDP combination (or how SR replaces this — see [Segment Routing MPLS](segment-routing-mpls.md))
- Route Distinguisher (RD) and Route Target (RT) in MP-BGP VPNv4
- Two-label stack: outer (transport) + inner (VPN)
- VRF separation and customer multi-tenancy

## Vendors Used

- Cisco IOL (all 5 routers)

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Add a second customer VRF (CUSTOMER-B) with overlapping IP ranges to demonstrate VRF isolation"
- "Add a route reflector for VPNv4 to scale beyond two PEs"
- "Replace LDP with Segment Routing MPLS"
- "Add an Inter-AS L3VPN scenario (Option B) with a second AS"

## Related Resources

- [RFC 4364 — BGP/MPLS IP Virtual Private Networks (VPNs)](https://datatracker.ietf.org/doc/html/rfc4364)
- [Related: Segment Routing MPLS](segment-routing-mpls.md)
- [Related: BGP Route Reflector Cluster](../routing/bgp-route-reflector-cluster.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
