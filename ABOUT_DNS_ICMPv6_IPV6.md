I opened Wireshark and captured packets while opening Google and Discord in the background. I observed and learned about the following protocols:

- **ICMPv6 and IPv6:**  
  IPv6 is like a map, providing addresses for devices. ICMPv6 helps IPv6 by discovering neighbors and reporting errors like "destination unreachable." I saw three source addresses sending packets to the same destination `ff02::16` multiple times.  
  - `ff02` = link-local  
  - `ff02::16` = multicast group for IPv6 routers  
  This shows communication with multicast routers. Routers (Layer 3 devices) help connect multiple networks.

- **mDNS:**  
  mDNS lets devices discover each other on the LAN.

- **DNS:**  
  DNS translates domain names like `google.com` or `discord.com` into IP addresses. My device used DNS to find Discord’s server IP before connecting.

- **TCP and TLS:**  
  TCP ensures reliable, in-order delivery of data. TLS runs on top of TCP to provide secure encrypted communication.

- **UDP and QUIC:**  
  UDP is fast but unreliable. QUIC runs on top of UDP to provide **fast and secure** delivery of data, similar to TLS over TCP.
