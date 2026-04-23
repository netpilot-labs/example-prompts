# Change Validation Workflow — Mirror, Snapshot, Apply, Diff

The overarching pattern behind every network change validation: build a multi-vendor mirror of the affected segment, snapshot state, apply the proposed change, snapshot again, diff. Evidence for the change advisory board in minutes instead of weeks.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a digital twin of a production BGP edge for change validation. Topology: Cisco IOL edge router (EDGE1, AS 65000) with eBGP to a Juniper cRPD transit (TRANSIT-A, AS 65100). Inside AS 65000, iBGP from EDGE1 to an Arista cEOS route-reflector (RR1) and a Cisco IOL internal router (CORE1). Advertise customer prefix 203.0.113.0/24 to TRANSIT-A. Add a Linux endpoint (OBSERVER) with Scapy + tcpdump so I can verify packet flow. Capture a pre-change snapshot: BGP neighbor state on every device, IP routing tables, interface counters, ACL hit counts on EDGE1. Apply the proposed change: add a new prefix-list DENY-BOGONS on EDGE1 inbound from TRANSIT-A that denies 10.0.0.0/8, 192.168.0.0/16, and 172.16.0.0/12. Capture a post-change snapshot. Diff pre and post — flag any BGP neighbor that went down, any route that disappeared unexpectedly from CORE1 or RR1, any interface-counter anomaly. Confirm the three bogon prefixes would now be rejected by OBSERVER injecting a test announcement.

## What You'll Build

- 4-device multi-vendor topology (Cisco IOL + Juniper cRPD + Arista cEOS + Linux)
- Pre-change snapshot: BGP state, routing tables, interface counters, ACL hits
- Change application: inbound prefix-list adding bogon filtering on the EDGE1 ↔ TRANSIT-A eBGP session
- Post-change snapshot with automated diff
- Observer-injected test to confirm filter behavior

## Concepts Demonstrated

- **The pre/post snapshot pattern** — the core change-validation workflow
- **Agent-first with SSH escape hatch** — agent captures state and applies the change in parallel; SSH in to verify by hand
- **Multi-vendor change validation in one topology** — same prompt handles Cisco, Juniper, Arista syntax differences
- **Observer AS pattern** — validate what the outside world sees, not just what your devices report
- **Rollback confidence building** — if the diff surfaces a regression, the change stays in the lab and gets fixed there

## Vendors Used

- Cisco IOL (edge + core routers)
- Juniper cRPD (transit)
- Arista cEOS (route reflector)
- Linux with Scapy + tcpdump (observer endpoint)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- Swap the change to an OSPF area-ID edit on EDGE1 and CORE1 — capture routing-table deltas
- Add a 4th router and test an iBGP route-reflector-cluster-ID change
- Inject 5% packet loss on the EDGE1 ↔ TRANSIT-A link with `tc netem` during the change to test resilience
- Re-apply the change as a BGP community-based filter instead of a prefix-list — compare behavioral equivalence
- Test the rollback: revert the change, snapshot, diff — confirm you're back at the pre-change baseline

## Why This Matters

Gartner pins network-outage cost at $5,600 per minute (~$336K/hour). Uptime Institute attributes 68% of outages to configuration errors. EMA's 2026 survey found 58% of network teams use a modeling tool or digital twin for pre-change validation — but traditional sandbox builds take 2-4 weeks, so most teams skip the step and ship to prod on hope. The pre/post snapshot workflow below compresses that build from weeks to minutes. Run it once; it becomes the template for every high-risk change.

## Related Resources

- [NetPilot Network Change Validation](https://www.netpilot.io/network-change-validation) — dedicated landing page for this workflow
- [Blog: Best Network Change Validation Tools in 2026](https://www.netpilot.io/blog/best-network-change-validation-tools-2026) — tier-ranked comparison
- [Blog: Stop Testing Network Changes in Production](https://www.netpilot.io/blog/network-change-validation-sandbox) — short tactical guide
- [NetPilot Network Digital Twin](https://www.netpilot.io/network-digital-twin) — umbrella platform
- [Related prompt: BGP Policy Change Validation](bgp-policy-change.md) — deeper dive on BGP-specific policy blast radius
- [Related prompt: OSPF Area Redesign Migration](ospf-area-redesign.md) — OSPF-specific change pattern
- [Related prompt: Firewall Rule Deployment Test](firewall-rule-deployment.md) — ACL / security-policy variant

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
