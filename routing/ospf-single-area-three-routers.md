# OSPF Single Area: Three Router Lab

The foundational OSPF lab. Three routers in Area 0 with loopback advertisement and adjacency verification, perfect for CCNA preparation and OSPF fundamentals.

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

## From ChatGPT

The same triangle from a ChatGPT chat, first as a Cisco Packet Tracer file, then on real Cisco IOS. Install NetPilot from [its listing in the ChatGPT plugin directory](https://chatgpt.com/plugins/plugin_asdk_app_6acaccdeab748191a29804ffe6127f32), pick NetPilot in the composer and paste the first prompt:

> Make me a CCNA practice lab as a Packet Tracer file: three Cisco routers, R1, R2 and R3, connected in a triangle with point-to-point links from 10.0.0.0/30, all in OSPF area 0, each with a loopback (1.1.1.1/32, 2.2.2.2/32 and 3.3.3.3/32) advertised into OSPF. Include the router configs so OSPF comes up when I open the file.

In the recorded run ChatGPT worked for 54 seconds and returned `CCNA-OSPF-Triangle-R1-R2-R3-20261109.pkt`: Packet Tracer 9.0, 3 routers, 3 links, the OSPF configs inside, no validation warnings. Then, in the same chat:

> Now build the same lab on real Cisco routers on my lab VM, then show me the OSPF neighbors on every router and the OSPF routes on R1.

ChatGPT started the lab VM, deployed three Cisco IOL routers on IOS 17.12.1 and read the routers back: two FULL neighbors on every router, and on R1 both remote loopbacks as OSPF routes plus two equal-cost paths to the R2 to R3 link. Open the lab viewer link from the answer to run `show ip ospf neighbor` yourself.

Watch it built and read every step: [NetPilot in ChatGPT](https://www.netpilot.io/blog/netpilot-in-chatgpt). Other assistants: [the connection guide](https://www.netpilot.io/docs/agent-route).

## Related Resources

- [NetPilot blog: NetPilot in ChatGPT, a Packet Tracer lab and real Cisco IOS from the chat](https://www.netpilot.io/blog/netpilot-in-chatgpt)
- [NetPilot blog: OSPF Configuration Lab Guide](https://www.netpilot.io/blog/ospf-configuration-lab-guide)
- [Related: OSPF Multi-Area with ABR](ospf-multi-area-with-abr.md)
- [RFC 2328: OSPF Version 2](https://datatracker.ietf.org/doc/html/rfc2328)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io/?prompt=Build%20a%203-router%20OSPF%20single-area%20lab%20with%20Cisco%20IOL.%20R1%2C%20R2%2C%20and%20R3%20are%20connected%20in%20a%20triangle%20topology%20%28R1-R2%2C%20R2-R3%2C%20R1-R3%29%20using%20point-to-point%20links%20in%20the%2010.0.0.0%2F30%20range.%20All%20interfaces%20in%20OSPF%20Area%200.%20Each%20router%20has%20a%20loopback%20%281.1.1.1%2F32%2C%202.2.2.2%2F32%2C%203.3.3.3%2F32%29%20advertised%20into%20OSPF.%20Verify%20OSPF%20neighbor%20adjacencies%20%28FULL%20state%29%2C%20confirm%20DR%2FBDR%20election%20on%20multi-access%20segments%20%28if%20any%29%2C%20and%20check%20that%20each%20router%20has%20routes%20to%20all%20three%20loopbacks%20in%20its%20routing%20table.&vendor=cisco)
