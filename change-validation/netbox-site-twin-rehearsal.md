# NetBox Site → Digital Twin — Rehearse a Change from Your Source of Truth

Point the agent at your NetBox, name a site, and get a runnable twin of what's actually deployed — then rehearse the change on the twin before production ever sees it.

> **Requires the NetBox connector** — read-only, added from the chat in about two minutes. See [NetPilot Integrations](https://www.netpilot.io/integrations).

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io) (with your NetBox connector enabled):

> Using my NetBox connector, pull site DC-East: devices, device roles, interfaces, cabling, the IP addresses assigned to each interface, and the site's prefixes. Build a matching lab — use Arista cEOS for the leaf switches, Cisco IOL for the core routers, and FRR for anything NetBox lists as a Linux router — with the same hostnames, interface names, and interface IP addresses NetBox records. Bring up the IGP exactly as deployed (OSPF area 0 on the core, according to the config contexts). Then rehearse this change: move leaf DC-E-LEAF-03's uplinks from CORE-1 to CORE-2, and show me a before/after diff of the routing table and OSPF adjacencies so I can prove the failover path works before we touch production.

## What You'll Build

- A runnable replica of a real NetBox site — hostnames, interfaces, and addressing from your own records
- Multi-vendor mix mapped from NetBox device roles (Arista cEOS + Cisco IOL + FRR)
- The candidate change applied in the lab only, with pre/post state snapshots
- A routing-table and adjacency diff as the sign-off evidence

## Concepts Demonstrated

- Source of truth → running lab: NetBox records become a topology you can SSH into, no exporter scripts or hand-maintained YAML
- Read-only ingest — the agent queries NetBox but cannot create, update, or delete records
- Change rehearsal on a twin: the change-window failure mode is discovered in the lab, not in production
- Config contexts as deployable intent, verified on real NOS CLIs

## Vendors Used

- Arista cEOS (leaves)
- Cisco IOL (core)
- FRR (Linux routers)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Pull site DC-West instead and build only the devices tagged `edge`"
- "Use the NetBox changelog to list what changed in this site in the last 30 days, and replay the latest change in the lab first"
- "Rehearse an OSPF-to-IS-IS migration for this site on the twin, one device at a time"
- "After the rehearsal, generate an NRFU-style acceptance checklist from the diff"

## Why This Matters

Every twin-building pipeline before this required exporter scripts (nrx/netreplica-style), device-type mappings, and YAML you maintain forever. With a read-only connector, the source of truth *is* the lab spec — and the lab is real NOS images you can verify on, not a mathematical model.

## Related Resources

- [NetPilot Integrations — NetBox, Nautobot & Nornir connectors](https://www.netpilot.io/integrations)
- [NetPilot Network Digital Twin](https://www.netpilot.io/network-digital-twin)
- [Related: Change Validation Workflow](change-validation-workflow.md)
- [Related: Source-of-Truth Drift Detection](sot-drift-detection.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
