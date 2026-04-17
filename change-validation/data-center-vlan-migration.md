# Data Center VLAN Migration

Migrate workloads from a legacy VLAN-based access layer to a modern EVPN-VXLAN fabric with zero downtime — the classic data center modernization scenario.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a data center migration validation lab. Legacy side: 2 Arista cEOS access switches (ACCESS-1, ACCESS-2) in a traditional MLAG pair, providing VLAN 100 (192.168.100.0/24) to 4 hosts. They uplink to a collapsed core switch CORE1 (Arista cEOS) that provides the SVI gateway (192.168.100.1) for VLAN 100. Modern side: 2 Arista cEOS spines + 2 Arista cEOS leaves in a new leaf-spine EVPN-VXLAN fabric. VLAN 100 is stretched to the new fabric as VNI 10100 with distributed anycast gateway 192.168.100.1 on the new leaves. Interconnect: a transit link between CORE1 and one of the new leaves, with both sides bridging VLAN 100. Configure the new leaves to announce the same gateway IP as anycast. Now simulate a host migration: move host2 from ACCESS-1 to the new leaf1 (same subnet 192.168.100.0/24, same VLAN 100). Verify (1) the host retains the same IP, (2) traffic to/from it is uninterrupted, (3) the new leaves take over gateway duty seamlessly, (4) legacy switches can be decommissioned once all hosts are migrated.

## What You'll Build

- 7-device mixed-topology (legacy + modern fabric)
- 4 hosts across legacy and modern segments
- Bridge between the two worlds
- Live migration demonstration

## Concepts Demonstrated

- L2 extension strategy between legacy and greenfield fabrics
- Anycast gateway migration (same IP, new owner)
- MAC mobility and gratuitous ARP behavior
- Why you can't just "cut over" — phased migration patterns
- Eventually decommissioning legacy hardware without downtime

## Vendors Used

- Arista cEOS (all 7 devices)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Replace legacy with Cisco IOS legacy switches to test multi-vendor migration"
- "Add a firewall between legacy and modern to test policy preservation"
- "Migrate multiple VLANs simultaneously (VLAN 100, 200, 300) to test complexity scaling"
- "Add an L2 loop-prevention mechanism during transit (storm control, STP)"

## Why This Matters

Every enterprise doing data center modernization faces this exact scenario: hundreds or thousands of VMs/workloads on legacy VLANs, plus a new EVPN-VXLAN fabric waiting to receive them. The migration can't cause downtime. This lab is the rehearsal.

## Related Resources

- [Related: Leaf-Spine EVPN-VXLAN with Symmetric IRB](../data-center/leaf-spine-evpn-vxlan-symmetric-irb.md)
- [Related: Vendor Migration Cisco to Arista](vendor-migration-cisco-to-arista.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
