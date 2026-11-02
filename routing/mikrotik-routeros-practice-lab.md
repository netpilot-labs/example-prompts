# MikroTik RouterOS Practice Lab: DHCP, Bridging, NAT, Firewall and Queues

A RouterOS lab that leaves the NAT and firewall work to you, so you type every command yourself.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io/?vendor=mikrotik), or [open it with the prompt filled in](https://app.netpilot.io/?prompt=Build%20an%20MTCNA%20practice%20lab%3A%20a%20MikroTik%20CHR%20gateway%20with%20a%20DHCP%20WAN%20from%20a%20CHR%20ISP%20router%2C%20a%20LAN%20bridge%20with%20a%20DHCP%20server%20and%20two%20Linux%20PCs%2C%20and%20a%20Linux%20web%20server%20behind%20the%20ISP.%20Leave%20NAT%20and%20the%20firewall%20for%20me%20to%20configure%2C%20and%20tell%20me%20how%20to%20test%20NAT%20from%20a%20PC%20by%20IP%20address.):

> Build an MTCNA practice lab: a MikroTik CHR gateway with a DHCP WAN from a CHR ISP router, a LAN bridge with a DHCP server and two Linux PCs, and a Linux web server behind the ISP. Leave NAT and the firewall for me to configure, and tell me how to test NAT from a PC by IP address.

## What You'll Build

- A MikroTik CHR gateway and a CHR ISP router
- A LAN bridge with a DHCP server and two Linux PCs
- A Linux web server behind the ISP
- NAT and the firewall left open for you

## Concepts Demonstrated

- A DHCP client on the WAN and a DHCP server on the LAN
- RouterOS bridges
- Source NAT and firewall filter rules, typed by hand
- Simple queues and the diagnostic tools, as variations

## Vendors Used

- MikroTik RouterOS (CHR), preloaded on every lab VM

## Difficulty

⭐ Beginner

## Variations to Try

- "Add a simple queue that limits one PC to 256 kbit/s"
- "Run PPPoE between the ISP and the gateway"
- "Break the default route and let me find it"

## Related Resources

- [NetPilot blog: MTCNA Practice Lab](https://www.netpilot.io/blog/mtcna-practice-lab)
- [NetPilot MikroTik lab page](https://www.netpilot.io/mikrotik-lab)
- [MikroTik docs: First Time Configuration](https://help.mikrotik.com/docs/spaces/ROS/pages/328151/First+Time+Configuration)
- [Public lab files: 02-mtcna-practice](https://github.com/netpilot-labs/mikrotik-labs/tree/main/02-mtcna-practice)
- [MikroTik CHR OSPF Lab: Two RouterOS Routers](mikrotik-chr-ospf-two-routers.md)
- [MikroTik Dual WAN Failover with PCC](mikrotik-dual-wan-pcc-failover.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io/?prompt=Build%20an%20MTCNA%20practice%20lab%3A%20a%20MikroTik%20CHR%20gateway%20with%20a%20DHCP%20WAN%20from%20a%20CHR%20ISP%20router%2C%20a%20LAN%20bridge%20with%20a%20DHCP%20server%20and%20two%20Linux%20PCs%2C%20and%20a%20Linux%20web%20server%20behind%20the%20ISP.%20Leave%20NAT%20and%20the%20firewall%20for%20me%20to%20configure%2C%20and%20tell%20me%20how%20to%20test%20NAT%20from%20a%20PC%20by%20IP%20address.)
