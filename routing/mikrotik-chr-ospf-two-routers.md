# MikroTik CHR OSPF Lab: Two RouterOS Routers

The smallest real RouterOS lab: two CHR routers, one link, OSPF up and verified.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io/?vendor=mikrotik), or [open it with the prompt filled in](https://app.netpilot.io/?prompt=Build%20two%20MikroTik%20CHR%20routers%20connected%20on%20ether2%2C%20with%20OSPF%20in%20area%200%20and%20a%20loopback%20on%20each.%20Verify%20the%20adjacency%20and%20ping%20loopback%20to%20loopback.):

> Build two MikroTik CHR routers connected on ether2, with OSPF in area 0 and a loopback on each. Verify the adjacency and ping loopback to loopback.

## What You'll Build

- Two MikroTik CHR routers on one link
- OSPF in area 0
- A loopback on each router, reachable from the other

## Concepts Demonstrated

- RouterOS 7 OSPF instances and areas
- Reading an adjacency with `/routing ospf neighbor print`
- Proving reachability from loopback to loopback

## Vendors Used

- MikroTik RouterOS (CHR), preloaded on every lab VM

## Difficulty

⭐ Beginner

## Variations to Try

- "Replace one router with FRR to test OSPF between vendors"
- "Add a third router and a second area"
- "Move to eBGP between the two routers"

## Related Resources

- [NetPilot blog: Run the Official MikroTik CHR Image in containerlab](https://www.netpilot.io/blog/mikrotik-chr-containerlab)
- [NetPilot MikroTik lab page](https://www.netpilot.io/mikrotik-lab)
- [MikroTik docs: OSPF](https://help.mikrotik.com/docs/spaces/ROS/pages/9863229/OSPF)
- [MikroTik RouterOS Practice Lab](mikrotik-routeros-practice-lab.md)
- [MikroTik Dual WAN Failover with PCC](mikrotik-dual-wan-pcc-failover.md)

## Run it yourself

The tested containerlab files for this lab, to deploy on your own Linux host: [network-labs/mikrotik/chr-two-routers](https://github.com/netpilot-labs/network-labs/tree/main/mikrotik/chr-two-routers).

## Try It

[**Open in NetPilot →**](https://app.netpilot.io/?prompt=Build%20two%20MikroTik%20CHR%20routers%20connected%20on%20ether2%2C%20with%20OSPF%20in%20area%200%20and%20a%20loopback%20on%20each.%20Verify%20the%20adjacency%20and%20ping%20loopback%20to%20loopback.)
