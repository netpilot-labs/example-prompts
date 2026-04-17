# Cisco + Juniper MPLS L3VPN Interop

An MPLS L3VPN where one PE is Cisco and the other is Juniper — the real-world scenario for carriers running mixed-vendor cores.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a Cisco + Juniper MPLS L3VPN interop lab with 5 routers: Cisco IOL PE1, Cisco IOL P1 (core), Juniper cRPD PE2, plus 2 Cisco IOL CE routers (CE1 attached to PE1, CE2 attached to PE2). PE1, P1, and PE2 form the provider core in AS 65000. Use OSPF Area 0 as the IGP and LDP for label distribution. MP-BGP VPNv4 session between PE1 and PE2 loopbacks (iBGP). Customer VRF "CUSTOMER-ACME" on both PEs with RD 65000:100 and RT 65000:100. CE1 (AS 65001) advertises 192.168.1.0/24 to PE1 via eBGP. CE2 (AS 65002) advertises 192.168.2.0/24 to PE2 via eBGP. Verify: (1) OSPF + LDP neighbors form across Cisco-Juniper boundaries in the core, (2) VPNv4 routes propagate with correct RD/RT, (3) label imposition on Cisco PE and label swap by Juniper PE work correctly, (4) customer CE1 reaches CE2's LAN across the mixed-vendor MPLS core.

## What You'll Build

- 5 routers: 3 Cisco IOL + 1 Juniper cRPD + 1 Cisco PE's customer
- MP-BGP VPNv4 across vendors
- OSPF + LDP mixed-vendor underlay
- End-to-end L3VPN service

## Concepts Demonstrated

- How MPLS L3VPN really is vendor-agnostic (RFC 4364 standard)
- Where Cisco and Juniper diverge: route-target auto-derivation, vrf-import policy vs route-target filtering
- Label operation consistency across vendors
- iBGP VPNv4 session establishment details
- Why most carriers run mixed-vendor MPLS today

## Vendors Used

- Cisco IOL (PE1, P1, CE1, CE2)
- Juniper cRPD (PE2)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Add an Arista PE for 3-vendor MPLS L3VPN test"
- "Replace LDP with Segment Routing MPLS for label distribution"
- "Add a route reflector to scale beyond 2 PEs"
- "Test Inter-AS L3VPN Option B between Cisco AS and Juniper AS"
- "Add IPv6 (6VPE) to the same VRF"

## Related Resources

- [RFC 4364 — BGP/MPLS IP Virtual Private Networks (VPNs)](https://datatracker.ietf.org/doc/html/rfc4364)
- [Related: MPLS L3VPN Basic (Cisco only)](../service-provider/mpls-l3vpn-basic.md)
- [Related: Inter-AS L3VPN Option B](../service-provider/inter-as-vpn-option-b.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
