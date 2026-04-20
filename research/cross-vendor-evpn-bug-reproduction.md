# Cross-Vendor EVPN Bug Reproduction

A minimum viable lab for reproducing cross-vendor EVPN protocol bugs — a Cisco router, a Juniper router, and a Linux endpoint with Scapy for crafting malformed packets. Used by carrier engineering teams for outage post-mortem forensics.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a 2-node lab: a Cisco IOL router (simulating an EOL production device) and a Juniper cRPD router (simulating a production vMX) in EVPN peering over VXLAN. Use AS 65001 for Cisco and AS 65002 for Juniper. Advertise 10.100.0.0/24 from both sides. Add a Linux endpoint connected to the Cisco side with Scapy pre-installed for malformed packet generation. Verify the EVPN session is up, Type-2 routes are exchanged, and baseline reachability works. The goal is to inject malformed EVPN Type-2 routes from the Linux endpoint into the BGP session and observe Juniper's parser behavior.

## What You'll Build

- 1 Cisco IOL router
- 1 Juniper cRPD router
- 1 Linux endpoint with Scapy
- EVPN peering over VXLAN
- Baseline BGP EVPN configuration on both vendors
- Scratch space on the Linux endpoint for custom Scapy scripts

## Concepts Demonstrated

- How to reproduce cross-vendor EVPN bugs without physical hardware
- Multi-vendor BGP EVPN peering (Cisco IOS syntax vs Junos groups)
- Scapy-driven malformed packet injection into a live BGP session
- Real vendor parser behavior under adversarial input
- Carrier-grade outage forensics workflow

## Vendors Used

- Cisco IOL (router)
- Juniper cRPD (router)
- Linux endpoint (Scapy, tcpdump)

## Difficulty

⭐⭐⭐ Advanced — requires understanding of BGP EVPN protocol internals and Scapy packet crafting

## Variations to Try

- "Replace the Cisco with Arista cEOS to test a Cisco-Arista interop bug instead"
- "Add a second Juniper device to test cascading failure behavior"
- "Swap the malformed Type-2 NLRI for a malformed Type-5 (IP Prefix) route"
- "Add link impairment via tc/netem to reproduce packet loss + malformed packet combination scenarios"
- "Extend to a 4-node topology: 2 Cisco + 2 Juniper to test fabric-wide blast radius of a single malformed packet"

## Why This Matters

Cross-vendor EVPN bugs are one of the most common causes of Tier-1 carrier outages. Traditional reproduction requires weeks of hardware logistics (source EOL gear, rack it, flash matching firmware, build the topology). This lab collapses that to ~10 minutes — describe the topology, get the lab, run your Scapy script, observe vendor behavior.

Use cases:
- **Carrier outage post-mortem:** reproduce the production trigger in a lab
- **Vendor TAC engagement:** ship the TAC team a reproducible prompt instead of a packet capture
- **Pre-purchase vendor validation:** stress-test new vendor gear with adversarial packets before committing
- **Security research:** RFC conformance testing and protocol fuzzing

## Related Resources

- [NetPilot blog: How to Reproduce a Cross-Vendor EVPN Bug in 10 Minutes](https://www.netpilot.io/blog/cross-vendor-evpn-bug-reproduction)
- [NetPilot blog: Debugging Cisco-Juniper EVPN Interop Issues](https://www.netpilot.io/blog/debugging-cisco-juniper-evpn-interop)
- [Network Research Lab hub](https://www.netpilot.io/network-research-lab)
- [RFC 7432 — BGP MPLS-Based Ethernet VPN](https://datatracker.ietf.org/doc/html/rfc7432)
- [Related: Cisco + Arista EVPN-VXLAN Interop](../multi-vendor/cisco-arista-evpn-vxlan-interop.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
