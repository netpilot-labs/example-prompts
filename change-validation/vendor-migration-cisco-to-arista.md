# Vendor Migration — Cisco IOS to Arista EOS

Test a production vendor migration safely. Spin up the old Cisco topology, the new Arista topology, and run both in parallel to validate behavior equivalence before cutting over.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a vendor migration validation lab. Deploy the "old" topology: 3 Cisco IOL routers (OLD-R1, OLD-R2, OLD-R3) in OSPF area 0 with eBGP to an upstream AS 65100, loopbacks 1.1.1.1/32, 2.2.2.2/32, 3.3.3.3/32, all advertising 192.168.0.0/22 downstream. Deploy a parallel "new" topology: 3 Arista cEOS switches (NEW-R1, NEW-R2, NEW-R3) with identical OSPF + BGP + addressing configuration. Both topologies connect to the same simulated upstream AS 65100. Verify that (1) routing tables match between old and new at each router pair, (2) BGP advertisements from both topologies appear identical to the upstream, (3) OSPF LSA contents are equivalent, (4) failure behavior matches when a link goes down in either topology.

## What You'll Build

- 6 routers total (3 Cisco + 3 Arista, running in parallel)
- Identical protocols and addressing on both sides
- Shared upstream for comparison
- Side-by-side behavior validation

## Concepts Demonstrated

- How to de-risk a vendor migration with parallel deployment
- What "behaviorally equivalent" actually means (protocol-level, not syntax-level)
- Detecting subtle differences: timer defaults, tiebreakers, authentication formats
- Operational value of digital-twin migration rehearsals
- Why this pattern applies to ANY migration (old-to-new versions, vendor swaps, OS upgrades)

## Vendors Used

- Cisco IOL (old topology, 3 devices)
- Arista cEOS (new topology, 3 devices)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Migrate Cisco → Juniper instead and compare configuration translation accuracy"
- "Add a BGP policy layer and test filter/prefix-list equivalence"
- "Extend to Layer 2: compare spanning-tree behavior vs MLAG across vendors"
- "Automate the comparison with Batfish for programmatic diff"

## Why This Matters

Vendor migrations are the #1 pain point for enterprises locked into expiring support contracts. Running both topologies in parallel — before production cutover — prevents the "we thought it would work the same way" disasters. This is a core NetPilot use case.

## Related Resources

- [NetPilot blog: Network Change Validation Sandbox](https://www.netpilot.io/blog/network-change-validation-sandbox)
- [NetPilot Network Digital Twin](https://www.netpilot.io/network-digital-twin)
- [Related: Firewall Rule Deployment Test](firewall-rule-deployment.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
