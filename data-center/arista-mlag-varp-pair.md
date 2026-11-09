# Arista MLAG Pair with VARP: Dual-Homed Host and Failover

An Arista MLAG pair built, checked and then broken on purpose: stop one leaf and measure how long traffic stops.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io/?vendor=arista), or [open it with the prompt filled in](https://app.netpilot.io/?prompt=Build%20an%20Arista%20MLAG%20pair%20with%20VARP%20on%20VLANs%2010%20and%2020%2C%20a%20dual-homed%20Linux%20host%20and%20a%20downstream%20switch%2C%20then%20stop%20one%20leaf%20and%20measure%20the%20outage.):

> Build an Arista MLAG pair with VARP on VLANs 10 and 20, a dual-homed Linux host and a downstream switch, then stop one leaf and measure the outage.

## What You'll Build

- Two Arista cEOS leaves in one MLAG domain, with a peer link and a peer address on VLAN 4094
- VARP anycast gateways on VLANs 10 and 20
- A Linux host on an LACP bond to both leaves
- A downstream switch on an MLAG port channel, with a host behind it

## What Came Back

On our run the agent confirmed MLAG Active and both port channels up on each leaf, and pinged between all hosts 5 of 5. It then ran three timed pings, checked which leaf each flow crossed, and stopped leaf1, the MLAG primary. The flows through leaf1 lost about 2.7 seconds, the host's fast LACP timeout. The flow through leaf2 lost nothing. It also flagged what it did not measure: the downstream switch kept default LACP timers, so a flow it sent to the dead leaf would drop for about 80 seconds.

## Concepts Demonstrated

- MLAG peer link, peer address and the `mlag` ID on each dual-homed port channel
- VARP: one virtual gateway MAC and address on both leaves
- Why a silent failure (no carrier loss) is ended by the LACP timeout, and why `lacp timer fast` matters
- Measuring a failover per flow, not as one number

## Vendors Used

- Arista cEOS (bring your own image, uploaded once)
- Linux hosts

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Set lacp timer fast on the downstream switch too and repeat the test with a flow pinned through leaf1"
- "Use docker pause instead of docker stop and compare the outage"
- "Replace VARP with a virtual-router on an EVPN anycast gateway"

## Related Resources

- [NetPilot blog: Arista MLAG lab](https://www.netpilot.io/blog/arista-mlag-lab), three runs from 79 seconds down to about 3.5
- [Arista EOS MLAG configuration guide](https://www.arista.com/en/um-eos/eos-multi-chassis-link-aggregation)
- [Arista cEOS eBGP Lab: Two Switches and Two Hosts](../routing/arista-ceos-ebgp-two-switches.md)
- [Firmware Upgrade Failover Test](../change-validation/firmware-upgrade-failover.md)
- [Data Center VLAN Migration](../change-validation/data-center-vlan-migration.md)

## Run it yourself

The tested containerlab files for this lab, configured at deploy: [network-labs/arista/mlag-pair](https://github.com/netpilot-labs/network-labs/tree/main/arista/mlag-pair).

## Try It

[**Open in NetPilot →**](https://app.netpilot.io/?prompt=Build%20an%20Arista%20MLAG%20pair%20with%20VARP%20on%20VLANs%2010%20and%2020%2C%20a%20dual-homed%20Linux%20host%20and%20a%20downstream%20switch%2C%20then%20stop%20one%20leaf%20and%20measure%20the%20outage.)
