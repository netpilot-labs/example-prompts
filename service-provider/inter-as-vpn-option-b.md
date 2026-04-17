# Inter-AS MPLS L3VPN — Option B

A two-provider L3VPN topology where customers have VPN service across two autonomous systems — Option B uses ASBR-to-ASBR VPNv4 exchange, the most common real-world inter-AS design.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build an Inter-AS L3VPN Option B topology with 6 Cisco IOL routers. Provider 1 (AS 65000) has PE1 and ASBR1 running OSPF + LDP + MP-BGP VPNv4. Provider 2 (AS 65100) has PE2 and ASBR2 running OSPF + LDP + MP-BGP VPNv4. The two providers connect via eBGP VPNv4 between ASBR1 and ASBR2 — no intra-VRF labels exchanged at the ASBR boundary, instead the ASBRs advertise VPNv4 routes to each other and swap labels. Customer CE1 attaches to PE1, CE2 attaches to PE2, both in VRF "CUSTOMER-GLOBAL". CE1 advertises 192.168.1.0/24, CE2 advertises 192.168.2.0/24. Verify end-to-end reachability between the two customer sites across the inter-AS boundary, confirm the ASBRs install downloaded VPN labels, and trace the label stack across each AS.

## What You'll Build

- 6-router topology split across 2 providers (AS 65000 + AS 65100)
- 2 PEs + 2 ASBRs + 2 CEs
- OSPF + LDP in each provider
- MP-BGP VPNv4 within each provider AND eBGP VPNv4 at the boundary
- Customer VRF spanning both providers

## Concepts Demonstrated

- Inter-AS options: A (VRF-to-VRF), B (ASBR-to-ASBR VPNv4), C (multi-hop VPNv4 + IPv4+label)
- Why Option B is the most common for carrier-to-carrier
- Label swap at the ASBR boundary
- Route-target import/export across AS boundaries
- How MPLS VPN scales across trust boundaries

## Vendors Used

- Cisco IOL (all 6 routers)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Compare by also implementing Option A (back-to-back VRFs) and Option C on the same topology"
- "Add a third AS to demonstrate multi-hop Option C"
- "Replace Provider 2's routers with Juniper cRPD to test multi-vendor inter-AS VPN"
- "Add IPv6 L3VPN (6VPE) to the same topology"

## Related Resources

- [RFC 4364 — BGP/MPLS IP VPNs (Section 10 covers inter-AS)](https://datatracker.ietf.org/doc/html/rfc4364)
- [Related: MPLS L3VPN Basic](mpls-l3vpn-basic.md)
- [Related: MPLS Traffic Engineering](mpls-traffic-engineering.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
