# Zero-Trust Microsegmentation

A zero-trust network architecture where every workload is its own segment, all traffic is policy-enforced, and there's no implicit "internal" trust.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a zero-trust microsegmented network with a Palo Alto PAN-OS firewall as the central enforcement point. Create 6 isolated VLANs representing different workload tiers: web-tier (192.168.10.0/24), app-tier (192.168.20.0/24), db-tier (192.168.30.0/24), management (192.168.40.0/24), dev-environment (192.168.50.0/24), and finance (192.168.60.0/24). Each VLAN is its own security zone — NO inter-VLAN routing without firewall policy. Configure policies that ONLY allow: web→app on port 8080, app→db on port 5432, management→all on SSH/22, deny everything else by default. Place one host per VLAN. Verify that web can reach app on 8080 but NOT on any other port, app can reach db on 5432 but web CANNOT reach db directly, and that lateral movement attempts (e.g., web→finance) are blocked.

## What You'll Build

- 1 Palo Alto PAN-OS firewall (zero-trust enforcement point)
- 6 isolated workload zones (each with one host)
- Explicit allow policies for only required flows
- Default-deny enforcement for everything else
- Lateral movement prevention

## Concepts Demonstrated

- Zero-trust principles: never trust, always verify — no implicit internal trust
- Microsegmentation vs traditional VLAN segmentation (the firewall is the gateway, not a routed switch)
- East-west traffic policy enforcement (not just north-south)
- Lateral movement prevention — a compromised web server cannot pivot to db or finance
- Policy-as-code mindset — every flow is explicit
- Compliance use case (PCI-DSS scope reduction, HIPAA isolation)

## Vendors Used

- Palo Alto PAN-OS (could swap for Fortinet FortiGate)
- Optional: Cisco IOL or Arista cEOS as L2 access switches

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Add a SIEM/syslog collector to the management zone and verify all firewall logs flow there"
- "Replace Palo Alto with Fortinet FortiGate to compare microsegmentation policy syntax"
- "Add a jump host pattern for management access with bastion enforcement"
- "Add identity-based policies using User-ID (Palo Alto) for user-aware segmentation"

## Why This Matters in 2026

Zero-trust is now a federal mandate (US Executive Order 14028) and an enterprise security baseline. NIST SP 800-207 codifies the principles. CCNP Security 2026 includes zero-trust architecture objectives.

## Related Resources

- [NetPilot blog: Zero-Trust Microsegmentation Enterprise Guide](https://netpilot.io/blog/zero-trust-microsegmentation-guide)
- [NIST SP 800-207 — Zero Trust Architecture](https://csrc.nist.gov/publications/detail/sp/800-207/final)
- [Related: Firewall DMZ Zones with Palo Alto](firewall-dmz-zones-palo-alto.md)
- [Related: Firewall Rule Deployment Test](../change-validation/firewall-rule-deployment.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
