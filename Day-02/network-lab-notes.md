# Day 2 — Networking Fundamentals and Windows Labs

## Objective
Understand basic networking concepts and practice Windows network investigation commands.

## Concepts studied
- IP addresses: IPv4 and IPv6
- Private vs. public IP addresses
- MAC addresses
- Ports and common services
- DNS and DHCP
- TCP vs. UDP
- OSI model

## Practical labs

### 1. Network configuration
Command: `ipconfig /all`

Observation:
- Active adapter:
- IPv4 address (redact if sharing):
- Default gateway (redact if sharing):
- DNS configuration:

### 2. DNS lookup
Command: `nslookup example.com`

Observation:
- DNS server responded:
- Lookup result:
- What I learned:

### 3. Connectivity test
Commands: `ping 127.0.0.1` and `ping example.com`

Observation:
- Loopback result:
- Domain ping result:
- Possible reasons for failure:

### 4. Active connections
Command: `netstat -ano`

Observation:
- Connections observed:
- Example TCP state:
- Why PID information is useful:

### 5. Routing table
Command: `route print`

Observation:
- What a gateway does


## SOC Analyst takeaway
Network commands provide useful evidence during an investigation, but no single output proves that activity is malicious. Findings should be correlated with logs, process information, and other available evidence.

## Further learning
- Review TCP vs. UDP.
- Practice explaining DNS.
- Learn to interpret common ports.
