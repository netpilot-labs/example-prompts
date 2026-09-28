# Source-of-Truth Queries: What to Ask an AI Connected to Your NetBox or Nautobot

Once NetPilot's read-only integration with your source of truth is in place, it answers in plain English. This is the query playbook, from IPAM lookups to changelog forensics.

> **Requires NetPilot's NetBox or Nautobot integration**, read-only and custom-built for your workflow by NetPilot's team. See [NetPilot Integrations](https://www.netpilot.io/integrations).

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io/sign-in) (with a NetBox or Nautobot integration in place):

> Audit my NetBox site DC-East using the integration: list every device with its role, platform, and rack position. Flag interfaces with no description, and routed (non-switchport) interfaces with no IP assigned. Find the prefixes in this site that are more than 80% utilized and suggest which free prefixes could take the overflow. Then summarize what changed in this site's records over the last 14 days from the changelog. Present it as a one-page site health report I can paste into a change-advisory ticket.

*Swap DC-East (and the rack/prefix names in the variations) for your own before running. Running Nautobot instead of NetBox? Say "my Nautobot location DC-East", swap both the tool name and site → location, since Nautobot 2.x models sites as Locations.*

## What You'll Build

- A one-page site health report straight from your own records: no export, no spreadsheet
- Hygiene flags: undescribed interfaces, unassigned IPs, near-full prefixes
- A 14-day changelog summary for audit trails
- All read-only: the agent can report on your records but never modify them

## Concepts Demonstrated

- The source of truth as a conversational interface: IPAM, DCIM, and changelog queries in plain English
- Read-only allow-lists: reporting without write risk
- Records → action: any finding can become a lab ("build me a twin of the flagged segment") in the same chat

## Vendors Used

- None deployed by default: this is a records-only prompt, and labs come from the follow-ups

## Difficulty

⭐ Beginner

## Variations to Try

- "Find me a free /28 in the 10.20.0.0/16 datacenter prefix and show which VLAN it should live in"
- "Show the rack elevation for rack DC-E-R07 and what changed in it this quarter"
- "Which devices in Nautobot have a config context that sets OSPF, and what area are they in?"
- "List the job results from the last week and summarize the failures" (Nautobot: job logs are readable, jobs are never runnable)
- "Build a lab replicating the two devices with the most changelog churn this month"

## Why This Matters

Most teams use their NetBox/Nautobot at 10% of its value because every question needs an API script or five UI clicks. A read-only agent turns the same records into answers, and because the connector structurally cannot write, the barrier to enabling it is a token, not a risk review.

## Related Resources

- [NetPilot Integrations: AI agent integration with your network stack](https://www.netpilot.io/integrations)
- [Related: NetBox Site → Digital Twin Rehearsal](../change-validation/netbox-site-twin-rehearsal.md)
- [Related: Source-of-Truth Drift Detection](../change-validation/sot-drift-detection.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io/sign-in)
