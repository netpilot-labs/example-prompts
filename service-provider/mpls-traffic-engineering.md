# MPLS Traffic Engineering with Segment Routing (SR-TE)

Explicit path steering across an MPLS core using Segment Routing TE — the modern replacement for RSVP-TE, widely deployed in service provider and large enterprise backbones.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a 5-router MPLS Segment Routing Traffic Engineering lab with Cisco IOL. R1 and R5 are edge routers (PE-like). R2, R3, R4 are transit core routers. Topology: R1↔R2↔R3↔R4↔R5 as the primary path, and a second link R2↔R4 as an alternate "low-latency" path skipping R3. All routers in IS-IS Level 2 with Segment Routing extensions enabled. Allocate Node SIDs: R1=16001 through R5=16005 from SRGB starting at 16000. Configure an SR-TE policy on R1 destined to R5 with two candidate paths: (1) the default shortest-path via R3, (2) an explicit path forcing R1→R2→R4→R5 to avoid R3. Use a color attribute to steer customer traffic to the alternate path. Verify the primary path via R3, then activate the SR-TE policy and observe traffic steered through R4 instead.

## What You'll Build

- 5 Cisco IOL routers forming an SP core with redundant paths
- IS-IS SR underlay
- Explicit SR-TE policy with candidate paths
- Color-based traffic steering
- Path validation via show commands

## Concepts Demonstrated

- Why SR-TE replaced RSVP-TE (no per-LSP state in the core)
- Candidate path selection and policy preference
- Explicit path encoding in the SID list
- Color community attribute for intent-based steering
- Segment Routing's source-routing model

## Vendors Used

- Cisco IOL (all 5 routers)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Add a third candidate path with specific bandwidth and latency constraints"
- "Use Flex-Algo to compute a min-latency path instead of manual encoding"
- "Combine with L3VPN services to deliver TE for specific VPN customers only"
- "Migrate from SR-MPLS to SRv6 dataplane"

## Related Resources

- [RFC 9256 — Segment Routing Policy Architecture](https://datatracker.ietf.org/doc/html/rfc9256)
- [Related: Segment Routing MPLS](segment-routing-mpls.md)
- [Related: MPLS L3VPN Basic](mpls-l3vpn-basic.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
