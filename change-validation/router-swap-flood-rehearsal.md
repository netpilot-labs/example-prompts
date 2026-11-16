# Router Swap Flood Rehearsal: a New Arista Edge Against a Cisco OSPF Core, with CoPP

Rehearse a site router replacement and find out what the new router does to the old network before the cutover window.

## The Prompt

Open it [prefilled in NetPilot](https://app.netpilot.io/?prompt=I%27m%20about%20to%20replace%20a%20site%20router%20on%20our%20network%20and%20I%20want%20to%20rehearse%20it%20first.%20Build%20three%20Cisco%20routers%20as%20the%20existing%20core%20running%20OSPF%20area%200%2C%20with%20a%20Linux%20host%20on%20two%20of%20them%20so%20we%20can%20ping%20across%20the%20core.%20Then%20add%20the%20replacement%3A%20an%20Arista%20router%20taking%20over%20one%20site%2C%20connected%20to%20two%20of%20the%20Cisco%20routers.%20Plant%20one%20misconfiguration%20on%20the%20new%20site%3A%20a%20Linux%20host%20behind%20the%20Arista%20router%20that%20sends%20about%20250%20TCP%20connection%20attempts%20a%20second%20to%20the%20Cisco%20routers%27%20addresses.%20Measure%20the%20Cisco%20routers%27%20CPU%2C%20the%20OSPF%20neighbors%20and%20ping%20loss%20between%20the%20two%20hosts%20before%20and%20during%20the%20flood.%20Then%20show%20me%20how%20I%20would%20find%20which%20site%20is%20flooding%2C%20add%20control%20plane%20policing%20on%20the%20Cisco%20routers%20and%20an%20inbound%20filter%20on%20the%20Arista%20edge%2C%20and%20measure%20everything%20again.), or paste it:

> I'm about to replace a site router on our network and I want to rehearse it first. Build three Cisco routers as the existing core running OSPF area 0, with a Linux host on two of them so we can ping across the core. Then add the replacement: an Arista router taking over one site, connected to two of the Cisco routers. Plant one misconfiguration on the new site: a Linux host behind the Arista router that sends about 250 TCP connection attempts a second to the Cisco routers' addresses. Measure the Cisco routers' CPU, the OSPF neighbors and ping loss between the two hosts before and during the flood. Then show me how I would find which site is flooding, add control plane policing on the Cisco routers and an inbound filter on the Arista edge, and measure everything again.

## What You'll Build

- 3 Cisco IOL routers as the existing core on OSPF area 0, a Linux host on two of them
- 1 Arista cEOS router as the replacement site, linked to two core routers
- A Linux host behind the Arista router that sends TCP connection attempts to port 179 on the core's addresses
- Before, during and after numbers: core CPU, OSPF neighbors, ping loss between the two hosts
- The trace to the flooding site, control plane policing on the Cisco routers and an inbound filter on the Arista edge

## Concepts Demonstrated

- Control plane policing (CoPP): police what reaches the route processor, keep OSPF in its own class
- Tracing a flood to its site with interface input rates and a counting ACL scoped to one subnet
- Containing a misbehaving site at its own edge, so the flood never crosses the core
- Measuring before and after on the same three numbers, so a cutover plan has evidence and not a guess

## What the Recorded Run Showed

At 250 attempts a second, the reported rate, the core's CPU stayed at 1 % or under, OSPF stayed FULL and no ping was lost. With both controls off, 20,000 attempts a second delivered about 6,447 a second to the core, and CPU rose to 6 to 8 %. CoPP alone dropped 99.4 % of that flood and the core went back to 0 %. The full numbers are in the lab's README.

## Vendors Used

- Cisco IOL (the core)
- Arista cEOS (the replacement)
- Linux hosts (network-multitool)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Rerun the flood at 5000 and 20000 attempts a second with both controls off, then put them back and measure again"
- "Add a second flood host so the core receives the full offered rate"
- "Swap the closed port for a port the routers listen on and compare the CPU"
- "Add CoPP on the Arista edge too and compare where the flood stops"

## Related Resources

- Run it yourself: [router-swap-control-plane-flood](https://github.com/netpilot-labs/network-labs/tree/main/multi-vendor/router-swap-control-plane-flood) in network-labs
- [Vendor Migration: Cisco IOS to Arista EOS](vendor-migration-cisco-to-arista.md)
- [Firmware Upgrade Failover Test](firmware-upgrade-failover.md)
- [NetPilot network change validation](https://www.netpilot.io/network-change-validation)
- [Cisco: Control Plane Policing configuration guide](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/qos_plcshp/configuration/xe-16/qos-plcshp-xe-16-book/qos-plcshp-ctrl-pln-plc.html)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io/?prompt=I%27m%20about%20to%20replace%20a%20site%20router%20on%20our%20network%20and%20I%20want%20to%20rehearse%20it%20first.%20Build%20three%20Cisco%20routers%20as%20the%20existing%20core%20running%20OSPF%20area%200%2C%20with%20a%20Linux%20host%20on%20two%20of%20them%20so%20we%20can%20ping%20across%20the%20core.%20Then%20add%20the%20replacement%3A%20an%20Arista%20router%20taking%20over%20one%20site%2C%20connected%20to%20two%20of%20the%20Cisco%20routers.%20Plant%20one%20misconfiguration%20on%20the%20new%20site%3A%20a%20Linux%20host%20behind%20the%20Arista%20router%20that%20sends%20about%20250%20TCP%20connection%20attempts%20a%20second%20to%20the%20Cisco%20routers%27%20addresses.%20Measure%20the%20Cisco%20routers%27%20CPU%2C%20the%20OSPF%20neighbors%20and%20ping%20loss%20between%20the%20two%20hosts%20before%20and%20during%20the%20flood.%20Then%20show%20me%20how%20I%20would%20find%20which%20site%20is%20flooding%2C%20add%20control%20plane%20policing%20on%20the%20Cisco%20routers%20and%20an%20inbound%20filter%20on%20the%20Arista%20edge%2C%20and%20measure%20everything%20again.)
