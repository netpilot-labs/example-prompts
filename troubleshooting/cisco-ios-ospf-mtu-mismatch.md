# Cisco IOS OSPF MTU Mismatch Lab: Neighbors Stuck in EXSTART

Two real Cisco IOS routers with one stray `ip mtu` that keeps OSPF from reaching FULL. The agent finds the cause on the CLI, fixes it, and hands the lab back as a Packet Tracer file.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io/?vendor=cisco), or [open it with the prompt filled in](https://app.netpilot.io/?prompt=Build%20the%20classic%20CCNA%20OSPF%20lab%20on%20real%20Cisco%20IOS%3A%20two%20Cisco%20IOL%20routers%2C%20R1%20and%20R2%2C%20linked%20on%2010.0.12.0%2F30%20in%20OSPF%20area%200%2C%20with%20a%20Linux%20host%20on%20each%20router%27s%20LAN%2C%20host1%20at%20192.168.1.10%2F24%20behind%20R1%20and%20host2%20at%20192.168.2.10%2F24%20behind%20R2.%20Set%20ip%20mtu%201400%20on%20R2%27s%20interface%20toward%20R1%20and%20leave%20R1%20at%20the%20default.%20Deploy%20it%2C%20then%20check%20the%20OSPF%20neighbors%20on%20both%20routers%20and%20ping%20host2%20from%20host1.%20If%20something%20does%20not%20come%20up%2C%20find%20the%20cause%20on%20the%20CLI%2C%20explain%20it%2C%20and%20fix%20it.%20Then%20save%20the%20working%20configs%20and%20export%20the%20lab%20as%20a%20Packet%20Tracer%20.pkt%20file.):

> Build the classic CCNA OSPF lab on real Cisco IOS: two Cisco IOL routers, R1 and R2, linked on 10.0.12.0/30 in OSPF area 0, with a Linux host on each router's LAN, host1 at 192.168.1.10/24 behind R1 and host2 at 192.168.2.10/24 behind R2. Set ip mtu 1400 on R2's interface toward R1 and leave R1 at the default. Deploy it, then check the OSPF neighbors on both routers and ping host2 from host1. If something does not come up, find the cause on the CLI, explain it, and fix it. Then save the working configs and export the lab as a Packet Tracer .pkt file.

## What You'll Build

- Two Cisco IOL routers, R1 and R2, on 10.0.12.0/30 in OSPF area 0
- A Linux host on each LAN: host1 at 192.168.1.10/24, host2 at 192.168.2.10/24
- One planted fault: `ip mtu 1400` on R2's link toward R1

## What Came Back

On a recorded run, R2 sat in EXSTART and R1 in EXCHANGE, and host1 could not reach host2. The agent ran `debug ip ospf adj` and read `Nbr 1.1.1.1 has larger interface MTU`. After the fix both routers read FULL, host1 pinged host2 5 of 5, and the export was a `.pkt` with 4 devices and 3 links.

## Concepts Demonstrated

- Why OSPF compares interface MTU only while an adjacency forms, in the database description exchange
- Reading EXSTART and EXCHANGE in `show ip ospf neighbor`
- The clean fix (remove the stray `ip mtu`) against the quick one (lower the good side)
- Moving a lab from real IOS back to Packet Tracer

## Vendors Used

- Cisco IOL 17.12.1 (bring your own image, uploaded once)
- Linux hosts

## Difficulty

⭐ Beginner

## Variations to Try

- "Use ip ospf mtu-ignore instead and explain why that hides the problem"
- "Change the network type on one side to point-to-point and find what breaks"
- "Add a third router in area 1 and make R2 the ABR"

## Related Resources

- [NetPilot blog: the same CCNA lab on real Cisco IOS](https://www.netpilot.io/blog/network-simulator-online-free#the-same-ccna-lab-on-real-cisco-ios), with the video
- [Why CCNA OSPF works in Packet Tracer and fails on real routers](https://www.netpilot.io/blog/ccna-ospf-works-in-packet-tracer-fails-on-real-routers)
- [RFC 2328, section 10.6: receiving database description packets](https://www.rfc-editor.org/rfc/rfc2328#section-10.6)
- [Cisco IOS Hub and Spoke OSPF with an AI Agent](ai-five-jobs-cisco-ios.md)
- [OSPF Single Area, Three Routers](../routing/ospf-single-area-three-routers.md)

## Run it yourself

The tested containerlab files for this lab, with the stray MTU left in for you to find: [network-labs/cisco/ccna-ospf-mtu](https://github.com/netpilot-labs/network-labs/tree/main/cisco/ccna-ospf-mtu).

## Try It

[**Open in NetPilot →**](https://app.netpilot.io/?prompt=Build%20the%20classic%20CCNA%20OSPF%20lab%20on%20real%20Cisco%20IOS%3A%20two%20Cisco%20IOL%20routers%2C%20R1%20and%20R2%2C%20linked%20on%2010.0.12.0%2F30%20in%20OSPF%20area%200%2C%20with%20a%20Linux%20host%20on%20each%20router%27s%20LAN%2C%20host1%20at%20192.168.1.10%2F24%20behind%20R1%20and%20host2%20at%20192.168.2.10%2F24%20behind%20R2.%20Set%20ip%20mtu%201400%20on%20R2%27s%20interface%20toward%20R1%20and%20leave%20R1%20at%20the%20default.%20Deploy%20it%2C%20then%20check%20the%20OSPF%20neighbors%20on%20both%20routers%20and%20ping%20host2%20from%20host1.%20If%20something%20does%20not%20come%20up%2C%20find%20the%20cause%20on%20the%20CLI%2C%20explain%20it%2C%20and%20fix%20it.%20Then%20save%20the%20working%20configs%20and%20export%20the%20lab%20as%20a%20Packet%20Tracer%20.pkt%20file.)
