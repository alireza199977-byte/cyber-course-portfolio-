# Network Profile — [TNT]

Q1
IPv4: 10.206.0.xxx  
MAC: C4-03-A8-2B-7F-xx

Q2
A private IP works only inside local networks, while a public IP is reachable on the internet; routers use private IPs to protect internal devices.

Q3
IP = Layer 3 and can change.
MAC = Layer 2 and mostly fixed to hardware.

Q4
/16 has 65,536 total and 65,534 usable addresses.
Network: 10.206.0.0  
Broadcast: 10.206.255.255

Q5
Default gateway: 10.206.0.1  
Yes, same subnet — same 10.206.x.x range under /16.

Q6
Gateway ping: 25 ms  
1.1.1.1 is slower because it goes across the internet, not just the local network.

Q7
DNS allows using domain names instead of IP addresses.

8
DNS servers: 62.241.198.xxx (ISP resolvers)

Q9
example.com → 93.184.216.34  
Large sites may have multiple IPs due to load balancing/CDNs.

Q10
DNS queries reveal which websites you visit, even if HTTPS hides the content.

Q11
Hops: Unreachable (ICMP blocked)  
First hop: 10.206.0.1

Q12
* * * means the router blocks ICMP responses, not that the connection is broken.

Q13
Most ports listen on localhost, not exposed.
Network‑facing ports include: 135, 139, 445, and Windows RPC ports.

Q14
Examples:

445 → SMB file sharing
22 → SSH
Listening on 0.0.0.0 exposes the port to the network; localhost is safer.

Q15
My machine exposes more network‑facing services than expected, especially legacy ones like port 139.


## Identity
- IPv4 address: 10.206.0.xxx
- Subnet mask / CIDR: 255.255.0.0 (/16)
- MAC address: C4-03-A8-2B-7F-xx
- Network address: 10.206.0.0
- Broadcast address: 10.206.255.255

## Gateway and reachability
- Default gateway: 10.206.0.1
- Ping to gateway (avg): 25 ms
- Ping to 1.1.1.1 (avg):  ms

## DNS
- Configured DNS server(s): 62.241.198.xxx, 62.241.198.xxx
- example.com resolves to: 93.184.216.34

## Path to the internet
- Hops to example.com: Unreachable (ICMP blocked)
- First hop: 10.206.0.1 (internal gateway) 

## Listening ports
| **[Port](ca://s?q=Explain_port_numbers)** | **Protocol** | **Interface (localhost / all)** | **Common use** |
| --- | --- | --- | --- |
| 51100 | TCP | 127.0.0.1 (localhost) | Local app service |
| 50923 | TCP | 127.0.0.1 (localhost) | Local app service |
| 50100 | TCP | 127.0.0.1 (localhost) | Local app service |
| 27339 | TCP | 127.0.0.1 (localhost) | Ephemeral local port |
| 24830 | TCP | 127.0.0.1 (localhost) | Ephemeral local port |
| 22112 | TCP | 127.0.0.1 (localhost) | Ephemeral local port |
| 13032 | TCP | 127.0.0.1 (localhost) | Internal process |
| 13031 | TCP | 127.0.0.1 (localhost) | Internal process |
| 13030 | TCP | 127.0.0.1 (localhost) | Internal process |
| 11001 | TCP | 127.0.0.1 (localhost) | Internal service |
| 9013 | TCP | 127.0.0.1 (localhost) | Debug / local service |
| 9012 | TCP | 127.0.0.1 (localhost) | Debug / local service |
| 7778 | TCP | 127.0.0.1 (localhost) | Internal |
| 1043 | TCP | 127.0.0.1 (localhost) | Internal |
| 1042 | TCP | 127.0.0.1 (localhost) | Internal |
| **49677** | TCP | 0.0.0.0 (all interfaces) | Windows RPC / ephemeral |
| **49668** | TCP | 0.0.0.0 (all interfaces) | Windows RPC / ephemeral |
| **49667** | TCP | 0.0.0.0 (all interfaces) | Windows RPC / ephemeral |
| **49666** | TCP | 0.0.0.0 (all interfaces) | Windows RPC / ephemeral |
| **49665** | TCP | 0.0.0.0 (all interfaces) | Windows RPC / ephemeral |
| **49664** | TCP | 0.0.0.0 (all interfaces) | Windows RPC / ephemeral |
| 12177 | TCP | 0.0.0.0 (all interfaces) | System service |
| 5040 | TCP | 0.0.0.0 (all interfaces) | System service |
| **135** | TCP | 0.0.0.0 (all interfaces) | RPC Endpoint Mapper |
| **445** | TCP | :: (IPv6, all interfaces) | SMB file sharing |
| **139** | TCP | 10.206.0.xxx | NetBIOS (legacy file sharing) |
| 7680 | TCP | :: (IPv6) | Windows Update Delivery Optimization |
| 5357 | TCP | :: (IPv6) | WSD (printer discovery) |
| 42050 | TCP | ::1 (IPv6 localhost) | Local service |
| 28337 | TCP | ::1 (IPv6 localhost) | Local service |

## Reflection (150–200 words)
- What surprised you about your own network?
I was surprised by how many services on my machine were listening only on localhost. I expected fewer internal processes, but Windows uses many ephemeral ports for RPC and system functions. Seeing ports like 445 and 139 open to the network was also unexpected, since they are well‑known targets in local network attacks.
- Which open port (if any) would you want to investigate or close?
The port I would most likely investigate or close is port 139, because NetBIOS is an old protocol and usually not needed anymore. If file sharing is not required, disabling ports 139 and 445 would reduce the attack surface and make the system safer.
- Which command do you think you'll use most often, and why?
The command I think I’ll use most often is netstat / ss, because it quickly shows what services are listening and whether they are exposed to the network or only to localhost. It’s a simple but powerful way to understand the security posture of my machine.
