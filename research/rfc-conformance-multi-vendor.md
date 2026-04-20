# Multi-Vendor RFC Conformance Lab

A focused two-vendor lab for RFC conformance testing. The template vendor PSIRT teams and operator security teams use for interop and behavioral conformance checks.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a two-vendor RFC conformance test lab: 1 Cisco IOL router (as leaf1) and 1 Juniper cRPD router (as leaf2), both connected to a shared underlay via an Arista cEOS spine. Cisco in AS 65001, Juniper in AS 65002, Arista in AS 65000 for the spine-leaf eBGP underlay. Enable BGP EVPN address family for leaf-leaf overlay. Configure VLAN 100 mapped to VNI 10100 on both leaves. Advertise one /32 host route from each leaf as a Type-2 EVPN route. Add a Linux test harness node with Python 3, Scapy, tshark, and a git-cloneable test-suite directory for conformance scripts. Goal: run positive, interop, and negative RFC 7432 conformance tests across the vendor pair.

## What You'll Build

- 1 Cisco IOL leaf
- 1 Juniper cRPD leaf
- 1 Arista cEOS spine
- 1 Linux test harness node
- BGP EVPN overlay across vendors
- Pre-configured for automated conformance script execution

## Concepts Demonstrated

- Positive RFC conformance testing (specified behavior validation)
- Interop conformance testing (joint behavior across vendor pair)
- Negative RFC conformance testing (malformed input handling)
- Automated test harness pattern for regression suites
- Vendor-pair pre-release testing workflow

## Vendors Used

- Cisco IOL (conformance target 1)
- Juniper cRPD (conformance target 2)
- Arista cEOS (spine)
- Linux test harness node

## Difficulty

⭐⭐⭐ Advanced — assumes RFC reading familiarity and conformance-testing methodology

## Variations to Try

- "Replace Juniper with Arista cEOS for Cisco-Arista EVPN conformance"
- "Replace Juniper with Nokia SR Linux for Cisco-Nokia Segment Routing conformance (RFC 8665)"
- "Add MPLS L3VPN (RFC 4364) overlay on top of existing EVPN for multi-RFC interop"
- "Pin Cisco IOS version to a specific release (via enterprise BYOI) to test against CVE-affected versions"
- "Add a fuzzer endpoint to extend into negative conformance sweeps"

## Why This Matters

RFC conformance testing is the gap between "we implemented the feature" and "our implementation matches the spec when combined with other vendors." Annual EANTC events cover a snapshot of industry-wide interop. Commercial conformance suites (Fortra, Spirent, Keysight) are thorough but expensive and hardware-bound. Cloud-hosted multi-vendor labs fit the rapid-iteration tier:

- **Vendor PSIRT teams** — pre-release conformance checks between releases
- **Operator security teams** — validate candidate vendor gear against RFC edge cases
- **Standards implementers** — verify implementations as they build against draft or published RFCs
- **Academic researchers** — formal methods work validated against real implementations

## Related Resources

- [NetPilot blog: Multi-Vendor RFC Compliance Testing](https://www.netpilot.io/blog/rfc-compliance-multi-vendor-testing)
- [NetPilot blog: Debugging Cisco-Juniper EVPN Interop Issues](https://www.netpilot.io/blog/debugging-cisco-juniper-evpn-interop)
- [Network Research Lab hub](https://www.netpilot.io/network-research-lab)
- [EANTC Test Reports](https://wiki.eantc.de/wiki/publicreports/view/Main/)
- [Related: Cross-Vendor EVPN Bug Reproduction](./cross-vendor-evpn-bug-reproduction.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
