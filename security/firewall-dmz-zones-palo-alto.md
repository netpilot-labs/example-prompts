# Firewall DMZ Zones with Palo Alto

A classic 3-zone firewall topology (Trust / Untrust / DMZ) using Palo Alto PAN-OS — the foundational design pattern for any perimeter security architecture.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a Palo Alto PAN-OS firewall lab with 3 security zones: Trust (internal LAN, 192.168.1.0/24), Untrust (internet edge, simulated by an external Cisco IOL router with public IP space 203.0.113.0/24), and DMZ (web/email server segment, 192.168.100.0/24). Place a web server (HTTP/HTTPS) and a mail server (SMTP/IMAP) in DMZ. Configure these security policies: (1) Trust → DMZ allow web and mail services. (2) Untrust → DMZ allow HTTP, HTTPS, SMTP only — destination NAT from public IPs to DMZ private IPs. (3) DMZ → Untrust allow outbound DNS and software updates. (4) Trust → Untrust allow with NAT, default deny everything else. Verify policy hits, NAT translation, and that the implicit deny blocks unauthorized flows.

## What You'll Build

- 1 Palo Alto PAN-OS firewall (the perimeter)
- 1 Cisco IOL router (simulating Untrust/internet)
- 2 servers in DMZ (web + mail)
- 1 internal client in Trust
- 3 security zones with explicit policies
- Both source and destination NAT

## Concepts Demonstrated

- Zone-based firewall architecture (vs traditional ACL approach)
- DMZ design — isolating exposed services from internal trust boundary
- Asymmetric trust model (Trust > DMZ > Untrust)
- Source NAT (outbound) vs Destination NAT (inbound)
- Implicit deny + explicit allow security model
- App-ID and service-based policies (Palo Alto specific)

## Vendors Used

- Palo Alto PAN-OS (firewall)
- Cisco IOL (Untrust router)

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Add a Fortinet FortiGate as a second firewall in HA active/passive pair"
- "Replace Palo Alto with Fortinet FortiGate to compare zone configuration syntax"
- "Add an IPsec VPN tunnel from Untrust to a remote site"
- "Add a fourth zone for IoT devices with strict isolation"

## Related Resources

- [NetPilot blog: Firewall Lab Palo Alto + Fortinet](https://www.netpilot.io/blog/firewall-lab-palo-alto-fortinet)
- [Related: Multi-Vendor Firewall Comparison](#) (coming soon)
- [Palo Alto Security Zones Best Practices](https://docs.paloaltonetworks.com/)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
