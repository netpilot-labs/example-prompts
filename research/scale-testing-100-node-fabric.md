# Scale Testing 100-Node CLOS Fabric

A 100-node CLOS fabric for scale testing — 4 spines, 96 leaves in 4 PODs, EVPN overlay, measurement node. The template for fabric convergence and scale-effect studies.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io) (enterprise plan recommended for 100-node lab):

> Build a 100-node CLOS fabric: 4 spine routers and 96 leaf routers arranged in 4 PODs of 24 leaves each, all using FRR. Spine routers in AS 65000, each leaf in its own AS 65001-65096 for eBGP underlay. Enable BGP EVPN address family for leaf-to-leaf Type-2 and Type-5 route exchange. Configure 10 VNIs (VNI 10100-10109) mapped to 10 VLANs per leaf. Advertise 5 unique /32 loopback prefixes from each leaf (total 480 prefixes). Place 1 host per leaf. Include a Linux measurement node with tcpdump, tshark, iperf3, and tc/netem for scripted impairment and convergence measurement. Connect the measurement node to spine uplinks for full-fabric packet capture visibility.

## What You'll Build

- 4 spine FRR routers
- 96 leaf FRR routers (24 per POD × 4 PODs)
- 96 Linux hosts (one per leaf)
- 1 Linux measurement node with fabric-wide visibility
- eBGP underlay + BGP EVPN overlay with 10 VNIs
- 480 total loopback prefixes
- ~200 virtual links

## Concepts Demonstrated

- Large-scale CLOS fabric convergence testing
- EVPN BUM replication at scale (96 VTEPs, 10 VNIs each)
- Cold convergence measurement methodology
- Churn propagation studies
- Route table scale effects at ~500-prefix tier

## Vendors Used

- FRRouting (100 routers — chosen for container efficiency at scale)
- Linux endpoints (96 hosts + 1 measurement node)

## Difficulty

⭐⭐⭐ Advanced — requires enterprise plan and scale testing methodology

## Variations to Try

- "Scale up to 200 leaves in 8 PODs for larger fabric studies"
- "Replace spine FRR with Arista cEOS for mixed-vendor scale testing"
- "Add 5 route reflectors for iBGP scale study instead of eBGP"
- "Reduce to 50 nodes for faster iteration on specific convergence scenarios"
- "Add cross-POD BUM replication stress testing with simultaneous multi-VNI traffic"

## Why This Matters

Scale testing at 100+ nodes used to require dedicated physical lab gear — hundreds of switches, weeks of cabling, significant capital expense. Cloud-hosted labs with FRR containers collapse this to a single prompt deploying in minutes, making scale-testable properties (cold convergence, churn propagation, BUM replication scale, memory footprint) accessible to research teams without physical infrastructure budgets.

Use cases:
- **Hyperscaler fabric engineering** — validate topology changes against cold convergence thresholds
- **BGP timer and feature tuning research** — measure effects at realistic fabric scale
- **EVPN scale studies** — BUM replication, Type-2 route flood testing
- **Pre-deployment validation** — test production-equivalent topology behavior before rollout

Limitations: line-rate traffic requires hardware testers (Keysight/Spirent). Very large scale (1000+ nodes) exceeds single-VM lab capacity.

## Related Resources

- [NetPilot blog: Scale Testing a 100-Node Network Fabric Without Physical Hardware](https://www.netpilot.io/blog/scale-testing-100-node-fabric)
- [Network Research Lab hub](https://www.netpilot.io/network-research-lab)
- [Related: Clos Fabric BGP Underlay](../data-center/clos-fabric-bgp-underlay.md)
- [Related: Leaf-Spine EVPN-VXLAN Symmetric IRB](../data-center/leaf-spine-evpn-vxlan-symmetric-irb.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
