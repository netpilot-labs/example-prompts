# Juniper + Nokia IS-IS Interop

IS-IS running across Juniper cRPD and Nokia SR Linux — the SP-vendor pairing that underpins most tier-1 service provider backbones.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a 4-router IS-IS interop lab with 2 Juniper cRPD routers (R1, R2) and 2 Nokia SR Linux routers (R3, R4), connected in a ring topology (R1-R2-R3-R4-R1) with /30 point-to-point links. All routers in IS-IS Level 2, same area (49.0001). Use NET addresses based on loopback IPs: e.g., R1 = 49.0001.0000.0000.0001.00, R2 = 49.0001.0000.0000.0002.00, etc. Each router advertises a loopback (1.1.1.1/32, 2.2.2.2/32, 3.3.3.3/32, 4.4.4.4/32). Enable IS-IS wide metrics (TLV 135) and IPv6 multi-topology support. Verify that Juniper and Nokia form IS-IS adjacencies across vendor boundaries, LSPs are exchanged with correct TLV parsing on both sides, the full mesh of loopbacks is reachable from any router, and wide metrics are preserved across the mixed vendor fabric.

## What You'll Build

- 4 routers across 2 SP-grade vendors
- Single IS-IS Level 2 area
- Ring topology with redundant paths
- Wide metrics enabled
- Loopback reachability validation

## Concepts Demonstrated

- IS-IS as an SP/hyperscaler routing protocol
- NET address construction and area design
- Why wide metrics (TLV 135) matter (>63 metric values)
- Multi-topology IS-IS for IPv4 + IPv6
- Real interop testing between two SP-focused vendors

## Vendors Used

- Juniper cRPD (2 routers)
- Nokia SR Linux (2 routers)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Add Segment Routing IS-IS extensions for SR-MPLS labels"
- "Add a Cisco IOS-XR router to test 3-vendor IS-IS interop"
- "Enable IS-IS authentication (HMAC-MD5) and verify vendor interop"
- "Run IS-IS Level 1 + Level 2 hierarchy and test L1/L2 boundary"

## Why SP Teams Care

Tier-1 ISPs and hyperscalers overwhelmingly prefer IS-IS over OSPF for IGP. Juniper and Nokia dominate the SP router market alongside Cisco. Testing interop between these two is a daily concern for anyone operating multi-vendor SP cores.

## Related Resources

- [ISO/IEC 10589 — IS-IS](https://www.iso.org/standard/30932.html)
- [RFC 1195 — Use of IS-IS for Routing in TCP/IP and Dual Environments](https://datatracker.ietf.org/doc/html/rfc1195)
- [Related: Segment Routing MPLS](../service-provider/segment-routing-mpls.md)
- [Related: All-Vendors OSPF Area 0](all-vendors-ospf-area-0.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
