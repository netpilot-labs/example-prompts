# DMVPN Hub-and-Spoke

Dynamic Multipoint VPN with a hub and multiple spokes — Cisco's flagship enterprise WAN architecture, still widely deployed even in the SD-WAN era.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a DMVPN Phase 3 hub-and-spoke lab with Cisco IOL. 1 hub router (HUB) with public IP 198.51.100.1 and internal LAN 192.168.1.0/24. 3 spoke routers (SPOKE1, SPOKE2, SPOKE3) with public IPs 203.0.113.1, 203.0.113.2, 203.0.113.3 and internal LANs 192.168.10.0/24, 192.168.20.0/24, 192.168.30.0/24. All connect via a simulated "internet" (one additional Cisco IOL acting as transit). Configure mGRE tunnels on all devices using tunnel IP range 172.16.0.0/24 (HUB = .1, SPOKE1 = .10, SPOKE2 = .20, SPOKE3 = .30). NHRP with NHS = hub, registration intervals standard. IPsec protection on the mGRE tunnels using a shared pre-shared key. Run EIGRP over the tunnels as the overlay IGP. Verify (1) all spokes register with the hub via NHRP, (2) EIGRP neighbor adjacencies form hub-to-spoke, (3) spoke-to-spoke traffic initially transits the hub then switches to direct spoke-to-spoke (Phase 3 behavior), (4) IPsec tunnels are established on demand.

## What You'll Build

- 5 Cisco IOL routers (1 hub + 3 spokes + 1 transit)
- mGRE tunnels over simulated public internet
- NHRP for dynamic spoke registration
- IPsec-protected overlay
- EIGRP routing over the tunnels

## Concepts Demonstrated

- DMVPN Phases 1, 2, 3 — and why Phase 3 is the standard
- NHRP (Next Hop Resolution Protocol) — dynamic spoke discovery
- mGRE vs point-to-point GRE
- Why IPsec protects the GRE tunnel (not the other way around)
- When DMVPN vs SD-WAN is the right choice

## Vendors Used

- Cisco IOL (all 5 routers) — DMVPN is a Cisco-proprietary architecture

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Scale to 10 spokes to observe NHRP table growth"
- "Replace EIGRP with OSPF over the tunnels (network type broadcast vs point-to-multipoint)"
- "Add a second hub for dual-hub redundancy"
- "Compare with SD-WAN (centralized overlay + dynamic path selection)"

## Why This Matters

Many enterprises still run DMVPN as their primary WAN overlay, even as SD-WAN adoption grows. For hybrid cloud connectivity, branch office WAN, and disaster recovery links, DMVPN remains cost-effective and well-understood.

## Related Resources

- [Related: IPsec VPN Site-to-Site](../security/ipsec-vpn-site-to-site.md)
- [Cisco DMVPN Design Guide](https://www.cisco.com/c/en/us/td/docs/solutions/Enterprise/WAN_and_MAN/DMVPN/dmvpn.html)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
