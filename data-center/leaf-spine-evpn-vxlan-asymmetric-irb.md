# Leaf-Spine EVPN-VXLAN with Asymmetric IRB

The same topology as [Symmetric IRB](leaf-spine-evpn-vxlan-symmetric-irb.md) but using the asymmetric routing model — useful for understanding the tradeoffs and for fabrics where asymmetric is preferred (simpler config, legacy compatibility).

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a leaf-spine fabric with 2 Arista cEOS spines and 4 Arista cEOS leaves. eBGP IPv4 underlay: spines in AS 65000, leaves in AS 65001-65004. BGP EVPN overlay between leaves and spines using loopback peering. Configure two tenant VLANs with L2 VNIs: VLAN 10 → VNI 10010 (192.168.10.0/24) and VLAN 20 → VNI 10020 (192.168.20.0/24). Use ASYMMETRIC IRB (no L3 VNI) — each leaf bridges within VNIs and routes between them locally. Each leaf has SVIs for both VLAN 10 and VLAN 20 as distributed anycast gateway. Connect a host to leaf1 in VLAN 10 and a host to leaf3 in VLAN 20. Verify inter-VLAN traffic is routed AT THE INGRESS LEAF (not centralized), confirm Type-2 (MAC/IP) route exchange with both MACs and IPs, and observe that EVERY leaf needs both source and destination VLANs configured (asymmetric constraint).

## What You'll Build

- 6 Arista cEOS devices + 2 hosts
- Asymmetric IRB (every leaf runs every tenant VLAN)
- Type-2 MAC+IP EVPN routes (not Type-5)
- Per-leaf distributed anycast gateway

## Concepts Demonstrated

- Asymmetric vs Symmetric IRB tradeoffs (simpler config vs scale)
- Why asymmetric requires every leaf to know every VLAN
- When asymmetric fits (smaller deployments, legacy hardware)
- When symmetric fits (large fabrics, strict multi-tenancy)

## Vendors Used

- Arista cEOS (all 6 devices)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Compare side-by-side — deploy both [Symmetric IRB](leaf-spine-evpn-vxlan-symmetric-irb.md) and this Asymmetric version in parallel"
- "Scale the fabric to 16 leaves and 100 VLANs to see the asymmetric configuration overhead"
- "Replace 2 leaves with Cisco Nexus to test multi-vendor asymmetric IRB"

## Asymmetric vs Symmetric IRB

| Aspect | Asymmetric | Symmetric |
|--------|-----------|-----------|
| VLANs per leaf | ALL tenant VLANs | Only VLANs with local hosts |
| Route types | Type-2 only | Type-2 + Type-5 |
| Scale limit | Lower (config explosion) | Higher |
| VRF leaking | Harder | Native |

## Related Resources

- [Related: Leaf-Spine EVPN-VXLAN with Symmetric IRB](leaf-spine-evpn-vxlan-symmetric-irb.md)
- [RFC 7432 — BGP MPLS-Based Ethernet VPN](https://datatracker.ietf.org/doc/html/rfc7432)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
