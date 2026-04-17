# All-Vendors OSPF Area 0 — The Ultimate Interop Test

A single OSPF Area 0 running across Cisco, Juniper, Arista, Nokia, and FRR — if you want to know if OSPF is truly vendor-agnostic, run this lab.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a 5-router OSPF Area 0 lab with one router per major vendor: Cisco IOL (R1), Juniper cRPD (R2), Arista cEOS (R3), Nokia SR Linux (R4), FRR (R5). Connect them in a ring topology (R1-R2-R3-R4-R5-R1) with point-to-point /30 links. All interfaces in OSPF Area 0. Each router advertises its loopback (1.1.1.1/32 to 5.5.5.5/32). Use MD5 authentication on all OSPF adjacencies (shared key: "netpilot2026"). Verify that every router forms full OSPF adjacencies with its neighbors, all loopbacks are in every router's routing table, and that MD5 authentication is working across all vendor pairs.

## What You'll Build

- 5-router ring, one per major vendor
- OSPF Area 0 across all 5 devices
- Point-to-point /30 inter-router links
- Loopback advertisement
- MD5 authentication (common interop stumbling block)

## Concepts Demonstrated

- OSPF as a truly standards-based protocol (RFC 2328)
- Vendor syntax differences: network statements (Cisco) vs interface mode (Juniper) vs area assignment (Arista/Nokia/FRR)
- MD5 authentication interop across vendors
- How each vendor's "show ip ospf neighbors" differs
- Confidence that mixed-vendor deployments work in production

## Vendors Used

- Cisco IOL (R1)
- Juniper cRPD (R2)
- Arista cEOS (R3)
- Nokia SR Linux (R4)
- FRR (R5)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Replace MD5 with OSPF SHA authentication — check which vendors support it"
- "Add an ABR to split into multiple areas and observe inter-vendor Type 3 LSA exchange"
- "Add external routes via redistribution from one vendor and observe Type 5 LSAs"
- "Configure OSPFv3 for IPv6 instead"

## Why This Matters

Vendor marketing claims "OSPF is standard" — but real interop testing exposes edge cases: authentication key format differences, DR election tiebreakers, timer defaults, and LSA aging behaviors. This lab catches them.

## Related Resources

- [NetPilot blog: OSPF Multi-Vendor Lab](https://netpilot.io/blog/ospf-multi-vendor-lab)
- [RFC 2328 — OSPF Version 2](https://datatracker.ietf.org/doc/html/rfc2328)
- [Related: OSPF Multi-Area with ABR](../routing/ospf-multi-area-with-abr.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
