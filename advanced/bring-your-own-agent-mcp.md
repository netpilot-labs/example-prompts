# Bring Your Own Agent: Drive NetPilot from Claude, Cursor or Your In-House Agent over MCP

Your agent already plans the work. Give it a lab it can build, validate and tear down on demand: connect it to NetPilot's MCP server and send it this.

> **Requires access to NetPilot's MCP server**, set up for your workflow by NetPilot's team (the server is private to NetPilot and its customers). See [NetPilot Integrations](https://www.netpilot.io/integrations) and [talk to us about your stack](https://www.netpilot.io/enterprise).

## The Prompt

Copy this into your own agent (Claude, Cursor, or an in-house agent) once it is connected to NetPilot's MCP server:

> Using the NetPilot tools, build a three-node lab: an Arista cEOS spine, a Cisco IOL leaf and an FRR router, with point-to-point /31 links, eBGP between all three (AS 65001, 65002 and 65003) and a loopback per device advertised into BGP. Deploy it, wait for the BGP sessions to establish, then run the platform-appropriate BGP summary on each device and return the output. Flag any session that is not Established. Leave the lab running so I can SSH in, and tell me the hostnames and management addresses.

*Swap the vendors, AS numbers and the validation step for your own. The agent on your side keeps the conversation; NetPilot does the building.*

## What You'll Build

- A running three-vendor eBGP lab, driven end to end by your own agent
- Validation output (BGP summaries) returned into your agent's context, not a UI you have to open
- A lab that stays up for hand verification over SSH

## Concepts Demonstrated

- Bring your own agent: your Claude, Cursor or in-house agent calls NetPilot's MCP tools to design, deploy and validate
- MCP-connectable both ways: this is the inbound direction; NetPilot's own agent connecting to your stack is the outbound one
- The engineer verifies: every result is reproducible on real NOS CLIs over SSH

## Vendors Used

- Arista cEOS (spine)
- Cisco IOL (leaf)
- FRR (router)

## Difficulty

⭐⭐ Intermediate

## Variations to Try

- "Tear the lab down when the checks pass and return only the report"
- "Build the lab from my NetBox site DC-East instead, then run the same checks" (needs the NetBox integration)
- "Run this as a step in my CI pipeline on every pull request that touches the BGP policy"
- "Add a Nokia SR Linux leaf and compare its BGP summary format to the others"

## Why This Matters

Most MCP servers in networking are connectors into one tool. NetPilot's is a lab platform your agent can drive: it builds real multi-vendor networks on demand, validates them, and hands the evidence back to the agent that asked. Custom-built for your workflow; NetBox, Nautobot and Nornir are a few examples of what NetPilot connects to in the other direction.

## Related Resources

- [NetPilot Integrations: AI agent integration with your network stack](https://www.netpilot.io/integrations)
- [What Is MCP for Network Engineers? (2026 Guide)](https://www.netpilot.io/blog/what-is-mcp-for-network-engineers)
- [Model Context Protocol specification](https://modelcontextprotocol.io/)
- [Related: NetBox Site → Digital Twin Rehearsal](../change-validation/netbox-site-twin-rehearsal.md)

## Try It

[**Open in NetPilot →**](https://app.netpilot.io/sign-in)
