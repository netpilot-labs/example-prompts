# eBGP Three-AS Multi-Vendor Lab

A 3-router eBGP topology spanning Cisco, Juniper and Arista, for learning how BGP behaves across vendors.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a 3-router eBGP lab with Cisco IOL as R1 in AS 65001, Juniper cRPD as R2 in AS 65002, and Arista cEOS as R3 in AS 65003. R1 connects to R2 via 10.1.2.0/30 (R1 = .1, R2 = .2). R2 connects to R3 via 10.2.3.0/30 (R2 = .1, R3 = .2). Each router has a loopback advertised into BGP: R1 = 1.1.1.1/32, R2 = 2.2.2.2/32, R3 = 3.3.3.3/32. Verify full reachability between all loopbacks and confirm BGP next-hop behavior across vendor boundaries.

## From Claude

The same three-AS lab from a Claude chat, with Arista, Nokia and FRR: connect NetPilot from the composer (the + menu, Connectors, the directory, NetPilot) and paste this prompt. Claude starts your lab VM, reads the device guide for each vendor, writes the Arista and SR Linux configs, deploys the lab, configures FRR, and comes back with the BGP summary from every router and the loopback ping. The same prompt works in ChatGPT and any AI assistant that connects to MCP servers.

> Using NetPilot, build me a three-router eBGP lab: Arista cEOS as R1 in AS 65001, Nokia SR Linux as R2 in AS 65002, FRR as R3 in AS 65003. Link R1 to R2 on 10.1.2.0/30 and R2 to R3 on 10.2.3.0/30. Give each router a loopback (1.1.1.1/32, 2.2.2.2/32, 3.3.3.3/32) and advertise it into BGP. Deploy it, then show me the BGP summary from each router and a ping from R1's loopback to R3's loopback.

Ran as written in Claude on 2026-11-11: both of R2's sessions established, and the ping from 1.1.1.1 to 3.3.3.3 got 5 of 5 replies. Arista cEOS is your own image, uploaded once to your lab VM. SR Linux and FRR are built in. The topology and configs from the run are the [public lab](https://github.com/netpilot-labs/network-labs/tree/main/multi-vendor/ebgp-three-as-arista-nokia-frr), the walkthrough is the [multi-vendor run in Claude](https://www.netpilot.io/blog/netpilot-in-claude#multi-vendor-ebgp-from-one-prompt), and the 40-second [Short](https://www.youtube.com/shorts/XzZNgu5dECI) shows it.

## What You'll Build

- 3 routers, 3 different vendors (Cisco, Juniper, Arista)
- Point-to-point eBGP peering between each adjacent pair
- Loopback advertisement and propagation
- Cross-vendor route exchange

## Concepts Demonstrated

- eBGP fundamentals: peering, AS path, next-hop
- How each vendor handles BGP configuration syntax (very different across Cisco/Juniper/Arista)
- Default behaviors that differ: route filtering, eBGP multihop, next-hop-self
- Real interop testing, so your skills are not tied to one vendor

## Vendors Used

- Cisco IOL (R1)
- Juniper cRPD (R2)
- Arista cEOS (R3)

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Add an iBGP session between R1 loopback and R3 loopback (transit through R2 with eBGP multihop)"
- "Add an inbound prefix-list/policy on R2 to filter R1's loopback"
- "Replace eBGP with iBGP and add a route reflector on R2"
- "Add MED and LOCAL_PREF manipulation between R1 and R3"

## Related Resources

- [NetPilot blog: BGP Multi-Vendor Lab](https://www.netpilot.io/blog/bgp-multi-vendor-lab)
- [NetPilot blog: BGP Basics Lab](https://www.netpilot.io/blog/bgp-basics-lab)
- [RFC 4271: A Border Gateway Protocol 4 (BGP-4)](https://datatracker.ietf.org/doc/html/rfc4271)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
