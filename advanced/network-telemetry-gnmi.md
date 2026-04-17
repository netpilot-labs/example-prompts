# Network Telemetry with gNMI Streaming

A multi-vendor telemetry lab exporting real-time operational state via gNMI — the modern replacement for SNMP polling, used for intent-based networking, observability pipelines, and AIOps.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a multi-vendor telemetry lab: 2 Cisco IOL routers, 2 Arista cEOS switches, and 1 Nokia SR Linux router, connected in a hub-and-spoke where all 4 edge devices connect to a central Nokia SR Linux "aggregator". Enable gNMI on all devices (mTLS encrypted, port 9339 standard) with a shared test CA. Configure dial-in telemetry subscriptions from an external collector (simulated by an additional Linux host) to stream the following per-device paths: interface counters (YANG path `/interfaces/interface/state/counters`), BGP session state, CPU and memory utilization, every 10 seconds. Enable OSPF area 0 between the 5 devices for basic reachability. Verify gNMI Get requests work, Subscribe mode delivers streaming updates, and vendor YANG models are queryable with correct paths.

## What You'll Build

- 5-device multi-vendor topology
- 1 Linux host as gNMI collector
- gNMI streaming telemetry over mTLS
- OpenConfig + vendor-specific YANG queries
- Sub-minute telemetry intervals

## Concepts Demonstrated

- Why gNMI replaced SNMP (push vs poll, structured YANG data vs OID trees)
- OpenConfig YANG vs native vendor YANG tradeoffs
- Dial-in vs dial-out telemetry patterns
- mTLS for gNMI (certificates, SANs, trust chains)
- Integration points for TSDBs (InfluxDB, Prometheus) and AIOps platforms

## Vendors Used

- Cisco IOL (2 routers)
- Arista cEOS (2 switches)
- Nokia SR Linux (1 aggregator)
- Linux (collector)

## Difficulty

⭐⭐⭐ Advanced

## Variations to Try

- "Replace gNMI dial-in with dial-out (device initiates connection to collector)"
- "Add gRIBI for programmatic routing injection alongside gNMI for state observation"
- "Layer this on top of a full EVPN-VXLAN fabric and stream BGP EVPN state"
- "Compare OpenConfig YANG path with each vendor's native path for the same data"

## Related Resources

- [gNMI Specification](https://github.com/openconfig/reference/tree/master/rpc/gnmi)
- [OpenConfig YANG models](https://github.com/openconfig/public)
- [Related: Network-as-Code with Ansible](network-as-code-with-ansible.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
