# BGP Policy Change — Validation Lab

Test a proposed BGP inbound/outbound policy change against a digital twin of production before deploying. The highest-blast-radius change type in any network — prefix filters, AS-path manipulation, MED, LOCAL_PREF.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a digital twin of a multi-homed enterprise edge for BGP policy validation. Two Cisco IOL edge routers (EDGE1, EDGE2) in AS 65000. Each has an eBGP session to a different transit provider: EDGE1 ↔ TRANSIT-A (AS 65100, Cisco IOL), EDGE2 ↔ TRANSIT-B (AS 65200, Cisco IOL). Inside AS 65000, iBGP full-mesh between EDGE1, EDGE2, and an internal core router CORE1 (Cisco IOL). Advertise 100.64.0.0/20 (customer space) to both transits. Pre-load existing policies: LOCAL_PREF 200 on routes from TRANSIT-A, LOCAL_PREF 100 from TRANSIT-B (prefer TRANSIT-A for outbound). Now test this proposed change: add AS-path prepending (3x) to TRANSIT-B on the 100.64.0.0/20 advertisement to make inbound traffic prefer TRANSIT-A. Verify (1) outbound preference still works, (2) external AS 65300 (an observer) sees AS 65000 with prepends via TRANSIT-B, (3) the internal iBGP routes match expectations, (4) no unintended leaks.

## What You'll Build

- 5 Cisco IOL routers (2 edge + 1 core + 2 simulated transits)
- 1 observer AS to validate advertisement shape
- Pre-loaded "production" BGP policies
- Proposed change applied in lab only
- Before/after comparison

## Concepts Demonstrated

- BGP policy blast radius — why changes feel scary
- AS-path prepending for inbound traffic engineering
- LOCAL_PREF for outbound traffic engineering
- Why you can't test BGP policies in production safely
- Observer AS pattern — validate what the outside world sees

## Vendors Used

- Cisco IOL (all 5 routers)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Replace AS-path prepending with BGP Community signaling to transits that support local-pref communities"
- "Add MED manipulation for inter-AS traffic engineering"
- "Test a prefix filter change — add a route-map denying a /24 and verify no unintended impact"
- "Simulate TRANSIT-A failure and verify failover behavior"

## Why This Matters

BGP is the internet's routing protocol, and policy mistakes have caused famous outages (Facebook 2021, Rogers 2022, Cloudflare incidents). Every sane network runs BGP changes through a digital twin first. This lab is that digital twin.

## Related Resources

- [NetPilot Network Digital Twin](https://netpilot.io/network-digital-twin)
- [Related: Firewall Rule Deployment Test](firewall-rule-deployment.md)
- [Related: eBGP Three-AS Multi-Vendor](../routing/bgp-ebgp-three-as.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
