# Network-as-Code with Ansible

Build a multi-vendor lab that's perfect for testing Ansible playbooks against real device CLIs — the staging environment every NetOps automation team needs.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a multi-vendor lab perfect for Ansible playbook development and testing: 2 Cisco IOL routers (R1, R2), 2 Juniper cRPD routers (R3, R4), and 2 Arista cEOS switches (S1, S2). Connect them in a partial mesh: R1↔R2, R3↔R4, S1↔S2, plus R2↔R3 and R4↔S1 to enable end-to-end paths. All devices need a management IP reachable on a flat 192.168.100.0/24 management network. Configure SSH access on all devices with username "admin" and verify each platform exposes its API: NETCONF on Juniper, RESTCONF on Cisco IOL, eAPI on Arista. Set up loopbacks (1.1.1.1/32 to 6.6.6.6/32) so an Ansible playbook can iterate over all 6 devices and verify reachability across vendor boundaries.

## What You'll Build

- 6 devices across 3 vendors (Cisco, Juniper, Arista)
- Partial-mesh topology with end-to-end reachability paths
- Flat management network for Ansible inventory
- All standard automation interfaces enabled (SSH + vendor APIs)
- Loopback addressing pattern that's easy to template

## Concepts Demonstrated

- Multi-vendor automation testing in one environment
- Why Ansible's network modules differ per vendor (collection-specific modules)
- The difference between SSH-screen-scraping (`network_cli`) and structured APIs (NETCONF/RESTCONF/eAPI)
- Idempotent network configuration patterns
- Inventory design for heterogeneous fleets

## Vendors Used

- Cisco IOL (2 routers)
- Juniper cRPD (2 routers)
- Arista cEOS (2 switches)

## Difficulty

⭐⭐⭐ Advanced

## Suggested Ansible Playbook Patterns

Once your lab is up, try Ansible playbooks like:

- **Inventory generation** — auto-build inventory from device lookups
- **Backup/restore** — pull running configs from all 6 devices in parallel
- **Compliance check** — verify standard banner, NTP, SNMP across vendors
- **Configuration push** — deploy a common access-list across all 6 devices
- **Drift detection** — compare desired-state YAML against running config

Reference Ansible collections:
- `cisco.ios` for Cisco IOL
- `junipernetworks.junos` for Juniper cRPD
- `arista.eos` for Arista cEOS

## Variations to Try

- "Add a Nokia SR Linux router (4-vendor test)"
- "Add a Palo Alto firewall and test policy push with `paloaltonetworks.panos`"
- "Add a NetBox instance as the source of truth and demo Nornir + NetBox integration"
- "Replace Ansible with Nornir in the test design"

## Why This Matters

Network automation in 2026 is non-negotiable for any team operating more than ~50 devices. The hardest part of automation isn't writing playbooks — it's having a safe place to test them. This lab gives you exactly that.

## Related Resources

- [NetPilot blog: Python Network Automation Lab](https://netpilot.io/blog/python-network-automation-lab)
- [NetPilot blog: AI Tools for Network Engineers](https://netpilot.io/blog/ai-tools-for-network-engineers)
- [Ansible Network Collections Index](https://docs.ansible.com/ansible/latest/collections/index_module.html)
- [Related: BGP eBGP Three-AS Multi-Vendor](../routing/bgp-ebgp-three-as.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
