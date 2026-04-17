# EVPN-VXLAN Multi-Site Data Center Interconnect

Two data center sites, each with its own EVPN-VXLAN fabric, connected via EVPN multi-site for seamless Layer 2 and Layer 3 extension — the modern replacement for OTV, VPLS, and legacy DCI designs.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a 2-site EVPN-VXLAN multi-site topology with Arista cEOS. Site A has 1 spine and 2 leaves. Site B has 1 spine and 2 leaves. Each site runs its own intra-site BGP EVPN fabric (spines in unique AS per site, leaves in per-leaf AS). A pair of border gateways (one in each site) connects the two sites via EVPN multi-site with a shared fabric-external AS for DCI peering. Configure tenant VLAN 100 (192.168.100.0/24) as an L2 VNI 10100 stretched across both sites. Configure L3 VNI 50000 in tenant VRF "GLOBAL-TENANT" for inter-site routing. Place a host in Site A leaf1 and a host in Site B leaf2, both in VLAN 100. Verify site-local Type-2 routes stay local, cross-site Type-2 routes are re-originated by the border gateway (with BGW's own IP as next-hop), and end-to-end host reachability across sites.

## What You'll Build

- 2 complete EVPN-VXLAN fabrics (1 spine + 2 leaves each)
- 2 border gateways providing DCI
- Stretched L2 VNI across sites
- Shared L3 VNI for cross-site routing
- 2 hosts (one per site)

## Concepts Demonstrated

- EVPN multi-site architecture (RFC 7432 + vendor extensions)
- Border gateway role: re-originate EVPN routes with local next-hop
- Why raw EVPN-VXLAN across WAN is a bad idea (full-mesh VTEP, MAC flooding)
- How multi-site solves the DCI problem (selective flooding, BUM suppression)
- Comparison with legacy DCI: OTV, VPLS, dark fiber L2 extension

## Vendors Used

- Arista cEOS (all 6 devices)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Add a third site for a full-mesh 3-site EVPN multi-site topology"
- "Replace one site's leaves with Cisco Nexus equivalents to test cross-vendor multi-site"
- "Enable BUM (broadcast, unknown unicast, multicast) suppression on the border gateways"
- "Add dual border gateways per site for high availability"

## Why This Matters in 2026

Enterprise data center consolidation and cloud-region expansion both require robust DCI. EVPN multi-site is now the dominant design for greenfield deployments, replacing OTV and VPLS. Every hyperscaler and most Fortune 500 data centers run this pattern.

## Related Resources

- [RFC 7432 — BGP MPLS-Based Ethernet VPN](https://datatracker.ietf.org/doc/html/rfc7432)
- [Related: Leaf-Spine EVPN-VXLAN with Symmetric IRB](leaf-spine-evpn-vxlan-symmetric-irb.md)
- [Related: Cisco + Arista EVPN-VXLAN Interop](../multi-vendor/cisco-arista-evpn-vxlan-interop.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
