# Mesh Network Research Experiments

A mesh topology with FRR routers running multiple routing protocols side-by-side, plus a Linux control node for link impairment. The template for reproducible mesh network research experiments.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a mesh network research lab with 8 FRR routers arranged as a mesh topology — each router has 3-4 neighbors, forming a richly connected graph. Enable BGP, OSPF, IS-IS, and Babel on every router so all four protocols can be compared on the same topology. Advertise a loopback prefix from each router. Add 2 host endpoints at router1 and router5 for traffic generation with iperf3 and ping. Add a Linux control node connected to every link with tc and netem pre-installed for scripted packet loss, latency, and link flap injection. I want to run protocol convergence comparisons under different impairment conditions.

## What You'll Build

- 8 FRR routers (full-mesh-ish topology, each with 3-4 neighbors)
- All 4 routing protocols running concurrently (BGP, OSPF, IS-IS, Babel)
- 2 host endpoints for traffic generation
- Linux control node with tc/netem for impairment scripts
- Loopback prefix per router for full routing table population

## Concepts Demonstrated

- Multi-protocol routing on a single mesh topology
- Convergence comparison under controlled packet loss
- Scripted link impairment via tc/netem
- Reproducible mesh network experimental methodology

## Vendors Used

- FRRouting (8 routers — open-source, no licensing)
- Linux endpoints (hosts + control node)

## Difficulty

⭐⭐⭐ Advanced — assumes familiarity with routing protocol internals and mesh research workflows

## Variations to Try

- "Increase to 16 routers for larger-scale mesh experiments"
- "Add Cisco IOL and Arista cEOS routers to compare commercial NOS behavior against FRR in the same topology"
- "Enable wireguard tunnels between non-adjacent routers to simulate partial mesh over overlay"
- "Add rate-limited links via tc/netem to test protocol behavior over constrained paths"
- "Run correlated packet loss (bursty) instead of random loss to model more realistic lossy channels"

## Why This Matters

Mesh network research for defense, academic, and industry teams traditionally relies on CORE/EMANE or ns-3 — both excellent tools but with self-hosted setup overhead and steep learning curves. This cloud-hosted AI-built lab template collapses iteration time from hours to minutes per experiment, which matters when the research workflow involves sweeping across many topologies, impairment conditions, and protocol combinations.

Use cases:
- **Protocol convergence research** — comparing Babel, OSPF, IS-IS under varying link conditions
- **Reproducibility** — ship a prompt instead of a tarball to peer-review teams
- **Academic paper experiments** — deterministic setup for citation reproducibility
- **Defense research program milestones** — rapid iteration on tactical network models
- **Community mesh network protocol development** — prototype before deploying to a real mesh

## Related Resources

- [NetPilot blog: AI-Powered MANET Research Labs](https://www.netpilot.io/blog/ai-manet-research-lab)
- [NetPilot blog: OSPF vs Babel Under Link Failure](https://www.netpilot.io/blog/ospf-vs-babel-link-failure)
- [Network Research Lab hub](https://www.netpilot.io/network-research-lab)
- [FRRouting project](https://frrouting.org/)
- [Related: All Vendors OSPF Area 0](../multi-vendor/all-vendors-ospf-area-0.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
