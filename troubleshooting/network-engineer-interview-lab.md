# Network Engineer Interview Lab: 3 OSPF and BGP Faults on Real Cisco IOS

A technical interview the candidate takes on real routers, not on a whiteboard. One prompt builds a broken Cisco branch with three faults, easy to hard, and an answer key. The candidate opens the lab link and fixes it while you watch.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io/?vendor=cisco), or [open it with the prompt filled in](https://app.netpilot.io/?prompt=Build%20me%20a%20troubleshooting%20interview%20lab%20on%20Cisco%20routers%3A%20a%20branch%20that%20can%27t%20reach%20the%20internet%2C%20OSPF%20inside%2C%20BGP%20to%20a%20provider.%20Plant%20three%20faults%2C%20easy%20to%20hard%3A%20an%20OSPF%20neighbor%20that%20won%27t%20form%2C%20a%20BGP%20session%20that%20is%20up%20but%20advertises%20nothing%2C%20and%20return%20traffic%20taking%20the%20wrong%20exit.%20Give%20me%20the%20answer%20key.&vendor=cisco):

> Build me a troubleshooting interview lab on Cisco routers: a branch that can't reach the internet, OSPF inside, BGP to a provider. Plant three faults, easy to hard: an OSPF neighbor that won't form, a BGP session that is up but advertises nothing, and return traffic taking the wrong exit. Give me the answer key.

Then, after the candidate is done:

> The candidate is done. What did they change, and is anything still broken?

## What You'll Build

- Four Cisco IOL routers (CORE, EDGE1, EDGE2, ISP) and two Linux hosts (PC1 on the branch LAN, INET as "the internet")
- A branch in AS 65010 running OSPF area 0, with a primary and a backup eBGP circuit to one provider in AS 64500
- Three faults in the startup configs, so a redeploy resets the lab for the next candidate

## What Came Back

On a recorded run the build took 9 min 44 s. The agent planted the three faults, fixed each one live to prove it, then redeployed the broken version. On its first try fault 3 had no effect, so it changed the BGP metrics and proved it again. It wrote an answer key with a brief to read aloud, the symptoms, the commands, the fixes and a scoring guide.

The faults, as planted on that run:

1. Easy: EDGE1 runs OSPF hello 5 and dead 20 against CORE's 10 and 40, so CORE has one OSPF neighbor instead of two.
2. Medium: EDGE2's BGP session is up with 0 prefixes advertised. Its `network` statement asks for a /16 that is not in the routing table.
3. Hard: return traffic comes in through the backup circuit. EDGE2's prefix-list misses the /24, so the route skips `set metric 200` and leaves with its IGP metric, 20, which beats the primary's 50.

Fixing fault 1 brings the internet back, so the ticket looks solved. Fixing fault 2 is what makes fault 3 show. The review prompt returned 3 of 3 faults fixed, the lines the candidate changed on each router, and a point for the debrief.

## Concepts Demonstrated

- OSPF hello and dead timers must match for an adjacency to form
- BGP only advertises a `network` that exactly matches a route in the routing table
- MED, route-map fall-through and prefix-list `le` matching decide the return path
- Checking the return path, not only the forward path

## Vendors Used

- Cisco IOL 17.12.1 (bring your own image, uploaded once)
- Linux hosts

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Make the metric fault harder without changing the topology"
- "Add a scoring rubric with point values per fault"
- "Swap fault 1 for an OSPF MTU mismatch"

## Related Resources

- [Run it yourself: the lab files and the answer key](https://github.com/netpilot-labs/network-labs/tree/main/cisco/interview-ospf-bgp-troubleshooting)
- [Cisco IOS OSPF MTU Mismatch Lab](cisco-ios-ospf-mtu-mismatch.md)
- [RFC 4271, BGP-4](https://www.rfc-editor.org/rfc/rfc4271)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io/?prompt=Build%20me%20a%20troubleshooting%20interview%20lab%20on%20Cisco%20routers%3A%20a%20branch%20that%20can%27t%20reach%20the%20internet%2C%20OSPF%20inside%2C%20BGP%20to%20a%20provider.%20Plant%20three%20faults%2C%20easy%20to%20hard%3A%20an%20OSPF%20neighbor%20that%20won%27t%20form%2C%20a%20BGP%20session%20that%20is%20up%20but%20advertises%20nothing%2C%20and%20return%20traffic%20taking%20the%20wrong%20exit.%20Give%20me%20the%20answer%20key.&vendor=cisco)
