# Outage Forensics Playbook

A minimum viable lab for reproducing carrier-scale network outages. Three devices + a packet-crafting endpoint — the template carrier engineering teams start from when running a post-mortem.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a 3-node outage reproduction lab: Cisco IOL router, Juniper cRPD router, and Arista cEOS switch, peering via eBGP (Cisco AS 65001, Juniper AS 65002, Arista AS 65003) with BGP EVPN address family enabled for cross-vendor Type-2 route exchange. Place a route reflector role on Juniper. Add a Linux control node connected to all three devices with tc, netem, and Scapy pre-installed for link impairment and malformed packet generation. Advertise 10.100.0.0/24 from Cisco and Arista. I want to reproduce a specific production outage trigger — the lab should be a minimum viable topology that can exhibit cross-vendor EVPN bugs, BGP session flaps, and BUM replication issues.

## What You'll Build

- 1 Cisco IOL router (production-equivalent role)
- 1 Juniper cRPD router (with route-reflector configuration)
- 1 Arista cEOS switch
- 1 Linux control node (tc, netem, Scapy, hping3, iperf3)
- Full eBGP underlay + BGP EVPN overlay
- Baseline verification commands

## Concepts Demonstrated

- Minimum viable topology for carrier outage reproduction
- Multi-vendor BGP EVPN with a route reflector
- Scripted trigger injection via Linux control node
- Post-mortem playbook Phase 2 (minimum viable topology) + Phase 3 (prompt)

## Vendors Used

- Cisco IOL
- Juniper cRPD
- Arista cEOS
- Linux control node

## Difficulty

⭐⭐⭐ Advanced — assumes familiarity with BGP EVPN and outage post-mortem workflow

## Variations to Try

- "Swap Arista for Nokia SR Linux to test SP-specific interop"
- "Add a second Juniper route reflector to test iBGP mesh scale"
- "Pin vendor versions to match production firmware exactly (via enterprise BYOI)"
- "Add firewall (Palo Alto or Fortinet) between two leaves to test policy-driven outage scenarios"
- "Add sustained link impairment on one spine-leaf link to test convergence under stress"

## Why This Matters

Carrier outages take weeks to post-mortem when reproduction requires physical hardware. This template collapses that to hours: stand up a minimum viable topology, match production config, script the trigger, iterate on fixes. Each repro lab is a saved artifact — when the same bug class reappears, the lab is already waiting.

Use cases:
- **Incident post-mortem** — reproduce and validate before closing the ticket
- **Vendor TAC engagement** — ship vendors a prompt, not a packet capture
- **Pre-deployment validation** — test a candidate config change against historical bug repros
- **Team training** — new engineers debug historical incidents as ramp-up

## Related Resources

- [NetPilot blog: Reproducing Carrier-Grade Outages in a Virtual Lab](https://www.netpilot.io/blog/carrier-outage-forensics-virtual-lab)
- [NetPilot blog: How to Reproduce a Cross-Vendor EVPN Bug in 10 Minutes](https://www.netpilot.io/blog/cross-vendor-evpn-bug-reproduction)
- [Network Research Lab hub](https://www.netpilot.io/network-research-lab)
- [Related: Cross-Vendor EVPN Bug Reproduction](./cross-vendor-evpn-bug-reproduction.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
