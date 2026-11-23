# SRv6: Segment Routing over IPv6 Dataplane

Modern segment routing using IPv6 as the dataplane (no MPLS labels), built with micro-SIDs (uSID) on FRR. It is the foundation of modern SP networks, 5G transport, and cloud-native infrastructure.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a 4-router SRv6 network on FRR. R1, R2, R3, R4 in a square topology (R1-R2-R3-R4-R1), all in IS-IS Level 2 with SRv6 enabled. Give each router a uSID locator in the shared block fcbb:bb00::/32: R1 = fcbb:bb00:1::/48, R2 = fcbb:bb00:2::/48, R3 = fcbb:bb00:3::/48, R4 = fcbb:bb00:4::/48, with block-len 32, node-len 16, func-bits 16 and behavior usid. Each router has an IPv6 loopback (fc00:0:1::1/128 through fc00:0:4::1/128). Put R1 and R3 in a BGP L3VPN over SRv6 in VRF CUST (one SID per VRF, exported automatically), with a Linux host behind each: 192.168.1.0/24 behind R1, 192.168.2.0/24 behind R3. Verify (1) each router's SID table shows its uN node SID and a uA adjacency SID per IS-IS link, (2) every locator is in every router's IPv6 route table via IS-IS, (3) R1's VPN route to 192.168.2.0/24 carries R3's uDT46 SID, (4) the hosts ping each other with 0% loss, and (5) a capture on a core link shows the packet carried in IPv6 to R3's SID, with no MPLS label.

## What You'll Build

- 4 FRR routers in a square topology
- IS-IS Level 2 underlay with SRv6 locators in a shared uSID block
- uN (node) and uA (adjacency) micro-SIDs, allocated by IS-IS
- A BGP L3VPN over SRv6 with a uDT46 SID per VRF
- 2 Linux hosts in the tenant VRF to prove reachability

## Concepts Demonstrated

- Why SRv6 vs SR-MPLS (no MPLS required, native IPv6 encapsulation)
- SRv6 SID structure (Locator + Function + Args) and the uSID block, node and function lengths
- uN vs uA vs uDT46: node, adjacency and VPN-context SIDs
- How an L3VPN rides on one IPv6 destination address instead of a label stack
- Why SRv6 is central to 5G transport and cloud-native networking

## Vendors Used

- FRR (all 4 routers), open-source SRv6 with uSID
- Linux hosts as the tenant endpoints

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Add a second VRF and show each VRF gets its own uDT46 SID"
- "Shut the R1-R2 link and show IS-IS reroutes the locators while the VPN stays up"
- "Build the same square in SR-MPLS on Cisco IOL with TI-LFA and an explicit SR-TE policy, then compare the two data planes" (see [Segment Routing MPLS](segment-routing-mpls.md))

## Why This Matters in 2026

5G transport, cloud-native networking, and hyperscaler backbones are converging on SRv6. Carriers deploying 5G need SRv6 for mobility anchor points. Hyperscalers are moving from MPLS to SRv6 to eliminate the MPLS control plane entirely.

## Related Resources

- [RFC 8986: Segment Routing over IPv6 (SRv6) Network Programming](https://datatracker.ietf.org/doc/html/rfc8986)
- [Related: Segment Routing MPLS](segment-routing-mpls.md)
- [Related: FRR SRv6 L3VPN Lab](frr-srv6-mpls.md)
- [Related: MPLS Traffic Engineering (SR-TE)](mpls-traffic-engineering.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
