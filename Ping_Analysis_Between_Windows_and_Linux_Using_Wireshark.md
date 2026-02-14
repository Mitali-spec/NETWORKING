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
