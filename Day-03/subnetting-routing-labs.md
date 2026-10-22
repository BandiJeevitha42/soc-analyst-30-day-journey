
# Day 3 — Subnetting, Routing, ARP, and Windows Network Troubleshooting

## Objective

Understand how devices communicate within and across networks, learn basic subnetting, explore ARP and routing, and practice Windows commands used for network troubleshooting and SOC investigations.

## Concepts studied

- **Subnetting:** Dividing a larger network into smaller logical networks.
- **CIDR:** Classless Inter-Domain Routing; represents a network prefix, such as `/24` or `/26`.
- **Subnet mask:** Identifies which part of an IPv4 address represents the network and which part represents the host.
- **Network address:** Identifies a subnet.
- **Broadcast address:** Used to reach all hosts on a conventional IPv4 subnet.
- **ARP:** Address Resolution Protocol; maps a local IPv4 address to a MAC address.
- **Routing:** Forwarding packets between networks using routing tables.
- **Default gateway:** The router a device typically uses to reach destinations outside its local subnet.
- **Routing table:** Contains network destinations, next hops, interfaces, and routing information.
- **TTL:** Time to Live; limits how many router hops an IP packet can traverse.
- **Network troubleshooting:** Checking IP configuration, DNS, connectivity, and routes systematically.

## Practical labs

### 1. Inspect network configuration

**Command:** `ipconfig /all`

**Observation:**

- Active network adapter:
- IPv4 address (redact if sharing):
- Subnet mask:
- Default gateway (redact if sharing):
- DHCP enabled:
- DNS servers:
- What I learned about my network:

**Purpose:** Understand how the computer identifies its local network and which gateway and DNS servers it uses.

### 2. Understand subnetting and CIDR

**Example:** `192.168.10.20/24`

- Subnet mask: `255.255.255.0`
- Network address: `192.168.10.0`
- Broadcast address: `192.168.10.255`
- Conventional usable host range: `192.168.10.1`–`192.168.10.254`

**Practice questions:**

- Are `192.168.10.20/24` and `192.168.10.90/24` in the same subnet? **Yes.**
- Are `192.168.10.20/24` and `192.168.11.20/24` in the same subnet? **No.**
- Which subnet contains `192.168.5.130/26`? **`192.168.5.128/26`**
- What is the broadcast address for `192.168.5.128/26`? **`192.168.5.191`**

**What I learned:**

- How a subnet mask separates network and host portions.
- How CIDR notation represents the network prefix length.
- Why devices in different subnets generally need routing to communicate.

### 3. Inspect the ARP cache

**Command:** `arp -a`

**Observation:**

- Interface or network entries displayed:
- Example IP-to-MAC mapping:
- What I learned about ARP:
- Why a device needs a MAC address for local network delivery:

**Purpose:** Observe cached IP-to-MAC mappings used for communication on the local network.

**Security note:** An unfamiliar ARP entry alone does not prove an attack. Investigate it alongside other evidence if necessary.

### 4. Examine the routing table

**Command:** `route print`

**Observation:**

- Default route, if present:
- Default gateway:
- Network routes observed:
- What I learned about packet forwarding:

**Purpose:** Understand how Windows decides where to send packets destined for local and remote networks.

### 5. Trace a network path

**Command:** `tracert example.com`

**Observation:**

- Destination:
- Number of hops displayed:
- Any hops showing `* * *`:
- What I learned about the route:

**Purpose:** Observe the intermediate network hops toward a destination.

**Note:** Some routers do not respond to traceroute probes. Asterisks do not automatically mean the connection is broken.

### 6. Test connectivity to a service

**Commands:**

`Test-NetConnection example.com -Port 443`

`Test-NetConnection example.com -Port 80`

**Observation:**

- Port 443 — `TcpTestSucceeded`:
- Port 80 — `TcpTestSucceeded`:
- What I learned about TCP connectivity:
- Possible reasons a test might fail:

**Purpose:** Test whether a TCP connection can be established to a destination port. A failed test may result from filtering, routing problems, service availability, or other network conditions.

### 7. Investigate active network connections

**Command:** `netstat -ano`

**Observation:**

- Example local address and port:
- Example foreign address and port:
- TCP state observed:
- PID associated with a connection:
- Why process information is useful during a security investigation:

**Optional follow-up:** Replace `<PID>` with an actual process ID from your output.

`Get-Process -Id <PID>`

**Purpose:** Connect network activity to a local process when the PID is available. Investigate unexpected connections using process details, timestamps, endpoint logs, and approved security tools.

## SOC investigation scenario

### Scenario: Unexpected SMB connections

A workstation in `192.168.10.0/24` makes repeated connections to port `445` on a server in `192.168.20.0/24`.

**Investigation approach:**

1. Identify the source workstation and destination server.
2. Confirm that SMB (Server Message Block) communication is expected.
3. Check the frequency and timing of the connections.
4. Correlate available endpoint, authentication, firewall, and network logs.
5. Record findings and escalate according to the organization's incident-response procedure.

**Key lesson:** Port 445 is commonly associated with SMB, but its presence alone does not prove malicious activity.

## SOC Analyst takeaway

Subnetting helps analysts understand network boundaries, routing explains how traffic travels between networks, and ARP helps devices deliver traffic locally. Windows network commands provide useful evidence during troubleshooting and security investigations.

No single command or unfamiliar network entry proves malicious activity. Correlate findings with endpoint processes, authentication events, firewall logs, and other available evidence before drawing conclusions.

## Further learning

- Practice identifying network addresses and broadcast addresses.
- Review CIDR prefixes `/24`, `/25`, `/26`, and `/27`.
- Explain the difference between ARP and DNS.
- Explain the role of a default gateway.
- Practice describing `route print`, `tracert`, and `netstat -ano`.
- Review why repeated SMB connections may deserve investigation without automatically indicating an attack.

