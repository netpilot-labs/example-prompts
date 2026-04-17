# IS-IS Level 1/2 Hierarchical Backbone

A multi-level IS-IS design with Level 1 areas at the edge and Level 2 backbone in the core — the canonical SP/hyperscaler IGP pattern.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a 6-router IS-IS hierarchical lab with Cisco IOL. R1, R2 in IS-IS area 49.0001 as Level 1-only routers. R3, R4 in area 49.0002 as Level 1/Level 2 routers (ABR equivalents). R5, R6 in area 49.0003 as Level 1-only routers. R3 and R4 also participate in Level 2 with each other (the backbone), connecting the three areas. NET addresses: R1 = 49.0001.0000.0000.0001.00, R2 = 49.0001.0000.0000.0002.00, R3 = 49.0002.0000.0000.0003.00 (L1/L2), R4 = 49.0002.0000.0000.0004.00 (L1/L2), R5 = 49.0003.0000.0000.0005.00, R6 = 49.0003.0000.0000.0006.00. Each router has a loopback (1.1.1.1/32 through 6.6.6.6/32). Verify L1 routers see only intra-area routes + default from L1/L2 routers, L2 backbone has full topology visibility, and end-to-end connectivity works across areas via the L2 backbone.

## What You'll Build

- 6 Cisco IOL routers in 3 IS-IS areas
- Level 1-only, Level 1/2, and Level 2-only routing
- Hierarchical backbone pattern
- ATT (attached) bit and default-route behavior

## Concepts Demonstrated

- IS-IS hierarchy vs OSPF areas (subtle differences)
- NET address construction (area + system-ID + NSEL)
- L1 route leaking via default + ATT bit
- Why SPs prefer IS-IS over OSPF (larger LSP, native TLV extensibility)
- Path to Segment Routing IS-IS extensions

## Vendors Used

- Cisco IOL (all 6 routers)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Enable Segment Routing IS-IS extensions and allocate Node SIDs"
- "Replace 2 routers with Juniper cRPD to test IS-IS interop"
- "Add route leaking policy from L2 → L1 for more specific prefixes"
- "Enable IS-IS authentication (HMAC-SHA) across levels"

## Related Resources

- [Related: Juniper + Nokia IS-IS Interop](../multi-vendor/juniper-nokia-isis.md)
- [Related: Segment Routing MPLS](../service-provider/segment-routing-mpls.md)
- [RFC 1195 — Use of IS-IS for Routing in TCP/IP and Dual Environments](https://datatracker.ietf.org/doc/html/rfc1195)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
