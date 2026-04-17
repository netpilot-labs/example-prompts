# OSPF Area Redesign — Migration Validation

You're splitting a large single-area OSPF domain into multiple areas for scaling. Build the old and new topologies in parallel to prove the new design works before cutting over.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build an OSPF area redesign validation lab. Deploy the "current" single-area design: 6 Cisco IOL routers (R1-R6) in a partial mesh, ALL interfaces in OSPF Area 0, loopbacks 1.1.1.1/32 through 6.6.6.6/32 advertised. Deploy the "proposed" multi-area design in parallel: same 6 routers with the same physical topology, but R1-R2 in Area 1, R3-R4 in Area 0 (new backbone), R5-R6 in Area 2, and R3 acting as ABR between Area 0 and Area 1 while R4 acts as ABR between Area 0 and Area 2. Both designs advertise the same prefixes. Verify: (1) reachability is identical between current and proposed at all 6 router pairs, (2) LSA database sizes shrink significantly in the proposed design (inter-area summarization works), (3) convergence time improves when a leaf link fails (LSA flooding is bounded by area), (4) no routing loops or black holes introduced.

## What You'll Build

- 12 Cisco IOL routers total (6 current + 6 proposed, running in parallel)
- Same physical topology with different OSPF configurations
- Side-by-side LSA database comparison
- Convergence time testing

## Concepts Demonstrated

- Why large single-area OSPF doesn't scale (LSA flooding, SPF computation)
- Area design principles — where to place ABRs
- Stub/totally-stubby area options for LSA reduction
- Validation methodology for any protocol redesign
- How to prove "the new way is better" before migration day

## Vendors Used

- Cisco IOL (all 12 routers)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Make Area 1 a stub area and Area 2 a totally stubby area to test LSA filtering"
- "Add OSPF manual area-range summarization at the ABRs"
- "Simulate a link flap and compare convergence time between the two designs"
- "Test the migration path: start with all Area 0 on real routers, then reconfigure area assignments incrementally"

## Why This Matters

OSPF area redesigns are one of the scariest migrations for network teams. They touch every router, change adjacency states, and can cause transient black holes. Doing it in a lab first — with a side-by-side comparison — is the safest path.

## Related Resources

- [Related: OSPF Multi-Area with ABR](../routing/ospf-multi-area-with-abr.md)
- [Related: Vendor Migration Cisco to Arista](vendor-migration-cisco-to-arista.md)
- [RFC 2328 — OSPF Version 2](https://datatracker.ietf.org/doc/html/rfc2328)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
