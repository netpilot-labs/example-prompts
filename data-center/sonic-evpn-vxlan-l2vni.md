# SONiC EVPN-VXLAN with an L2 VNI: Built and Verified Step by Step

Two SONiC leaves and a spine with a BGP EVPN overlay, one VLAN stretched over VXLAN, and the verification output after every step.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io/?vendor=sonic), or [open it with the prompt filled in](https://app.netpilot.io/?prompt=Build%20two%20SONiC%20leaves%20and%20one%20SONiC%20spine.%20eBGP%20underlay%20on%20point-to-point%20links%2C%20spine%20AS%2065000%2C%20leaf1%20AS%2065001%2C%20leaf2%20AS%2065002%2C%20loopbacks%2010.1.1.1%20and%2010.1.1.2%20on%20the%20leaves.%20BGP%20EVPN%20overlay%20between%20the%20leaves%20through%20the%20spine.%20On%20each%20leaf%20create%20VLAN%20100%2C%20map%20it%20to%20VNI%2010100%20and%20attach%20one%20Linux%20host%20in%20VLAN%20100.%20After%20each%20step%20run%20the%20verification%20command%20and%20show%20me%20the%20output.):

> Build two SONiC leaves and one SONiC spine. eBGP underlay on point-to-point links, spine AS 65000, leaf1 AS 65001, leaf2 AS 65002, loopbacks 10.1.1.1 and 10.1.1.2 on the leaves. BGP EVPN overlay between the leaves through the spine. On each leaf create VLAN 100, map it to VNI 10100 and attach one Linux host in VLAN 100. After each step run the verification command and show me the output.

## What You'll Build

- One SONiC spine in AS 65000 and two leaves in AS 65001 and AS 65002
- An eBGP underlay on point-to-point links, leaf loopbacks 10.1.1.1 and 10.1.1.2 as the VTEPs
- A BGP EVPN overlay through the spine
- VLAN 100 on VNI 10100 with one Linux host on each leaf

## What Came Back

On our run the agent reported each layer before the next: the underlay routes to the other leaf's loopback, the EVPN sessions on the spine, the VNI map with the remote VTEP, then the hosts. host1 and host2 pinged each other 5 of 5, each leaf listed the other host's MAC as remote in `show evpn mac vni 10100`, and a capture on the spine showed the ping inside VXLAN with VNI 10100.

## Concepts Demonstrated

- The order an EVPN fabric comes up in: links, underlay, overlay, VNI, hosts
- SONiC's VXLAN objects: a VTEP on the loopback, an EVPN NVO, and a VLAN to VNI map
- Type-2 MAC routes and head-end replication between two VTEPs
- Why EVPN sessions reset when the address family is turned on

## Vendors Used

- SONiC (`docker-sonic-vs`), preloaded on every lab VM
- Linux hosts

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Add an anycast gateway for VLAN 100 in a VRF with an L3 VNI"
- "Replace leaf2 with an Arista cEOS leaf and keep the same VNI"
- "Add a second VLAN on VNI 10200 and show both MAC tables"

## Related Resources

- [NetPilot: Learn VXLAN EVPN on SONiC](https://www.netpilot.io/solutions/learn-vxlan-evpn-sonic)
- [RFC 7432: BGP MPLS-based Ethernet VPN](https://www.rfc-editor.org/rfc/rfc7432) and [RFC 8365: EVPN as a network virtualization overlay](https://www.rfc-editor.org/rfc/rfc8365)
- [SONiC Leaf-Spine with eBGP and ECMP](sonic-bgp-leaf-spine-ecmp.md)
- [Leaf-Spine EVPN-VXLAN with Symmetric IRB](leaf-spine-evpn-vxlan-symmetric-irb.md)
- [Cisco + Arista EVPN-VXLAN Interop](../multi-vendor/cisco-arista-evpn-vxlan-interop.md)

## Run it yourself

The tested containerlab files for this lab, configured at deploy: [network-labs/sonic/evpn-l2vni](https://github.com/netpilot-labs/network-labs/tree/main/sonic/evpn-l2vni).

## Try It

[**Open in NetPilot →**](https://app.netpilot.io/?prompt=Build%20two%20SONiC%20leaves%20and%20one%20SONiC%20spine.%20eBGP%20underlay%20on%20point-to-point%20links%2C%20spine%20AS%2065000%2C%20leaf1%20AS%2065001%2C%20leaf2%20AS%2065002%2C%20loopbacks%2010.1.1.1%20and%2010.1.1.2%20on%20the%20leaves.%20BGP%20EVPN%20overlay%20between%20the%20leaves%20through%20the%20spine.%20On%20each%20leaf%20create%20VLAN%20100%2C%20map%20it%20to%20VNI%2010100%20and%20attach%20one%20Linux%20host%20in%20VLAN%20100.%20After%20each%20step%20run%20the%20verification%20command%20and%20show%20me%20the%20output.)
