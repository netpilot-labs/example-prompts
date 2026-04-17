# Segment Routing MPLS (SR-MPLS)

A modern SP backbone using Segment Routing over MPLS — the LDP-free, source-routed alternative that's replacing traditional MPLS designs.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a 4-router Segment Routing MPLS network with Cisco IOL. R1, R2, R3, R4 form a square topology, all in IS-IS Level 2, AS 65000. Enable Segment Routing extensions in IS-IS to advertise SR-MPLS prefix and adjacency SIDs. Allocate Node SIDs from the SRGB (start 16000): R1=16001, R2=16002, R3=16003, R4=16004. No LDP — labels come from the IGP. Add a TI-LFA (Topology-Independent Loop-Free Alternates) post-convergence backup path on each router. Loopbacks: 1.1.1.1/32 to 4.4.4.4/32. Verify SR labels in the LFIB, confirm IS-IS SR sub-TLV exchange, and test sub-50ms convergence by failing one inter-router link.

## What You'll Build

- 4-router square SP topology, all Cisco IOL
- IS-IS Level 2 with SR-MPLS extensions
- LDP-free MPLS forwarding
- Node SIDs and adjacency SIDs
- TI-LFA fast reroute

## Concepts Demonstrated

- Why Segment Routing replaces LDP (one less protocol = less complexity)
- Source routing semantics — encoded path in the label stack
- IGP-based label distribution
- TI-LFA — guaranteed loop-free backup paths
- Foundation for SR-TE (traffic engineering) without RSVP-TE complexity

## Vendors Used

- Cisco IOL (all 4 routers)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Replace IS-IS with OSPFv3 SR extensions"
- "Add Segment Routing Traffic Engineering (SR-TE) policies for explicit path steering"
- "Layer SR-MPLS L3VPN on top (combine with [MPLS L3VPN Basic](mpls-l3vpn-basic.md))"
- "Migrate to SRv6 (IPv6 dataplane) by adding SRv6 SIDs"

## Why This Matters in 2026

Most SP and large enterprise networks are migrating from LDP-based MPLS to Segment Routing. SR is the foundation for next-generation SR-TE, SRv6, and SR-Policy use cases — and it's heavily tested in CCIE Service Provider and JNCIE-SP exams.

## Related Resources

- [RFC 8402 — Segment Routing Architecture](https://datatracker.ietf.org/doc/html/rfc8402)
- [RFC 8667 — IS-IS Extensions for Segment Routing](https://datatracker.ietf.org/doc/html/rfc8667)
- [Related: MPLS L3VPN Basic](mpls-l3vpn-basic.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
