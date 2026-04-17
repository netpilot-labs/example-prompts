# Leaf-Spine EVPN-VXLAN with Symmetric IRB

A 2-spine, 4-leaf data center fabric using BGP EVPN as the control plane and VXLAN as the data plane, with Symmetric IRB for inter-VXLAN routing.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a leaf-spine data center fabric with 2 Arista cEOS spines and 4 Arista cEOS leaves. Use eBGP underlay with each leaf in a unique AS (65001-65004) and each spine in AS 65000. Run BGP EVPN address-family overlay between leaves and spines using loopback peering. Configure VXLAN with two VNIs: VNI 10010 for tenant VLAN 10 (192.168.10.0/24) and VNI 10020 for tenant VLAN 20 (192.168.20.0/24). Use Symmetric IRB with an L3 VNI 50000 for inter-VXLAN routing in tenant VRF "TENANT-A". Connect a host to leaf1 in VLAN 10 and a host to leaf3 in VLAN 20. Verify host-to-host reachability across the fabric and confirm Type-2 and Type-5 EVPN routes.

## What You'll Build

- 6 Arista cEOS devices (2 spines + 4 leaves) + 2 hosts
- eBGP IPv4 underlay (multi-AS)
- iBGP-style EVPN overlay between loopbacks
- 2 tenant VLANs mapped to L2 VNIs
- L3 VNI for inter-subnet routing in a tenant VRF
- Symmetric IRB (Integrated Routing and Bridging)

## Concepts Demonstrated

- The de-facto modern data center fabric pattern (Arista, Cisco, and Juniper all converged on this)
- Why BGP EVPN replaced spanning-tree and proprietary fabrics
- Symmetric IRB vs Asymmetric IRB tradeoffs
- VXLAN encapsulation and the role of the VTEP
- Type-2 (MAC/IP) vs Type-5 (IP prefix) EVPN routes
- VRF separation across a shared underlay (multi-tenancy)

## Vendors Used

- Arista cEOS (all devices)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Replace 2 of the leaves with Cisco Nexus or Juniper QFX equivalents to test multi-vendor EVPN interop"
- "Add a third tenant VRF to demonstrate VRF leaking via route targets"
- "Add a border leaf with an external BGP peer to test EVPN-to-IP gateway"
- "Add a second site connected via EVPN-VXLAN multi-site DCI"

## Related Resources

- [RFC 7432 — BGP MPLS-Based Ethernet VPN](https://datatracker.ietf.org/doc/html/rfc7432)
- [RFC 8365 — Network Virtualization Overlay Solution Using EVPN](https://datatracker.ietf.org/doc/html/rfc8365)
- [Arista EVPN-VXLAN Design Guide](https://www.arista.com/en/solutions/data-center)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
