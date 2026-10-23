# Day 4 — Firewalls and Network Security Investigation

## Objective

Understand how firewalls filter network traffic, distinguish inbound from outbound connections, inspect Windows Firewall configuration, and practise investigating suspicious network activity.

## Concepts studied

- Firewalls and firewall rules
- Inbound and outbound traffic
- Allow and block actions
- Stateful and stateless firewalls
- Windows Firewall profiles: Domain, Private, and Public
- IDS (Intrusion Detection System) and IPS (Intrusion Prevention System)
- Common ports and protocols
- Firewall logging and network evidence
- SOC alert triage and evidence correlation

## Practical labs

### 1. Inspect Windows Firewall profiles

**Command:** `Get-NetFirewallProfile | Format-Table Name, Enabled, DefaultInboundAction, DefaultOutboundAction`

**Observation:**

- Domain profile status:
- Private profile status:
- Public profile status:
- What I learned about default actions:

### 2. Inspect firewall rules

**Command:** `Get-NetFirewallRule | Select-Object -First 15 DisplayName, Enabled, Direction, Action`

**Observation:**

- Example rule name:
- Rule direction:
- Rule action:
- Is the rule enabled?
- What I learned:

### 3. Test TCP connectivity

**Commands:**

- `Test-NetConnection example.com -Port 443`
- `Test-NetConnection example.com -Port 80`

**Observation:**

- Port 443 result:
- Port 80 result:
- What `TcpTestSucceeded` means:
- Possible reasons a connection may fail:

### 4. Inspect active TCP connections

**Command:** `Get-NetTCPConnection | Select-Object -First 15 LocalAddress, LocalPort, RemoteAddress, RemotePort, State, OwningProcess`

**Observation:**

- Example local port:
- Example remote address and port:
- Connection state:
- Owning process ID:
- Process name, if identified:
- Why process information matters:

### 5. Inspect firewall logging configuration

**Command:** `Get-NetFirewallProfile | Select-Object Name, LogAllowed, LogBlocked, LogFileName`

**Observation:**

- Is allowed-traffic logging configured?
- Is blocked-traffic logging configured?
- Configured log path:
- What I learned about firewall evidence:

## SOC investigation scenario

A workstation generates repeated outbound connections to an unfamiliar external IP address on TCP port 443.

**Investigation steps:**

1. Identify the source device and destination.
2. Confirm the protocol, port, timing, and connection outcome.
3. Identify the process responsible for the connection when possible.
4. Check firewall and DNS logs, endpoint telemetry, and user activity.
5. Determine whether the activity is expected, suspicious, or inconclusive.
6. Document the evidence and follow the organization's escalation procedure.

**Key lesson:** An unfamiliar destination or repeated HTTPS connections do not independently prove malicious activity. Findings must be correlated with additional evidence.

## SOC Analyst takeaway

Firewalls enforce network-access policies, while IDS and IPS technologies detect or prevent suspicious traffic. SOC analysts use firewall settings, connection details, process information, and logs to investigate alerts and understand whether activity was permitted, blocked, or suspicious.

## Further learning

- Explain inbound versus outbound traffic.
- Explain stateful versus stateless firewalls.
- Differentiate firewalls, IDS, and IPS.
- Review common services on ports 22, 53, 80, 443, 445, and 3389.
- Practise identifying a process associated with a network connection.
- Review why an allowed connection can still be malicious.


