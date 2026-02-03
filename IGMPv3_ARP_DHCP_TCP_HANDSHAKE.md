# 🦈 Wireshark – Packet Capture Observation

Today, I opened **Wireshark**, started capturing packets, then:
- Opened **Mozilla Firefox**
- Logged into **Discord**
- Navigated to **Discord Nitro**

Below are the protocols I observed and my understanding of them.

---

## ICMPv6
- ICMPv6 works over **IPv6**
- It helps in:
  - Neighbor Discovery
  - Finding neighbor devices
  - Duplicate Address Detection
- In IPv6 networks, ICMPv6 replaces ARP

---

## IPv6 Multicast Addresses
- **FF02::1** → All IPv6 devices on the local network listen
- **FF02::2** → All IPv6 routers listen

---

## IGMPv3
- IGMPv3 works over **IPv4**
- It is used for multicast group management in IPv4 networks

---

## DHCP and DHCPv6
- **DHCP** assigns IP addresses to devices in a LAN (IPv4)
- **DHCPv6** assigns IPv6 addresses and network configuration to IPv6 devices

---

## ARP (Address Resolution Protocol)
- ARP works with **IPv4**
- It finds the **MAC address** of a given **IP address**

---

## DNS and DNS Server
- **DNS converts domain names** (e.g., google.com, discord.com) into IP addresses
- A **DNS server** provides IP addresses for domain names using the **DNS protocol**
- DNS messages **travel using IP packets**

---

## DNS Queries
- **Standard Query**:
  - A DNS question such as:
    “What is the IP address of discord.com?”
- **Standard Query Response**:
  - The DNS server’s reply containing the IP address

---

## Manufacturer Names in Wireshark
- Names like **INTEL**, **PCSSYSTEM_TEC**, **SPEEDTECH** appear due to:
  - MAC address **OUI (Organizationally Unique Identifier)**
- These indicate the **company that manufactured the network interface**
- They are not device names or hostnames

---

## Neighbor Discovery (IPv6)
- **Neighbor Solicitation (NS)**:
  - Asks: “What is the MAC address of this IPv6 address?”
  - Works under **ICMPv6**
- **Neighbor Advertisement (NA)**:
  - Reply to Neighbor Solicitation
  - Provides the MAC address
- Difference from ARP:
  - ARP works on **IPv4**
  - NS/NA work on **IPv6**

---

## TCP 3-Way Handshake
Used to establish a TCP connection.

1. **SYN**  
   Client → Server  
   “Hi, can we talk?”

2. **SYN-ACK**  
   Server → Client  
   “Sure.”

3. **ACK**  
   Client → Server  
   “Great, let’s talk.”

✅ TCP connection is established.

---

## Conclusion
This packet capture helped me understand how different networking protocols work together in real traffic, including ICMPv6, DNS, ARP, and TCP.
