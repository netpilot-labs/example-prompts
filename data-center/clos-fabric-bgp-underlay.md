# Clos Fabric with BGP Underlay (L3-Only)

A pure IP/BGP Clos fabric — no overlay, no VXLAN — just clean Layer 3 ECMP between leaves and spines. The foundation that EVPN-VXLAN builds on top of.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a 2-spine, 4-leaf Clos fabric with Arista cEOS. Use eBGP IPv4 underlay only (no overlay): each leaf in its own AS (65001-65004), both spines in AS 65000. Use /31 point-to-point addressing between spine-leaf pairs. Each leaf advertises a host-facing /24 subnet (192.168.1.0/24 through 192.168.4.0/24). Enable maximum-paths on all devices for ECMP load balancing. Place one host on each leaf. Verify: (1) each leaf has equal-cost routes to other leaf's subnets via both spines, (2) traffic is hashed across both spines per-flow, (3) failing one spine does NOT cause packet loss (fast convergence via BGP best-external).

## What You'll Build

- 6-device leaf-spine topology, all Arista cEOS
- eBGP IPv4 underlay (no iBGP, no IGP)
- /31 point-to-point addressing (RFC 3021)
- ECMP load balancing
- 4 hosts (one per leaf)

## Concepts Demonstrated

- Why Clos architecture replaced 3-tier for data centers
- eBGP as underlay (pioneered by Microsoft, codified in RFC 7938)
- ECMP behavior and flow-based hashing
- Failure convergence with BGP PIC / best-external
- When you DON'T need EVPN-VXLAN (pure L3 use cases, no multi-tenancy needed)

## Vendors Used

- Arista cEOS (all 6 devices)

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Add a third spine to demonstrate horizontal scaling of the fabric"
- "Replace eBGP with OSPF as the underlay and compare convergence"
- "Add BFD for sub-second failure detection"
- "Layer EVPN-VXLAN on top (see [Leaf-Spine EVPN-VXLAN with Symmetric IRB](leaf-spine-evpn-vxlan-symmetric-irb.md))"

## Why Start Here

Before diving into EVPN-VXLAN, understanding pure-L3 Clos is essential. If your data center doesn't need L2 extension or multi-tenancy, this design is simpler, easier to troubleshoot, and has fewer failure modes.

## Related Resources

- [RFC 7938 — Use of BGP for Routing in Large-Scale Data Centers](https://datatracker.ietf.org/doc/html/rfc7938)
- [Related: Leaf-Spine EVPN-VXLAN with Symmetric IRB](leaf-spine-evpn-vxlan-symmetric-irb.md)
- [Related: AI Cluster RoCEv2 Fabric](ai-cluster-rocev2-fabric.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
