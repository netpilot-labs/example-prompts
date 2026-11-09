# SONiC eBGP Lab: Two Switches on One Link

The smallest SONiC lab that runs a routing protocol: two switches, one /31, the ports brought up, and an eBGP session read in vtysh.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io/?vendor=sonic), or [open it with the prompt filled in](https://app.netpilot.io/?prompt=Build%20two%20SONiC%20switches%2C%20sw1%20in%20AS%2065001%20and%20sw2%20in%20AS%2065002%2C%20on%20one%20link%20with%2010.0.0.0%2F31%20on%20sw1%20and%2010.0.0.1%2F31%20on%20sw2.%20Bring%20the%20ports%20up%2C%20ping%20across%20the%20link%2C%20and%20start%20an%20eBGP%20session%20between%20them.%20Show%20me%20the%20BGP%20summary%20on%20both%20switches.):

> Build two SONiC switches, sw1 in AS 65001 and sw2 in AS 65002, on one link with 10.0.0.0/31 on sw1 and 10.0.0.1/31 on sw2. Bring the ports up, ping across the link, and start an eBGP session between them. Show me the BGP summary on both switches.

## What You'll Build

- Two SONiC switches (the community `docker-sonic-vs` image) on one link
- 10.0.0.0/31 on sw1's Ethernet0 and 10.0.0.1/31 on sw2's Ethernet0
- eBGP between AS 65001 and AS 65002 in FRR

## What Came Back

On our run the agent brought Ethernet0 up on both switches, pinged the /31 5 of 5 in both directions, and quoted `show bgp summary` from each switch with the session up. It also set `no bgp ebgp-requires-policy`, which this FRR release needs before eBGP exchanges any prefix.

## Concepts Demonstrated

- SONiC splits config in two: interfaces in CONFIG_DB through the `config` command, BGP in FRR through `vtysh`
- Ports boot admin down, and `bgpd` is stopped on this image until it is started
- Why eBGP on FRR exchanges nothing without a policy, unless `ebgp-requires-policy` is turned off

## Vendors Used

- SONiC (`docker-sonic-vs`), preloaded on every lab VM

## Difficulty

⭐ Beginner

## Variations to Try

- "Add a loopback on each switch and advertise it, then show the route learned over BGP"
- "Put the config in startup scripts so a redeploy rebuilds it"
- "Replace sw2 with an Arista cEOS switch and keep the same eBGP session"

## Related Resources

- [NetPilot blog: Run SONiC in containerlab](https://www.netpilot.io/blog/sonic-containerlab), the same two switches by hand
- [SONiC Leaf-Spine with eBGP and ECMP](../data-center/sonic-bgp-leaf-spine-ecmp.md)
- [SONiC configuration reference](https://github.com/sonic-net/SONiC/wiki/Configuration)
- [OSPF Single Area, Three Routers](ospf-single-area-three-routers.md)

## Run it yourself

The tested containerlab topology for this lab, to deploy on your own Linux host: [network-labs/sonic/two-switches](https://github.com/netpilot-labs/network-labs/tree/main/sonic/two-switches).

## Try It

[**Open in NetPilot →**](https://app.netpilot.io/?prompt=Build%20two%20SONiC%20switches%2C%20sw1%20in%20AS%2065001%20and%20sw2%20in%20AS%2065002%2C%20on%20one%20link%20with%2010.0.0.0%2F31%20on%20sw1%20and%2010.0.0.1%2F31%20on%20sw2.%20Bring%20the%20ports%20up%2C%20ping%20across%20the%20link%2C%20and%20start%20an%20eBGP%20session%20between%20them.%20Show%20me%20the%20BGP%20summary%20on%20both%20switches.)
