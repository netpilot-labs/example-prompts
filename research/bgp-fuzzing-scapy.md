# BGP Protocol Fuzzing with Scapy

A target lab for BGP protocol fuzzing: two vendor routers in eBGP peering with a Linux fuzzing node in between. The template security researchers and vendor PSIRT teams use for structure-aware BGP fuzzing.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a BGP fuzzing target lab: 2 vendor routers (Cisco IOL and Juniper cRPD) in eBGP peering. Cisco in AS 65001, Juniper in AS 65002. Advertise 10.100.0.0/24 from Cisco to establish a normal BGP session. Insert a Linux fuzzing node as a transparent bridge between Cisco and Juniper so all BGP traffic flows through it. The Linux node should have Scapy, Python 3, tcpdump, tshark, and the scapy.contrib.bgp module pre-installed. Goal: inject structure-aware malformed BGP UPDATE messages and observe vendor parser behavior.

## What You'll Build

- 1 Cisco IOL router (AS 65001)
- 1 Juniper cRPD router (AS 65002)
- 1 Linux fuzzing node as transparent bridge
- Pre-installed Scapy with BGP contrib module
- tcpdump, tshark, Python 3 for packet analysis
- Baseline BGP session over the bridge

## Concepts Demonstrated

- Structure-aware BGP protocol fuzzing methodology
- Scapy-based malformed packet crafting (path attributes, NLRI, headers)
- Transparent-bridge-based session injection (lab-only technique)
- Vendor parser behavior observation under adversarial input
- Responsible disclosure workflow for BGP vulnerabilities

## Vendors Used

- Cisco IOL (router, fuzzing target 1)
- Juniper cRPD (router, fuzzing target 2)
- Linux fuzzing node (bridge + Scapy)

## Difficulty

⭐⭐⭐ Advanced — assumes BGP protocol knowledge and Python/Scapy familiarity

## Variations to Try

- "Swap Cisco for Arista cEOS to test Arista's BGP parser"
- "Swap Juniper for Nokia SR Linux to test Nokia's BGP parser"
- "Pin Cisco IOS version to a specific CVE-affected release (via enterprise BYOI) to reproduce historical bugs"
- "Add a third vendor downstream to test how malformed messages propagate via route reflection"
- "Combine BGP fuzzing with tc/netem packet loss to test parser behavior under lossy conditions"

## Why This Matters

BGP fuzzing has historically been performed with commercial tools (Fortra, Spirent), academic frameworks (BGPFuzz), or custom Scapy scripts against hardware. Cloud-hosted multi-vendor labs collapse the setup time and make the workflow accessible for:

- **Vendor PSIRT teams** hunting bugs in their own implementations pre-release
- **Security researchers** investigating parser boundary behaviors across vendors
- **Operator security teams** validating vendor implementations against known CVE classes
- **Academic researchers** building on top of BGPFuzz or similar frameworks

Ethical use is defensive research against your own lab devices and licensed vendor images — never against production BGP peers.

## Related Resources

- [NetPilot blog: BGP Protocol Fuzzing with Scapy and AI-Built Labs](https://www.netpilot.io/blog/bgp-fuzzing-scapy-tutorial)
- [Network Research Lab hub](https://www.netpilot.io/network-research-lab)
- [BGPFuzz academic paper](https://arxiv.org/abs/2512.05358)
- [Scapy BGP contrib module](https://scapy.readthedocs.io/en/latest/api/scapy.contrib.bgp.html)
- [Related: Cross-Vendor EVPN Bug Reproduction](./cross-vendor-evpn-bug-reproduction.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
