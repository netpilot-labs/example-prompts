# Juniper vJunos OSPF Lab: Two Routers and Two Hosts

Two real Junos routers in OSPF area 0 with a host on each LAN, verified end to end, and a rescue configuration saved on both.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io/?vendor=juniper), or [open it with the prompt filled in](https://app.netpilot.io/?prompt=Build%20two%20Juniper%20vJunos-routers%2C%20r1%20and%20r2%2C%20linked%20on%2010.0.12.0%2F30%20with%20loopbacks%2010.255.0.1%20and%2010.255.0.2%2C%20and%20a%20Linux%20host%20on%20each%20LAN%3A%20h1%20at%2010.1.1.10%2F24%20behind%20r1%20and%20h2%20at%2010.2.2.10%2F24%20behind%20r2.%20Run%20OSPF%20area%200%20on%20the%20link%20and%20both%20loopbacks%20and%20advertise%20both%20LANs.%20Deploy%20it%2C%20show%20the%20OSPF%20neighbor%20Full%20on%20both%20routers%2C%20and%20ping%20h2%20from%20h1.%20Then%20save%20a%20rescue%20configuration%20on%20both%20routers.):

> Build two Juniper vJunos-routers, r1 and r2, linked on 10.0.12.0/30 with loopbacks 10.255.0.1 and 10.255.0.2, and a Linux host on each LAN: h1 at 10.1.1.10/24 behind r1 and h2 at 10.2.2.10/24 behind r2. Run OSPF area 0 on the link and both loopbacks and advertise both LANs. Deploy it, show the OSPF neighbor Full on both routers, and ping h2 from h1. Then save a rescue configuration on both routers.

## What You'll Build

- Two Juniper vJunos-routers, r1 and r2, on 10.0.12.0/30
- Loopbacks 10.255.0.1 and 10.255.0.2
- h1 at 10.1.1.10/24 behind r1 and h2 at 10.2.2.10/24 behind r2
- OSPF area 0 on the link, with the LANs and loopbacks passive

## What Came Back

On our run both routers booted with the config in their startup files. `show ospf neighbor` read Full on each side, each router learned the other's LAN and loopback through OSPF, and h1 and h2 pinged each other 5 of 5. `request system configuration rescue save` returned Success on both, and the agent read the rescue file back.

## Concepts Demonstrated

- Junos OSPF with passive interfaces for the LANs and loopbacks
- Reading `show ospf neighbor` and `show route protocol ospf`
- The rescue configuration: what it is for and how to read it back
- The JNCIA-Junos topics a two-router lab covers: interfaces, routing, OSPF and configuration management

## Vendors Used

- Juniper vJunos-router (bring your own image, uploaded once)
- Linux hosts

## Difficulty

⭐ Beginner

## Variations to Try

- "Add static routes first, then OSPF, and show which one the routing table prefers"
- "Add a firewall filter with a counter on r1's link to r2 and commit it with commit confirmed 2"
- "Take r2's LAN out of OSPF and bring it back with an export policy"

## Related Resources

- [NetPilot blog: JNCIA-Junos practice lab](https://www.netpilot.io/blog/jncia-practice-lab), seven exercises on the same two routers
- [Juniper docs: OSPF configuration overview](https://www.juniper.net/documentation/us/en/software/junos/ospf/index.html)
- [Juniper EVPN-VXLAN Spine-Leaf on vJunos](../data-center/juniper-evpn-vxlan-vjunos.md)
- [OSPF Single Area, Three Routers](ospf-single-area-three-routers.md)
- [Juniper + Nokia IS-IS Interop](../multi-vendor/juniper-nokia-isis.md)

## Run it yourself

The tested containerlab files for these two routers, with addresses only so you can practice each step by hand: [network-labs/juniper/jncia-practice](https://github.com/netpilot-labs/network-labs/tree/main/juniper/jncia-practice).

## Try It

[**Open in NetPilot →**](https://app.netpilot.io/?prompt=Build%20two%20Juniper%20vJunos-routers%2C%20r1%20and%20r2%2C%20linked%20on%2010.0.12.0%2F30%20with%20loopbacks%2010.255.0.1%20and%2010.255.0.2%2C%20and%20a%20Linux%20host%20on%20each%20LAN%3A%20h1%20at%2010.1.1.10%2F24%20behind%20r1%20and%20h2%20at%2010.2.2.10%2F24%20behind%20r2.%20Run%20OSPF%20area%200%20on%20the%20link%20and%20both%20loopbacks%20and%20advertise%20both%20LANs.%20Deploy%20it%2C%20show%20the%20OSPF%20neighbor%20Full%20on%20both%20routers%2C%20and%20ping%20h2%20from%20h1.%20Then%20save%20a%20rescue%20configuration%20on%20both%20routers.)
