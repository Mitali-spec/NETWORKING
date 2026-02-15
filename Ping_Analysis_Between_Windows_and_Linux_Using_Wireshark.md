# ICMP and ARP Packet Observation Using Wireshark (Windows ↔ Linux)

## Setup
- Windows IP address obtained using `ipconfig`
- Linux IP address obtained using `ip a`
- Wireshark used to capture packets
- Ping performed between Linux and Windows in both directions

---

## Packet Observation: Linux → Windows

### 1. ICMPv6 Traffic
- ICMPv6 packets were observed initially.
- ICMPv6 works with IPv6 and supports:
  - Neighbor Discovery
  - Router discovery
  - IPv6 ping
- IPv6 provides logical addressing for devices, while ICMPv6 supports control and discovery functions in IPv6 networks.

---

### 2. Neighbor Solicitation (IPv6)
- Neighbor Solicitation (NS) packets were observed.
- NS is used to find the MAC address corresponding to an IPv6 address.
- This is similar to ARP in IPv4 but is part of ICMPv6.
- NS works only with IPv6.

---

### 3. ICMP Echo Request
- When ping was initiated from Linux to Windows:
  - ICMP Echo Request packets were sent.
  - Echo Request means: *“Are you reachable?”*
- Initially, Wireshark showed **“No response found”**, because address resolution was still in progress.

MAC not resolved means the system has not yet mapped the destination IP address to a MAC address, so it cannot deliver packets on the local network.
---

### 4. ARP (IPv4)
- ARP packets appeared after that.
- ARP is used in IPv4 networks to resolve an IP address to a MAC address.
- Observed ARP message:
  - “Who has IP (Windows)? Tell IP (Linux)”
- Windows replied with:
  - “IP (Windows) is at MAC (Windows)”

---

### 5. ICMP Echo Request (Successful)
- After ARP resolution:
  - ICMP Echo Request packets were sent again
  - Windows was now reachable
- Communication succeeded

---

## Packet Observation: Windows → Linux

- Ping was initiated from Windows to Linux.
- ICMP Echo Reply packets were observed.
- Echo Reply confirms that the destination device is reachable.

---

## Key Learnings

- IPv4 uses **ARP** for IP-to-MAC mapping
- IPv6 uses **Neighbor Solicitation (ICMPv6)** for address resolution
- ICMP Echo Request and Reply are used by the `ping` command
- Address resolution occurs before successful ping communication


# DHCP IP Assignment – Concept Explanation

## Statement
Devices get IP addresses from a DHCP server using the DHCP protocol.

## What Actually Happens

- A computer is just a normal machine by default.
- When a DHCP server **program** is executed, the operating system starts a **process**.
- This process binds to a **network port** (UDP port 67).
- Once the process starts listening on this port, the machine acts as a **DHCP server**.
- Devices (clients) communicate with this server using the **DHCP protocol**.
- Inside the DHCP server program, the logic for assigning IP addresses is defined.
- This logic includes selecting an IP address, binding it to a MAC address, and setting lease parameters.
- Through this process, the device receives an IP address and can communicate on the network.

## Key Points

- DHCP server is a **program + process**, not special hardware
- Server functionality depends on the **service running**
- IP assignment follows the **DHCP protocol rules**

## Protocol Details

- Protocol: DHCP
- Transport Layer: UDP
- Server Port: 67
- Client Port: 68

### Mobile Network Addressing Observation

- The mobile device receives its IPv4 address from a DHCP server.
- MAC address randomization is used to protect user privacy.
- The device maintains multiple IPv6 addresses, including:
  - Global IPv6 address
  - Temporary (privacy) IPv6 address
  - Multicast IPv6 addresses for network communication

## Understanding 192.168.x.x and the Default Gateway

If devices receive IP addresses in the 192.168.1.x range, then 192.168.1.1 is very likely the router’s default gateway.
However, this should always be verified by checking the network configuration.

On Windows, this can be confirmed using the ipconfig command and looking for the Default Gateway field.
