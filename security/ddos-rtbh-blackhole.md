# DDoS Blackhole with Remote-Triggered Black Hole (RTBH)

A classic DDoS mitigation pattern: advertise a /32 for the attacked host with a special community, and edge routers drop all traffic to it — stopping the attack at the ingress instead of the target.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build an RTBH DDoS mitigation lab with 4 Cisco IOL routers in AS 65000. EDGE1 and EDGE2 are dual-homed edge routers with eBGP sessions to upstream transits (AS 65100 and AS 65200, each a single Cisco IOL). CORE1 is an internal iBGP router, RTBH-TRIGGER is a specialized iBGP router that injects blackhole routes. All internal routers run OSPF as IGP and iBGP full-mesh. Configure static route 192.0.2.1 → Null0 on EDGE1 and EDGE2 (the blackhole next-hop). Set up an inbound route-map on both edges that, when a route has BGP community 65000:666, rewrites the next-hop to 192.0.2.1 (sending traffic to Null0). Now simulate: an internal host at 10.10.10.100 is under DDoS. RTBH-TRIGGER announces 10.10.10.100/32 with community 65000:666. Verify (1) the blackhole route propagates to both edges via iBGP, (2) both edges install a route for 10.10.10.100/32 via Null0, (3) traffic from the transits to 10.10.10.100 is dropped at ingress, (4) other prefixes for 10.10.10.0/24 continue to work normally.

## What You'll Build

- 4 Cisco IOL routers inside AS 65000
- 2 Cisco IOL upstream transits
- Static blackhole next-hop (192.0.2.1/32 → Null0)
- Community-based policy for selective blackholing
- iBGP full-mesh with dedicated trigger router

## Concepts Demonstrated

- Remote-Triggered Black Hole (RTBH) — classic DDoS mitigation (RFC 5635)
- Why you drop at ingress (protect the core, save the target)
- BGP community tagging for policy signaling
- Source-based RTBH vs destination-based RTBH
- Where RTBH helps and where it fails (volumetric attacks only)

## Vendors Used

- Cisco IOL (all 6 routers)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Add source-based RTBH using uRPF to drop traffic FROM specific attacker IPs"
- "Integrate with Flowspec (RFC 8955) for more granular filtering"
- "Add multiple mitigation tiers: rate-limit before blackhole, scrub before drop"
- "Announce the blackhole to upstream transits that support RFC 7999 (community 65535:666)"

## Why This Matters

DDoS mitigation is a mandatory capability for every service provider and many enterprises. RTBH is the simplest, most widely-deployed pattern — every NOC engineer should know it. This lab is also a common CCIE SP and JNCIE-SP exam topic.

## Related Resources

- [RFC 5635 — Remote Triggered Black Hole Filtering with Unicast Reverse Path Forwarding](https://datatracker.ietf.org/doc/html/rfc5635)
- [RFC 7999 — BLACKHOLE Community](https://datatracker.ietf.org/doc/html/rfc7999)
- [Related: BGP Policy Change Validation](../change-validation/bgp-policy-change.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
