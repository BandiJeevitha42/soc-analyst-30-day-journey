# Day 8 — Networking Fundamentals for SOC Analyst L1

## Objectives
- Review IP addresses, ports, TCP, UDP, DNS, HTTP, and HTTPS.
- Practice basic Linux network-inspection commands.
- Analyze a synthetic network log.
- Document findings using a SOC-style investigation report.

## Tools
- Ubuntu on WSL
- Linux CLI utilities: `ip`, `ss`, `grep`, `cut`, `sort`, `uniq`, and `wc`

## Lab Summary
Analyzed 10 synthetic network events. Identified five denied events, including four denied RDP attempts to the same destination.

## Initial Assessment
Repeated denied connections to TCP port 3389 warrant contextual review. The supplied data does not prove an attack or system compromise.

## Skills Practiced
- Network protocol and port identification
- Linux command-line filtering
- Log analysis and event counting
- Evidence-based reporting
- Investigation limitations and escalation recommendations

## Limitations
This is a simulated lab, not a production SOC investigation. IP addresses are reserved documentation examples.

## Next Steps
Correlate firewall, endpoint, DNS, and authentication telemetry in future labs.
