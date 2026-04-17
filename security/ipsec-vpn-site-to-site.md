# IPsec VPN — Site-to-Site

A classic two-site IPsec VPN lab over an untrusted transit — fundamental for any network engineer working on branch connectivity or cloud interconnect.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a site-to-site IPsec VPN lab. Site A: Cisco IOL router ASA1 (public IP 198.51.100.1) with internal LAN 192.168.10.0/24. Site B: Cisco IOL router ASA2 (public IP 203.0.113.1) with internal LAN 192.168.20.0/24. Between them, one Cisco IOL router acting as the "internet" transit (simulating an untrusted public network). Configure an IKEv2 IPsec tunnel between ASA1 and ASA2 with AES-256 encryption and SHA-256 integrity. Use pre-shared key authentication. Define crypto ACL for interesting traffic (LAN A to LAN B). Place one host in each LAN. Verify tunnel establishment, ESP packet encryption between public IPs, and end-to-end reachability between 192.168.10.x and 192.168.20.x across the tunnel.

## What You'll Build

- 3 Cisco IOL routers (2 VPN endpoints + 1 transit)
- 2 hosts (one per site)
- IKEv2 + IPsec ESP tunnel
- Crypto ACL for interesting traffic
- Pre-shared key authentication

## Concepts Demonstrated

- IKE Phase 1 (security association) vs Phase 2 (crypto SA)
- AES-256, SHA-256, DH group selection
- ESP (Encapsulating Security Payload) tunnel mode
- Crypto ACL scope ("what traffic to encrypt")
- Why NAT-T (NAT traversal) matters when endpoints are behind NAT
- Split tunnel vs full tunnel tradeoffs

## Vendors Used

- Cisco IOL (all 3 routers)

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Replace IKEv2 with IKEv1 to compare the handshake phases"
- "Add a third site for a hub-and-spoke VPN topology (DMVPN alternative)"
- "Replace one endpoint with Juniper cRPD to test multi-vendor IPsec interop"
- "Add GRE-over-IPsec to support dynamic routing across the tunnel"

## Related Resources

- [RFC 7296 — Internet Key Exchange Protocol Version 2 (IKEv2)](https://datatracker.ietf.org/doc/html/rfc7296)
- [RFC 4303 — IP Encapsulating Security Payload (ESP)](https://datatracker.ietf.org/doc/html/rfc4303)
- [Related: Firewall DMZ Zones (Palo Alto)](firewall-dmz-zones-palo-alto.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
