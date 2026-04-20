# Firewall DMZ Zones with Fortinet

The same 3-zone firewall architecture as our [Palo Alto lab](firewall-dmz-zones-palo-alto.md), implemented on Fortinet FortiGate — useful for learning vendor syntax differences and for Fortinet-specific certification prep (NSE).

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a Fortinet FortiGate firewall lab with 3 zones: internal-zone (Trust, 192.168.1.0/24), dmz-zone (DMZ, 192.168.100.0/24), and wan-zone (Untrust, 203.0.113.0/24 simulated by a Cisco IOL upstream router). Place a web server and mail server in DMZ. Configure policies: (1) internal-zone → dmz-zone allow HTTP, HTTPS, SSH, SMTP, (2) wan-zone → dmz-zone destination NAT (VIPs) for HTTP/HTTPS/SMTP to servers in DMZ, (3) dmz-zone → wan-zone allow DNS + NTP + software-update FortiGuard services, (4) internal-zone → wan-zone allow outbound with source NAT, default deny all else. Verify traffic flows, VIP NAT translations, and blocked return paths.

## What You'll Build

- 1 Fortinet FortiGate firewall
- 1 Cisco IOL upstream (simulating internet)
- 3 zones with explicit policy control
- VIP (Virtual IP) destination NAT for inbound services
- Source NAT for outbound

## Concepts Demonstrated

- FortiGate zone-based security model
- Policy order (Fortinet evaluates top-down)
- VIP vs central NAT (Fortinet-specific terms)
- FortiGuard service policies (unique to Fortinet)
- Side-by-side comparison with Palo Alto zone model

## Vendors Used

- Fortinet FortiGate (firewall)
- Cisco IOL (upstream)

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Compare by deploying the [Palo Alto version](firewall-dmz-zones-palo-alto.md) side-by-side in the same topology"
- "Add SSL inspection to outbound traffic"
- "Add a FortiGate HA pair with FGCP (Fortinet Cluster Protocol)"
- "Layer a FortiAnalyzer for centralized logging"

## Fortinet vs Palo Alto

A key decision for most enterprises. Both use zones, but syntax, default behaviors, and ecosystem integrations differ significantly. Running the same lab on both is the fastest way to understand the tradeoffs.

## Related Resources

- [NetPilot blog: Firewall Lab Palo Alto + Fortinet](https://www.netpilot.io/blog/firewall-lab-palo-alto-fortinet)
- [Related: Firewall DMZ Zones with Palo Alto](firewall-dmz-zones-palo-alto.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
