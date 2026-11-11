# All-Vendors OSPF Area 0: The Ultimate Interop Test

A single OSPF Area 0 running across Cisco, Juniper, Arista, Nokia, and FRR. If you want to know if OSPF is truly vendor-agnostic, run this lab.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a 5-router OSPF Area 0 lab with one router per major vendor: Cisco IOL (R1), Juniper cRPD (R2), Arista cEOS (R3), Nokia SR Linux (R4), FRR (R5). Connect them in a ring topology (R1-R2-R3-R4-R5-R1) with point-to-point /30 links. All interfaces in OSPF Area 0. Each router advertises its loopback (1.1.1.1/32 to 5.5.5.5/32). Use MD5 authentication on all OSPF adjacencies (shared key: "netpilot2026"). Verify that every router forms full OSPF adjacencies with its neighbors, all loopbacks are in every router's routing table, and that MD5 authentication is working across all vendor pairs.

## From ChatGPT

A three-vendor version of this lab from a ChatGPT chat: Cisco, Arista and a Junos router in a line, all in area 0. Add NetPilot from ChatGPT's plugin directory, type @NetPilot in the composer, pick it, and paste this prompt. ChatGPT reads the device guide for each vendor, writes the three startup configs, deploys the lab on your lab VM, and comes back with each router's OSPF neighbors from its own CLI and the loopback ping. The same prompt works in Claude and any AI assistant that connects to MCP servers.

> Build a three-vendor OSPF lab on my lab VM: R1 a Cisco router, R2 an Arista router, R3 a Juniper router, connected in a line R1 - R2 - R3, all in OSPF area 0. Give each router a loopback (1.1.1.1, 2.2.2.2, 3.3.3.3) and advertise it into OSPF. Deploy it, show me each router's OSPF neighbors on its own CLI, and ping 3.3.3.3 from 1.1.1.1.

Ran as written in ChatGPT on 2026-11-11: R2 read two neighbors FULL, R1 and R3 one each, and the ping from 1.1.1.1 to 3.3.3.3 got 5 of 5 replies. ChatGPT set MTU 1500 on the Junos link and the Arista side, since an MTU mismatch keeps OSPF from reaching FULL. The three images are your own, uploaded once to your lab VM (the Juniper router runs cRPD, which needs no license for OSPF). The topology and configs from the run are the [public lab](https://github.com/netpilot-labs/network-labs/tree/main/multi-vendor/ospf-three-vendor-cisco-arista-junos), the walkthrough is [Build a multi-vendor network lab from ChatGPT](https://www.netpilot.io/blog/chatgpt-multi-vendor-network-lab), and the [video](https://www.youtube.com/watch?v=TmKdDaRiwr4) shows the run.

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

- "Replace MD5 with OSPF SHA authentication, then check which vendors support it"
- "Add an ABR to split into multiple areas and observe inter-vendor Type 3 LSA exchange"
- "Add external routes via redistribution from one vendor and observe Type 5 LSAs"
- "Configure OSPFv3 for IPv6 instead"

## Why This Matters

Vendor marketing claims "OSPF is standard", but real interop testing exposes edge cases: authentication key format differences, DR election tiebreakers, timer defaults, and LSA aging behaviors. This lab catches them.

## Related Resources

- [NetPilot blog: OSPF Multi-Vendor Lab](https://www.netpilot.io/blog/ospf-multi-vendor-lab)
- [RFC 2328: OSPF Version 2](https://datatracker.ietf.org/doc/html/rfc2328)
- [Related: OSPF Multi-Area with ABR](../routing/ospf-multi-area-with-abr.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
