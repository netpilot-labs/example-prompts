# Multi-Vendor SONiC Integration Lab

A leaf-spine fabric with SONiC leaves alongside Cisco and Arista. The integration test pattern hyperscaler fabric teams use to validate SONiC against commercial vendor NOS before production deployment.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io) (SONiC requires enterprise plan with BYOI):

> Build a leaf-spine data center fabric with 2 Arista cEOS spines (spine1, spine2) and 3 leaves: 1 Cisco IOL leaf (leaf1), 1 SONiC-VS leaf (leaf2, BYOI), and 1 Arista cEOS leaf (leaf3). All leaves run eBGP with the spines for the underlay (spines in AS 65000, each leaf in AS 65001-65003). Enable BGP EVPN address family between leaves and spines. Configure VLAN 100 mapped to VNI 10100 on all three leaves with subnet 192.168.100.0/24 and distributed anycast gateway 192.168.100.1 using anycast MAC 0000.0000.1234. Place one host on each leaf. I want to verify: Type-2 EVPN route exchange works across SONiC and commercial vendors, host-to-host reachability between Cisco, SONiC, and Arista leaves, MAC mobility when a host moves between leaves, and BUM replication via ingress replication mode across all three leaves.

## What You'll Build

- 2 Arista cEOS spines
- 1 Cisco IOL leaf
- 1 SONiC-VS leaf (enterprise BYOI)
- 1 Arista cEOS leaf
- 3 hosts (one per leaf)
- eBGP underlay + BGP EVPN overlay with consistent anycast gateway

## Concepts Demonstrated

- SONiC in a real multi-vendor fabric (not SONiC-only)
- Route-target handling across SONiC explicit RT + commercial vendors' auto-RT
- BUM replication mode alignment (ingress replication on all sides)
- Anycast gateway MAC consistency across vendor boundaries
- Type-2 EVPN route interop between SONiC and commercial NOSes

## Vendors Used

- Arista cEOS (spines + 1 leaf)
- Cisco IOL (1 leaf)
- SONiC-VS (1 leaf, enterprise BYOI)

## Difficulty

⭐⭐⭐ Advanced — requires enterprise plan and SONiC familiarity

## Variations to Try

- "Add 1 Nokia SR Linux leaf for 4-vendor interop coverage"
- "Enable active-active multihoming (ESI-LAG) across SONiC and Arista for the same tenant"
- "Test BGP-LU between SONiC and Juniper on separate spines"
- "Add a firewall (Palo Alto or Fortinet) as a service node off leaf1"
- "Pin the SONiC image version to match production for candidate-version validation"

## Why This Matters

SONiC production deployments rarely exist in a SONiC-only fabric. They coexist with commercial vendor NOS at spines, aggregation, and for specific service tiers. Integration bugs live at the vendor boundary — route-target mismatches, BUM replication inconsistencies, anycast gateway MAC drift. Physical validation of this interop requires multi-vendor lab hardware, which is expensive and slow to iterate on.

Use cases:
- **Pre-deployment validation** of SONiC upgrades against the production vendor mix
- **Hyperscaler fabric engineering** iteration on multi-vendor test scenarios
- **SONiC custom feature development** testing against real commercial NOS behavior
- **CI/CD integration** for SONiC image promotion pipelines

## Related Resources

- [NetPilot blog: Multi-Vendor SONiC Labs](https://www.netpilot.io/blog/multi-vendor-sonic-integration-lab)
- [Network Research Lab hub](https://www.netpilot.io/network-research-lab)
- [Microsoft sonic-mgmt testbed](https://github.com/sonic-net/sonic-mgmt)
- [Related: Cisco + Arista EVPN-VXLAN Interop](../multi-vendor/cisco-arista-evpn-vxlan-interop.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
