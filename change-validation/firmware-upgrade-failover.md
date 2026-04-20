# Firmware Upgrade Failover Test

Simulate a pair of redundant routers, upgrade one, and validate that failover is clean and zero-packet-loss — the universal test before touching production pairs.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build an HSRP failover validation lab with 2 Cisco IOL routers in an active/standby pair. R1 (priority 110, preempt) and R2 (priority 100) share HSRP group 1 with virtual IP 192.168.1.1 on the LAN interface (192.168.1.0/24). Both routers uplink to a simulated WAN (single Cisco IOL "upstream" router). R1 is the active, R2 is the standby. A test host sits on the LAN, continuously pinging the default gateway (192.168.1.1). Now: simulate a firmware upgrade on R1 by reloading it. Measure (1) HSRP failover time to R2, (2) packet loss during the transition, (3) whether R1 resumes the active role after coming back (preempt behavior), (4) whether any asymmetric routing occurs during the transition.

## What You'll Build

- 2 Cisco IOL routers in HSRP active/standby
- 1 upstream router (WAN simulation)
- 1 LAN test host running continuous reachability test
- Measurable failover events

## Concepts Demonstrated

- First-hop redundancy protocols (HSRP, VRRP, GLBP)
- Preempt vs non-preempt — tradeoffs
- Measuring failover time and packet loss
- Why you test firmware upgrades in a lab pair before production
- Tracking object integration (interface/route tracking for failover trigger)

## Vendors Used

- Cisco IOL (3 routers)

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Replace HSRP with VRRP for a vendor-neutral comparison"
- "Add GLBP for load balancing instead of active/standby"
- "Add BFD for sub-second failover detection"
- "Simulate a graceful restart / NSF scenario and compare with a hard reload"
- "Layer this under a BGP peer to test session re-establishment timing"

## Why This Matters

Every firmware upgrade touches a redundant pair. The question is always the same: *will the failover work?* Testing in a lab pair — with real traffic and real timing measurements — is the difference between a 5am maintenance window and a 5am outage.

## Related Resources

- [NetPilot Network Digital Twin](https://www.netpilot.io/network-digital-twin)
- [RFC 2281 — Cisco Hot Standby Router Protocol (HSRP)](https://datatracker.ietf.org/doc/html/rfc2281)
- [Related: Vendor Migration Cisco to Arista](vendor-migration-cisco-to-arista.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
