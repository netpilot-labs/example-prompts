# SRv6 — Segment Routing over IPv6 Dataplane

Modern segment routing using IPv6 as the dataplane (no MPLS labels) — the foundation of next-generation SP networks, 5G transport, and cloud-native infrastructure.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a 4-router SRv6 network with Nokia SR Linux. R1, R2, R3, R4 in a square topology, all in IS-IS Level 2 with SRv6 extensions enabled. Assign SRv6 locators to each router: R1 = fc00:0:1::/64, R2 = fc00:0:2::/64, R3 = fc00:0:3::/64, R4 = fc00:0:4::/64. Configure End.X SIDs for adjacency-based steering and End SIDs (node) for endpoint reachability. Each router has a loopback IPv6 address (2001:db8::1/128 through 2001:db8::4/128). Configure an SRv6-TE policy on R1 destined to R4 steering through the explicit path R1→R2→R3→R4 (bypassing the direct shortest-path link). Verify (1) IS-IS SRv6 TLVs are advertised, (2) SRv6 SIDs are programmed into the forwarding table, (3) packets from R1 to R4 follow the explicit SID list, (4) TI-LFA backup paths exist for each segment.

## What You'll Build

- 4 Nokia SR Linux routers in a square topology
- IS-IS Level 2 underlay with SRv6 extensions
- SRv6 locators, End, and End.X SIDs
- SRv6-TE explicit path policy
- TI-LFA fast reroute

## Concepts Demonstrated

- Why SRv6 vs SR-MPLS (no MPLS required, native IPv6 encapsulation)
- SRv6 SID structure (Locator + Function + Args)
- End SID vs End.X SID vs End.DT4 (VPN context)
- SR-TE over SRv6 — explicit source routing in IPv6
- Why SRv6 is central to 5G transport and cloud-native networking

## Vendors Used

- Nokia SR Linux (all 4 routers) — leading SRv6 implementation

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Add Cisco IOS-XR routers for multi-vendor SRv6 interop (watch for SID compression differences)"
- "Layer a VPN service on top using End.DT4 (IPv4 VPN over SRv6)"
- "Migrate from this SRv6 design to a parallel SR-MPLS design and compare operational differences"
- "Add SRv6 Flex-Algo for computed min-latency paths"

## Why This Matters in 2026

5G transport, cloud-native networking, and hyperscaler backbones are converging on SRv6. Carriers deploying 5G need SRv6 for mobility anchor points. Hyperscalers are moving from MPLS to SRv6 to eliminate the MPLS control plane entirely.

## Related Resources

- [RFC 8986 — Segment Routing over IPv6 (SRv6) Network Programming](https://datatracker.ietf.org/doc/html/rfc8986)
- [Related: Segment Routing MPLS](segment-routing-mpls.md)
- [Related: MPLS Traffic Engineering (SR-TE)](mpls-traffic-engineering.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
