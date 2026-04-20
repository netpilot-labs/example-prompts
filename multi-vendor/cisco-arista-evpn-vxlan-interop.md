# Cisco + Arista EVPN-VXLAN Interop

A multi-vendor EVPN-VXLAN fabric where Cisco and Arista leaves participate in the same overlay — the real-world scenario every multi-vendor enterprise faces.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a leaf-spine fabric with 2 Arista cEOS spines, 2 Arista cEOS leaves (leaf1, leaf2), and 2 Cisco IOL leaves (leaf3, leaf4). All devices in eBGP underlay (spines AS 65000, each leaf in AS 65001-65004). Establish BGP EVPN address family between leaves and spines. Configure a single tenant VLAN 100 mapped to VNI 10100, with subnet 192.168.100.0/24 as a stretched L2 segment across all four leaves. Use distributed anycast gateway 192.168.100.1 on every leaf. Place hosts on each leaf in VLAN 100. Verify that Type-2 EVPN routes (MAC/IP) advertised from a Cisco leaf are correctly imported by Arista leaves (and vice versa), confirm host-to-host reachability across vendor boundaries, and observe MAC mobility behavior when a host moves between vendors.

## What You'll Build

- 2 Arista cEOS spines
- 2 Arista cEOS leaves + 2 Cisco IOL leaves
- 4 hosts (one per leaf)
- Common EVPN-VXLAN overlay across vendors
- Distributed anycast gateway (DAG)
- Single stretched L2 segment

## Concepts Demonstrated

- Why multi-vendor EVPN-VXLAN works (it's standards-based — RFC 7432 / RFC 8365)
- Where vendors differ in implementation (route-target auto-derivation, ESI handling, anycast gateway syntax)
- Type-2 (MAC/IP) route exchange across vendor boundaries
- VTEP-to-VTEP VXLAN tunneling regardless of switch vendor
- Real interop testing — what your vendor's "EVPN compliant" claim actually means

## Vendors Used

- Arista cEOS (2 spines + 2 leaves)
- Cisco IOL (2 leaves)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Add 2 Juniper QFX leaves for a true 3-vendor EVPN test"
- "Add a Layer 3 VNI to test inter-VXLAN routing interop (Symmetric IRB)"
- "Add an EVPN multi-homing scenario (ESI-LAG) across vendors — the hardest interop case"
- "Force a vendor-specific EVPN feature (e.g., Cisco's iBGP within site) and observe interop impact"

## Why This Matters

The single biggest reason multi-vendor data centers fail at EVPN: every vendor implements the same RFC slightly differently. This lab catches interop bugs in dev/staging instead of in 3 AM production debugging.

## Related Resources

- [RFC 7432 — BGP MPLS-Based Ethernet VPN](https://datatracker.ietf.org/doc/html/rfc7432)
- [RFC 8365 — Network Virtualization Overlay Solution Using EVPN](https://datatracker.ietf.org/doc/html/rfc8365)
- [NetPilot blog: Multi-Vendor Labs with AI](https://www.netpilot.io/blog/multi-vendor-labs-with-ai)
- [Related: Leaf-Spine EVPN-VXLAN with Symmetric IRB](../data-center/leaf-spine-evpn-vxlan-symmetric-irb.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
