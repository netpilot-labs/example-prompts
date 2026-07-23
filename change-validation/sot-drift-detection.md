# Source-of-Truth Drift Detection — Nautobot Records vs Live State

Your Nautobot says one thing; the network runs another. Have the agent diff intended state against live show-command output — read-only on both sides — and hand you the delta.

> **Requires the Nautobot connector** (and the Nornir connector for live checks) — both read-only, added from the chat. See [NetPilot Integrations](https://www.netpilot.io/integrations).

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io) (with Nautobot + Nornir connectors enabled):

> Using my Nautobot connector, pull the intended state for the devices in location HQ: interfaces with their descriptions, IP addresses, VLANs, and the rendered config context for each device. Then, using the Nornir connector, run read-only show commands against the same devices — the platform-appropriate equivalents of interface/IP status, VLAN summary, and interface descriptions (for example show ip interface brief on Cisco IOS; pick each device's syntax from the platform recorded in Nautobot). Diff intended vs actual per device and give me a drift report in three buckets: (1) records that are stale in Nautobot, (2) live config that violates the intended state, (3) matches. For the violations, build a small lab replicating the affected devices so I can rehearse the correcting change before pushing anything to production.

## What You'll Build

- A per-device drift report: Nautobot records vs live show-command output
- Three-bucket triage — stale records, live violations, verified matches
- A rehearsal lab for the correcting change, built only from the drifted segment
- Zero writes anywhere: Nautobot ingest is read-only and Nornir is show-commands-only

## Concepts Demonstrated

- Drift detection without an assurance platform: SoT read + live read + diff in one conversation
- Credentials stay in your perimeter — Nornir inventory and secrets are brokered from your Nautobot at call time, never stored by NetPilot
- The rehearse-then-fix loop: the correcting change is proven on a lab replica before production
- Why read-only matters: the agent can find drift but structurally cannot "fix" your source of truth behind your back

## Vendors Used

- Whatever your Nautobot records — the rehearsal lab maps roles to Cisco IOL / Arista cEOS / Nokia SR Linux / FRR

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Scope the drift check to interfaces tagged `uplink` only"
- NetBox shop? Pull intended state from your NetBox connector instead ("Using my NetBox connector, pull intended state for site HQ…"). Note the live-check leg still requires the Nornir connector, which brokers device credentials from a Nautobot — without one, true drift detection against the live network isn't possible — you can still audit the records themselves (stale entries, missing data) and rehearse the correcting change on a lab built from them, but don't call a NetBox-vs-NetBox-built-lab diff "drift detection"
- "Check BGP: intended neighbors from Nautobot vs show ip bgp summary from the live core"
- "Run the same drift report weekly and show me only what changed since last run"
- "For bucket 1 (stale records), draft the Nautobot updates for my review — but do not apply them"

## Why This Matters

Out-of-date source-of-truth data is the top objection to automating against it — and the reason teams distrust their own Nautobot (or NetBox — see Variations). A read-only agent that continuously surfaces the delta (and rehearses the fix in a lab) makes the source of truth trustworthy again without granting anything write access.

## Related Resources

- [NetPilot Integrations — NetBox, Nautobot & Nornir connectors](https://www.netpilot.io/integrations)
- [NetPilot Network Change Validation](https://www.netpilot.io/network-change-validation)
- [Related: NetBox Site → Digital Twin Rehearsal](netbox-site-twin-rehearsal.md)
- [Related: Change Validation Workflow](change-validation-workflow.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
