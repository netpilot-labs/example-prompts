# Multi-Tenant VRFs with EVPN

An EVPN-VXLAN fabric with three isolated tenant VRFs — the enterprise multi-tenancy pattern for shared-infrastructure data centers, MSPs, and cloud providers.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a multi-tenant EVPN-VXLAN fabric with 2 Arista cEOS spines and 3 Arista cEOS leaves. eBGP underlay (spines AS 65000, leaves AS 65001-65003). BGP EVPN overlay. Configure three isolated tenant VRFs with unique route-targets: TENANT-A (RT 100:100, VNI 50100), TENANT-B (RT 200:200, VNI 50200), TENANT-C (RT 300:300, VNI 50300). Each tenant has two L2 VNIs: TENANT-A uses VNI 10101 (192.168.11.0/24) and VNI 10102 (192.168.12.0/24), TENANT-B uses VNI 10201 (192.168.21.0/24) and VNI 10202 (192.168.22.0/24), TENANT-C uses VNI 10301 (192.168.31.0/24). Use Symmetric IRB in each tenant VRF. Place hosts on different leaves for each tenant. Verify (1) hosts in the same tenant reach each other across VLANs and leaves, (2) hosts in DIFFERENT tenants CANNOT reach each other (strict isolation), (3) Type-5 route announcements use correct RTs per tenant, (4) selective route leaking between TENANT-A and TENANT-B via shared services VRF can be added later.

## What You'll Build

- 5-device EVPN-VXLAN fabric (2 spine + 3 leaves)
- 3 isolated tenant VRFs
- 5 total L2 VNIs across tenants
- 3 L3 VNIs (one per tenant)
- 5+ hosts distributed across tenants

## Concepts Demonstrated

- Multi-tenancy as the #1 reason to deploy EVPN-VXLAN (vs pure L3 Clos)
- Route-target design for tenant isolation
- Why strict RT separation prevents cross-tenant leakage
- When to add shared-services VRFs (DNS, DHCP, SIEM shared across tenants)
- Comparison with traditional VRF-Lite + MPLS approach

## Vendors Used

- Arista cEOS (all 5 devices)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Add a SHARED-SERVICES VRF (RT 999:999) providing DNS to all tenants"
- "Leak specific routes between TENANT-A and TENANT-B for business partnerships"
- "Add 2 Cisco Nexus leaves to test multi-vendor tenant VRF implementation"
- "Scale to 10 tenants to observe RT and VNI management complexity"

## Related Resources

- [NetPilot blog: EVPN-VXLAN Data Center Fabric Guide](https://www.netpilot.io/blog/evpn-vxlan-data-center-guide)
- [Related: Leaf-Spine EVPN-VXLAN Symmetric IRB](leaf-spine-evpn-vxlan-symmetric-irb.md)
- [Related: Cisco + Arista EVPN-VXLAN Interop](../multi-vendor/cisco-arista-evpn-vxlan-interop.md)
- [RFC 7432 — BGP MPLS-Based Ethernet VPN](https://datatracker.ietf.org/doc/html/rfc7432)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
