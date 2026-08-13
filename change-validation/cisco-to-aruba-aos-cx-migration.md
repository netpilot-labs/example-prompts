# Cisco to Aruba AOS-CX Migration — VSX Core Rehearsal with STP and Failover Validation

Rehearse a Cisco-campus-to-Aruba-AOS-CX core refresh end to end: translate the IOS configs, verify the MSTP root landed where the design says, and fail the VSX primary with a continuous ping running.

**Availability:** Aruba AOS-CX runs on NetPilot through **Signature & Enterprise custom vendor support** — NetPilot builds the AOS-CX Switch Simulator into a dedicated environment for you. HPE distributes the simulator image at no charge through the [HPE Networking Support Portal](https://networkingsupport.hpe.com/) (formerly the Aruba Support Portal; free account required); NetPilot never distributes vendor images. On self-serve tiers, the translation step needs no Aruba image at all, and you can rehearse the full deploy/validate flow with a stand-in NOS — see [Variations](#variations-to-try).

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a Cisco-to-Aruba migration rehearsal lab. Current state: a Cisco core pair (CORE-A, CORE-B) running HSRP for VLANs 10, 20, and 30 (virtual IPs 10.1.10.1, 10.1.20.1, 10.1.30.1, CORE-A active with priority 110 and preempt), two access switches uplinked on port-channels, RPVST+ everywhere, and a routed uplink from each core to a WAN edge router running OSPF area 0 and advertising its loopback 198.51.100.1/32. Target state: the same topology on Aruba AOS-CX — a VSX pair with active-gateway for the three VLANs, LAGs to the access switches, and MSTP with VLANs 10 and 20 in instance 1 and VLAN 30 in instance 2, with every target switch in one MST region (name MIGRATION, revision 1, identical VLAN-to-instance mapping) — deployed as a fully separate topology with its own identically configured WAN edge. Generate the full current-state IOS configs for this design first and show them to me — or, if I have pasted my sanitized production configs below, use those as the source instead and derive the device names, VLANs, virtual IPs, and probe targets from my configs rather than the sample values, keeping the same validation steps. Then translate them to AOS-CX and flag every line that doesn't map cleanly — switchport to vlan access/trunk, port-channel to lag with lacp, HSRP to active-gateway, GigabitEthernet1/0/1-style names to 1/1/1, dotted masks to CIDR, and AOS-CX's interfaces-default-to-shutdown gotcha. Deploy both sides with a Linux host in each of the three VLANs on each access switch (six hosts per side), so a VLAN or LAG fault on either access switch can't hide behind the other, then validate: (1) diff the routing tables and OSPF neighbor state between the old and new cores, flagging any prefix, next-hop, or metric difference beyond interface renames; (2) verify spanning tree — confirm every target switch reports the same MST region, that the VSX pair is root for instances 1 and 2, and list any port that newly went blocking; (3) run two simultaneous continuous pings from every host — one to its own gateway and one through the core to the WAN loopback 198.51.100.1, so a surviving peer that answers ARP but black-holes routed traffic still fails — then fail the VSX primary and restore it, fail the VSX secondary and restore it, and then, for each access switch's LAG in turn, drop the member the probe flows actually hash onto (confirm with per-member counters before choosing it) and restore it, so both LAGs get exercised. After every restoration, confirm the restored device or member is actually back in service (VSX peering up, LAG member forwarding) before starting the next event. Report and grade seconds of loss per host per probe destination per event — the gateway probe and the WAN-loopback probe must each independently pass: 2 seconds of loss or less for a node event, 1 second or less for a LAG-member event, unless I give different thresholds. Finish with a go/no-go report for the cutover: every check pass/fail with command output as evidence, plus the translated lines that need human review.

## What You'll Build

- Current side: a Cisco core pair (HSRP on VLANs 10/20/30, RPVST+) with two port-channeled access switches and a WAN edge (OSPF area 0)
- Target side: an Aruba AOS-CX VSX pair with active-gateway, LAGs to access, a single verified MST region with two instances, and its own WAN edge
- A line-by-line IOS-to-AOS-CX translation with every non-clean mapping flagged (generated current-state configs, or your own sanitized ones)
- A routing-table and OSPF-neighbor diff between old and new cores
- STP verification: one MST region across the target topology, roots for both instances on the VSX pair, newly blocking ports listed
- A VSX failover battery — both node failures plus a counter-verified LAG-member drop on each access switch's LAG — under dual probes from a host per VLAN per access switch (gateway + routed WAN loopback), each probe graded independently against explicit loss thresholds
- A go/no-go cutover report with command-level evidence

## Concepts Demonstrated

- The IOS-to-AOS-CX translation surface: `switchport` → `vlan access`/`vlan trunk allowed`, port-channel → LAG, HSRP → VSX active-gateway, RPVST+ → MSTP instance mapping
- The gotchas that don't announce themselves: interfaces default to shutdown, CIDR-only masks, `1/1/1` interface naming
- Why STP root verification is a *migration* check — a per-VLAN RPVST+ root doesn't automatically become the right MSTP instance root, and a mismatched MST region name, revision, or VLAN map silently turns an access switch into a boundary
- Measuring VSX failover with in-flight probes instead of trusting the datasheet — probing *through* the gateway to a routed destination, failing both peers in turn, and dropping the LAG member the flows actually use
- Translation ≠ validation: converting the config is the start of the rehearsal, not the end of the migration

## Vendors Used

- Aruba AOS-CX (VSX core pair — via Signature & Enterprise custom vendor support, see the availability note above)
- Cisco (current-side core, access, and WAN edge, per your environment)
- Linux (one test host per VLAN per access switch for continuous ping)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Stand in Arista cEOS for the target while my Aruba environment is provisioned — MLAG plus VRRP in place of VSX active-gateway, same MSTP instance layout — and run the same STP-root and failover checks"
- "Translate only — here are my IOS configs; give me the AOS-CX equivalents and the flag list, no lab deploy" (runs on any tier)
- "The current side is Comware/ProCurve instead of IOS — rerun the translation from that syntax"
- "Add a VSX split-brain scenario: cut the ISL and keepalive, and report what the access layer experiences"
- "Extend the go/no-go report with a rollback rehearsal back to the Cisco pair"

## Why This Matters

Cisco-to-Aruba core refreshes are where two config dialects that look almost identical diverge in exactly the places that page you at 2am: STP mode defaults, gateway redundancy semantics, and ports that stay shutdown until told otherwise. Rehearsing the translation, the STP root placement, and the VSX failover in a lab turns each of those into a checked box on the go/no-go report instead of a cutover-night discovery.

## Related Resources

- [Blog: Cisco to Aruba (AOS-CX) Migration — Translation Table + Lab Validation](https://www.netpilot.io/blog/cisco-to-aruba-migration-lab) — the full translation table this prompt is built from
- [NetPilot Network Migration Lab](https://www.netpilot.io/network-migration-lab) — dedicated landing page for migration rehearsals
- [HPE Networking Support Portal](https://networkingsupport.hpe.com/) — where HPE distributes the AOS-CX Switch Simulator (free account required)
- [Related: Vendor Migration Rehearsal](vendor-migration-rehearsal.md) — the vendor-generic version of this workflow, runnable self-serve as pasted
- [Related: Vendor Migration — Cisco IOS to Arista EOS](vendor-migration-cisco-to-arista.md) — behavior-equivalence testing between parallel topologies
- [Related: Change Validation Workflow](change-validation-workflow.md) — the underlying mirror → snapshot → apply → diff pattern

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
