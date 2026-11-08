# Cisco IOS Hub and Spoke OSPF: Design, Deploy, Troubleshoot and Document with an AI Agent

Give an AI agent the four jobs a network engineer has every week on one real Cisco IOS lab: design from a written requirement, configure and deploy, find a fault from a user's symptom, and write the handover. Check every answer on the CLI.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io/), or [open it with the prompt filled in](https://app.netpilot.io/?prompt=Here%20is%20a%20requirement%20from%20a%20customer.%20Design%20and%20build%20the%20network%20for%20it%20on%20Cisco%20IOS%20routers.%20We%20have%20a%20head%20office%20and%20two%20branches.%20Each%20site%20has%20one%20router%20and%20one%20user%20LAN%3A%20head%20office%2010.10.0.0%2F24%2C%20branch%20A%2010.20.0.0%2F24%2C%20branch%20B%2010.30.0.0%2F24.%20Each%20branch%20connects%20only%20to%20the%20head%20office%2C%20not%20to%20the%20other%20branch.%20Use%20OSPF%20area%200%20everywhere.%20Put%20a%20Linux%20host%20on%20each%20LAN%20at%20.10.%20Design%20the%20topology%2C%20write%20the%20router%20configs%20and%20review%20them%20before%20you%20deploy%2C%20then%20deploy%20the%20lab%20and%20prove%20it%20works%3A%20OSPF%20neighbors%20on%20the%20head%20office%20router%20and%20a%20ping%20from%20each%20branch%20host%20to%20the%20head%20office%20host.):

> Here is a requirement from a customer. Design and build the network for it on Cisco IOS routers. We have a head office and two branches. Each site has one router and one user LAN: head office 10.10.0.0/24, branch A 10.20.0.0/24, branch B 10.30.0.0/24. Each branch connects only to the head office, not to the other branch. Use OSPF area 0 everywhere. Put a Linux host on each LAN at .10. Design the topology, write the router configs and review them before you deploy, then deploy the lab and prove it works: OSPF neighbors on the head office router and a ping from each branch host to the head office host.

Once it passes, plant one fault by hand on branch B's router, on the interface that faces the head office (find it with `show ip interface brief`), without telling the agent:

```
configure terminal
interface <the interface toward the head office>
ip ospf 1 area 1
end
```

Then send the user's symptom:

> A user at branch B says they cannot reach anything at the head office since this morning. Nobody says they changed anything. Find the cause, fix it, and prove it is fixed.

Last, the handover:

> Write the handover document for this network for the engineer who takes it over tomorrow: sites, addressing, routing, what failed today, what you changed, and how to verify it is healthy. Include a diagram.

## What You'll Build

- Three Cisco IOL 17.12.1 routers in a hub and spoke: head office 10.10.0.0/24, branch A 10.20.0.0/24, branch B 10.30.0.0/24, no branch-to-branch link
- OSPF area 0 on /30 WAN links with loopback router IDs, a Linux host at .10 on each LAN
- A planted OSPF area mismatch on branch B's WAN link, found from the symptom alone
- A handover document with a diagram, the incident timeline from the router logs and a runbook

## Concepts Demonstrated

- An OSPF area mismatch: the head office only logs the neighbor going down on its dead timer, while branch B logs `%OSPF-4-ERRRCV: Received invalid packet: mismatched area ID from backbone area` every 10 seconds. Look on both sides
- An interface-level `ip ospf 1 area 1` overrides a `network` statement for area 0
- Checking the premise: `%SYS-5-CONFIG_I` in the log shows a change was made, even when nobody says so
- Evidence that disappears: IOL's 4096-byte log buffer overwrote the fault lines about 20 minutes after the fix. In our run the agent flagged it in the handover
- In our run: tasks 1 to 3 in 2 min 31 s, the fault found and fixed 43 s after the symptom prompt, the handover in 3 min 8 s

## Vendors Used

- Cisco IOL (IOS 17.12.1), your own image (BYOI)
- Linux endpoints

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- Plant an IP MTU mismatch on the same link instead and see whether the agent finds the EXSTART state
- "Add a branch C on 10.40.0.0/24 and update the handover document"
- "Make branch A's LAN passive and prove OSPF still advertises it"
- "Add a backup link between the two branches with a higher OSPF cost, then shut the head office link to branch B and prove the failover"

## Related Resources

- [NetPilot blog: Best AI tools for network engineers, with this test's scorecard](https://www.netpilot.io/blog/ai-tools-for-network-engineers#tested-on-a-real-cisco-lab-five-tasks-one-scorecard)
- [Video: AI for Network Engineers: 5 Real Tasks on a Real Cisco Lab, Scored](https://www.youtube.com/watch?v=H2xePvVEauA)
- [Public lab files: 02-hub-spoke-ospf](https://github.com/netpilot-labs/cisco-labs/tree/main/02-hub-spoke-ospf)
- [Cisco: Troubleshoot OSPF neighbor problems](https://www.cisco.com/c/en/us/support/docs/ip/open-shortest-path-first-ospf/13699-29.html)
- [RFC 2328: OSPF Version 2](https://datatracker.ietf.org/doc/html/rfc2328)
- [DMVPN Hub-and-Spoke](../routing/dmvpn-hub-and-spoke.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io/?prompt=Here%20is%20a%20requirement%20from%20a%20customer.%20Design%20and%20build%20the%20network%20for%20it%20on%20Cisco%20IOS%20routers.%20We%20have%20a%20head%20office%20and%20two%20branches.%20Each%20site%20has%20one%20router%20and%20one%20user%20LAN%3A%20head%20office%2010.10.0.0%2F24%2C%20branch%20A%2010.20.0.0%2F24%2C%20branch%20B%2010.30.0.0%2F24.%20Each%20branch%20connects%20only%20to%20the%20head%20office%2C%20not%20to%20the%20other%20branch.%20Use%20OSPF%20area%200%20everywhere.%20Put%20a%20Linux%20host%20on%20each%20LAN%20at%20.10.%20Design%20the%20topology%2C%20write%20the%20router%20configs%20and%20review%20them%20before%20you%20deploy%2C%20then%20deploy%20the%20lab%20and%20prove%20it%20works%3A%20OSPF%20neighbors%20on%20the%20head%20office%20router%20and%20a%20ping%20from%20each%20branch%20host%20to%20the%20head%20office%20host.)
