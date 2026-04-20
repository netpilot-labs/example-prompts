# BGP Convergence Research Experiment

A 5-router BGP convergence research lab with partial mesh topology, measurement scripting, and impairment injection. The template for reproducible BGP convergence studies.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a BGP convergence research lab with 5 FRR routers in a partial mesh: R1-R5, with R1-R2, R2-R3, R3-R4, R4-R5, R1-R3, R2-R5 as the only links (forms a non-trivial but small research topology). Each router in its own AS (65001-65005) for eBGP. Default BGP timers unless overridden. Advertise 1 loopback prefix from every router plus a 100-prefix synthetic BGP table from R1 using AS_PATH prepending for distinction. Add a Linux control node with tcpdump, tshark, and tc/netem pre-installed for measurement and scripted impairment. Connect the control node to every inter-router link as a tap for traffic capture.

## What You'll Build

- 5 FRR routers (R1-R5) with partial-mesh eBGP
- 1 Linux control node with tap access to all links
- 100+5 prefix BGP table for convergence measurement
- Default timers as baseline
- Capture and impairment tooling pre-configured

## Concepts Demonstrated

- Minimum viable topology for BGP convergence research
- Scripted measurement methodology (PCAP + CLI polling)
- Controlled impairment via tc/netem
- Baseline vs variable experimental design
- Reproducible measurement across trials

## Vendors Used

- FRRouting (5 routers)
- Linux control node

## Difficulty

⭐⭐⭐ Advanced — assumes BGP research methodology familiarity

## Variations to Try

- "Enable route flap damping on R3 with Cisco default parameters"
- "Add graceful restart capabilities to the BGP sessions and measure restart-induced convergence"
- "Replace FRR with Cisco IOL on 2 routers for commercial NOS behavior comparison"
- "Scale to 20 routers in full iBGP mesh within a single AS for scale studies"
- "Add asymmetric link capacities via tc/netem to study convergence under non-uniform paths"

## Why This Matters

BGP convergence research has been dominated by ns-3 simulation (fast, scalable, but not faithful to vendor behavior) and hardware testbeds (faithful but expensive and slow to iterate). Cloud-hosted labs with real routing daemons add a middle ground — real protocol behavior with fast iteration, enabling 30-trial statistical sweeps in minutes instead of days.

Use cases:
- **Academic BGP research** — hypothesis-test-iterate cycles compatible with paper timelines
- **Vendor product testing** — validate timer changes, feature rollouts against production-like convergence
- **Operator planning** — test candidate topology changes against current network's convergence behavior
- **Standards work** — validate proposed RFC behavior changes experimentally

## Related Resources

- [NetPilot blog: BGP Convergence Research Lab](https://www.netpilot.io/blog/bgp-convergence-research-lab)
- [Network Research Lab hub](https://www.netpilot.io/network-research-lab)
- [Related: BGP eBGP Three AS](../routing/bgp-ebgp-three-as.md)
- [Related: BGP Route Reflector Cluster](../routing/bgp-route-reflector-cluster.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
