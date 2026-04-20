# OTV-to-EVPN DCI Migration

Migrate a legacy Cisco OTV-based data center interconnect to modern EVPN-VXLAN multi-site — the urgent 2026 migration scenario driven by DCNM end-of-support.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build an OTV-to-EVPN migration validation lab. Legacy side: 2 Cisco IOL OTV edge devices (OTV-EDGE-A, OTV-EDGE-B) stretching VLAN 100 (192.168.100.0/24) between two simulated sites via OTV over a transit router (Cisco IOL). Legacy hosts in VLAN 100 on both sides. Modern side: a parallel Arista cEOS EVPN-VXLAN multi-site topology (2 leaf-spine fabrics, 2 border gateways) also stretching the same VLAN 100 / VNI 10100 between the same two sites. During migration, BOTH legacy OTV and modern EVPN-VXLAN are active simultaneously — with temporary L2 adjacency between OTV edges and EVPN leaves at each site. Verify (1) hosts retain L2 reachability during the migration overlap, (2) MAC mobility works across the legacy-modern boundary, (3) broadcast/multicast containment holds, (4) no L2 loops form, (5) the legacy OTV can be decommissioned once all hosts move to the EVPN side.

## What You'll Build

- Legacy side: 3 Cisco IOL routers (2 OTV edges + 1 transit)
- Modern side: 6 Arista cEOS devices (2 spines + 2 leaves at each of 2 sites + 2 border gateways via separate logical paths)
- L2 bridge at each site between legacy and modern
- Hosts on both sides for migration testing
- Parallel active-active DCI during overlap phase

## Concepts Demonstrated

- Why OTV was the DCI standard for a decade
- Why DCNM end-of-support (April 2026) forces the migration
- How to run both dataplanes simultaneously during migration
- MAC mobility across vendor + technology boundary
- Decommissioning OTV once hosts are moved

## Vendors Used

- Cisco IOL (legacy OTV side)
- Arista cEOS (modern EVPN-VXLAN side)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Run the migration in reverse (EVPN → OTV) to study rollback scenarios"
- "Replace OTV with legacy VPLS and migrate to EVPN-VPWS (the VPLS replacement)"
- "Test a failure mid-migration — what happens if the modern side breaks while legacy is being drained?"
- "Add per-VLAN migration sequencing to avoid big-bang cutover"

## Why This Is Urgent (2026)

Cisco DCNM reaches end-of-support April 2026. Thousands of enterprises running OTV via DCNM are being forced to migrate. The replacement — EVPN-VXLAN with NDFC or multi-vendor alternatives — requires careful rehearsal. This lab is the rehearsal.

## Related Resources

- [NetPilot blog: EVPN-VXLAN Data Center Fabric Guide](https://www.netpilot.io/blog/evpn-vxlan-data-center-guide)
- [Related: EVPN-VXLAN Multi-Site DCI](../data-center/evpn-vxlan-multi-site-dci.md)
- [Related: Vendor Migration Cisco to Arista](vendor-migration-cisco-to-arista.md)
- [Related: Data Center VLAN Migration](data-center-vlan-migration.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
