# Day 6 — Linux Users, Permissions, Processes and Services

## Objectives
- Understand Linux users, groups, UIDs and GIDs.
- Practise reading and changing file permissions.
- Inspect running processes and resource usage.
- Understand services and system logs.
- Investigate a simulated file-permissions security issue.

## Environment
- Windows laptop
- Ubuntu on WSL
- Bash terminal
- Local synthetic training files

## Commands Practised
`whoami`, `id`, `groups`, `getent`, `ls -l`, `chmod`, `ps`, `top`, `pgrep`, `systemctl`, `journalctl`

## Practical Investigation
Created a harmless training script with overly permissive permissions, inspected the permissions, and changed them from 777 to 750.

## Findings
- The original permissions granted read, write and execute access to owner, group and others.
- The revised permissions restricted access to the owner and group.
- The script's content was a harmless training message.
- No malicious execution or compromise was established.

## Security Lessons
- Apply least privilege.
- Investigate unfamiliar processes and unexpected file changes.
- Review file ownership, permissions and execution context.
- Correlate multiple sources of evidence before concluding that an incident occurred.

## Limitations
This was a local training exercise. No production system or real malicious process was investigated.
