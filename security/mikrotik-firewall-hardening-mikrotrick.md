# MikroTik Firewall Hardening After MikroTrick: Audit a Patched RouterOS Router

Build an exposed MikroTik edge router, audit it against the MikroTrick advisory, harden it, and prove from outside that management is closed.

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io/?vendor=mikrotik), or [open it with the prompt filled in](https://app.netpilot.io/?prompt=Build%20a%20small%20lab%20on%20real%20MikroTik%20RouterOS%3A%20EDGE-RTR%20with%20a%20LAN%20PC%20behind%20it%20and%20an%20outside%20host%20on%20the%20WAN%20side.%20Set%20EDGE-RTR%20up%20the%20way%20many%20routers%20really%20end%20up%3A%20NAT%20for%20the%20LAN%20but%20no%20firewall%20rules%2C%20so%20SSH%2C%20WebFig%2C%20WinBox%20and%20the%20bandwidth%20test%20server%20all%20answer%20from%20the%20WAN.%20From%20the%20outside%20host%2C%20scan%20the%20router%20and%20show%20what%20answers.%20Then%20audit%20it%20against%20MikroTik%27s%20September%202026%20MikroTrick%20advisory%3A%20the%20version%20against%20the%20fixed%20releases%2C%20IP%20services%2C%20the%20input%20chain%2C%20users%2C%20scripts%20and%20the%20scheduler.%20Harden%20it%2C%20keep%20management%20reachable%20from%20the%20LAN%20only%2C%20and%20prove%20it%3A%20rescan%20from%20outside%2C%20and%20confirm%20the%20PC%20still%20reaches%20the%20outside%20host%20and%20can%20still%20manage%20the%20router.%20End%20with%20a%20before%20and%20after%20table.%20No%20exploit%2C%20just%20the%20audit%20and%20the%20hardening.):

> Build a small lab on real MikroTik RouterOS: EDGE-RTR with a LAN PC behind it and an outside host on the WAN side. Set EDGE-RTR up the way many routers really end up: NAT for the LAN but no firewall rules, so SSH, WebFig, WinBox and the bandwidth test server all answer from the WAN. From the outside host, scan the router and show what answers. Then audit it against MikroTik's September 2026 MikroTrick advisory: the version against the fixed releases, IP services, the input chain, users, scripts and the scheduler. Harden it, keep management reachable from the LAN only, and prove it: rescan from outside, and confirm the PC still reaches the outside host and can still manage the router. End with a before and after table. No exploit, just the audit and the hardening.

## What You'll Build

- An edge router on MikroTik RouterOS 7.24.5, past every MikroTrick fix, with a PC on the LAN and an outside host on the WAN
- A scan from outside before and after hardening
- An audit of the version, IP services, the input chain, users, scripts and the scheduler
- An input chain that keeps management on the LAN, with services limited by address

## Concepts Demonstrated

- Why a patched router can still be open: in our run, 8 TCP ports answered from the WAN on RouterOS 7.24.5
- The RouterOS input chain: accept established, drop invalid, allow management from a LAN address list, drop the rest
- `/ip service` with `available-from`, and turning off Telnet, FTP and the API
- Proving a change from outside: the same 8 ports read filtered, while the LAN keeps working

## Vendors Used

- MikroTik RouterOS (CHR), preloaded on every lab VM

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Add a port forward to a web server on the LAN and prove only that port answers from outside"
- "Move management to a dedicated VLAN and allow it only from there"
- "Replace the default admin account and prove the old login no longer works"
- "Add WireGuard for remote management instead of opening SSH"

## Related Resources

- [NetPilot blog: MikroTik firewall hardening after MikroTrick](https://www.netpilot.io/blog/mikrotik-firewall-hardening)
- [Video: MikroTrick: Your Patched MikroTik Can Still Be Wide Open](https://www.youtube.com/watch?v=Dr9VXWuxe6Y)
- [NetPilot MikroTik lab page](https://www.netpilot.io/mikrotik-lab)
- [MikroTik security advisory, September 2026](https://mikrotik.com/supportsec/september-2026-vulnerability/)
- [MikroTik Dual WAN Failover with PCC](../routing/mikrotik-dual-wan-pcc-failover.md)
- [MikroTik RouterOS Practice Lab](../routing/mikrotik-routeros-practice-lab.md)

## Run it yourself

The tested containerlab files for this lab, to deploy on your own Linux host: [network-labs/mikrotik/mikrotrick-hardening](https://github.com/netpilot-labs/network-labs/tree/main/mikrotik/mikrotrick-hardening).

## Try It

[**Open in NetPilot →**](https://app.netpilot.io/?prompt=Build%20a%20small%20lab%20on%20real%20MikroTik%20RouterOS%3A%20EDGE-RTR%20with%20a%20LAN%20PC%20behind%20it%20and%20an%20outside%20host%20on%20the%20WAN%20side.%20Set%20EDGE-RTR%20up%20the%20way%20many%20routers%20really%20end%20up%3A%20NAT%20for%20the%20LAN%20but%20no%20firewall%20rules%2C%20so%20SSH%2C%20WebFig%2C%20WinBox%20and%20the%20bandwidth%20test%20server%20all%20answer%20from%20the%20WAN.%20From%20the%20outside%20host%2C%20scan%20the%20router%20and%20show%20what%20answers.%20Then%20audit%20it%20against%20MikroTik%27s%20September%202026%20MikroTrick%20advisory%3A%20the%20version%20against%20the%20fixed%20releases%2C%20IP%20services%2C%20the%20input%20chain%2C%20users%2C%20scripts%20and%20the%20scheduler.%20Harden%20it%2C%20keep%20management%20reachable%20from%20the%20LAN%20only%2C%20and%20prove%20it%3A%20rescan%20from%20outside%2C%20and%20confirm%20the%20PC%20still%20reaches%20the%20outside%20host%20and%20can%20still%20manage%20the%20router.%20End%20with%20a%20before%20and%20after%20table.%20No%20exploit%2C%20just%20the%20audit%20and%20the%20hardening.)
