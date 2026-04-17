# IPv6 Dual-Stack Network

A dual-stack IPv4 + IPv6 network running both address families in parallel — the modern deployment reality, since IPv6-only is still rare outside specific environments.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a 4-router dual-stack lab with Cisco IOL. R1, R2, R3, R4 in a ring topology. Each inter-router link has both IPv4 (10.0.0.0/30 series) and IPv6 (2001:db8:0:X::/64) addressing. Each router has an IPv4 loopback (1.1.1.1/32 through 4.4.4.4/32) AND an IPv6 loopback (2001:db8:1::1/128 through 2001:db8:4::1/128). Run OSPFv2 for IPv4 and OSPFv3 for IPv6 in parallel — both in area 0. Place a dual-stack host on R1 (IPv4 192.168.1.10, IPv6 2001:db8:10::10) and another on R3 (IPv4 192.168.3.10, IPv6 2001:db8:30::10). Verify that OSPFv2 neighbor adjacencies and OSPFv3 neighbor adjacencies form independently, that both protocols install routes in their respective RIBs, and that host-to-host reachability works over both IPv4 and IPv6.

## What You'll Build

- 4 Cisco IOL routers in a ring
- Full dual-stack (IPv4 + IPv6) on every link
- OSPFv2 + OSPFv3 running in parallel (two separate protocol instances)
- Dual-stack hosts
- Parallel RIBs

## Concepts Demonstrated

- Why OSPFv3 is a separate protocol (not just OSPFv2 with IPv6 address family)
- Link-local addresses (fe80::/10) and their role in IPv6 neighbor discovery
- Independent convergence — IPv4 failure does not automatically affect IPv6
- Why dual-stack beats tunneling (6in4, 6to4, ISATAP) for production
- Operational complexity of running two address families

## Vendors Used

- Cisco IOL (all 4 routers)

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Add BGP with IPv4 + IPv6 address families (multi-protocol BGP)"
- "Configure address-family-specific routing policies to prefer IPv6 over IPv4"
- "Add NAT64 to enable IPv6-only clients to reach IPv4-only destinations"
- "Migrate to IPv6-only by removing IPv4 and observing what breaks"

## Related Resources

- [RFC 5340 — OSPF for IPv6](https://datatracker.ietf.org/doc/html/rfc5340)
- [RFC 8200 — Internet Protocol, Version 6 (IPv6) Specification](https://datatracker.ietf.org/doc/html/rfc8200)
- [Related: OSPF Multi-Area with ABR](ospf-multi-area-with-abr.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
