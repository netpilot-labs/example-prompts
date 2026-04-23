# Customer-Matched POC Demo Lab — Mirror the Prospect's Network in 2 Minutes

Describe the prospect's environment in plain English, ship them a dedicated URL they can SSH into and drive themselves.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a customer-matched POC lab for a sales demo. Topology: two Cisco IOL edge routers (EDGE1, EDGE2, AS 65000) with eBGP to a Juniper cRPD transit (TRANSIT1, AS 65100). Inside AS 65000, iBGP from both edges to an Arista cEOS route reflector (RR1) and an internal core Cisco IOL (CORE1). Pre-load production-realistic BGP policies: LOCAL_PREF 200 on TRANSIT1 inbound, AS-path prepending on the secondary path, prefix-list filtering for customer space 203.0.113.0/24. Add a Linux endpoint (DEMO-HOST) with iperf3 and tcpdump so the prospect can run throughput and packet-capture demos during the call. Tag every interface with the customer's IP addressing scheme (10.50.x.x/24 per the prospect's ask). Make the dedicated URL shareable so the prospect can SSH in directly during our demo.

## What You'll Build

- 5-device multi-vendor customer-matched topology (2 Cisco IOL edges + Juniper cRPD transit + Arista cEOS route reflector + Cisco IOL core + Linux demo host)
- Pre-loaded production-realistic BGP policies (LOCAL_PREF, AS-path prepending, prefix-list filtering)
- Customer-specific IP addressing (parameterize per prospect)
- Linux endpoint with iperf3 + tcpdump for live data-plane demos
- Dedicated cloud environment + shareable URL for prospect-driven exploration

## Concepts Demonstrated

- **Customer-matching workflow** — describe prospect infra in plain English, AI builds matching topology in ~2 min
- **Dedicated-env-per-demo pattern** — no shared-lab corruption, one isolated environment per customer
- **Shareable URL for prospect hands-on** — flip demos from "watch me click" to "try it yourself"
- **Agent-first with SSH escape hatch** — agent builds, you verify by hand; the prospect drives the lab during the call
- **Vibe labbing register** — conversational, velocity-first lab building for sales-eng workflows

## Vendors Used

Cisco IOL, Juniper cRPD, Arista cEOS, Linux (iperf3 + tcpdump)

## Difficulty

⭐⭐ Intermediate — assembly of proven building blocks, customized per prospect

## Variations to Try

- Swap Cisco edges for Palo Alto PAN-OS if the prospect is firewall-focused
- Add a second DC site (Arista leaf-spine) for multi-site customer demos
- Pre-break the TRANSIT1 peer for a "come find the misconfig" challenge demo
- Add MPLS L3VPN on top of the BGP fabric if the customer runs a service-provider overlay
- Pre-load ACL patterns that match the customer's stated pain point
- Include multi-vendor QoS examples if the prospect asks about traffic engineering

## Why This Matters

Prospects' attention windows close faster than traditional POC labs get built. A sales engineer who can ship a customer-matched lab same-day (instead of same-quarter) gets 3x more qualification demos into the pipeline — and prospects who SSH in and drive the lab themselves during the call convert 2-3x higher than passive-demo audiences. This prompt compresses the "build a customer-matched POC lab" step from weeks to a single copy-paste.

## Related Resources

- [NetPilot Network POC Lab](https://www.netpilot.io/poc-network-lab) — dedicated landing page for this workflow
- [Blog: Best POC Lab Platforms for Sales Engineers in 2026](https://www.netpilot.io/blog/best-poc-lab-platforms-2026) — tier-ranked comparison
- [NetPilot For Network Software Vendors](https://www.netpilot.io/for-software-vendors) — vendor-specific vertical under the parent hub
- [Blog: Stop Testing Network Changes in Production](https://www.netpilot.io/blog/network-change-validation-sandbox) — adjacent enterprise use case
- [BGP Policy Change prompt](../change-validation/bgp-policy-change.md) — change-validation variant of the BGP policy scenario

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
