# Juniper EVPN-VXLAN Spine-Leaf on vJunos: OSPF Underlay, BGP EVPN Overlay

Build a Junos EVPN-VXLAN fabric on vJunos-router and vJunos-switch, and prove each layer on the Junos CLI.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io/?vendor=juniper), or [open it with the prompt filled in](https://app.netpilot.io/?prompt=Build%20a%20Juniper%20EVPN-VXLAN%20lab%3A%20one%20spine%20on%20vJunos-router%20and%20two%20leaves%20on%20vJunos-switch%2C%20with%20a%20Linux%20host%20on%20each%20leaf.%20Use%20OSPF%20area%200%20as%20the%20underlay%20between%20the%20loopbacks%2C%20iBGP%20in%20AS%2065000%20with%20the%20spine%20as%20route%20reflector%20for%20the%20EVPN%20overlay%2C%20and%20map%20VLAN%2010%20to%20VXLAN%20VNI%2010010%20on%20both%20leaves.%20Put%20host1%20at%20192.168.10.11%2F24%20and%20host2%20at%20192.168.10.12%2F24%20in%20VLAN%2010.%20Deploy%20it%2C%20wait%20for%20every%20node%20to%20boot%2C%20then%20prove%20it%3A%20OSPF%20neighbors%20on%20the%20spine%2C%20BGP%20EVPN%20sessions%2C%20the%20remote%20VTEP%20on%20each%20leaf%2C%20the%20host%20MACs%20in%20the%20EVPN%20database%2C%20and%20a%20ping%20from%20host1%20to%20host2.):

> Build a Juniper EVPN-VXLAN lab: one spine on vJunos-router and two leaves on vJunos-switch, with a Linux host on each leaf. Use OSPF area 0 as the underlay between the loopbacks, iBGP in AS 65000 with the spine as route reflector for the EVPN overlay, and map VLAN 10 to VXLAN VNI 10010 on both leaves. Put host1 at 192.168.10.11/24 and host2 at 192.168.10.12/24 in VLAN 10. Deploy it, wait for every node to boot, then prove it: OSPF neighbors on the spine, BGP EVPN sessions, the remote VTEP on each leaf, the host MACs in the EVPN database, and a ping from host1 to host2.

## What You'll Build

- One spine on Juniper vJunos-router and two leaves on vJunos-switch, Junos 26.2R1.7, with a Linux host on each leaf
- OSPF area 0 between the loopbacks on point-to-point fabric links
- iBGP in AS 65000 with `family evpn signaling`, the spine as route reflector
- VLAN 10 mapped to VXLAN VNI 10010 on both leaves, host1 and host2 in one /24 across the fabric
- Five checks: OSPF neighbors, BGP EVPN sessions, the remote VTEP per leaf, the host MACs in the EVPN database, a ping from host1 to host2

## Concepts Demonstrated

- The three layers of EVPN-VXLAN: OSPF reaches the loopbacks, BGP EVPN carries the MACs, VXLAN carries the frames
- EVPN type-2 (MAC and MAC/IP) and type-3 (VTEP) routes: in our run, 6 routes in `bgp.evpn.0`, 3 per leaf
- A route reflector with no EVPN instance of its own
- The vJunos boot: `device ge-0/0/0 not found` until `show chassis fpc 0` reads `Online`. In our run the fabric was usable 47 minutes after the deploy
- Proof on the data plane: 5 of 5 pings from host1 to host2 with 0% loss

## Vendors Used

- Juniper vJunos-router and vJunos-switch, your own images (BYOI), free from Juniper for non-production use
- Linux endpoints

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Shut leaf2's uplink and show the EVPN routes leave the spine and the remote VTEP disappear from leaf1"
- "Add VLAN 20 on VNI 10020 with a second host on each leaf"
- "Add IRB interfaces so hosts in VLAN 10 and VLAN 20 can route to each other"
- "Replace leaf2 with an Arista cEOS leaf and debug the EVPN interop"

## Related Resources

- [NetPilot blog: Juniper EVPN-VXLAN lab](https://www.netpilot.io/blog/juniper-evpn-vxlan-lab)
- [Video: Juniper EVPN-VXLAN Lab After vLabs: OSPF Underlay, BGP Overlay on Real Junos](https://www.youtube.com/watch?v=FILLVIDEOID)
- [NetPilot Juniper lab page](https://www.netpilot.io/juniper-lab)
- [Public lab files: 02-evpn-vxlan-spine-leaf](https://github.com/netpilot-labs/juniper-labs/tree/main/02-evpn-vxlan-spine-leaf)
- [Juniper EVPN User Guide (Junos OS)](https://www.juniper.net/documentation/us/en/software/junos/evpn-vxlan/index.html)
- [RFC 8365: A Network Virtualization Overlay Solution Using EVPN](https://datatracker.ietf.org/doc/html/rfc8365)
- [Leaf-Spine EVPN-VXLAN with Symmetric IRB](leaf-spine-evpn-vxlan-symmetric-irb.md)
- [Clos Fabric with BGP Underlay](clos-fabric-bgp-underlay.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io/?prompt=Build%20a%20Juniper%20EVPN-VXLAN%20lab%3A%20one%20spine%20on%20vJunos-router%20and%20two%20leaves%20on%20vJunos-switch%2C%20with%20a%20Linux%20host%20on%20each%20leaf.%20Use%20OSPF%20area%200%20as%20the%20underlay%20between%20the%20loopbacks%2C%20iBGP%20in%20AS%2065000%20with%20the%20spine%20as%20route%20reflector%20for%20the%20EVPN%20overlay%2C%20and%20map%20VLAN%2010%20to%20VXLAN%20VNI%2010010%20on%20both%20leaves.%20Put%20host1%20at%20192.168.10.11%2F24%20and%20host2%20at%20192.168.10.12%2F24%20in%20VLAN%2010.%20Deploy%20it%2C%20wait%20for%20every%20node%20to%20boot%2C%20then%20prove%20it%3A%20OSPF%20neighbors%20on%20the%20spine%2C%20BGP%20EVPN%20sessions%2C%20the%20remote%20VTEP%20on%20each%20leaf%2C%20the%20host%20MACs%20in%20the%20EVPN%20database%2C%20and%20a%20ping%20from%20host1%20to%20host2.)
