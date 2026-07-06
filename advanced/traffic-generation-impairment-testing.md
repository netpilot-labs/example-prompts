# Traffic Generation & Impairment Testing — iperf3 Flows Over a Degraded WAN

Prove a path meets its throughput, loss, jitter, and latency targets while the link degrades under it — the software traffic-gen battery every functional test needs, run by the agent.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> Build a WAN path test lab: two sites, each with a Cisco IOL edge router, connected over two parallel WAN links — a primary and a backup. Put a Linux test host on each site LAN (10.10.1.0/24 at site A, 10.20.1.0/24 at site B), with OSPF between the routers preferring the primary link. Then run this test battery and give me a per-case pass/fail report with measured numbers: (1) baseline — iperf3 TCP and UDP from host A to host B over the primary link, report throughput, retransmits, loss, jitter, and RTT; (2) impairment — apply tc/netem on the backup link with 30ms delay, 5ms jitter, and 1% loss, fail the primary link, and prove the backup still sustains at least 500 Mbps TCP with the measured added latency; (3) QoS — send two simultaneous iperf3 UDP flows, one marked DSCP EF and one best-effort, congest the backup link, and report which flow kept its loss and jitter targets.

## What You'll Build

- 2 Cisco IOL edge routers, dual WAN links (primary + backup), OSPF path preference
- 2 Linux test hosts as traffic endpoints
- An executed 3-case test battery: baseline flows, failover under impairment, QoS under congestion
- A pass/fail report with measured throughput, loss, jitter, and RTT per case

## Concepts Demonstrated

- Software traffic generation with iperf3 — real TCP/UDP flows, not modeled estimates
- Link impairment with tc/netem — modeling WAN delay, jitter, and loss on a chosen interface
- DSCP marking per flow and verifying QoS treatment under congestion
- Measuring failover behavior with traffic in flight, not just adjacency state
- Agent-run testing: the battery executes from one plain-English request; every number is reproducible by hand over SSH

## Vendors Used

- Cisco IOL (2 routers)
- Linux (2 test hosts)

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Make the backup a MikroTik or FRR router — same battery, mixed vendors"
- "Sweep the netem loss from 0.5% to 5% and chart TCP throughput at each step"
- "Add a third flow marked AF31 and build a full 3-class QoS treatment table"
- "Replace the OSPF preference with BGP local-preference and rerun case 2"

## Related Resources

- [Best Network Traffic Generators for Lab Testing 2026](https://www.netpilot.io/blog/network-traffic-generator-lab-testing)
- [NetPilot AI Network Testing Lab](https://www.netpilot.io/network-testing-lab)
- [tc-netem man page](https://man7.org/linux/man-pages/man8/tc-netem.8.html)
- [Related: QoS End-to-End Marking and Queuing](qos-end-to-end-marking.md)
- [Related: Firmware Upgrade Failover Test](../change-validation/firmware-upgrade-failover.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
