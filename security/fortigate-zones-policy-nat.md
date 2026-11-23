# FortiGate Firewall Lab: Zones, a Firewall Policy and Source NAT

Build a real FortiGate between an inside and an outside zone, with source NAT out and nothing in, and prove it from a PC with the session table.

## The Prompt

Open it [prefilled in NetPilot](https://app.netpilot.io/?prompt=Build%20me%20a%20FortiGate%20firewall%20lab%3A%20one%20FortiGate%20between%20an%20inside%20zone%20and%20an%20outside%20zone%2C%20a%20PC%20on%20the%20inside%20and%20a%20web%20server%20on%20the%20outside.%20Allow%20the%20inside%20to%20reach%20the%20outside%20with%20source%20NAT%2C%20and%20nothing%20in%20from%20the%20outside.%20Deploy%20it%20and%20prove%20it%3A%20ping%20the%20web%20server%20from%20the%20PC%2C%20then%20show%20me%20the%20FortiGate%27s%20session%20for%20that%20ping%20with%20the%20NAT%20address.), or paste it:

> Build me a FortiGate firewall lab: one FortiGate between an inside zone and an outside zone, a PC on the inside and a web server on the outside. Allow the inside to reach the outside with source NAT, and nothing in from the outside. Deploy it and prove it: ping the web server from the PC, then show me the FortiGate's session for that ping with the NAT address.

## What You'll Build

- One Fortinet FortiGate (FortiOS 7.0.9) with port2 in an INSIDE zone and port3 in an OUTSIDE zone
- A Linux PC on 192.168.10.0/24 and a Linux web server on 203.0.113.0/24 (a documentation range)
- Policy 1, INSIDE to OUTSIDE, accept with `nat enable`, and the implicit deny for everything else
- The proof: ping and HTTP from the PC, a blocked ping from the web server, and the FortiGate session with the NAT address

## Concepts Demonstrated

- FortiGate zones and why a policy names zones, not interfaces
- Source NAT on the policy: in our run the session read `act=snat 192.168.10.10:42795->203.0.113.10:8(203.0.113.1:42795)`
- The implicit deny: the web server's 3 pings to the PC were dropped
- First match wins: a deny above the allow blocks ping while web traffic keeps working (the first variation below)

## Vendors Used

- Fortinet FortiGate (FortiOS 7.0.9), bring your own image
- Linux hosts for the PC and the web server

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Now block ping from the inside to the outside but keep web traffic working. Prove both with the PC, and show me each policy's hit counters."
- "Add policy 2 to the startup config so it persists, then save the topology and the FortiGate config to the workspace."
- "Publish a web service on PC1 to the outside with a VIP, and prove WEB1 reaches it while everything else stays blocked"
- "Add a DMZ zone with its own server and allow only HTTPS into it"

## Related Resources

- [NetPilot blog: Firewall lab with Palo Alto and FortiGate](https://www.netpilot.io/blog/firewall-lab-palo-alto-fortinet)
- [NetPilot firewall lab page](https://www.netpilot.io/firewall-lab)
- [Fortinet FortiGate documentation](https://docs.fortinet.com/product/fortigate/7.0)
- [Firewall DMZ Zones with Fortinet](firewall-dmz-zones-fortinet.md)
- [Firewall DMZ Zones with Palo Alto](firewall-dmz-zones-palo-alto.md)
- [Firewall Rule Deployment Test](../change-validation/firewall-rule-deployment.md)

## Run it yourself

The tested containerlab files for this lab, to deploy on your own Linux host: [network-labs/fortinet/fortigate-zones-policy-nat](https://github.com/netpilot-labs/network-labs/tree/main/fortinet/fortigate-zones-policy-nat).

## Try It

[**Open in NetPilot →**](https://app.netpilot.io/?prompt=Build%20me%20a%20FortiGate%20firewall%20lab%3A%20one%20FortiGate%20between%20an%20inside%20zone%20and%20an%20outside%20zone%2C%20a%20PC%20on%20the%20inside%20and%20a%20web%20server%20on%20the%20outside.%20Allow%20the%20inside%20to%20reach%20the%20outside%20with%20source%20NAT%2C%20and%20nothing%20in%20from%20the%20outside.%20Deploy%20it%20and%20prove%20it%3A%20ping%20the%20web%20server%20from%20the%20PC%2C%20then%20show%20me%20the%20FortiGate%27s%20session%20for%20that%20ping%20with%20the%20NAT%20address.)
