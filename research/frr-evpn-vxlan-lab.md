# FRR EVPN/VXLAN Leaf-Spine Fabric

A pure-FRR EVPN/VXLAN leaf-spine fabric — the open-source equivalent of the EVPN labs you'd run on Cisco or Arista, but entirely on FRRouting containers. Used for open networking validation, SONiC fabric testing, and EVPN implementation research.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a 4-node FRR EVPN/VXLAN leaf-spine fabric: 2 FRR spines (spine1 in AS 65000, spine2 in AS 65001) and 2 FRR leaves (leaf1 in AS 65002, leaf2 in AS 65003). eBGP underlay between each leaf and both spines. BGP EVPN address family on all four routers for the overlay. Configure VNI 10100 mapped to VLAN 100 on both leaves, subnet 192.168.100.0/24, distributed anycast gateway 192.168.100.1 with anycast MAC 0000.0000.5a5a. Place one Linux host on each leaf in VLAN 100. Verify Type-2 (MAC/IP) and Type-3 (IMET) route exchange across the fabric, and confirm end-to-end host-to-host reachability.

## What You'll Build

- 2 FRR spine routers (BGP route reflectors for EVPN)
- 2 FRR leaf routers (VTEPs with EVPN overlay)
- 2 Linux hosts
- eBGP underlay + BGP EVPN overlay (same model as SONiC and Cumulus)
- Distributed anycast gateway
- Full Type-2 and Type-3 route exchange

## Concepts Demonstrated

- FRR as the open-source alternative to Cisco/Arista EVPN implementations
- Same BGP EVPN control plane as SONiC — FRR is SONiC's routing daemon
- Type-2 MAC/IP route advertisement and import across VTEPs
- Type-3 Inclusive Multicast Ethernet Tag (IMET) for BUM replication
- Distributed anycast gateway (same IP/MAC on all leaves) for L3 gateway

## Vendors Used

- FRRouting (all 4 routers — open-source, no licensing)
- Linux endpoints (2 hosts)

## Difficulty

⭐⭐⭐ Advanced — requires BGP EVPN knowledge and FRR daemon familiarity

## Variations to Try

- "Add a 3rd leaf as an FRR router and verify Type-2 routes propagate to all 3 VTEPs"
- "Mix in a Cisco IOL or Arista cEOS leaf to test multi-vendor EVPN interop with FRR"
- "Configure a Layer-3 VNI for EVPN symmetric IRB and test inter-tenant routing"
- "Introduce 10% packet loss on the leaf1-spine1 link and observe BUM replication behavior"
- "Compare FRR EVPN behavior with and without proxy-ARP enabled"

## Why This Matters

FRR is the BGP EVPN implementation inside SONiC, Cumulus Linux, and DENT — the dominant open NOS platforms in hyperscaler and modern enterprise fabrics. Testing EVPN behavior on FRR directly validates what production SONiC deployments do. This lab is also useful for:

- **Open networking engineers** migrating from proprietary Cisco/Arista EVPN to FRR/SONiC
- **SONiC developers** needing a quick EVPN interop testbed
- **Research teams** studying EVPN implementation differences across vendors

## Related Resources

- [NetPilot blog: FRRouting Cloud Labs](https://www.netpilot.io/blog/frr-cloud-lab-guide)
- [NetPilot blog: Debugging Cisco-Juniper EVPN Interop Issues](https://www.netpilot.io/blog/debugging-cisco-juniper-evpn-interop)
- [Network Research Lab hub](https://www.netpilot.io/network-research-lab)
- [FRRouting EVPN documentation](https://docs.frrouting.org/en/latest/evpn.html)
- [Related: Cisco + Arista EVPN-VXLAN Interop](../multi-vendor/cisco-arista-evpn-vxlan-interop.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
