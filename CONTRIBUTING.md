# Contributing a Prompt

Thanks for contributing. The library grows when network engineers share what works.

## Quick Start

1. Fork this repo
2. Pick a category folder (or propose a new one in an issue first)
3. Create a new file using [the template below](#template)
4. Add an entry to the category list in [README.md](README.md)
5. Submit a PR

## What Makes a Good Prompt

- **Specific** — vendor names, AS numbers, IPs, interface names
- **Realistic** — represents a real-world scenario, not a toy example
- **Verifiable** — include explicit verification expectations (routes, adjacencies, reachability)
- **Self-contained** — works as-is when copy-pasted into NetPilot
- **Educational** — the "Concepts Demonstrated" section explains *why* this lab matters

## Template

Copy this template into your new file:

````markdown
# [Topology Name] — [What It Demonstrates]

[One-sentence description of what this lab shows.]

## The Prompt

Copy this into [NetPilot](https://app.netpilot.io):

> [The actual natural-language prompt — describe the topology, devices, vendors, IPs, protocols, and verification expectations in plain English. 3-6 sentences.]

## What You'll Build

- [Device count and vendor mix]
- [Protocols and features]
- [Verification scenarios]

## Concepts Demonstrated

- [Why this lab is valuable]
- [What you learn from running it]
- [Edge cases or gotchas]

## Vendors Used

[List of vendor OSes: Cisco IOL, Juniper cRPD, etc.]

## Difficulty

⭐ / ⭐⭐ / ⭐⭐⭐

## Variations to Try

- [Suggested modification 1]
- [Suggested modification 2]

## Related Resources

- [Link to relevant NetPilot blog post if applicable]
- [Vendor doc or RFC]

## Try It

[**Open in NetPilot →**](https://app.netpilot.io)
````

## Style Guide

- Filenames: lowercase, kebab-case, descriptive (e.g., `bgp-ebgp-three-as.md`, NOT `lab-1.md`)
- Use H1 (`#`) for the title only; H2 (`##`) for sections
- The prompt block uses `>` markdown blockquote for visibility
- Cross-link to other prompts in this repo where relevant
- Don't duplicate NetPilot's blog content — link to it instead

## Code of Conduct

By contributing, you agree to follow our [Code of Conduct](https://github.com/netpilot-labs/community/blob/main/CODE_OF_CONDUCT.md).
