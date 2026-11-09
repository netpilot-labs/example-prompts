# Arista cEOS eBGP Lab: Two Switches and Two Hosts

The shortest prompt in the library: one sentence builds two Arista switches on eBGP and proves the hosts behind them can talk.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io/?vendor=arista), or [open it with the prompt filled in](https://app.netpilot.io/?prompt=Build%20two%20Arista%20cEOS%20switches%20on%20eBGP%2C%20each%20with%20a%20Linux%20host%2C%20and%20prove%20the%20hosts%20can%20reach%20each%20other.):

> Build two Arista cEOS switches on eBGP, each with a Linux host, and prove the hosts can reach each other.

## What You'll Build

- Two Arista cEOS switches, one AS each, on a routed /31 link
- A Linux host on each switch's LAN
- Each switch advertising its loopback and its LAN in BGP

## What Came Back

The prompt leaves the addressing to the agent. On our run it picked AS 65001 and 65002, 10.0.12.0/31 between the switches and a /24 per LAN. Each switch learned the other's two routes, the hosts pinged each other 5 of 5 in both directions, and a traceroute went host, sw1, sw2, host. The run took 102 seconds.

## Concepts Demonstrated

- eBGP between two EOS switches with routed ports (`no switchport`)
- Advertising a LAN and a loopback with `network` statements
- Proving a design from the hosts, not only from `show ip bgp summary`

## Vendors Used

- Arista cEOS (bring your own image, uploaded once)
- Linux hosts

## Difficulty

⭐ Beginner

## Variations to Try

- "Use 10.255.0.1 and 10.255.0.2 as loopbacks and put the hosts at 10.1.1.10 and 10.2.2.10", to match the lab files exactly
- "Shut sw2's host port and show the route leave sw1's table"
- "Add BFD to the session and measure how fast it drops"

## Related Resources

- [NetPilot blog: Run Arista cEOS in containerlab](https://www.netpilot.io/blog/arista-ceos-containerlab)
- [RFC 4271: A Border Gateway Protocol 4 (BGP-4)](https://www.rfc-editor.org/rfc/rfc4271)
- [Arista MLAG Pair with VARP](../data-center/arista-mlag-varp-pair.md)
- [SONiC eBGP Lab: Two Switches on One Link](sonic-ebgp-two-switches.md)
- [eBGP Three-AS Multi-Vendor](bgp-ebgp-three-as.md)

## Run it yourself

The tested containerlab files for this lab, configured at deploy: [network-labs/arista/two-switches](https://github.com/netpilot-labs/network-labs/tree/main/arista/two-switches).

## Try It

[**Open in NetPilot →**](https://app.netpilot.io/?prompt=Build%20two%20Arista%20cEOS%20switches%20on%20eBGP%2C%20each%20with%20a%20Linux%20host%2C%20and%20prove%20the%20hosts%20can%20reach%20each%20other.)
