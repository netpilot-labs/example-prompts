# FRR Babel Mesh Network

A mesh network running FRR's Babel routing protocol — purpose-built for lossy, dynamic topologies. Used for MANET research, community mesh operator testing, and protocol comparison against OSPF.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a mesh network lab with 6 FRR routers running Babel. Connect them in a partial mesh: R1-R2, R2-R3, R3-R4, R4-R5, R5-R6, R1-R3, R2-R5, R3-R6 as links (non-trivial path diversity, multiple ECMP options). Enable Babel on all interfaces. Also run OSPF on all routers so both protocols can be compared side-by-side on the same topology. Advertise a unique loopback /32 from each router. Add a Linux control node with tc/netem for link impairment. Inject 20% packet loss on the R2-R3 and R4-R5 links and compare how Babel vs OSPF respond to the impairment — show neighbor state and route tables for both protocols.

## What You'll Build

- 6 FRR routers in partial mesh (richly connected, not full)
- Both Babel and OSPF running simultaneously on all routers
- 1 Linux control node with tc/netem for impairment injection
- Unique loopback prefix per router
- Side-by-side protocol comparison under packet loss

## Concepts Demonstrated

- Babel's distance-vector approach vs OSPF's link-state for mesh convergence
- How Babel handles lossy links vs OSPF's dead-interval-based failure detection
- Multi-path routing differences between the two protocols
- Reproducible mesh protocol comparison methodology

## Vendors Used

- FRRouting (6 routers — Babel + OSPF daemons, open-source)
- Linux control node (tc/netem for impairment)

## Difficulty

⭐⭐⭐ Advanced — assumes routing protocol knowledge and mesh topology familiarity

## Variations to Try

- "Add IS-IS to the comparison — run all three protocols simultaneously"
- "Change the impairment to correlated bursty loss to model wireless channel conditions"
- "Scale to 12 routers for a larger mesh study"
- "Add link asymmetry: different loss rates in each direction on R2-R3"
- "Enable Babel's automatic metric estimation based on loss rate and compare it to static OSPF cost"

## Why This Matters

Babel was designed specifically for mesh networks where OSPF struggles: high topology change frequency, lossy links, and partial connectivity. It is the default routing protocol for many MANET (Mobile Ad-hoc Network) systems and community mesh deployments.

Use cases:
- **MANET and tactical network research** — defense labs and academic teams studying protocol behavior under adversarial conditions
- **Community mesh operators** (Althea, Guifi.net adjacent) evaluating Babel vs OSPF for their deployments
- **Protocol researchers** publishing comparative studies on mesh routing behavior
- **Open networking engineers** evaluating FRR Babel for wireless/mesh overlay networks

## Related Resources

- [NetPilot blog: FRRouting Cloud Labs](https://www.netpilot.io/blog/frr-cloud-lab-guide)
- [NetPilot blog: AI-Powered MANET Research Labs](https://www.netpilot.io/blog/ai-manet-research-lab)
- [Network Research Lab hub](https://www.netpilot.io/network-research-lab)
- [Babel RFC 8966](https://www.rfc-editor.org/rfc/rfc8966)
- [Related: Mesh Network Research Experiments](../research/mesh-network-experiments.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
