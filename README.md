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

- [OSPF Multi-Area with ABR](routing/ospf-multi-area-with-abr.md) ⭐⭐
- [eBGP Three-AS Multi-Vendor](routing/bgp-ebgp-three-as.md) ⭐⭐
- [BGP Route Reflector Cluster](routing/bgp-route-reflector-cluster.md) ⭐⭐⭐

### 🏢 Data Center
Modern leaf-spine, EVPN-VXLAN, and AI workload fabrics.

- [Leaf-Spine EVPN-VXLAN with Symmetric IRB](data-center/leaf-spine-evpn-vxlan-symmetric-irb.md) ⭐⭐⭐
- [AI Cluster RoCEv2 Fabric](data-center/ai-cluster-rocev2-fabric.md) ⭐⭐⭐

### 🌐 Service Provider
MPLS L3VPN, Segment Routing, traffic engineering.

- [MPLS L3VPN Basic](service-provider/mpls-l3vpn-basic.md) ⭐⭐
- [Segment Routing MPLS](service-provider/segment-routing-mpls.md) ⭐⭐⭐

### 🔒 Security
Firewall zones, microsegmentation, zero-trust patterns.

- [Firewall DMZ Zones (Palo Alto)](security/firewall-dmz-zones-palo-alto.md) ⭐⭐
- [Zero-Trust Microsegmentation](security/zero-trust-microsegmentation.md) ⭐⭐⭐

### 🔀 Multi-Vendor Interop
Where vendors must talk to each other — NetPilot's superpower.

- [Cisco + Arista EVPN-VXLAN Interop](multi-vendor/cisco-arista-evpn-vxlan-interop.md) ⭐⭐⭐

### ✅ Change Validation
Test changes safely before pushing to production.

- [Firewall Rule Deployment Test](change-validation/firewall-rule-deployment.md) ⭐⭐

### 🛠️ Advanced
Automation, integration, and complex scenarios.

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
