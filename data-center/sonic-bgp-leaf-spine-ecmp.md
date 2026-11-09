# SONiC Leaf-Spine with eBGP and ECMP

A two-spine, two-leaf SONiC fabric where each leaf reaches the other leaf's LAN over two equal-cost paths, proven from the hosts.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io/?vendor=sonic), or [open it with the prompt filled in](https://app.netpilot.io/?prompt=Build%20a%20SONiC%20leaf-spine%20fabric%3A%20two%20spines%20in%20AS%2065000%2C%20leaf1%20in%20AS%2065001%20and%20leaf2%20in%20AS%2065002%2C%20eBGP%20on%20%2F31%20point-to-point%20links%2C%20and%20loopbacks%2010.255.0.11%20and%2010.255.0.12%20on%20the%20leaves.%20Put%20a%20Linux%20host%20on%20each%20leaf%2C%20host1%20at%20192.168.1.10%2F24%20behind%20leaf1%20and%20host2%20at%20192.168.2.10%2F24%20behind%20leaf2%2C%20and%20advertise%20both%20LANs.%20Deploy%20it%2C%20show%20each%20leaf%20learning%20the%20other%20LAN%20over%20two%20ECMP%20paths%2C%20and%20ping%20host2%20from%20host1.):

> Build a SONiC leaf-spine fabric: two spines in AS 65000, leaf1 in AS 65001 and leaf2 in AS 65002, eBGP on /31 point-to-point links, and loopbacks 10.255.0.11 and 10.255.0.12 on the leaves. Put a Linux host on each leaf, host1 at 192.168.1.10/24 behind leaf1 and host2 at 192.168.2.10/24 behind leaf2, and advertise both LANs. Deploy it, show each leaf learning the other LAN over two ECMP paths, and ping host2 from host1.

## What You'll Build

- Two SONiC spines in AS 65000, leaf1 in AS 65001, leaf2 in AS 65002
- eBGP on four /31 point-to-point links, each leaf to each spine
- Loopbacks 10.255.0.11 and 10.255.0.12 on the leaves
- host1 at 192.168.1.10/24 behind leaf1, host2 at 192.168.2.10/24 behind leaf2

## What Came Back

On our run all 8 eBGP session ends were Established, and `ip route show 192.168.2.0/24` on leaf1 listed two next hops, one through each spine, in the kernel as well as in FRR. host1 and host2 pinged each other 5 of 5, and a traceroute showed the flow taking one spine, picked by hash.

## Concepts Demonstrated

- The RFC 7938 pattern: one AS for the spines, one per leaf, so a route never loops back up through the other spine
- ECMP in FRR and in the Linux kernel of a SONiC switch
- Per-flow hashing: each flow takes one path, the fabric uses both

## Vendors Used

- SONiC (`docker-sonic-vs`), preloaded on every lab VM
- Linux hosts

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Shut one spine's links and measure how long host1 loses traffic to host2"
- "Add BFD on every leaf-to-spine session and measure the failover again"
- "Add a VXLAN EVPN overlay on top of this underlay"

## Related Resources

- [NetPilot blog: SONiC FRR, configure BGP](https://www.netpilot.io/blog/sonic-frr-bgp), the same fabric with failover numbers
- [RFC 7938: Use of BGP for routing in large-scale data centers](https://www.rfc-editor.org/rfc/rfc7938)
- [SONiC eBGP Lab: Two Switches on One Link](../routing/sonic-ebgp-two-switches.md)
- [SONiC EVPN-VXLAN with an L2 VNI](sonic-evpn-vxlan-l2vni.md)
- [Clos Fabric with BGP Underlay](clos-fabric-bgp-underlay.md)

## Run it yourself

The tested containerlab files for this lab, configured at deploy: [network-labs/sonic/bgp-leaf-spine](https://github.com/netpilot-labs/network-labs/tree/main/sonic/bgp-leaf-spine).

## Try It

[**Open in NetPilot →**](https://app.netpilot.io/?prompt=Build%20a%20SONiC%20leaf-spine%20fabric%3A%20two%20spines%20in%20AS%2065000%2C%20leaf1%20in%20AS%2065001%20and%20leaf2%20in%20AS%2065002%2C%20eBGP%20on%20%2F31%20point-to-point%20links%2C%20and%20loopbacks%2010.255.0.11%20and%2010.255.0.12%20on%20the%20leaves.%20Put%20a%20Linux%20host%20on%20each%20leaf%2C%20host1%20at%20192.168.1.10%2F24%20behind%20leaf1%20and%20host2%20at%20192.168.2.10%2F24%20behind%20leaf2%2C%20and%20advertise%20both%20LANs.%20Deploy%20it%2C%20show%20each%20leaf%20learning%20the%20other%20LAN%20over%20two%20ECMP%20paths%2C%20and%20ping%20host2%20from%20host1.)
