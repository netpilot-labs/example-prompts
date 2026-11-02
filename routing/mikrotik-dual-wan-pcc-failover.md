# MikroTik Dual WAN Failover: PCC Load Balancing on RouterOS 7

Build a MikroTik dual WAN lab with two ISPs you can break, then measure how long users really lose traffic.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io/?vendor=mikrotik), or [open it with the prompt filled in](https://app.netpilot.io/?prompt=Build%20me%20a%20MikroTik%20dual%20WAN%20lab%20on%20RouterOS%207%3A%20a%20gateway%20with%20uplinks%20to%20two%20ISP%20routers%2C%20both%20reaching%20one%20web%20server%2C%20and%20a%20PC%20on%20the%20LAN.%20Set%20up%20PCC%20load%20balancing%20with%20failover.%20Then%20kill%20ISP-1%20upstream%20while%20the%20gateway%20link%20stays%20up%2C%20and%20measure%20how%20long%20the%20PC%20loses%20traffic.):

> Build me a MikroTik dual WAN lab on RouterOS 7: a gateway with uplinks to two ISP routers, both reaching one web server, and a PC on the LAN. Set up PCC load balancing with failover. Then kill ISP-1 upstream while the gateway link stays up, and measure how long the PC loses traffic.

## What You'll Build

- A gateway, two ISP routers and an upstream router on MikroTik RouterOS 7, plus a web server and a PC
- PCC load balancing across both WANs
- Recursive check-gateway, so the gateway sees a failure past its neighbor
- A measured outage for a flow through ISP 1, with a control flow on ISP 2

## Concepts Demonstrated

- How PCC keeps a connection on one WAN
- Why plain check-gateway misses a failure one hop past the next hop
- Recursive routing with scope and target-scope on RouterOS 7
- Why one failover test can flatter you: our three runs read 23.50, 29.95 and 30.36 seconds

## Vendors Used

- MikroTik RouterOS (CHR), preloaded on every lab VM

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Replace check-gateway with Netwatch and shorter probes, then measure again"
- "Use DHCP on both WAN links"
- "Add a failover alert to the router log and an email"
- "Weight PCC 2 to 1 for a faster primary link"

## Related Resources

- [NetPilot blog: MikroTik Load Balancing with PCC](https://www.netpilot.io/blog/mikrotik-load-balancing-pcc)
- [Video: MikroTik Dual WAN Failover](https://www.youtube.com/watch?v=JV5ShYpbps8)
- [NetPilot MikroTik lab page](https://www.netpilot.io/mikrotik-lab)
- [MikroTik docs: Load Balancing](https://help.mikrotik.com/docs/spaces/ROS/pages/4390920/Load+Balancing)
- [Public lab files: 03-dual-wan-pcc](https://github.com/netpilot-labs/mikrotik-labs/tree/main/03-dual-wan-pcc)
- [MikroTik CHR OSPF Lab: Two RouterOS Routers](mikrotik-chr-ospf-two-routers.md)
- [MikroTik RouterOS Practice Lab](mikrotik-routeros-practice-lab.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io/?prompt=Build%20me%20a%20MikroTik%20dual%20WAN%20lab%20on%20RouterOS%207%3A%20a%20gateway%20with%20uplinks%20to%20two%20ISP%20routers%2C%20both%20reaching%20one%20web%20server%2C%20and%20a%20PC%20on%20the%20LAN.%20Set%20up%20PCC%20load%20balancing%20with%20failover.%20Then%20kill%20ISP-1%20upstream%20while%20the%20gateway%20link%20stays%20up%2C%20and%20measure%20how%20long%20the%20PC%20loses%20traffic.)
