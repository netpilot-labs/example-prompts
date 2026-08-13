# Vendor Migration Rehearsal — Translate, Diff-Validate, Failover-Test, Go/No-Go

Run a full vendor-swap rehearsal before cutover night: translate the configs, deploy current and target side by side, diff the state, break the target on purpose with traffic running, and walk away with a go/no-go report.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Run a vendor-migration rehearsal for a core refresh. Current state: two Cisco IOL core routers (CUR-CORE1, CUR-CORE2) sharing HSRP group 10 (virtual IP 10.1.10.1, CUR-CORE1 active with priority 110, preempt, and uplink interface tracking with decrement 20) on the user segment 10.1.10.0/24, OSPF area 0 between them, and eBGP from each core to its own upstream observer router (FRR, AS 65100) advertising 10.1.0.0/16. Target state: the same design — same addressing, same tracking behavior — on two Arista cEOS devices (TGT-CORE1, TGT-CORE2) with VRRP group 10 replacing HSRP, as a fully separate topology with its own identically configured FRR observer so the two data planes never share a return path. Generate the full current-state IOS configs for this design first and show them to me — or, if I have pasted my sanitized production configs below, use those as the source instead. Then translate the Cisco configs to EOS, flagging every line that doesn't map one-to-one — HSRP-to-VRRP semantics, interface names, timer, preempt, and tracking defaults — and deploy both topologies in parallel, with a Linux host on each side's user segment. Diff-validate: routing tables and OSPF neighbor state must match between the current and target pairs, and the two observers must have received identical BGP advertisements from their respective sides. Then failover-test the target with a continuous ping running from its host to 10.1.10.1 and to its observer's loopback: fail TGT-CORE1, restore it, then drop TGT-CORE1's uplink (tracking should demote it) and restore it — report seconds of loss per event, and run the same two failures on the current pair as the baseline to beat. Finish with a go/no-go report: every check pass/fail with command output as evidence, plus the list of translated lines that need human review before cutover.

## What You'll Build

- Current side: 2 Cisco IOL cores in HSRP active/standby with uplink tracking, OSPF area 0, eBGP upstream
- Target side: 2 Arista cEOS cores with the translated config and VRRP
- Twin FRR observers (AS 65100, identically configured, one per side — isolated data planes), plus a Linux host per side
- A config translation with every non-1:1 line flagged for review
- A state diff (routing tables, OSPF neighbors, BGP advertisements) between old and new
- A failover battery under continuous ping, measured on both sides
- A go/no-go cutover report with command-level evidence

## Concepts Demonstrated

- The five-step rehearsal: translate → deploy in parallel → diff state → failover under traffic → go/no-go
- Translation review as a first-class artifact — syntax that converts cleanly vs semantics that don't (timers, preempt, interface tracking, tiebreakers)
- Diffing what the *upstream* sees, not just what your devices report — with an observer per side so the parallel data planes stay isolated
- Measuring failover with in-flight probes and a current-side baseline, so "the new pair is fine" is a number, not a feeling
- The same rehearsal pattern applies to any swap: vendor refresh, OS upgrade, or generational replacement

## Vendors Used

- Cisco IOL (current core pair)
- Arista cEOS (target core pair)
- FRR (2 upstream observers, one per side)
- Linux (test hosts for continuous ping)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Make the target Juniper cRPD instead and rerun — same rehearsal, different translation table"
- "Paste your own sanitized production configs as the current state — the rehearsal runs the same way"
- "Add an Arista cEOS access switch under the target pair and verify MSTP root placement and blocking ports before go/no-go"
- "Build the current side from my NetBox source of truth instead of the description"
- "Add a rollback rehearsal: cut back to the current pair and measure the loss window in reverse"

## Why This Matters

Vendor refreshes fail on the lines that translate *syntactically* but not *behaviorally* — timer defaults, preempt semantics, route-selection tiebreakers. A rehearsal moves those discoveries from the cutover window into a lab, and turns the change-board conversation into a go/no-go report with evidence attached. For the L2 half of this pattern — RPVST+ to MSTP root verification on a campus core — see the [Cisco to Aruba AOS-CX companion prompt](cisco-to-aruba-aos-cx-migration.md).

## Related Resources

- [NetPilot Network Migration Lab](https://www.netpilot.io/network-migration-lab) — dedicated landing page for this workflow
- [Blog: Cisco to Aruba (AOS-CX) Migration — Translation Table + Lab Validation](https://www.netpilot.io/blog/cisco-to-aruba-migration-lab)
- [RFC 5798 — VRRP Version 3](https://datatracker.ietf.org/doc/html/rfc5798)
- [Related: Cisco to Aruba AOS-CX Migration](cisco-to-aruba-aos-cx-migration.md) — the L2/STP campus variant of this rehearsal
- [Related: Vendor Migration — Cisco IOS to Arista EOS](vendor-migration-cisco-to-arista.md) — deeper dive on behavior equivalence between parallel topologies
- [Related: Change Validation Workflow](change-validation-workflow.md) — the underlying mirror → snapshot → apply → diff pattern
- [Related: NetBox Site → Digital Twin](netbox-site-twin-rehearsal.md) — build the current side from your source of truth

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
