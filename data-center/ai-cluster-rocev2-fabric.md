# AI Cluster RoCEv2 Lossless Fabric

A leaf-spine fabric tuned for AI/ML training traffic, with PFC, ECN, and ECMP hashing optimized for RDMA over Converged Ethernet (RoCEv2).

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a non-blocking 2-spine, 4-leaf fabric with all Arista cEOS, designed for an AI training cluster. Use eBGP underlay (spines in AS 65000, leaves in AS 65001-65004). Configure ECMP across both spines for symmetric load balancing. Enable PFC (Priority Flow Control) on traffic class 3 to support lossless RoCEv2, and enable ECN (Explicit Congestion Notification) marking on the same class for congestion signaling back to GPU endpoints. Connect 4 hosts to each leaf simulating GPU servers, all in a single tenant VLAN 100 (10.100.0.0/16) for east-west GPU-to-GPU traffic. Verify ECMP load distribution, PFC pause behavior under load, and ECN marking thresholds.

## What You'll Build

- 6-device leaf-spine fabric (2 spines + 4 leaves)
- 16 GPU-server hosts (4 per leaf)
- eBGP underlay with ECMP load balancing
- PFC class 3 for lossless RoCEv2
- ECN marking for congestion signaling
- Single flat L2 VLAN for east-west GPU traffic

## Concepts Demonstrated

- Why traditional Ethernet drops packets — and why AI workloads can't tolerate it
- How PFC + ECN combine to deliver lossless behavior without head-of-line blocking
- ECMP hashing decisions for elephant flows (GPU-to-GPU)
- Why traditional VLAN bridging is a bottleneck for AI clusters (and where VXLAN helps)
- The role of buffer tuning and traffic class isolation

## Vendors Used

- Arista cEOS (all devices)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Add a third spine and additional leaves to scale to 32 GPU hosts"
- "Add VXLAN overlay with VNI per tenant for multi-tenant AI hosting"
- "Replace one leaf with a Nokia SR Linux to test multi-vendor RoCEv2 interop"
- "Add a separate management network for out-of-band telemetry"

## Why This Matters in 2026

AI inference and training workloads have made lossless Ethernet a hard requirement. Hyperscalers and enterprises building on-prem AI clusters need fabrics that can sustain RDMA traffic without packet drops. This lab represents the modern foundation.

## Related Resources

- [NetPilot blog: RoCEv2 vs InfiniBand — AI Cluster Networking Compared](https://www.netpilot.io/blog/ai-cluster-networking-rocev2)
- [NetPilot blog: EVPN-VXLAN Data Center Fabric Guide](https://www.netpilot.io/blog/evpn-vxlan-data-center-guide)
- [RFC 8087 — The Benefits of Using Explicit Congestion Notification (ECN)](https://datatracker.ietf.org/doc/html/rfc8087)
- [IEEE 802.1Qbb — Priority-based Flow Control](https://standards.ieee.org/standard/802_1Qbb-2011.html)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
