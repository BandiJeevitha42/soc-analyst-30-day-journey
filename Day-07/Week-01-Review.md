# Day 7 — Week 1 Review and Mini SOC Investigation

## Overview

This document summarises my first week of preparation for the SOC Analyst Level 1 role. I revised networking fundamentals, Linux commands, basic security concepts and authentication log analysis.

## Learning Objectives

- Understand the responsibilities of a SOC Analyst L1.
- Revise networking fundamentals and common ports.
- Practise Linux command-line operations.
- Understand Linux users, groups, permissions and processes.
- Investigate suspicious authentication activity.
- Develop evidence-based investigation and reporting skills.

## Topics Covered

### 1. Networking Fundamentals

- IP addresses and MAC addresses
- DNS and DHCP
- TCP vs UDP
- HTTP and HTTPS
- SSH
- Common ports: 22, 53, 80, 443 and 3389
- Basic firewall concepts

### 2. Linux Fundamentals

Commands practised:

`pwd`, `ls`, `cd`, `mkdir`, `cat`, `less`, `head`, `tail`, `grep`, `sort`, `uniq`, `awk`, `wc`, `chmod`, `whoami`, `id`, `ps`, `top`, `df`, `ip`

Key concepts:

- Linux filesystem and directory structure
- Reading and searching log files
- Users and groups
- File permissions and ownership
- Running processes
- Services and system logs

### 3. Security Fundamentals

- CIA triad: Confidentiality, Integrity and Availability
- Security events, alerts and incidents
- Threats and vulnerabilities
- Indicators of Compromise (IOCs)
- False positives
- Basic SOC alert triage and escalation

## Practical Lab: SSH Authentication Log Investigation

### Scenario

A simulated Linux authentication log was provided for investigation. The objective was to identify repeated failed SSH login attempts and determine whether further investigation was necessary.

### Tools Used

- Ubuntu on Windows Subsystem for Linux (WSL)
- Bash terminal
- Linux text-processing commands
- Synthetic authentication logs

### Investigation Commands

Count failed authentication records:

```bash
grep -ic "Failed password" auth.log
```

Count failures against Alice:

```bash
grep -ic "Failed password for alice" auth.log
```

Extract and count source IP addresses:

```bash
grep -i "Failed password" auth.log |
grep -oE 'from [0-9]+\.[0-9]+\.[0-9]+\.[0-9]+' |
awk '{print $2}' |
sort |
uniq -c
```

Find successful authentication events:

```bash
grep -i "Accepted" auth.log
```

### Findings

- Total authentication log records: 9
- Failed authentication records: 7
- Failed attempts against Alice: 6
- Repeated source IP: `203.0.113.45`
- Successful authentication records: 2
- Alice's successful login was recorded from a different source IP using public-key authentication.

### Initial Assessment

Repeated failed SSH authentication attempts against Alice from the same source IP are suspicious and warrant further investigation.

However, the available evidence does not establish that Alice's account was compromised. The successful login came from a different IP address, and additional evidence is required to determine whether the events are related.

### Recommended Next Steps

1. Review the source IP and relevant network telemetry.
2. Verify whether Alice's successful login was expected.
3. Correlate SSH logs with identity and endpoint records.
4. Review the account's authentication history.
5. Document the findings and escalate according to the incident-response procedure if concerns remain.

## Key Learnings

- Linux commands can help analysts filter and investigate authentication logs.
- Repeated login failures can indicate suspicious activity.
- Successful authentication after failed attempts does not automatically prove account compromise.
- Source IP addresses, timestamps, accounts and authentication methods provide useful investigation context.
- SOC analysts must document evidence, acknowledge limitations and follow approved escalation procedures.

## Limitations

This investigation used synthetic log data. No production system, real user account or live attacker was investigated.

## Week 1 Reflection

During the first week, I developed a foundation in networking, Linux command-line operations and SOC investigation concepts. I practised filtering authentication logs, counting events, extracting IP addresses and documenting investigation findings.

My next learning objective is to strengthen my understanding of cybersecurity threats, vulnerabilities, security controls, SIEM fundamentals and incident response.

## Next Steps

- Study common cyberattacks and attack techniques.
- Learn phishing and malware investigation fundamentals.
- Understand firewalls, IDS/IPS and endpoint security.
- Study SIEM concepts and alert triage.
- Continue building practical SOC investigation projects.

---

**Disclaimer:** This repository documents my personal cybersecurity learning journey and simulated lab exercises. It does not represent professional production SOC experience.
