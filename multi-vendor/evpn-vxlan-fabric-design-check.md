# EVPN-VXLAN Fabric Design Check: Arista and Nokia SR Linux Leaves with a Cisco WAN Edge

State your data center fabric design in plain words, and NetPilot builds it on real Arista, Nokia and Cisco CLIs, checks every claim on each device, and fails a spine to show what the design does under failure.

## The Prompt

Open it [prefilled in NetPilot](https://app.netpilot.io/?prompt=Here%27s%20my%20data%20center%20fabric%20design.%20Two%20Arista%20spines.%20Two%20leaves%3A%20an%20Arista%20border%20leaf%20and%20a%20Nokia%20SR%20Linux%20leaf.%20eBGP%20underlay%2C%20BGP%20EVPN%20overlay%2C%20one%20stretched%20VLAN%20and%20one%20routed%20VRF%2C%20with%20a%20Linux%20host%20on%20each%20leaf.%20A%20Cisco%20router%20is%20the%20WAN%20edge%2C%20peering%20with%20the%20border%20leaf%20and%20sending%20a%20default%20route%20into%20the%20VRF.%20Build%20it%2C%20then%20show%20me%20on%20each%20device%27s%20CLI%20that%20it%20works%2C%20and%20that%20the%20hosts%20still%20reach%20each%20other%20with%20one%20spine%20down.), or paste it:

> Here's my data center fabric design. Two Arista spines. Two leaves: an Arista border leaf and a Nokia SR Linux leaf. eBGP underlay, BGP EVPN overlay, one stretched VLAN and one routed VRF, with a Linux host on each leaf. A Cisco router is the WAN edge, peering with the border leaf and sending a default route into the VRF. Build it, then show me on each device's CLI that it works, and that the hosts still reach each other with one spine down.

Then, in the same chat:

> Add BFD to the underlay sessions and run the same spine test again. How long is the outage now?

The prompt gives no IP plan, AS numbers or VNIs. The agent picks them and tells you what it chose.

## What You'll Build

- Two Arista cEOS spines, an Arista cEOS border leaf and a Nokia SR Linux leaf
- A Cisco IOL router as the WAN edge, in BGP with the border leaf inside the tenant VRF
- eBGP underlay, BGP EVPN overlay, one VLAN stretched over VXLAN and one routed VRF on an L3 VNI
- A Linux host on each leaf, in the same stretched subnet
- A spine failure test with the hosts pinging through it, then the same test with BFD

## What Came Back

On our run, recorded on 2026-11-13:

- The agent chose the plan itself: spines in AS 65100, leaf1 in AS 65001, leaf2 in AS 65002, the Cisco edge in AS 65500, VLAN 10 on VNI 10010, VRF TENANT on L3 VNI 50001, an anycast gateway at 10.10.10.1 and the spines as EVPN route servers.
- All 9 BGP sessions were Established on both ends: 4 underlay, 4 EVPN overlay and 1 VRF session from the border leaf to the Cisco edge.
- host1 reached host2 5 of 5 both ways over the stretched VLAN, and each host reached 203.0.113.1, a loopback on the Cisco edge, 5 of 5 through the default route.
- The Nokia leaf received the default route as an EVPN route in VRF TENANT, pointing at the Arista border leaf on VNI 50001.
- With spine1 frozen for about 71 seconds, all 4 flows still returned 5 of 5. The outage while the fabric moved to spine2 was 8.52 s (host1 to host2) and 8.31 s (host2 to the WAN), set by the 9 s BGP hold timer.

The follow-up:

- The agent added BFD live without resetting any BGP session: 300 ms × 3 on the Arista side, 1 s × 3 on the Nokia leaf. 8 of 8 BFD peers came up.
- The same spine test, run on spine2 since all traffic had moved onto it, gave an outage of 2.90 s on both flows, about 66% shorter.
- In this lab the Nokia leaf's 1 s × 3 BFD timers set the floor: the gap ended 16 ms after its BFD expired. A shorter outage needs a faster timer on that leaf, not more tuning on the Arista side.

The whole build and both tests took minutes, and every result is a show command you can run yourself on the device.

## Run It Yourself

The topology and startup configs from this run, with BFD saved in, are the [public lab](https://github.com/netpilot-labs/network-labs/tree/main/multi-vendor/evpn-vxlan-arista-nokia-cisco-edge). Deploy it with containerlab on your own Linux host.

## Concepts Demonstrated

- Design validation: each claim of a fabric design checked on each vendor's own CLI before the design is built
- Multi-vendor EVPN-VXLAN between Arista EOS and Nokia SR Linux, with MAC routes for the stretched VLAN and IP prefix routes for the VRF
- A border leaf that takes a default route from a WAN edge and carries it into the fabric as an EVPN route
- Why a spine failure costs as long as the BGP hold timer, and what BFD changes
- How mixed BFD timers across vendors decide the failover time

## Vendors Used

- Arista cEOS 4.36.1F (spines and the border leaf), your own image, uploaded once to your lab VM
- Nokia SR Linux 25.10.1 (leaf), a public image
- Cisco IOL 17.12.1 (WAN edge), your own image, uploaded once to your lab VM
- Linux hosts (network-multitool), a public image

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Set the Nokia leaf's BFD to 300 ms × 3 to match the Arista side and run the spine test again"
- "Fail one leaf uplink instead of a whole spine and compare the outage"
- "Add a second tenant VRF and show the two tenants cannot reach each other"
- "Move the WAN edge to the Nokia leaf and check the Arista leaf still gets the default route"

## Related Resources

- [Run it yourself: the EVPN-VXLAN lab on Arista, Nokia and a Cisco edge](https://github.com/netpilot-labs/network-labs/tree/main/multi-vendor/evpn-vxlan-arista-nokia-cisco-edge)
- [Network change validation with NetPilot](https://www.netpilot.io/network-change-validation)
- [SONiC fabric design validation: prove it survives a spine failure](../poc/design-validation-spine-failure.md)
- [Cisco + Arista EVPN-VXLAN interop](cisco-arista-evpn-vxlan-interop.md)
- [Leaf-spine EVPN-VXLAN with symmetric IRB](../data-center/leaf-spine-evpn-vxlan-symmetric-irb.md)
- [RFC 8365: A Network Virtualization Overlay Solution Using EVPN](https://www.rfc-editor.org/rfc/rfc8365)
- [RFC 5880: Bidirectional Forwarding Detection](https://www.rfc-editor.org/rfc/rfc5880)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io/?prompt=Here%27s%20my%20data%20center%20fabric%20design.%20Two%20Arista%20spines.%20Two%20leaves%3A%20an%20Arista%20border%20leaf%20and%20a%20Nokia%20SR%20Linux%20leaf.%20eBGP%20underlay%2C%20BGP%20EVPN%20overlay%2C%20one%20stretched%20VLAN%20and%20one%20routed%20VRF%2C%20with%20a%20Linux%20host%20on%20each%20leaf.%20A%20Cisco%20router%20is%20the%20WAN%20edge%2C%20peering%20with%20the%20border%20leaf%20and%20sending%20a%20default%20route%20into%20the%20VRF.%20Build%20it%2C%20then%20show%20me%20on%20each%20device%27s%20CLI%20that%20it%20works%2C%20and%20that%20the%20hosts%20still%20reach%20each%20other%20with%20one%20spine%20down.)
