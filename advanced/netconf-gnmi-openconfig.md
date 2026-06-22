# NETCONF, gNMI & OpenConfig — Programmable Multi-Vendor Lab

A two-node programmability lab — push YANG-modeled OpenConfig over NETCONF and stream telemetry over gNMI, across Nokia SR Linux and Arista cEOS, so you can compare the two management planes on real gear.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a 2-node lab: one Nokia SR Linux node (srl1) and one Arista cEOS node (ceos1) connected back-to-back on ethernet-1/1 ↔ Ethernet1. Enable NETCONF (port 830) and gNMI on both, and enable OpenConfig on SR Linux. Assign srl1 ethernet-1/1 to 10.0.0.1/30 and ceos1 Ethernet1 to 10.0.0.2/30, and verify reachability. Then push an OpenConfig interface description to each device over NETCONF, and start a gNMI streaming-telemetry subscription for interface counters. Show me the NETCONF `<get-config>` reply and the gNMI Subscribe output side by side.

## What You'll Build

- 2 nodes, 2 vendors (Nokia SR Linux + Arista cEOS), both with native NETCONF + gNMI
- An OpenConfig (vendor-neutral YANG) config push delivered over NETCONF
- A gNMI streaming-telemetry subscription for interface counters
- A side-by-side NETCONF-vs-gNMI comparison against real network OSes

## Concepts Demonstrated

- NETCONF transactional config (candidate / commit / rollback) over SSH on port 830
- gNMI `Subscribe` (STREAM mode) telemetry over gRPC
- YANG and OpenConfig as the shared schema that makes one config path work across vendors
- Management-plane differences that trip people up — e.g. SR Linux serves gNMI on 57400 while cEOS uses 6030, and SR Linux needs OpenConfig explicitly enabled

## Vendors Used

- Nokia SR Linux (srl1, built-in)
- Arista cEOS (ceos1, BYOI)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Add a RESTCONF GET against cEOS and compare it to the NETCONF get-config" (RESTCONF on cEOS only — SR Linux doesn't expose it)
- "Subscribe to BGP neighbor state over gNMI, then flap the session and watch the stream"
- "Push the same OpenConfig interface path to both vendors in one workflow and diff the replies"
- "Add a third vendor (Cisco IOL via BYOI) and extend the OpenConfig push to all three"

## Related Resources

- [NetPilot blog: NETCONF, gNMI & YANG Lab](https://www.netpilot.io/blog/netconf-gnmi-yang-lab)
- [NetPilot blog: Build Multi-Vendor Labs with AI](https://www.netpilot.io/blog/multi-vendor-labs-with-ai)
- [OpenConfig](https://www.openconfig.net/)
- [RFC 6241 — NETCONF](https://datatracker.ietf.org/doc/html/rfc6241)
- [gNMI Specification](https://github.com/openconfig/reference/blob/master/rpc/gnmi/gnmi-specification.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
