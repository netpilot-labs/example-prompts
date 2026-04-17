# OSPF Single Area — Three Router Lab

The foundational OSPF lab. Three routers in Area 0 with loopback advertisement and adjacency verification — perfect for CCNA preparation and OSPF fundamentals.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a 3-router OSPF single-area lab with Cisco IOL. R1, R2, and R3 are connected in a triangle topology (R1-R2, R2-R3, R1-R3) using point-to-point links in the 10.0.0.0/30 range. All interfaces in OSPF Area 0. Each router has a loopback (1.1.1.1/32, 2.2.2.2/32, 3.3.3.3/32) advertised into OSPF. Verify OSPF neighbor adjacencies (FULL state), confirm DR/BDR election on multi-access segments (if any), and check that each router has routes to all three loopbacks in its routing table.

## What You'll Build

- 3 Cisco IOL routers in a triangle topology
- Single OSPF Area 0
- Point-to-point links between all pairs
- Loopback advertisement for each router

## Concepts Demonstrated

- OSPF neighbor discovery and adjacency formation
- States: DOWN → INIT → 2-WAY → EXSTART → EXCHANGE → LOADING → FULL
- LSA flooding within an area
- Cost calculation based on bandwidth
- Why single-area designs are fine for small networks

## Vendors Used

- Cisco IOL (all 3 routers)

## Difficulty

⭐ Beginner

## Variations to Try

- "Add R4 via a broadcast segment to observe DR/BDR election"
- "Modify OSPF cost on one link and watch path selection change"
- "Split the triangle into two areas with an ABR at R2"
- "Replace one router with Juniper cRPD to test multi-vendor OSPF"

## Related Resources

- [NetPilot blog: OSPF Configuration Lab Guide](https://netpilot.io/blog/ospf-configuration-lab-guide)
- [Related: OSPF Multi-Area with ABR](ospf-multi-area-with-abr.md)
- [RFC 2328 — OSPF Version 2](https://datatracker.ietf.org/doc/html/rfc2328)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
