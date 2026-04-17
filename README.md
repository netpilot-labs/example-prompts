<p align="center">
  <a href="https://netpilot.io">
    <img src="https://netpilot.io/netpilot-logo.svg" alt="NetPilot" width="280" />
  </a>
</p>

<p align="center">
  <strong>Copy-paste prompts for NetPilot.</strong> Describe any network in plain English; deploy a working multi-vendor lab in 2 minutes.
</p>

<p align="center">
  <a href="https://app.netpilot.io">Open NetPilot</a> &middot;
  <a href="https://netpilot.io">Website</a> &middot;
  <a href="https://netpilot.io/docs">Docs</a> &middot;
  <a href="https://netpilot.io/blog">Blog</a>
</p>

---

## What is this?

A curated library of natural-language prompts you can copy and paste directly into [NetPilot](https://app.netpilot.io). Each prompt builds a fully working multi-vendor network lab — real device CLIs, isolated cloud infrastructure, ready in 2 minutes.

**Vendors supported:** Cisco IOL · Juniper cRPD · Arista cEOS · Nokia SR Linux · Palo Alto PAN-OS · Fortinet FortiGate · FRR

## How to use

1. Browse the categories below
2. Open a prompt file
3. Copy the prompt block
4. Paste it into [app.netpilot.io](https://app.netpilot.io)
5. Watch your lab deploy

## Categories

### 🚦 Routing
Foundational and advanced routing protocol labs.

- [OSPF Single Area — Three Router Lab](routing/ospf-single-area-three-routers.md) ⭐
- [OSPF Multi-Area with ABR](routing/ospf-multi-area-with-abr.md) ⭐⭐
- [OSPF ↔ BGP Redistribution](routing/ospf-bgp-redistribution.md) ⭐⭐
- [eBGP Three-AS Multi-Vendor](routing/bgp-ebgp-three-as.md) ⭐⭐
- [IPv6 Dual-Stack Network](routing/ipv6-dual-stack.md) ⭐⭐
- [BGP Route Reflector Cluster](routing/bgp-route-reflector-cluster.md) ⭐⭐⭐
- [BGP Confederation](routing/bgp-confederation.md) ⭐⭐⭐
- [IS-IS Level 1/2 Hierarchical Backbone](routing/isis-level-1-2-backbone.md) ⭐⭐⭐
- [DMVPN Hub-and-Spoke](routing/dmvpn-hub-and-spoke.md) ⭐⭐⭐

### 🏢 Data Center
Modern leaf-spine, EVPN-VXLAN, and AI workload fabrics.

- [Clos Fabric with BGP Underlay (L3-Only)](data-center/clos-fabric-bgp-underlay.md) ⭐⭐
- [Leaf-Spine EVPN-VXLAN with Symmetric IRB](data-center/leaf-spine-evpn-vxlan-symmetric-irb.md) ⭐⭐⭐
- [Leaf-Spine EVPN-VXLAN with Asymmetric IRB](data-center/leaf-spine-evpn-vxlan-asymmetric-irb.md) ⭐⭐⭐
- [EVPN-VXLAN Multi-Site DCI](data-center/evpn-vxlan-multi-site-dci.md) ⭐⭐⭐
- [Multi-Tenant VRFs with EVPN](data-center/multi-tenant-vrfs-evpn.md) ⭐⭐⭐
- [AI Cluster RoCEv2 Fabric](data-center/ai-cluster-rocev2-fabric.md) ⭐⭐⭐

### 🌐 Service Provider
MPLS L3VPN, Segment Routing, traffic engineering.

- [MPLS L3VPN Basic](service-provider/mpls-l3vpn-basic.md) ⭐⭐
- [Segment Routing MPLS](service-provider/segment-routing-mpls.md) ⭐⭐⭐
- [SRv6 — Segment Routing over IPv6](service-provider/srv6-segment-routing-v6.md) ⭐⭐⭐
- [MPLS Traffic Engineering (SR-TE)](service-provider/mpls-traffic-engineering.md) ⭐⭐⭐
- [Inter-AS L3VPN Option B](service-provider/inter-as-vpn-option-b.md) ⭐⭐⭐

### 🔒 Security
Firewall zones, microsegmentation, zero-trust patterns.

- [Firewall DMZ Zones (Palo Alto)](security/firewall-dmz-zones-palo-alto.md) ⭐⭐
- [Firewall DMZ Zones (Fortinet)](security/firewall-dmz-zones-fortinet.md) ⭐⭐
- [IPsec VPN — Site-to-Site](security/ipsec-vpn-site-to-site.md) ⭐⭐
- [Zero-Trust Microsegmentation](security/zero-trust-microsegmentation.md) ⭐⭐⭐
- [DDoS Blackhole (RTBH)](security/ddos-rtbh-blackhole.md) ⭐⭐⭐

### 🔀 Multi-Vendor Interop
Where vendors must talk to each other — NetPilot's superpower.

- [Cisco + Arista EVPN-VXLAN Interop](multi-vendor/cisco-arista-evpn-vxlan-interop.md) ⭐⭐⭐
- [Cisco + Juniper MPLS L3VPN Interop](multi-vendor/cisco-juniper-mpls-l3vpn.md) ⭐⭐⭐
- [Juniper + Nokia IS-IS Interop](multi-vendor/juniper-nokia-isis.md) ⭐⭐⭐
- [All-Vendors OSPF Area 0 (5-vendor)](multi-vendor/all-vendors-ospf-area-0.md) ⭐⭐⭐

### ✅ Change Validation
Test changes safely before pushing to production.

- [Firewall Rule Deployment Test](change-validation/firewall-rule-deployment.md) ⭐⭐
- [Firmware Upgrade Failover Test](change-validation/firmware-upgrade-failover.md) ⭐⭐
- [BGP Policy Change Validation](change-validation/bgp-policy-change.md) ⭐⭐⭐
- [OSPF Area Redesign Migration](change-validation/ospf-area-redesign.md) ⭐⭐⭐
- [Data Center VLAN Migration](change-validation/data-center-vlan-migration.md) ⭐⭐⭐
- [OTV-to-EVPN DCI Migration](change-validation/otv-to-evpn-migration.md) ⭐⭐⭐
- [Vendor Migration — Cisco IOS to Arista EOS](change-validation/vendor-migration-cisco-to-arista.md) ⭐⭐⭐

### 🛠️ Advanced
Automation, integration, and complex scenarios.

- [QoS End-to-End Marking and Queuing](advanced/qos-end-to-end-marking.md) ⭐⭐⭐
- [Multicast PIM Sparse Mode](advanced/multicast-pim-sparse-mode.md) ⭐⭐⭐
- [Network Telemetry with gNMI Streaming](advanced/network-telemetry-gnmi.md) ⭐⭐⭐
- [Network-as-Code with Ansible](advanced/network-as-code-with-ansible.md) ⭐⭐⭐

## Difficulty Levels

- ⭐ **Beginner** — single protocol, 2-3 devices, foundational concepts
- ⭐⭐ **Intermediate** — multi-feature, 4-6 devices, real-world patterns
- ⭐⭐⭐ **Advanced** — complex topologies, multi-vendor interop, production-grade scenarios

## Contributing

We welcome community-contributed prompts. See [CONTRIBUTING.md](CONTRIBUTING.md) for the template and submission guide.

Have a prompt that worked great? [Open a PR](https://github.com/netpilot-labs/example-prompts/compare) or [suggest one in an issue](https://github.com/netpilot-labs/example-prompts/issues/new).

## Related Resources

| | |
|---|---|
| **NetPilot platform** | [app.netpilot.io](https://app.netpilot.io) |
| **Documentation** | [netpilot.io/docs](https://netpilot.io/docs) |
| **Blog tutorials** | [netpilot.io/blog](https://netpilot.io/blog) |
| **Community discussions** | [github.com/netpilot-labs/community](https://github.com/netpilot-labs/community) |
| **Status** | [status.netpilot.io](https://status.netpilot.io) |

## License

MIT — copy, fork, remix anything in this repo.
