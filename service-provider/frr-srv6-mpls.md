# FRR SRv6 L3VPN Lab

A 4-node FRR lab running SRv6 (Segment Routing over IPv6) with IS-IS as the underlay and BGP SRv6 L3VPN for tenant isolation. The open-source implementation of the same SRv6 uSID patterns hyperscalers use in AI cluster fabrics.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a 4-node FRR SRv6 network: 2 provider-edge routers (PE1, PE2) and 2 provider-core routers (P1, P2) in a square topology (PE1-P1-P2-PE2-PE1). Run IS-IS Level-2 on all 4 routers for the underlay. Configure SRv6 Locator blocks: PE1 gets fcbb:aa00:1::/48, PE2 gets fcbb:aa00:2::/48, P1 gets fcbb:aa00:3::/48, P2 gets fcbb:aa00:4::/48. Set up a BGP L3VPN between PE1 and PE2 using SRv6 as the dataplane (no MPLS). Add one Linux endpoint behind each PE in VRF TENANT1 (subnet 172.16.1.0/24 on PE1 side, 172.16.2.0/24 on PE2 side). Verify end-to-end VPN reachability and show the SRv6 SID table and BGP VPNv4 routes on each PE.

## What You'll Build

- 2 FRR PE routers with SRv6 L3VPN
- 2 FRR P routers as the SRv6 core
- IS-IS Level-2 underlay
- SRv6 Locator blocks per router
- BGP SRv6 VPN (no MPLS labels — pure IPv6 SIDs)
- 2 Linux endpoints in the tenant VRF

## Concepts Demonstrated

- SRv6 as the carrier-grade alternative to MPLS L3VPN
- How FRR implements SRv6 uSID (same as hyperscaler AI cluster fabrics)
- IS-IS as the SRv6 underlay (standard for carrier SRv6 deployments)
- BGP SRv6 VPN signaling (same control plane as commercial vendor SRv6)
- SRv6 SID allocation and the Locator block model

## Vendors Used

- FRRouting (all 4 routers — IS-IS, BGP, SRv6 daemons)
- Linux endpoints (2 VRF clients)

## Difficulty

⭐⭐⭐ Advanced — requires SRv6 and BGP VPN knowledge

## Variations to Try

- "Add a 3rd tenant VRF with different route policies"
- "Replace IS-IS underlay with OSPF to compare underlay IGP behavior"
- "Add traffic engineering: configure an explicit SRv6 segment list to steer tenant traffic via P1 rather than P2"
- "Mix FRR PEs with a Cisco IOL or Nokia SR Linux P router to test multi-vendor SRv6 interop"
- "Pin FRR version to 10.3+ to test SRv6 uSID F4816 format support"

## Why This Matters

SRv6 is the next-generation dataplane for both carrier networks and hyperscaler AI cluster fabrics. Alibaba, Cisco, Microsoft, and Nvidia have collaborated on SRv6 uSID for AI backend use-cases — and FRR 10.3+ ships the same feature set. This lab validates:

- **Carrier teams** evaluating SRv6 as a replacement for MPLS L3VPN
- **Hyperscaler fabric engineers** testing FRR SRv6 behavior alongside SONiC deployments
- **Open networking researchers** studying SRv6 implementation differences
- **Enterprise teams** evaluating FRR as a migration path off proprietary carrier-class routers

## Related Resources

- [NetPilot blog: FRRouting Cloud Labs](https://www.netpilot.io/blog/frr-cloud-lab-guide)
- [Network Research Lab hub](https://www.netpilot.io/network-research-lab)
- [FRRouting SRv6 documentation](https://docs.frrouting.org/en/latest/srte.html)
- [Related: MPLS L3VPN Basic](./mpls-l3vpn-basic.md)
- [Related: Segment Routing MPLS](./segment-routing-mpls.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
