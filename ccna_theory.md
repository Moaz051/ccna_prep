# **Comprehensive CCNA Study Guide (Theory Focused)**

## **Table of Contents**

- [1. Network Fundamentals](#1-network-fundamentals)
  - [1.1 Network Design Models](#11-network-design-models)
  - [1.2 MAC Addresses and Frames](#12-mac-addresses-and-frames)
  - [1.3 TCP vs UDP](#13-tcp-vs-udp)
  - [1.4 Common Network Protocols and Ports](#14-common-network-protocols-and-ports)
  - [1.5 HTTP Response Codes](#15-http-response-codes)
  - [1.6 Physical Interface and Cabling Types](#16-physical-interface-and-cabling-types)
  - [1.7 Interface and Cable Issues](#17-interface-and-cable-issues)
  - [1.8 IPv4 Addressing and Subnetting](#18-ipv4-addressing-and-subnetting)
  - [1.9 IPv6 Addressing and Types](#19-ipv6-addressing-and-types)
  - [1.10 Client OS IP Parameters](#110-client-os-ip-parameters)
  - [1.11 Wireless Principles](#111-wireless-principles)
  - [1.12 Virtualization Fundamentals](#112-virtualization-fundamentals)
  - [1.13 Switching Concepts](#113-switching-concepts)
- [2. Network Access](#2-network-access)
  - [2.1 Discovery Protocols (CDP & LLDP)](#21-discovery-protocols-cdp--lldp)
  - [2.2 Link Aggregation (EtherChannel)](#22-link-aggregation-etherchannel)
  - [2.3 VLANs and Trunking](#23-vlans-and-trunking)
  - [2.4 Spanning Tree Protocol (STP)](#24-spanning-tree-protocol-stp)
  - [2.5 Wireless Principles](#25-wireless-principles)
  - [2.6 Wireless LAN Controllers (WLC) & APs](#26-wireless-lan-controllers-wlc--aps)
  - [2.7 Power over Ethernet (PoE)](#27-power-over-ethernet-poe)
  - [2.8 Network Device Management Access](#28-network-device-management-access)
  - [2.9 Wireless LAN GUI Configuration (WLC)](#29-wireless-lan-gui-configuration-wlc)
- [3. IP Connectivity](#3-ip-connectivity)
  - [3.1 IP Addressing](#31-ip-addressing)
  - [3.2 Route Selection Process](#32-route-selection-process)
  - [3.3 Static Routes](#33-static-routes)
  - [3.4 OSPF (Open Shortest Path First)](#34-ospf-open-shortest-path-first)
  - [3.5 EIGRP (Enhanced Interior Gateway Routing Protocol)](#35-eigrp-enhanced-interior-gateway-routing-protocol)
  - [3.6 Important Network Tables](#36-important-network-tables)
- [4. IP Services](#4-ip-services)
  - [4.1 First Hop Redundancy Protocols (FHRP)](#41-first-hop-redundancy-protocols-fhrp)
  - [4.2 NAT (Network Address Translation)](#42-nat-network-address-translation)
  - [4.3 Quality of Service (QoS)](#43-quality-of-service-qos)
  - [4.4 Network Time Protocol (NTP)](#44-network-time-protocol-ntp)
  - [4.5 DHCP (Dynamic Host Configuration Protocol)](#45-dhcp-dynamic-host-configuration-protocol)
  - [4.6 DNS (Domain Name System)](#46-dns-domain-name-system)
  - [4.7 Syslog](#47-syslog)
  - [4.8 SSH Configuration](#48-ssh-configuration)
- [5. Security Fundamentals](#5-security-fundamentals)
  - [5.1 Security Concepts & Threats](#51-security-concepts--threats)
  - [5.2 AAA (Authentication, Authorization, Accounting)](#52-aaa-authentication-authorization-accounting)
  - [5.3 Access Control Lists (ACLs)](#53-access-control-lists-acls)
  - [5.4 Layer 2 Security Features](#54-layer-2-security-features)
  - [5.5 Wireless Security](#55-wireless-security)
  - [5.6 IPsec (Internet Protocol Security)](#56-ipsec-internet-protocol-security)
  - [5.7 Intrusion Detection & Prevention (IDS/IPS)](#57-intrusion-detection--prevention-idsips)
  - [5.8 Security Best Practices](#58-security-best-practices)
- [6. Automation and Programmability](#6-automation-and-programmability)
  - [6.1 Network Automation Benefits](#61-network-automation-benefits)
  - [6.2 Traditional vs Controller-Based Networking](#62-traditional-vs-controller-based-networking)
  - [6.3 Software-Defined Architecture (SDN)](#63-software-defined-architecture-sdn)
  - [6.4 Cisco Network Management Solutions](#64-cisco-network-management-solutions)
  - [6.5 REST APIs](#65-rest-apis)
  - [6.6 Configuration Management Tools](#66-configuration-management-tools)
  - [6.7 JSON (JavaScript Object Notation)](#67-json-javascript-object-notation)
  - [6.8 AI and Machine Learning in Networking](#68-ai-and-machine-learning-in-networking)
- [CCNA Exam Preparation Tips](#ccna-exam-preparation-tips)

## **1. Network Fundamentals**

### **1.1 Network Design Models**

**Two-Tier Model (Collapsed Core)**

- **Layers:** Access, Combined Core/Distribution
- **Concept:** Merges the Core and Distribution layers into one
- **Pros:** Simpler design, lower latency, cost-effective
- **Use Cases:** Small to medium-sized networks, branch offices where complexity isn't needed

**Three-Tier Model (Hierarchical)**

- **Layers & Functions:**
  - **Core:** Backbone; high-speed switching, reliability, redundancy. *Focus: Speed & Availability.*
  - **Distribution:** Policy enforcement; routing between VLANs (Inter-VLAN routing), Quality of Service (QoS), security policies, aggregation point for Access layer switches. *Focus: Control & Aggregation.*
  - **Access:** User connection point; end-device connectivity, Power over Ethernet (PoE), port security, VLAN assignment. *Focus: End User Access.*
- **Pros:** Scalable, modular, easy to troubleshoot, clear function separation
- **Use Cases:** Large enterprise networks, campus networks, data centers requiring structure and scalability

**Spine-Leaf Architecture**

- **Concept:** Modern data center design. Every Leaf switch connects to *every* Spine switch. Servers/endpoints connect *only* to Leaf switches. No direct Leaf-to-Leaf or Spine-to-Spine connections.
- **Layers:**
  - **Spine:** High-speed core/backbone switches
  - **Leaf:** Access layer switches providing endpoint connectivity
- **Benefits:** Predictable latency (max 2 hops), high bandwidth, easily scalable, consistent performance
- **Use Cases:** Data centers, cloud environments, high-performance computing (HPC)

**Other Topologies**

- **WAN (Wide Area Network):** Connects geographically separate sites (e.g., offices across cities/countries), often using service provider links
- **SOHO (Small Office/Home Office):** Simple setup, usually a single router/firewall and maybe a small switch or integrated wireless router
- **On-Premises vs. Cloud:**
  - **On-Premises:** You own and manage the physical hardware (servers, switches) at your location
  - **Cloud:** Resources (servers, storage, networking) are virtualized and accessed over the internet from a provider (AWS, Azure, GCP)

> 💡 **Exam Focus:** Know the roles of each layer in the **Three-Tier model**. Understand the benefits and use cases for **Two-Tier**, **Three-Tier**, and **Spine-Leaf** architectures.

### **1.2 MAC Addresses and Frames**

**MAC Address Structure**

- **What:** Unique 48-bit (6-byte) hardware address burned into a Network Interface Card (NIC)
- **Format:** MM:MM:MM:SS:SS:SS (Hexadecimal)
- **Parts:**
  - **OUI (Organizationally Unique Identifier):** First 3 bytes (MM:MM:MM). Assigned to vendors by IEEE. Identifies the manufacturer
  - **Device ID:** Last 3 bytes (SS:SS:SS). Assigned by the vendor, unique to the specific device

**Ethernet Frame Structure**

- **Preamble (7 bytes):** Alternating 1s and 0s (10101010...) used for clock synchronization
- **SFD (Start Frame Delimiter) (1 byte):** 10101011. Indicates the start of the frame content
- **Destination MAC (6 bytes):** MAC address of the intended recipient
- **Source MAC (6 bytes):** MAC address of the sender
- **EtherType/Length (2 bytes):**
  - If >= 1536 (0x0600): Indicates the Layer 3 protocol inside (e.g., 0x0800 for IPv4, 0x86DD for IPv6)
  - If < 1536: Indicates the length of the data field (older IEEE 802.3)
- **Data & Pad (46-1500 bytes):** The actual payload (e.g., IP packet). Padding is added if data is less than 46 bytes
- **FCS (Frame Check Sequence) (4 bytes):** Error detection field (CRC - Cyclic Redundancy Check). Calculated by sender, verified by receiver

**Frame Size Categories**

- **Runt:** < 64 bytes (with a bad FCS). Usually caused by collisions
- **Normal:** 64 - 1518 bytes (including FCS, excluding Preamble/SFD)
- **Giant:** > 1518 bytes (with a bad FCS)
- **Baby Giant:** Slightly larger than standard (e.g., up to 1600 bytes). Often allowed for protocols like QinQ or MPLS
- **Jumbo:** Much larger frames (e.g., up to 9216 bytes). Require configuration on all devices in the path. Used in data centers/storage networks

**Special MAC Addresses**

- **Broadcast:** FF:FF:FF:FF:FF:FF. Sent to all devices on the local network segment/VLAN
- **IPv4 Multicast:** Starts with 01:00:5E. Last 23 bits map to the IPv4 multicast group address
- **IPv6 Multicast:** Starts with 33:33. Last 32 bits map to the IPv6 multicast group address
- **Locally Administered:** Second bit of the first byte is set to 1 (e.g., 02:xx:xx:xx:xx:xx). Manually assigned MACs, overriding the burned-in address

**MAC Learning Process (Switches)**

1. Switch receives a frame on a port
2. Switch inspects the **Source MAC address**
3. Switch records the Source MAC and the **inbound port** in its **MAC address table**
   - If the MAC is new, a new entry is created
   - If the MAC exists but on a different port, the entry is updated (device moved)
   - The timestamp for the entry is updated
4. Switch inspects the **Destination MAC address**
5. Switch looks up the Destination MAC in its MAC address table:
   - **Match Found:** Forward the frame *only* out the specific port listed in the table. (Filtering)
   - **No Match Found (Unknown Unicast):** Flood the frame out *all other ports* within the same VLAN
   - **Broadcast/Multicast MAC:** Flood the frame out *all other ports* within the same VLAN
6. **Aging:** Entries are removed from the table if no frames are received from that MAC address for a certain period (default: **300 seconds / 5 minutes**)

> 💡 **Exam Focus:** Know the structure of a MAC address (OUI + Device ID). Understand the fields in an Ethernet frame. Recognize special MAC addresses (Broadcast, Multicast). Explain the switch MAC learning and forwarding process.

### **1.3 TCP vs UDP**

**TCP (Transmission Control Protocol)**

- **Type:** Connection-oriented (like a phone call)
- **Setup:** Establishes a connection using a **Three-Way Handshake** (SYN -> SYN/ACK -> ACK) before data transfer
- **Reliability:** **Guaranteed delivery**. Uses acknowledgments (ACKs) and retransmissions for lost packets
- **Ordering:** Sequence numbers ensure data is reassembled in the correct order
- **Flow Control:** Uses a **sliding window** mechanism to prevent the sender from overwhelming the receiver
- **Congestion Control:** Adjusts sending rate based on network conditions (slow start, etc.)
- **Error Detection:** Checksum validation
- **Overhead:** Higher (larger header: 20-60 bytes, connection state maintenance)
- **Speed:** Slower due to reliability mechanisms
- **Examples:** HTTP/HTTPS (Web), FTP (File Transfer), SMTP (Email Sending), SSH/Telnet (Remote Access)

**UDP (User Datagram Protocol)**

- **Type:** Connectionless (like sending a postcard)
- **Setup:** No handshake; just sends data
- **Reliability:** **Best-effort delivery**. No acknowledgments, no retransmissions. "Fire and forget"
- **Ordering:** No sequence numbers; packets may arrive out of order
- **Flow Control:** None. Sender can overwhelm receiver
- **Congestion Control:** None. Doesn't react to network congestion
- **Error Detection:** Basic checksum (optional in IPv4, mandatory in IPv6)
- **Overhead:** Lower (smaller header: 8 bytes, no connection state)
- **Speed:** Faster due to less overhead
- **Examples:** DNS (Name Resolution), DHCP (IP Assignment), SNMP (Network Management), VoIP (Voice), Video Streaming, Online Gaming (where speed is critical)

**Comparison Table**

| **Feature** | **TCP** | **UDP** |
|-------------|---------|---------|
| **Connection** | Connection-oriented | Connectionless |
| **Reliability** | Guaranteed delivery | Best-effort delivery |
| **Ordering** | Maintains order | No order guarantee |
| **Speed** | Slower | Faster |
| **Header Size** | 20-60 bytes | 8 bytes |
| **Flow Control** | Yes (Windowing) | No |
| **Error Recovery** | Yes (Retransmissions) | No |
| **Use Case** | Web, Email, File Transfer | Real-time apps, DNS, DHCP |

> 💡 **Exam Focus:** Understand the core differences: **TCP is reliable, ordered, connection-oriented, and slower**. **UDP is unreliable, unordered, connectionless, and faster**. Know common applications for each.

### **1.4 Common Network Protocols and Ports**

**Common TCP Protocols**

| **Protocol** | **Port(s)** | **Purpose** | **Notes** |
|--------------|-------------|-------------|-----------|
| HTTP | 80 | Web Browsing | Request/Response (GET, POST, etc.) |
| HTTPS | 443 | Secure Web Browsing | HTTP over TLS/SSL, encrypted |
| FTP | 20, 21 | File Transfer Protocol | Port 21 (Control), Port 20 (Data - Active) |
| SMTP | 25 | Email Sending | Outgoing mail; SMTPS (587) common now |
| POP3 | 110 | Email Retrieval | Downloads mail to client |
| IMAP | 143 | Email Management | Keeps mail on server, folders |
| SSH | 22 | Secure Shell | Encrypted remote login, file transfer (SFTP) |
| Telnet | 23 | Remote Login | **Insecure** (plaintext), legacy |
| SQL* | 1433 | MS SQL Server Database Access | Other DBs use different ports |
| RDP | 3389 | Remote Desktop Protocol (Windows) | Graphical remote access |

**Common UDP Protocols**

| **Protocol** | **Port(s)** | **Purpose** | **Notes** |
|--------------|-------------|-------------|-----------|
| DHCP | 67, 68 | Dynamic Host Configuration Protocol | Port 67 (Server), Port 68 (Client) |
| SNMP | 161, 162 | Simple Network Management Protocol | Port 161 (Queries), Port 162 (Traps) |
| TFTP | 69 | Trivial File Transfer Protocol | Simple, no authentication |
| NTP | 123 | Network Time Protocol | Time synchronization |
| DNS | 53 | Domain Name System | Name to IP resolution (can also use TCP 53) |
| RADIUS | 1812, 1813 | Remote Authentication Dial-In User Service | Port 1812 (Auth), Port 1813 (Acct) |
| SIP | 5060, 5061 | Session Initiation Protocol | VoIP/Video call setup (5061 for TLS) |
| RTP | Dynamic | Real-time Transport Protocol | Carries actual voice/video media stream |

**Protocol Categories by Layer (Simplified)**

| **Category** | **Examples** | **Key Characteristics** |
|--------------|--------------|-------------------------|
| **Application** | HTTP, FTP, SMTP, DNS | Provides services to end-users |
| **Transport** | TCP, UDP | Handles connections, port numbers |
| **Internet** | IP, ICMP | Logical addressing, routing |
| **Link** | Ethernet, PPP | Physical addressing, framing |
| **Management** | SNMP, NetFlow | Network monitoring & operations |
| **Security** | SSH, TLS, IPsec | Protection mechanisms |

> 💡 **Exam Focus:** Memorize the **port numbers** for common protocols (especially HTTP, HTTPS, FTP, SMTP, POP3, IMAP, SSH, Telnet, DNS, DHCP, RDP). Know which use **TCP** vs. **UDP**. Understand the basic **function** of each protocol.

### **1.5 HTTP Response Codes**

**Categories**

- **1xx (Informational):** Request received, processing continues. (Rarely seen by end users)
- **2xx (Success):** Action was successfully received, understood, and accepted
- **3xx (Redirection):** Further action must be taken to complete the request (e.g., go to a different URL)
- **4xx (Client Error):** The request contains bad syntax or cannot be fulfilled by the server. *It's the client's fault*
- **5xx (Server Error):** The server failed to fulfill an apparently valid request. *It's the server's fault*

**Common Codes**

| **Code** | **Meaning** | **Description** |
|----------|-------------|-----------------|
| **200** | **OK** | Standard success response. Content returned depends on request |
| 201 | Created | Resource successfully created (e.g., after a POST request) |
| 204 | No Content | Success, but there's no content to return in the response body |
| **301** | **Moved Permanently** | Resource has permanently moved to a new URL. Use the new URL |
| 302 | Found (Moved Temporarily) | Resource is temporarily at a different URL. Use original URL later |
| **400** | **Bad Request** | Server couldn't understand the request (e.g., invalid syntax) |
| **401** | **Unauthorized** | Authentication is required and failed, or wasn't provided |
| **403** | **Forbidden** | Server understood the request, but refuses to authorize it |
| **404** | **Not Found** | Requested resource could not be found on the server |
| **500** | **Internal Server Error** | Generic server error; something went wrong on the server side |
| 503 | Service Unavailable | Server is temporarily unable to handle the request (overloaded/maintenance) |
| 504 | Gateway Timeout | Server acting as a gateway didn't receive a timely response from upstream |

**HTTP Response Structure Example**

```
HTTP/1.1 200 OK <-- Status Line (Version, Code, Reason)
Date: Fri, 18 Apr 2025 12:37:00 GMT <-- Headers
Server: Apache/2.4.41 (Ubuntu)
Content-Type: text/html; charset=UTF-8
Content-Length: 1234

<!DOCTYPE html> <-- Response Body (Content)
<html>
...content...
</html>
```

> 💡 **Exam Focus:** Know the **five categories** (1xx-5xx). Memorize the meaning of the most common codes: **200, 301, 400, 401, 403, 404, 500**. Understand the difference between client errors (4xx) and server errors (5xx).

### **1.6 Physical Interface and Cabling Types**

**Fiber Optic Cables** (Transmit data using light pulses)

- **Single-mode Fiber (SMF):**
  - **Core:** Very small (8-10 microns)
  - **Light Path:** Single, direct path (mode)
  - **Distance:** **Long** distances (many kilometers, up to 100km+)
  - **Bandwidth:** Very high
  - **Light Source:** Lasers (more expensive)
  - **Connectors:** LC, SC, ST common
  - **Use Cases:** ISP backbones, long-haul links, campus backbones

- **Multimode Fiber (MMF):**
  - **Core:** Larger (50 or 62.5 microns)
  - **Light Path:** Multiple paths bounce inside the core (modes)
  - **Distance:** **Shorter** distances (up to ~2km, often less for high speeds). Limited by *modal dispersion* (light paths arriving at different times)
  - **Bandwidth:** High, but less than SMF over distance
  - **Light Source:** LEDs or VCSELs (less expensive)
  - **Connectors:** LC, SC, ST common
  - **Use Cases:** Data centers (server-to-switch), building backbones, shorter campus links

**Gigabit Ethernet Fiber Standards**

| **Standard** | **Cable Type** | **Distance** | **Wavelength** | **IEEE Standard** | **Primary Use** |
|--------------|----------------|--------------|----------------|-------------------|----------------|
| **1000BaseLX** | **Single-mode fiber** | **Up to 3.1 miles (5 km)** | **1310 nm** | **802.3z** | **Long-distance campus backbones** |
| 1000BaseSX | Multimode fiber | Up to 1,640 ft (500 m) | 850 nm | 802.3z | Building backbones, data centers |
| 1000BaseCX | Twinaxial copper | Up to 82 ft (25 m) | N/A | 802.3z | Switch-to-server, short-distance |
| 1000BaseZX | Single-mode fiber | Up to 43.5 miles (70 km) | 1550 nm | Proprietary | Extended long-distance, service providers |

**1000BaseLX Details:**
- Uses single-mode fiber with glass core, reflective cladding, and protective buffer
- Fiber optic cable transmits data as pulses of light
- Not susceptible to electromagnetic interference (EMI)
- Covered with protective jacket, typically rubber
- Uses ST, SC, and LC connectors for termination
- Subset of IEEE 802.3z standard
- Provides gigabit Ethernet over longer distances than other standards

**Fiber Optic Advantages:**
- Immune to electromagnetic interference
- Higher bandwidth capabilities
- Greater distance support
- Better security (difficult to tap)
- Smaller diameter and lighter weight
- No risk of electrical sparks (safe for hazardous environments)

**Common Fiber Connectors:**
- ST (Straight Tip): Bayonet-style connector
- SC (Subscriber Connector): Push-pull connector with square face
- LC (Lucent Connector): Small form-factor connector, increasingly common

**Note:** Single-mode fiber has a smaller core diameter (8-10 microns) than multimode fiber (50-62.5 microns), allowing light to travel in a single path with less dispersion, enabling longer distances.


**Copper Cables** (Transmit data using electrical signals)

- **Unshielded Twisted Pair (UTP):**
  - **Structure:** Pairs of wires twisted together to reduce interference. No metallic shield
  - **Connectors:** RJ-45
  - **Pros:** Most common, flexible, inexpensive
  - **Cons:** Susceptible to Electromagnetic Interference (EMI) / Radio Frequency Interference (RFI)
  - **Categories (Common):**
    - **Cat5e:** Supports 1 Gbps up to 100m
    - **Cat6:** Supports 1 Gbps up to 100m, 10 Gbps up to 55m. (Tighter twists, less crosstalk)
    - **Cat6a:** Supports 10 Gbps up to 100m. (Often shielded)
    - **Cat7/Cat8:** Higher speeds, typically shielded
  - **Use Cases:** Most LAN connections (desktops, phones, APs)

- **Shielded Twisted Pair (STP):**
  - **Structure:** Similar to UTP but includes metallic shielding around pairs or the entire cable
  - **Pros:** Better noise immunity than UTP
  - **Cons:** More expensive, less flexible, requires proper grounding
  - **Use Cases:** High-interference environments (factories, near heavy machinery)

- **Coaxial Cable:**
  - **Structure:** Single center conductor, dielectric insulator, metallic shield, outer jacket
  - **Pros:** Higher bandwidth and better EMI resistance than early twisted pair
  - **Cons:** Bulky, less common for LANs now
  - **Use Cases:** Cable modems (DOCSIS), some video distribution (legacy)

**Ethernet Connection Types**

- **Shared Media (Legacy):** Multiple devices on the same physical segment contend for access (e.g., using a hub). Operates in **half-duplex** (transmit OR receive). Uses **CSMA/CD** (Carrier Sense Multiple Access / Collision Detection). Collisions are normal but reduce efficiency. *Rarely used today*

- **Point-to-Point (Switched):** Direct connection between two devices (e.g., switch-to-switch, switch-to-host). Operates in **full-duplex** (transmit AND receive simultaneously). No collisions. Standard in modern networks

**Common Media Standards & Distances**

| **Standard** | **Media** | **Speed** | **Max Distance** | **Connector** | **Notes** |
|--------------|-----------|-----------|------------------|---------------|-----------|
| 1000BASE-T | Cat5e/6 UTP | 1 Gbps | 100m | RJ-45 | Gigabit Ethernet over Copper |
| 1000BASE-SX | MMF | 1 Gbps | ~550m | LC/SC | Short wavelength fiber |
| 1000BASE-LX | SMF | 1 Gbps | 5km+ | LC/SC | Long wavelength fiber |
| 10GBASE-T | Cat6a/7 UTP | 10 Gbps | 100m | RJ-45 | 10 Gig over Copper |
| 10GBASE-SR | MMF | 10 Gbps | ~300-400m | LC | Short Reach fiber |
| 10GBASE-LR | SMF | 10 Gbps | 10km | LC | Long Reach fiber |
| 40GBASE-SR4 | MMF (Parallel) | 40 Gbps | ~100-150m | MPO/MTP | Uses multiple fiber strands |
| 100GBASE-SR4 | MMF (Parallel) | 100 Gbps | ~100m | MPO/MTP | Uses multiple fiber strands |

> 💡 **Exam Focus:** Differentiate **SMF vs. MMF** (distance, core size, cost, light source). Know common **UTP categories (Cat5e, Cat6, Cat6a)** and their speed/distance capabilities. Understand **Shared vs. Point-to-Point** media and **Half vs. Full Duplex**. Recognize common fiber standards (SX, LX, SR, LR).

**Digital WAN Circuit Standards Comparison**

| **Feature** | **T1** | **E1** | **T3** | **E3** |
|-------------|--------|--------|--------|--------|
| **Bandwidth** | 1.544 Mbps | 2.048 Mbps | 44.736 Mbps | 34.368 Mbps |
| **Channel Structure** | 24 DS0 channels + framing bit | 32 eight-bit timeslots | 672 DS0 channels | 16 E1 lines |
| **Frame Size** | 193 bits | 256 bits (32 × 8) | Multiple T1s (28) | Multiple E1s (16) |
| **Frame Rate** | 8,000 frames/second | 8,000 frames/second | 8,000 frames/second | 8,000 frames/second |
| **Calculation** | 193 × 8,000 = 1.544 Mbps | 256 × 8,000 = 2.048 Mbps | 5,592 × 8,000 = 44.736 Mbps | 4,296 × 8,000 = 34.368 Mbps |
| **Media** | 2 pairs shielded copper | 2 pairs shielded copper | Coaxial or fiber | Coaxial or fiber |
| **Primary Region** | North America, Japan | Europe, Australia, South America | North America, Japan | Europe, Australia, South America |
| **Common Application** | SMB internet, voice | SMB internet, voice | ISP backbones, large enterprises | ISP backbones, large enterprises |

**T-Carrier System (North American Standard)**

- **T1:**
  - **Bandwidth:** 1.544 Mbps
  - **Structure:** Uses DS1 (Digital Signal 1) signaling frames
  - **Composition:** 24 DS0 channels (64 Kbps each) plus 1 framing bit
  - **Channel Size:** Each DS0 transfers 8 bits at a time
  - **Frame Rate:** 8,000 DS1 frames per second
  - **Calculation:** 24 channels × 8 bits + 1 framing bit = 193 bits × 8,000 frames/sec = 1.544 Mbps
  - **Physical:** Two pairs of shielded copper wires (one for transmit, one for receive)

- **T3:**
  - **Bandwidth:** 44.736 Mbps
  - **Structure:** Equivalent to 28 T1 circuits
  - **Composition:** 672 DS0 channels
  - **Usage:** Typically cost-prohibitive except for ISPs and large enterprises
  - **Media:** Typically delivered over coaxial cable or fiber

**E-Carrier System (European Standard)**

- **E1:**
  - **Bandwidth:** 2.048 Mbps
  - **Structure:** 32 eight-bit timeslots
  - **Differences from T1:**
    - More bandwidth (2.048 vs 1.544 Mbps)
    - More channels (32 vs 24)
    - Used primarily in Europe vs North America
  - **Frame Rate:** 8,000 timeslot groups per second
  - **Calculation:** 32 timeslots × 8 bits × 8,000 frames/sec = 2.048 Mbps

- **E3:**
  - **Bandwidth:** 34.368 Mbps
  - **Structure:** Equivalent to 16 E1 circuits
  - **Usage:** Typically used by service providers for backbone connections
  - **Regional Deployment:** European standard

**Fractional Services**

- **Fractional T1/E1:** Allows organizations to purchase only the channels they need
- **Typical Increments:** T1 (in 64 Kbps DS0 increments), E1 (in 64 Kbps timeslot increments)
- **Cost Efficiency:** Pay only for required bandwidth while using same physical infrastructure

**Channel Service Unit/Data Service Unit (CSU/DSU)**

- Required equipment to connect router/network to T1/E1 service
- Handles encoding, electrical termination, and clocking
- Modern routers often have integrated CSU/DSU in WAN interface cards

> 💡 **Exam Focus:** Remember the exact bandwidth values of common WAN circuits: T1 (1.544 Mbps), E1 (2.048 Mbps), T3 (44.736 Mbps), and E3 (34.368 Mbps). Know that T-carrier is used primarily in North America and Japan, while E-carrier is used in Europe. Understand how the bandwidth is calculated based on channel structure and frame rate.




### **1.7 Interface and Cable Issues**

**Common Layer 1 (Physical) Issues**

- **Connectivity:**
  - Cables unplugged or loose
  - Wrong cable type used (e.g., crossover vs. straight-through on older devices *without* Auto-MDIX)
  - Damaged cables (kinks, cuts, excessive bends violating bend radius)
  - Faulty ports, transceivers (SFPs, QSFPs), or NICs
  - Exceeded cable distance limitations
  - Bent pins in connectors

- **Diagnosis:**
  - Check **link lights** on devices (solid green usually means good link)
  - Physically inspect cables and connections
  - Swap with known-good cables or ports
  - Use cable testers for continuity, shorts, wiring map issues

**Common Layer 2 (Data Link) Interface Issues**

- **Collisions:**
  - **What:** Occur when two devices transmit simultaneously on a **shared medium (half-duplex)**
  - **Normal Collisions:** Expected in half-duplex, but excessive collisions indicate high traffic load
  - **Late Collisions:** Occur *after* the first 64 bytes of the frame. **Always indicate a problem**, usually a **duplex mismatch**
  - **Impact:** Reduced throughput due to retransmissions

- **Duplex Mismatch:**
  - **What:** One side of a link is configured for full-duplex, the other for half-duplex
  - **Symptoms:** Very slow performance, high error counts (especially **CRC errors** and **late collisions** on the half-duplex side)
  - **Cause:** Auto-negotiation failure or manual misconfiguration
  - **Fix:** Ensure both sides are set to **auto-negotiate** (best practice) or manually configure **both sides identically** (e.g., both full, both 1000 Mbps)

**Duplex Mismatch Indicators**

When troubleshooting suspected duplex mismatches on Ethernet LANs, look for these error counter increases:

- **Alignment Errors:** 
  - Frames that don't end with an even multiple of 8 bits (octets)
  - Strong indicator of duplex mismatch
  - Typically appear on the half-duplex side of a mismatch

- **FCS (Frame Check Sequence) Errors:**
  - Frames that fail the CRC check
  - Common symptom of duplex mismatch
  - Also seen with cable issues and EMI/RFI interference

- **Runts:**
  - Frames smaller than 64 bytes with a bad FCS
  - Often caused by collisions due to duplex mismatch
  - A runt is a frame that is fewer than 64 bytes and has a bad FCS

- **Late Collisions:**
  - Collisions detected after 512 bits (64 bytes) have been transmitted
  - **Always indicate a problem**, nearly always a duplex mismatch
  - Typically, half-duplex interfaces report late collisions when connected to full-duplex interfaces

- **NOT Indicators of Duplex Mismatch:**
  - **Baby Giants:** Slightly larger than standard frames (up to 1,600 bytes)
    - Caused by Q-in-Q encapsulation, MPLS, or other features adding to frame size
    - Normal for certain configurations

**Connection Type Symptoms:**
- A half-duplex port connected to a full-duplex port will report late collisions on the half-duplex side
- The full-duplex side will report different errors: runts, FCS errors, and alignment errors

**Performance Impact:**
- Severe performance degradation (often 30-99% packet loss)
- Intermittent connectivity
- Slow file transfers




- **Speed Mismatch:**
  - **What:** Interfaces configured for different speeds (e.g., 100 Mbps vs 1000 Mbps)
  - **Symptoms:** Usually **no link** at all, or interface flapping (up/down)
  - **Cause:** Manual misconfiguration or auto-negotiation failure
  - **Fix:** Ensure both sides are set to **auto-negotiate** or manually configure **both sides identically**

**Common Interface Errors**

- **Input Errors:** Problems with frames received by the interface
  - **Runts:** Frames < 64 bytes with bad FCS. Often due to collisions
  - **Giants:** Frames > max size (e.g., 1518 bytes) with bad FCS. Often faulty NIC
  - **CRC (Cyclic Redundancy Check) errors:** Frame failed the FCS check. Indicates data corruption. *Causes: Bad cable, faulty NIC/port, interference, duplex mismatch*
  - **Frame errors:** Incorrect frame format (e.g., alignment errors). Often related to CRC errors
  - **Input errors (generic counter):** Sum of various input problems

- **Output Errors:** Problems with frames transmitted by the interface
  - **Collisions:** (See above - relevant for half-duplex)
  - **Late Collisions:** (See above - indicates duplex mismatch)
  - **Output errors (generic counter):** Sum of various output problems
  - **Buffer failures / Output drops:** Interface buffers are full due to congestion; frames are dropped





**Interface Status**

- **up/up**: Layer 1 (Physical) is up, Layer 2 (Data Link protocol) is up. **Operational**
- **down/down**: Layer 1 is down (e.g., cable unplugged, other end off, bad port). Layer 2 is consequently down
- **administratively down/down**: Interface was manually shut down using the shutdown command
- **up/down**: Layer 1 is up, but Layer 2 protocol isn't running correctly (e.g., keepalive issues, encapsulation mismatch on WAN links, STP blocking *can sometimes* show this)

**Interface Flapping:** Interface repeatedly goes up and down. Causes include loose cables, bad hardware, power issues, duplex/speed mismatches, STP topology changes.

> 💡 **Exam Focus:** Understand how to interpret interface status and error counters. Recognize symptoms of **duplex mismatch** (slow speed, CRC errors, late collisions). Know common causes for interfaces being down/down or admin down.

### **1.8 IPv4 Addressing and Subnetting**

**IPv4 Address Structure**

- **Format:** 32-bit number, usually written as four 8-bit numbers (octets) in dotted-decimal notation (e.g., 192.168.1.1)
- **Components:** Divided into a **Network portion** and a **Host portion**
- **Subnet Mask:** A 32-bit number that defines the boundary between the Network and Host portions. Written in dotted-decimal (e.g., 255.255.255.0) or CIDR notation (e.g., /24)
  - 1s in the mask correspond to the Network portion
  - 0s in the mask correspond to the Host portion

**Private IPv4 Ranges (RFC 1918)** - Not routable on the public internet

- **Class A:** 10.0.0.0 to 10.255.255.255 (10.0.0.0/8)
- **Class B:** 172.16.0.0 to 172.31.255.255 (172.16.0.0/12)
- **Class C:** 192.168.0.0 to 192.168.255.255 (192.168.0.0/16)

**APIPA (Automatic Private IP Addressing)**

- Range: 169.254.0.0 to 169.254.255.255 (169.254.0.0/16)
- Use: Self-assigned by a device if it's configured for DHCP but fails to contact a DHCP server. Allows communication on the *local* link only; not routable

**Subnetting Concepts**

- **CIDR (Classless Inter-Domain Routing):** Using prefix lengths (/prefix) instead of fixed classes (A, B, C) to define the network portion. Allows flexible network sizes
- **Subnetting:** Borrowing bits from the Host portion to create more Network portions (subnets)
- **Key Formulas:**
  - n = number of bits borrowed for subnets
  - m = number of bits remaining for hosts
  - **Number of Subnets Created:** 2^n
  - **Number of Usable Hosts per Subnet:** 2^m - 2 (Subtract 2 for the Network Address and Broadcast Address)
  - **Block Size (Increment):** 256 - <subnet mask value in the interesting octet>

**Subnetting Example:** Subnet 192.168.10.0/24 to create networks with at least 50 hosts each.

1. **Hosts Needed:** 50. Find the smallest m where 2^m - 2 >= 50
   - 2^5 - 2 = 30 (Too small)
   - 2^6 - 2 = 62 (Okay). Need m = 6 host bits
2. **Network Bits:** Total bits = 32. Host bits m = 6. Network bits = 32 - 6 = 26. New prefix is /26
3. **Subnet Mask:** /26 means 26 ones: 11111111.11111111.11111111.11000000 = 255.255.255.192
4. **Block Size:** In the 4th octet: 256 - 192 = 64
5. **Subnets:** Start at 0 and add the block size:
   - 192.168.10.0/26 (Network: .0, Usable: .1 to .62, Broadcast: .63)
   - 192.168.10.64/26 (Network: .64, Usable: .65 to .126, Broadcast: .127)
   - 192.168.10.128/26 (Network: .128, Usable: .129 to .190, Broadcast: .191)
   - 192.168.10.192/26 (Network: .192, Usable: .193 to .254, Broadcast: .255)

**Special Addresses within a Subnet**

- **Network Address:** First address (all host bits are 0). Identifies the subnet. Cannot be assigned to a host
- **Broadcast Address:** Last address (all host bits are 1). Used to send messages to all hosts in the subnet. Cannot be assigned to a host
- **Usable Host Addresses:** All addresses between the Network and Broadcast addresses
- **Default Gateway:** Router's IP address on that subnet, used by hosts to reach other networks. Typically the first (.1) or last (.254) usable address
- **Loopback Address:** 127.0.0.1 (part of 127.0.0.0/8). Used by a host to test its own TCP/IP stack

**VLSM (Variable Length Subnet Mask)**

- **Concept:** Using different subnet mask lengths (/prefixes) for different subnets within the same larger network block
- **Benefit:** Allocates addresses more efficiently based on the actual number of hosts needed per subnet, reducing waste

> 💡 **Exam Focus:** **Master subnetting!** Be able to quickly calculate: Network Address, Broadcast Address, Number of Usable Hosts, and Usable Host Range for any given IP/prefix. Understand private IP ranges (RFC 1918) and APIPA. Know the concept and benefit of VLSM.

### **1.9 IPv6 Addressing and Types**

**IPv6 Address Structure**

- **Size:** 128 bits (vs. 32 bits for IPv4)
- **Format:** Eight 16-bit blocks (hextets) separated by colons (:). Written in hexadecimal
  - Example: 2001:0db8:85a3:0000:0000:8a2e:0370:7334
- **Compression Rules (Shortening):**
  1. **Omit Leading Zeros:** Within any block, leading zeros can be removed. 0db8 -> db8, 0000 -> 0, 0370 -> 370
     - Example: 2001:db8:85a3:0:0:8a2e:370:7334
  2. **Omit Consecutive Zero Blocks:** One sequence of consecutive all-zero blocks can be replaced with a double colon ::. **This can only be used ONCE per address**
     - Example: 2001:db8:85a3::8a2e:370:7334 (Replaced :0:0:)
     - Example: fe80:0:0:0:aaaa:bbbb:cccc:dddd -> fe80::aaaa:bbbb:cccc:dddd

**IPv6 Address Types**

- **Unicast:** One-to-One communication
  - **Global Unicast (GUA):**
    - Prefix: 2000::/3 (Addresses starting with 2 or 3) assigned by ICANN/RIRs 
    - Scope: Public internet routable. Equivalent to public IPv4. Globally unique
    - Structure: Typically Global Routing Prefix (ISP assigned, e.g., /48) + Subnet ID (used internally, e.g., 16 bits) + Interface ID (64 bits)
  - **Unique Local (ULA):**
    - Prefix: FC00::/7 (Usually FD00::/8 used for local generation)
    - First 7 bits are always 1111110 (FC00::/7)
    - Scope: Private, not routable on the internet. Equivalent to private IPv4 (RFC 1918). Meant to be unique *within* an organization or site
    - Structure: FD + Global ID (random 40 bits) + Subnet ID (16 bits) + Interface ID (64 bits)
  - **Link-Local:**
    - Prefix: FE80::/10 (Interface ID usually makes it FE80::/64)
    - Scope: **Local link only**. Not routable off the local segment
    - Use: Automatically configured on *all* IPv6 interfaces. Used for Neighbor Discovery Protocol (NDP), DHCPv6 communication, routing protocol neighbor adjacencies
    - Structure: FE80:: (first 64 bits, often) + Interface ID (64 bits)

- **Multicast:** One-to-Many communication
  - Prefix: FF00::/8
  - Scope: Defined by flags and scope field (e.g., FF02:: is Link-Local scope)
  - Well-Known Addresses:
    - FF02::1: All IPv6 nodes on the link
    - FF02::2: All IPv6 routers on the link
    - FF02::1:FFxx:xxxx: Solicited-Node Multicast (used in NDP for address resolution, replaces ARP). xx:xxxx are the last 24 bits of the target unicast address

- **Anycast:** One-to-Nearest (from a group)
  - Uses the same address format as Unicast
  - Same address assigned to multiple devices (e.g., DNS servers)
  - Packets sent to an anycast address are routed to the *closest* device (in routing terms) advertising that address

**Interface ID (Last 64 bits)**

- Can be manually configured
- Can be automatically generated using **Modified EUI-64**

**Modified EUI-64 Process** (Generates Interface ID from MAC Address)

1. Take the 48-bit MAC address (e.g., 00:0C:29:1D:8A:B5)
2. Split it in the middle: 000C:29 and 1D:8A:B5
3. Insert FFFE in the middle: 000C:29:FF:FE:1D:8A:B5
4. Convert the first byte to binary: 00 -> 00000000
5. **Flip the 7th bit** (Universal/Local or U/L bit): 00000000 -> 00000010 = 02
6. Resulting Interface ID: 020C:29FF:FE1D:8AB5
7. Combine with Link-Local Prefix: FE80::020C:29FF:FE1D:8AB5

**Special IPv6 Addresses**

- **Unspecified Address:** ::/128 (All zeros). Used as a source address when a device doesn't have an IP yet (e.g., DHCPv6 discovery)
- **Loopback Address:** ::1/128. Equivalent to 127.0.0.1 in IPv4
- **IPv4-Mapped:** ::FFFF:<IPv4 Address>. Used to represent an IPv4 address within an IPv6 system

> 💡 **Exam Focus:** Understand the **different IPv6 address types** (GUA, ULA, Link-Local, Multicast) and their **scope/purpose**. Be able to **identify** these types based on their prefixes. Know the **address compression rules**. Understand the **EUI-64 process** for generating Interface IDs.

**IPv6 Address Type Comparison Table**

| **Feature** | **Global Unicast (GUA)** | **Unique Local (ULA)** | **Link-Local** | **Multicast** | **Anycast** |
|-------------|--------------------------|------------------------|----------------|---------------|-------------|
| **Prefix** | 2000::/3 (starts with 2 or 3) | FC00::/7 (FD00::/8 common) | FE80::/10 | FF00::/8 | Uses unicast format |
| **Scope** | Global (internet-routable) | Organization-wide | Single link only | Defined by scope field | Variable |
| **IPv4 Analog** | Public IP addresses | Private IP (RFC 1918) | 169.254.0.0/16 (APIPA) | Class D addresses | No direct equivalent |
| **Primary Purpose** | Internet connectivity | Internal communication | Neighbor discovery, local protocols | One-to-many communication | Service redundancy |
| **Configuration** | Manual, DHCPv6, SLAAC | Manual, internally generated | Automatic on all interfaces | Predefined or assigned | Manual (same as unicast) |
| **Structure** | Global Prefix (/48)<br>Subnet ID (16 bits)<br>Interface ID (64 bits) | FD + Global ID (40 bits)<br>Subnet ID (16 bits)<br>Interface ID (64 bits) | FE80::<br>Interface ID (64 bits) | Format: FF[flags][scope]:group-ID | Same as unicast |
| **Example** | 2001:db8:1234:5678::1/64 | fd12:3456:789a:1::1/64 | fe80::a1b2:c3ff:fe45:6789 | ff02::1 (all nodes) | 2001:db8:85a3::8a2e:370:7334 |
| **Uniqueness Scope** | Globally unique | Unique within organization | Unique on link | Based on scope field | Not unique (shared) |
| **Routable Outside Network** | Yes | No | No | Limited by scope | Yes (to nearest) |
| **Default Gateway** | Can serve as | Can serve as | Cannot serve as | N/A | Can serve as |
| **Used For** | Internet services, global communication | Internal services, private networks | NDP, routing protocols, DHCPv6 | Service discovery, network protocols | DNS servers, load balancing |
| **Autoconfiguration** | Yes (SLAAC) | No | Yes (always) | No | No |

**Special Multicast Addresses**

| **Address** | **Scope** | **Purpose** |
|-------------|-----------|-------------|
| **FF01::1** | Node-local | All interfaces on node |
| **FF02::1** | Link-local | All nodes on link |
| **FF02::2** | Link-local | All routers on link |
| **FF02::1:2** | Link-local | All DHCP servers/relays |
| **FF02::1:FFXX:XXXX** | Link-local | Solicited-node multicast (NDP) |
| **FF05::1:3** | Site-local | All DHCP servers |

**Multicast Scope Field Values**

| **Value** | **Scope** | **Range** |
|-----------|-----------|-----------|
| **1** | Node-local | Single node |
| **2** | Link-local | Single link |
| **3** | Subnet-local | Single subnet |
| **4** | Admin-local | Administrator-defined region |
| **5** | Site-local | Single site |
| **8** | Organization-local | Organization |
| **E** | Global | Internet |

**Memory Aid for IPv6 Address Types**

- **G-ULA:** **G**lobal unicast, 2000::/3, **G**oes to the internet (**G**lobally routable)
- **F-ULA:** **F**ederation unicast (Unique Local), **F**C00::/7, **F**orbidden from internet (organization only)
- **FELL:** **FE**80 = **L**ink-**L**ocal, never leaves the **L**ink
- **FIRE:** **F**F = mult**I**cast, **R**outed to **E**veryone in the group

> 💡 **Exam Focus:** Understand the prefixes and scope of each address type. Know that link-local addresses are automatically configured on all IPv6 interfaces and play a critical role in neighbor discovery. Recognize multicast addresses FF02::1 (all nodes) and FF02::2 (all routers). Understand that ULAs serve a similar purpose to RFC 1918 private addresses in IPv4.



### **1.10 Client OS IP Parameters**

**Windows**

- **Command-Line Tools:**
  - ipconfig: Display basic IP settings (IP, Mask, Gateway)
  - ipconfig /all: Show detailed configuration (MAC, DHCP server, DNS servers, Lease info)
  - ipconfig /release: Release DHCP lease
  - ipconfig /renew: Obtain a new DHCP lease
  - ipconfig /displaydns: Show DNS cache contents
  - ipconfig /flushdns: Clear the DNS resolver cache
  - ping <ip_or_hostname>: Test reachability using ICMP Echo Request/Reply
    - ping -4 <host>: Force IPv4
    - ping -6 <host>: Force IPv6
  - tracert <ip_or_hostname>: Trace the route (hops) to a destination
  - netstat -an: Show active TCP/UDP connections and listening ports
  - netstat -r or route print: Display the IP routing table
  - nslookup <hostname>: Query DNS servers

- **GUI:**
  - Control Panel > Network and Sharing Center > Change adapter settings
  - Right-click adapter > Properties > Select Internet Protocol Version 4 (TCP/IPv4) or Version 6 (TCP/IPv6) > Properties
  - Configure static IP or obtain automatically (DHCP). Set DNS servers

**macOS**

- **Command-Line Tools:**
  - ifconfig <interface>: Display interface configuration (e.g., ifconfig en0). (Legacy, ip command preferred if available)
  - networksetup -getinfo <network_service>: Display info for a service (e.g., networksetup -getinfo "Wi-Fi")
  - networksetup -setmanual <network_service> <ip> <mask> <gateway>: Configure static IP
  - ping, traceroute, netstat: Similar functionality to Windows/Linux
  - dig <hostname> or nslookup <hostname>: DNS queries

- **GUI:**
  - System Preferences (or System Settings) > Network
  - Select the interface (e.g., Wi-Fi, Ethernet)
  - Click Advanced... (if needed)
  - Configure TCP/IP settings (DHCP, Manual), DNS servers

**Linux**

- **Command-Line Tools:**
  - ip addr show or ip a: Display IP addresses and interface info (modern tool)
  - ip link show: Show interface status (Up/Down)
  - ip route show or ip r: Display the routing table
  - ifconfig: Display interface configuration (legacy tool)
  - ping, traceroute, netstat, ss (socket statistics, replaces netstat): Similar functionality
  - dig <hostname> or nslookup <hostname>: DNS queries

- **Configuration Files (Common Locations):**
  - /etc/network/interfaces (Debian/Ubuntu - older style)
  - /etc/sysconfig/network-scripts/ifcfg-<interface> (RHEL/CentOS/Fedora)
  - /etc/netplan/*.yaml (Modern Ubuntu)
  - /etc/resolv.conf: DNS server addresses
  - /etc/hosts: Static hostname-to-IP mappings

- **GUI:** Varies depending on the desktop environment (GNOME, KDE, etc.). Usually found in System Settings under "Network" or "Connections"

**Verification Checklist (General)**

1. **Check IP/Mask:** Is it correct for the network? (ipconfig, ip addr)
2. **Check Default Gateway:** Is it correct and reachable? (ipconfig, ip route, ping <gateway_ip>)
3. **Check DNS Servers:** Are they configured correctly? (ipconfig /all, cat /etc/resolv.conf)
4. **Test Local Connectivity:** ping <gateway_ip>
5. **Test Internet Connectivity (IP):** ping 8.8.8.8 (Google's public DNS)
6. **Test DNS Resolution:** ping google.com (or nslookup google.com)
7. **Trace Route:** tracert <destination> or traceroute <destination>

**Common IP Parameter Issues**

- **Duplicate IP Address:** Two devices with the same IP on the same network
- **Incorrect Subnet Mask:** Prevents proper communication within the local network or reaching the gateway
- **Incorrect/Missing Default Gateway:** Cannot reach devices outside the local subnet
- **Incorrect/Missing DNS Servers:** Cannot resolve hostnames to IP addresses
- **APIPA Address (169.254.x.x):** Indicates DHCP failure. Device couldn't get an IP from the server
- **Multiple Default Gateways:** Can cause unpredictable routing behavior

> 💡 **Exam Focus:** Know the primary commands for viewing IP configuration on **Windows (ipconfig /all)**, **Linux (ip addr show)**, and **macOS (ifconfig or networksetup)**. Understand the purpose of ping, tracert/traceroute, and nslookup/dig. Be able to identify common configuration problems based on symptoms.

### **1.11 Wireless Principles**

**RF (Radio Frequency) Basics**

- **Frequency Bands:**
  - **2.4 GHz (802.11b/g/n/ax):**
    - Pros: Longer range, better penetration through obstacles
    - Cons: More crowded, more interference (microwaves, Bluetooth, cordless phones), fewer non-overlapping channels
  - **5 GHz (802.11a/n/ac/ax):**
    - Pros: Less interference, more channels, higher potential speeds
    - Cons: Shorter range, less penetration through obstacles. Some channels require DFS (Dynamic Frequency Selection) to avoid radar interference
  - **6 GHz (802.11ax / Wi-Fi 6E):**
    - Pros: Newest band, very clean spectrum (less interference), even more channels
    - Cons: Shortest range, requires Wi-Fi 6E compatible devices

- **Signal Characteristics:**
  - **Attenuation:** Signal weakens with distance and when passing through objects (walls, floors)
  - **Interference:** Signals from other devices (Wi-Fi or non-Wi-Fi) can disrupt communication
  - **Reflection:** Signals bounce off surfaces
  - **Multipath:** Reflected signals arrive at the receiver at different times, potentially causing issues or being used constructively (MIMO)
  - **Signal Strength:** Measured in **dBm** (decibels relative to one milliwatt). Negative values, closer to 0 is stronger (e.g., -50 dBm is stronger than -70 dBm)

**Channel Management**

- **2.4 GHz Channels:**
  - North America: Channels 1-11
  - **Non-overlapping Channels: 1, 6, 11.** (Each is 20 MHz wide, need 25 MHz separation). Using overlapping channels causes interference

- **5 GHz Channels:**
  - Many more non-overlapping channels (e.g., 24+ in the US)
  - Wider channel options (20 MHz, 40 MHz, 80 MHz, 160 MHz) for higher speeds, but wider channels mean fewer non-overlapping options and higher potential for interference

- **Cell Planning:** Designing AP placement and channel assignments
  - Goal: Provide adequate coverage and capacity while minimizing interference
  - Use non-overlapping channels for adjacent APs (e.g., checkerboard pattern with 1, 6, 11)
  - Aim for cell overlap of 10-15% (around -67 dBm signal strength at the edge) for smooth roaming

**Wireless Identifiers**

- **SSID (Service Set Identifier):** The **network name** you see when connecting (e.g., "MyHomeWiFi"). Up to 32 characters. Can be broadcast or hidden
- **BSSID (Basic Service Set Identifier):** The **MAC address** of the AP's radio for a specific BSS. Uniquely identifies an access point's radio for a given band

**Service Set Types**

- **BSS (Basic Service Set):** A single Access Point (AP) and its connected clients. Identified by the AP's BSSID
- **ESS (Extended Service Set):** Two or more BSSs (APs) connected by a wired network (distribution system), all sharing the **same SSID**. Allows clients to roam between APs. This is the standard for most enterprise/campus Wi-Fi
- **IBSS (Independent BSS):** Also known as **Ad-Hoc mode**. Direct client-to-client communication without an AP. Limited use cases

**Wireless Encryption & Security**

- **Open:** No encryption. **Insecure**
- **WEP (Wired Equivalent Privacy):** **Obsolete and insecure.** Easily cracked. Do not use
- **WPA (Wi-Fi Protected Access):** Improvement over WEP, used TKIP encryption. Also considered **insecure** now
- **WPA2 (Wi-Fi Protected Access 2):** Current standard. Uses strong **AES-CCMP** encryption
  - **WPA2-Personal:** Uses a **Pre-Shared Key (PSK)** - a password shared among users
  - **WPA2-Enterprise:** Uses **802.1X authentication** with a RADIUS server. Each user authenticates individually (e.g., with username/password or certificates). More secure for organizations
- **WPA3 (Wi-Fi Protected Access 3):** Latest standard, enhances security over WPA2
  - **WPA3-Personal:** Replaces PSK with **SAE (Simultaneous Authentication of Equals)**, more resistant to offline password guessing attacks
  - **WPA3-Enterprise:** Offers stronger encryption modes

**Wireless Standards Evolution (Common)**

| **Standard** | **Wi-Fi Name** | **Max Speed*** | **Frequency** | **Key Features** |
|--------------|----------------|----------------|---------------|-----------------|
| 802.11b | - | 11 Mbps | 2.4 GHz | Legacy |
| 802.11a | - | 54 Mbps | 5 GHz | Less interference than b |
| 802.11g | - | 54 Mbps | 2.4 GHz | Faster than b, compatible with b |
| **802.11n** | **Wi-Fi 4** | ~600 Mbps | 2.4 / 5 GHz | MIMO, Channel Bonding |
| **802.11ac** | **Wi-Fi 5** | ~6.9 Gbps | 5 GHz only | MU-MIMO, Wider Channels (160MHz) |
| **802.11ax** | **Wi-Fi 6/6E** | ~9.6 Gbps | 2.4/5/6 GHz | **OFDMA**, TWT, BSS Coloring, MU-MIMO (Up/Down) |

*Max speeds are theoretical maximums.



**IEEE 802.11 Key Standards Comparison**

| **Standard** | **Primary Function** | **Key Features** | **Benefits** |
|--------------|----------------------|------------------|--------------|
| **802.11v** | **Network-assisted power savings** | - Directed Multicast Service (DMS)<br>- Sleep state management<br>- Extended idle time before disassociation | - Improved battery life<br>- Client remains in standby/sleep longer<br>- Buffers multicast messages during sleep |
| **802.11r** | **Fast transition roaming** | - Pairwise Master Key (PMK) precalculation<br>- Reduced authentication handshakes<br>- Faster AP transitions | - Minimizes roaming delays<br>- Reduces authentication overhead<br>- Maintains QoS during roaming |
| **802.11w** | **Management frame protection** | - Secures management frames<br>- Prevents management frame spoofing<br>- Protects against DoS attacks | - Enhanced security<br>- Protection against deauthentication attacks<br>- Network stability |
| **802.11k** | **Assisted roaming** | - Neighbor AP reports<br>- Optimized AP transition lists<br>- Same wireless band prioritization | - Faster handoffs<br>- Better roaming decisions<br>- Reduces unnecessary probing |



**Roaming in Wireless Networks**

- **Basic Roaming:** Client-driven process where device searches for better signal when current AP becomes weak
- **Assisted Roaming (802.11k):** AP provides client with list of neighbor APs for more efficient transitions
- **Fast Roaming (802.11r):** Accelerates security handshake when moving between APs in same network
- **Seamless Roaming:** Combination of 802.11k (assisted), 802.11r (fast), and 802.11v (power management)


**Memory Aid: "VRKW"**

To remember what each standard does, use the mnemonic **"Very Rapid Knowledgeable Wandering"**:

- **V (802.11v)** - **V**oltage/Power conservation (battery savings)
- **R (802.11r)** - **R**apid transitions (fast roaming)
- **K (802.11k)** - **K**nowledgeable neighbors (assisted roaming)
- **W (802.11w)** - **W**atchguard protection (security for management frames)

**Alternative Mnemonic: "KRVW"**

For a phrase-based memory aid: **"Keep Roaming Very Wisely"**

- **K (802.11k)** - **K**nows where to go (neighbor reports)
- **R (802.11r)** - **R**oams quickly (fast transition)
- **V (802.11v)** - **V**ery power efficient (battery savings)
- **W (802.11w)** - **W**ards off attacks (security)





> 💡 **Exam Focus:** Know the **non-overlapping 2.4 GHz channels (1, 6, 11)**. Differentiate **2.4 GHz vs. 5 GHz** (range, interference, channels). Understand **SSID vs. BSSID**. Know the service set types (**BSS, ESS, IBSS**). Differentiate **WPA2/WPA3 Personal (PSK/SAE)** vs. **Enterprise (802.1X/RADIUS)**. Recognize the common Wi-Fi standards (**Wi-Fi 4, 5, 6**).

### **1.12 Virtualization Fundamentals**

**Server Virtualization**

- **Concept:** Running multiple operating systems (Virtual Machines or VMs) simultaneously on a single physical server
- **Hypervisor:** The software layer that creates and manages VMs
  - **Type 1 (Bare Metal):** Installs directly onto the server hardware (no underlying host OS). *Examples: VMware ESXi, Microsoft Hyper-V, KVM.* **Higher performance, typical for data centers**
  - **Type 2 (Hosted):** Installs on top of an existing host operating system (like Windows or macOS). *Examples: VMware Workstation, Oracle VirtualBox, Parallels Desktop.* **Easier setup, good for labs/desktops**
- **Benefits:**
  - Hardware Consolidation (better resource utilization - CPU, RAM, storage)
  - Isolation (VMs are separate from each other)
  - Hardware Independence (VMs can be moved between physical servers)
  - Snapshots (easy rollback)
  - Faster Server Provisioning
  - Improved Disaster Recovery
- **Network Impact:** VMs connect to **virtual switches (vSwitches)** running on the hypervisor. Multiple VMs share physical NICs, requiring careful network configuration for VLANs, security, and performance

**Containers**

- **Concept:** Virtualizing the operating system *above* the kernel level. Multiple containers run isolated processes but **share the host OS kernel**
- **Contrast with VMs:** VMs virtualize hardware and run a full guest OS. Containers virtualize the OS and share the host kernel
- **Components:**
  - **Container Image:** A template containing the application and its dependencies
  - **Container Runtime:** Software that runs containers (e.g., Docker Engine, containerd)
  - **Orchestration:** Tools to manage many containers across multiple hosts (e.g., Kubernetes, Docker Swarm)
- **Benefits:**
  - **Lightweight & Fast:** Start in seconds (vs. minutes for VMs). Less overhead (no guest OS)
  - **Efficient:** Higher density (more containers than VMs on the same hardware)
  - **Portable:** Consistent environment across development, testing, production
  - **Microservices:** Well-suited for breaking applications into smaller, independent services
- **Network Impact:** Containers need networking too. Models include bridge networking (like VMs), overlay networks spanning multiple hosts, and direct host networking. Service discovery and network security are key considerations


**Virtualization Terminology**

- **VMM (Virtual Machine Monitor):**
  - Another name for a hypervisor
  - Software capable of virtualizing physical computer hardware components
  - Enables creation of multiple virtual machines that can run independently on the same hardware
  - Allows VMs to communicate over a physical network
  - Key to reducing hardware costs through consolidation

- **Hypervisor Types:**
  - **Type 1 (Bare Metal):**
    - Installed directly on bare metal server hardware
    - Acts as its own operating system
    - Direct access to physical hardware
    - Better performance due to proximity to hardware
    - Examples: VMware ESXi, Microsoft Hyper-V Server, Citrix XenServer, KVM
    
  - **Type 2 (Hosted):**
    - Application installed on a host operating system
    - Also called "hosted hypervisors"
    - Uses calls to host OS to translate between guest OS and server hardware
    - Easier to deploy and maintain than Type 1
    - Examples: VMware Workstation, Oracle VirtualBox, Microsoft Hyper-V role on Windows

- **VM (Virtual Machine):**
  - Not a hypervisor but rather an instance running on a hypervisor
  - A virtualized computing environment
  - Relies on a hypervisor to communicate with physical hardware
  - Contains virtual hardware, OS, and applications

- **Cloud Service Models:**
  - **IaaS (Infrastructure as a Service):**
    - Provides virtualized computing resources over the network
    - Enables organizations to use hardware resources of a third party
    - Offers processing, networking, and storage resources
    - Examples: AWS EC2, Microsoft Azure VMs, Google Compute Engine

  - **PaaS (Platform as a Service):**
    - Provides development tools and hosting environments
    - Focuses on application development rather than infrastructure
    - Built on IaaS but abstracts infrastructure complexity
    - Examples: AWS Elastic Beanstalk, Google App Engine, Heroku

  - **SaaS (Software as a Service):**
    - Delivers software applications over the internet
    - Uses internet-enabled licensing
    - Eliminates need for local installation and management
    - Examples: Microsoft 365, Google Workspace, Salesforce

**Security Considerations:**
- Access to the hypervisor itself is a critical security risk
- Compromise of a hypervisor potentially affects all VMs running on it
- Hypervisor security should be a top priority in virtualized environments



**Virtual Routing and Forwarding (VRF)**

- **Concept:** Allows a **single physical router** to host multiple independent **virtual routing tables** simultaneously
- **Analogy:** Like VLANs for Layer 2, VRFs are for Layer 3
- **Purpose:**
  - Network segmentation at Layer 3
  - Keep routing information for different customers or departments completely separate
  - Allows overlapping IP address spaces between different VRFs
- **Key Features:** Each VRF has its own:
  - Routing Table
  - Forwarding Table (FIB)
  - Set of interfaces assigned to it
  - Instances of routing protocols (if configured)
- **Use Cases:** Service Providers (MPLS VPNs), multi-tenant data centers, separating corporate vs. guest traffic on the same router

**Virtualization in Network Devices**

- **Virtual Switching:** Technologies that make multiple physical switches appear as one logical switch (e.g., Cisco StackWise, VSS, vPC). Simplifies management and enables multi-chassis EtherChannel
- **Virtual Firewalls:** Running multiple logical firewall instances (contexts/domains) on a single physical firewall appliance
- **Virtual WAN Optimization:** Running virtual instances of WAN optimization controllers

> 💡 **Exam Focus:** Understand the difference between **Type 1 and Type 2 hypervisors**. Contrast **VMs vs. Containers** (resource usage, kernel sharing, startup time). Understand the concept and purpose of **VRFs** (multiple routing tables on one router for segmentation).

### **1.13 Switching Concepts**

**MAC Learning Process (Recap)**

1. Frame arrives on a port
2. Switch learns the **Source MAC** and associates it with the **ingress port** in the **MAC Address Table**
3. Switch looks up the **Destination MAC** in the table
4. **Forwarding Decision:**
   - **Match Found:** Forward frame *only* out the specified port
   - **No Match (Unknown Unicast):** **Flood** frame out all other ports in the same VLAN
   - **Broadcast/Multicast:** **Flood** frame out all other ports in the same VLAN

**MAC Address Table**

- **Purpose:** Maps MAC addresses to switch ports and VLANs
- **Content:** MAC Address | Port | VLAN | Type (Dynamic/Static) | Age/Timestamp
- **Storage:** Typically stored in fast **CAM (Content Addressable Memory)** or TCAM
- **Aging:** Dynamic entries removed after inactivity (default: **300 seconds**). Configurable via mac address-table aging-time <seconds>
- **Static Entries:** Manually configured, never age out. mac address-table static <mac> vlan <vlan_id> interface <intf>

**Frame Switching Methods**

- **Store-and-Forward:**
  - Switch receives the **entire frame** before making a forwarding decision
  - Calculates the **FCS (checksum)** and **discards** the frame if it's corrupted
  - **Pros:** Highest accuracy (no bad frames forwarded)
  - **Cons:** Highest latency
  - *Required for QoS analysis and different speed ports*

- **Cut-Through:**
  - Switch starts forwarding the frame **as soon as the Destination MAC address is read**
  - Does **not** wait for the entire frame. Does **not** check the FCS
  - **Pros:** Lowest latency
  - **Cons:** Can forward corrupted frames (runts, giants, bad FCS)
  - *Sub-types:*
    - *Fast-Forward:* Forwards immediately after reading the destination MAC. Lowest latency
    - *Fragment-Free:* Reads the first 64 bytes (where most collision fragments occur) before forwarding. Slightly higher latency than fast-forward but avoids forwarding obvious collision fragments

**Frame Flooding**

- **When does it happen?**
  - **Unknown Unicast:** Destination MAC is not in the MAC address table
  - **Broadcast:** Destination MAC is FF:FF:FF:FF:FF:FF
  - **Multicast:** Destination MAC is a multicast address (unless limited by IGMP Snooping)
- **Scope:** Flooding is **limited to the boundaries of the VLAN** the frame originated in. Switches do not flood frames between different VLANs
- **Potential Issues:** Excessive flooding (especially broadcast storms) can consume significant bandwidth and CPU resources

**Switching Loop Prevention**

- **Problem:** Redundant physical paths between switches create loops. Ethernet frames have no TTL (Time-To-Live) like IP packets, so they would loop forever
- **Consequences of Loops:**
  - **Broadcast Storms:** Broadcasts are endlessly duplicated and flooded, consuming all bandwidth/CPU
  - **MAC Table Instability:** Switches constantly relearn the same MAC addresses on different ports due to looping frames
  - **Multiple Frame Delivery:** End devices receive multiple copies of the same unicast frames
- **Solution:** **Spanning Tree Protocol (STP)** logically blocks redundant paths to prevent loops while allowing physical redundancy. (See Section 2.4)

> 💡 **Exam Focus:** Thoroughly understand the **MAC learning and forwarding process**. Know the difference between **Store-and-Forward** and **Cut-Through** switching (latency vs. error checking). Understand **when and why flooding occurs**. Recognize the problems caused by switching loops and that **STP** is the solution.

## **2. Network Access**

### **2.1 Discovery Protocols (CDP & LLDP)**

**CDP (Cisco Discovery Protocol)**

- **Type:** **Cisco Proprietary**
- **Default State:** **Enabled** globally and on interfaces (on Cisco devices)
- **Operation:** Sends periodic multicast messages (every **60 seconds**) to 01:00:0C:CC:CC:CC
- **Holdtime:** How long to keep neighbor info before discarding (default: **180 seconds**)
- **Information Shared:** Device ID (hostname), Platform (model), Capabilities (Router, Switch), Interface names (local/remote), IP Addresses, IOS Version, **VLAN Info (Native, Voice VLAN)**, Duplex, PoE, etc.
- **Layer:** Operates at Layer 2

**LLDP (Link Layer Discovery Protocol)**

- **Type:** **Industry Standard (IEEE 802.1AB)**. Multi-vendor compatible
- **Default State:** **Disabled** globally (on Cisco devices)
- **Operation:** Sends periodic multicast messages (every **30 seconds**) to 01:80:C2:00:00:0E
- **Holdtime:** How long to keep neighbor info (default: **120 seconds**)
- **Information Shared:** Uses **TLVs (Type-Length-Value)** fields. Mandatory TLVs: Chassis ID, Port ID, TTL. Optional TLVs: System Name, System Description, Capabilities, Management Address, Port Description, etc. **Does NOT typically advertise detailed VLAN info like CDP**
- **Interface Modes:** Can be configured to transmit & receive (default when enabled), transmit only (lldp transmit), or receive only (lldp receive)
- **Layer:** Operates at Layer 2

**Comparison**

| **Feature** | **CDP** | **LLDP** |
|-------------|---------|----------|
| **Vendor** | Cisco Proprietary | IEEE Standard (802.1AB) |
| **Default State** | Enabled | Disabled |
| **Interval** | 60 sec | 30 sec |
| **Holdtime** | 180 sec | 120 sec |
| **VLAN Info** | Yes (Native, Voice) | Generally No |
| **Compatibility** | Cisco only | Multi-vendor |
| **Interface Config** | Enabled by default | Tx/Rx enabled when lldp run |
| **Extensibility** | Limited | More extensible (TLVs) |
| **Multicast MAC** | 01:00:0C:CC:CC:CC | 01:80:C2:00:00:0E |

**LLDP-MED (Media Endpoint Discovery):** An extension of LLDP specifically for voice/video devices (like IP phones). Shares additional info like Voice VLAN, QoS policies, location info, PoE requirements.

**Uses:**
- Network mapping and documentation
- Troubleshooting physical connectivity
- Verifying neighbor device identity and capabilities
- Power negotiation for PoE (using extensions)

**Security:** Discovery protocols advertise potentially sensitive information. **Best practice:** Disable CDP/LLDP on ports facing untrusted networks or end-users.

> 💡 **Exam Focus:** Know the **differences** between CDP and LLDP (vendor, default state, timers, VLAN info). Understand the security implications and best practices for disabling them on untrusted ports.

### **2.2 Link Aggregation (EtherChannel)**

**Overview**

- **Concept:** Group multiple physical Ethernet ports (up to 8 on most Cisco switches) into a single logical **Port-channel** interface
- **Benefits:**
  - **Increased Bandwidth:** Aggregates the bandwidth of member links (e.g., 2 x 1Gbps links = 2Gbps logical link)
  - **Redundancy:** If one physical link fails, traffic automatically uses the remaining links
  - **Load Balancing:** Distributes traffic across the active physical links based on a configurable hashing algorithm
  - **STP Simplification:** Spanning Tree sees the Port-channel as a *single* link, preventing loops among the bundled ports
- **Requirements:** All physical ports in an EtherChannel bundle **must** have identical configurations:
  - Speed
  - Duplex
  - Operational Mode (Access or Trunk)
  - Allowed VLANs (if Trunk)
  - Native VLAN (if Trunk)
  - STP settings (cost, priority)

**Negotiation Protocols**

Used to dynamically form and maintain the EtherChannel between switches.

- **PAgP (Port Aggregation Protocol):**
  - **Cisco Proprietary**
  - **Modes:**
    - on: Forces channel formation without negotiation (Static). **Requires on on both sides**
    - auto: Passive mode. Forms channel only if the other side initiates (desirable)
    - desirable: Active mode. Actively tries to form a channel with the other side (desirable or auto)

- **LACP (Link Aggregation Control Protocol):**
  - **IEEE Standard (802.3ad)**. Multi-vendor compatible
  - **Modes:**
    - on: Forces channel formation without negotiation (Static). **Requires on on both sides**
    - passive: Passive mode. Forms channel only if the other side initiates (active)
    - active: Active mode. Actively tries to form a channel with the other side (active or passive)

**Mode Compatibility**

| **Switch A Mode** | **Switch B Mode** | **Result** | **Protocol** |
|-------------------|-------------------|------------|--------------|
| on | on | EtherChannel Forms | Static |
| on | active/passive/auto/desirable | **No Channel** | - |
| auto | auto | **No Channel** (Both Passive) | PAgP |
| auto | desirable | EtherChannel Forms | PAgP |
| desirable | desirable | EtherChannel Forms | PAgP |
| passive | passive | **No Channel** (Both Passive) | LACP |
| passive | active | EtherChannel Forms | LACP |
| active | active | EtherChannel Forms | LACP |

*Best Practice:* Use **LACP active** on both sides for standard-based negotiation. Avoid on mode unless necessary, as it lacks misconfiguration checks.

**Load Balancing**

- Determines how traffic is distributed across the physical links in the bundle
- Based on a **hash** calculated from frame/packet headers. Traffic for the same "flow" (based on the hash inputs) will always use the same physical link
- **Common Methods (Configured globally):**
  - src-mac
  - dst-mac
  - src-dst-mac
  - src-ip
  - dst-ip
  - src-dst-ip (Often default, good general distribution)
  - src-port, dst-port, src-dst-port (Provides better distribution for multiple flows between the same two IPs)

**Troubleshooting**

- **Check for Inconsistent Configs:** Verify speed, duplex, trunk mode, allowed VLANs, native VLAN match on *all* member ports *on both sides*
- **Mode Mismatch:** Ensure LACP/PAgP modes are compatible (e.g., not auto/auto or passive/passive)
- **Cabling:** Ensure ports are connected correctly
- **Suspended Ports:** Ports might be suspended due to incompatibility

> 💡 **Exam Focus:** Understand the **benefits** of EtherChannel (bandwidth, redundancy). Know the **configuration requirements** for member ports. Differentiate **PAgP vs. LACP** and their **modes** (auto/desirable vs. passive/active). Understand the concept of **load balancing**.

### **2.3 VLANs and Trunking**

**VLAN (Virtual Local Area Network) Basics**

- **Concept:** Logically dividing a single physical switch into multiple, independent **broadcast domains**
- **Benefits:**
  - **Broadcast Containment:** Broadcasts are confined within a VLAN, reducing unnecessary traffic
  - **Security:** Isolates groups of users/devices even if connected to the same switch
  - **Flexibility/Scalability:** Users can be grouped logically regardless of physical location
  - **Efficiency:** Better bandwidth utilization by limiting broadcast scope
- **VLAN Ranges:**
  - **Normal Range:** **1 - 1005**
    - VLANs 1002-1005 are reserved for legacy Token Ring/FDDI
    - Configurations stored in vlan.dat file in flash memory (separate from running-config)
    - Compatible with VTP (VLAN Trunking Protocol) versions 1 and 2
  - **Extended Range:** **1006 - 4094**
    - Configurations stored in the running-config
    - Requires VTP version 3 or VTP Transparent mode
    - Used for large environments or service providers
- **Special VLANs:**
  - **VLAN 1:** Default VLAN. All ports are in VLAN 1 initially. Often avoided for user traffic due to security implications. Default Native VLAN. Default Management VLAN
  - **Native VLAN:** The *one* VLAN whose traffic crosses an 802.1Q trunk link **untagged**. Must match on both ends of the trunk. Default is VLAN 1
  - **Management VLAN:** VLAN used to access the switch for management (SSH, Telnet, SNMP). Should be separate from user data VLANs
  - **Voice VLAN:** A secondary VLAN assigned to an access port to carry VoIP phone traffic (tagged). Allows phone and PC to share one port
  - **Black Hole VLAN:** An unused, isolated VLAN. Unused ports are often assigned here for security

**Trunking**

- **Purpose:** To carry traffic for **multiple VLANs** over a single physical link, typically between switches or between a switch and a router/firewall
- **Protocol:** **IEEE 802.1Q** (Dot1q) is the industry standard
  - **Tagging:** Adds a 4-byte tag into the Ethernet frame header
  - **Tag Fields:** Includes VLAN ID (12 bits, identifies the VLAN), Priority Code Point (PCP, 3 bits for QoS), Drop Eligible Indicator (DEI, 1 bit)
  - **Native VLAN:** Traffic belonging to the Native VLAN is sent **untagged** across the trunk by default. **Must match** on both ends

**DTP (Dynamic Trunking Protocol)**

- **Cisco Proprietary** protocol used to automatically negotiate trunking between switch ports
- **Modes:**
  - switchport mode access: Forces the port into permanent access mode. Sends DTP frames to indicate it's an access port
  - switchport mode dynamic auto: Passive. Becomes a trunk *only if* the neighbor is trunk or dynamic desirable. **Default on many older switches**
  - switchport mode dynamic desirable: Active. Actively attempts to form a trunk. Becomes a trunk if the neighbor is trunk, dynamic desirable, or dynamic auto
  - switchport mode trunk: Forces the port into permanent trunk mode. Sends DTP frames to negotiate
  - switchport nonegotiate: Forces the port to trunk but **disables sending DTP frames**. Requires the other side to be manually configured as trunk or nonegotiate. **Recommended for static trunks**

**DTP Mode Combinations**

| **Switch A Mode** | **Switch B Mode** | **Result** |
|-------------------|-------------------|------------|
| Access | Any | Access |
| Dynamic Auto | Dynamic Auto | Access |
| Dynamic Auto | Dynamic Desirable | **Trunk** |
| Dynamic Auto | Trunk | **Trunk** |
| Dynamic Desirable | Dynamic Desirable | **Trunk** |
| Dynamic Desirable | Trunk | **Trunk** |
| Trunk | Trunk | **Trunk** |
| Nonegotiate | Nonegotiate | **Trunk** |

*Security Risk:* Leaving ports in dynamic modes (auto or desirable) can allow unauthorized devices to form trunks. **Best Practice:** Manually configure ports as access or trunk and use switchport nonegotiate on trunks.

**Inter-VLAN Routing**

Since VLANs are separate broadcast domains, a Layer 3 device (router or Layer 3 switch) is needed for communication *between* VLANs.

- **Router-on-a-Stick (ROAS):**
  - A router connected to a switch via a single **trunk link**
  - The router uses **sub-interfaces**, one per VLAN, configured with encapsulation dot1q <vlan_id> and an IP address in that VLAN's subnet
  - The router acts as the default gateway for hosts in each VLAN

- **Layer 3 Switch (Multilayer Switch) with SVIs:**
  - A switch capable of performing Layer 3 routing
  - **Switched Virtual Interfaces (SVIs)** are created (interface Vlan<vlan_id>)
  - Assign an IP address to each SVI to act as the default gateway for that VLAN
  - Requires ip routing to be enabled globally on the switch
  - Generally higher performance than ROAS

**VTP (VLAN Trunking Protocol)**

- Cisco proprietary protocol to synchronize VLAN databases across switches in a VTP domain. Simplifies VLAN management in large networks but can be dangerous if misconfigured
- Modes: Server (can create/modify/delete VLANs), Client (learns VLANs, cannot change), Transparent (manages only local VLANs, forwards VTP ads), Off
- *Not strictly required for CCNA; often Transparent mode is recommended*

> 💡 **Exam Focus:** Understand the **purpose and benefits of VLANs**. Know the **difference between access and trunk ports**. Understand **802.1Q tagging** and the concept of the **Native VLAN**. Know the **DTP modes** and their security implications. Understand the two main methods of **Inter-VLAN routing (ROAS and SVI)**.

### **2.4 Spanning Tree Protocol (STP)**

**Basic STP Concepts**

- **Purpose:** Prevents Layer 2 loops in networks with redundant switch paths
- **Standard:** IEEE 802.1D (Original), 802.1w (RSTP - Rapid), 802.1s (MST - Multiple)
- **Operation:** Elects a Root Bridge, determines best paths, and **blocks** redundant paths to create a single, loop-free logical topology
- **Convergence:** Time to stabilize after a change
  - 802.1D: ~30-50 seconds
  - 802.1w (RSTP): ~1-5 seconds

**Root Bridge Selection**

- **Criteria:** Switch with the **lowest Bridge ID (BID)** wins
- **BID = Bridge Priority + MAC Address**
  - **Priority:** Default 32768. Lower is better. Configurable in steps of 4096. (PVST+ adds VLAN ID: 32768 + VLAN ID)
  - **MAC Address:** Tie-breaker if priorities are equal (lowest MAC wins)
- **Best Practice:** Manually set a low priority on desired root switch(es)

**STP Port Roles (802.1D & RSTP)**

- **Root Port (RP):**
  - On non-root switches only (one per switch)
  - Port with the lowest cost path *to* the Root Bridge
  - *Tie-breakers:* Lowest Sender BID -> Lowest Sender Port Priority -> Lowest Sender Port ID
- **Designated Port (DP):**
  - One per network segment/link
  - Port responsible for forwarding traffic *onto* that segment (away from the root)
  - All ports on the Root Bridge are DPs
  - In Forwarding state
- **Non-Designated / Blocked / Alternate Port (AP - RSTP):**
  - Port that is blocked to prevent loops
  - Receives BPDUs but doesn't forward data
  - Alternate Port (RSTP) is a backup path towards the Root Bridge (alternative to the RP)
- **Backup Port (BP - RSTP):**
  - Backup path onto a segment where the *same switch* already has the DP
  - Rare (requires hubs/shared media)
- **Disabled Port:** Administratively shutdown

**STP Port States (802.1D)**

1. **Blocking (~20s):** Loop prevention. Listens to BPDUs. No data forwarding, no MAC learning
2. **Listening (15s):** Role decision. Sends/Receives BPDUs. No data forwarding, no MAC learning
3. **Learning (15s):** Prepare to forward. Learns MAC addresses. No data forwarding
4. **Forwarding:** Normal operation. Forwards data, learns MACs. (RPs and DPs end here)
5. **Disabled:** Admin down

**RSTP (802.1w) Improvements**

- **Faster Convergence:** Uses handshakes on point-to-point links, alternate/backup ports
- **RSTP States:**
  - **Discarding:** Combines Blocking & Listening. No data forwarding, no MAC learning
  - **Learning:** Same as 802.1D
  - **Forwarding:** Same as 802.1D
- **RSTP Link Types:**
  - **Edge:** Connects to end devices (like PortFast). Goes immediately to Forwarding
  - **Point-to-Point:** Connects to another switch. Enables rapid transitions
  - **Shared:** Connects to a hub (rare). Uses slower 802.1D timers

**STP Protection Features**

- **PortFast:** Skips Listening/Learning on **access ports** for immediate forwarding. **NEVER** on switch-to-switch links
- **BPDU Guard:** Disables (err-disabled) a PortFast port if it receives *any* BPDU. Protects against connecting switches to access ports
- **Root Guard:** Prevents a port from becoming a Root Port. Enforces Root Bridge location. Puts port in root-inconsistent state if superior BPDUs arrive
- **Loop Guard:** Prevents Alternate/Root ports from wrongly becoming Designated if BPDUs stop arriving (e.g., unidirectional link failure). Puts port in loop-inconsistent state
- **BPDU Filter:** Stops sending/receiving BPDUs. **Use with extreme caution!** Effectively disables STP on the port

**STP Protection Features Detailed Comparison**

| **Feature** | **Purpose** | **When to Use** | **Reaction When Triggered** | **Configuration Command** | **Recovery Method** |
|-------------|-------------|----------------|----------------------------|--------------------------|---------------------|
| **PortFast** | Bypasses STP waiting states | Access ports connecting to end devices only | N/A (not a protection mechanism) | `spanning-tree portfast` | N/A |
| **BPDU Guard** | Prevents rogue switch connections | PortFast-enabled access ports | **Err-disables** the port | `spanning-tree bpduguard enable` | Manual or auto recovery |
| **Root Guard** | Maintains root bridge placement | Ports that should not become root ports | Puts port in **root-inconsistent** state | `spanning-tree guard root` | Automatic when BPDU stops |
| **Loop Guard** | Prevents loops from unidirectional links | Non-designated ports (potential alternate/backup ports) | Puts port in **loop-inconsistent** state | `spanning-tree guard loop` | Automatic when BPDU received |
| **BPDU Filter** | Stops BPDU transmission/reception | Rarely used - extreme caution required | Effectively disables STP on the port | `spanning-tree bpdufilter enable` | N/A |

**PortFast Feature**

- **Purpose:** Immediately transitions port to forwarding state (skips listening/learning)
- **Normal STP Behavior:** Port takes 30+ seconds to start forwarding
- **PortFast Benefit:** Immediate network access for end devices
- **Critical Warning:** **ONLY** use on ports connected to single end devices (never switch-to-switch)
- **Risk:** Can cause temporary loops if connected to another switch
- **Global Configuration:** `spanning-tree portfast default` (applies to all access ports)
- **Interface Configuration:** `spanning-tree portfast` (specific port)

**BPDU Guard**

- **Purpose:** Enforces edge of STP domain, prevents unauthorized switch connections
- **Operation:** Immediately err-disables port if any BPDU is received
- **Best Practice:** Enable on **all PortFast-enabled ports**
- **Why It's Needed:** PortFast alone transitions to forwarding but still accepts BPDUs; BPDU Guard provides security
- **Global Configuration:** `spanning-tree portfast bpduguard default`
- **Interface Configuration:** `spanning-tree bpduguard enable`
- **Recovery:** 
  - Manual: `shutdown` followed by `no shutdown`
  - Automatic: Configure `errdisable recovery cause bpduguard` and `errdisable recovery interval <seconds>`

**Root Guard**

- **Purpose:** Prevents external switches from becoming root bridge
- **Operation:** Blocks BPDUs that would make the port a root port
- **Use Case:** Ports connecting to customer or other administrative domains
- **State When Triggered:** Root-inconsistent (blocks BPDUs but allows data traffic)
- **Recovery:** Automatic when superior BPDUs stop arriving
- **Configuration:** `spanning-tree guard root`

**Loop Guard**

- **Purpose:** Prevents loops caused by unidirectional link failures
- **Operation:** If BPDUs stop arriving on a non-designated port, prevents transition to designated/forwarding
- **Best Placement:** Non-designated ports (alternate/backup/root)
- **State When Triggered:** Loop-inconsistent
- **Recovery:** Automatic when BPDUs resume
- **Global Configuration:** `spanning-tree loopguard default`
- **Interface Configuration:** `spanning-tree guard loop`

**Common Issues and Troubleshooting**

- **Err-disabled Port Due to BPDU Guard:**
  - **Symptom:** Port in err-disabled state
  - **Verify:** `show spanning-tree summary` and `show interfaces status err-disabled`
  - **Cause:** PortFast + BPDU Guard enabled, and another switch connected
  - **Fix:** Remove the unauthorized switch, then recover the port

- **PortFast and BPDU Guard Interaction:**
  - PortFast transitions port to forwarding immediately
  - If another switch is connected to PortFast port with BPDU Guard:
    1. Port enters forwarding state (PortFast)
    2. Switch receives BPDU from connected switch
    3. BPDU Guard triggers, port goes err-disabled
    4. Connection is effectively shut down, preventing loops

**Best Practices**

- **PortFast:** Enable on all access ports connecting to end devices
- **BPDU Guard:** Enable on all PortFast-enabled ports
- **Root Guard:** Enable on ports where root bridge role should not change
- **Loop Guard:** Enable on non-designated ports
- **Comprehensive Protection:** Use `spanning-tree portfast bpduguard default` globally

> 💡 **Exam Focus:** Understand that **PortFast alone doesn't prevent loops** - it simply accelerates transition to forwarding. **BPDU Guard** is what actually protects by err-disabling the port. Know which feature to use for specific scenarios and what happens when triggered. Remember that PortFast should **NEVER** be enabled on switch-to-switch links.





**STP Variants**

| **Acronym** | **Standard** | **Key Features** | **Convergence** | **Notes** |
|-------------|--------------|------------------|-----------------|-----------|
| STP | 802.1D | Original, single tree | Slow (~50s) | Foundation |
| PVST+ | Cisco/802.1D | Per-VLAN tree | Slow (~50s) | Cisco legacy |
| **RSTP** | **802.1w** | **Rapid** convergence | **Fast (~1-5s)** | Standard improvement |
| **Rapid PVST+** | **Cisco/802.1w** | **Rapid + Per-VLAN** | **Fast (~1-5s)** | **Common Cisco Default** |
| MST(P) | 802.1w | Multiple instances (groups VLANs) | Fast (~1-5s) | Scalable for many VLANs |


**Spanning Tree Protocol (STP) Port Roles**

| **Port Role** | **Quantity Per Switch** | **State** | **Function** | **Selection Criteria** |
|---------------|-------------------------|-----------|--------------|------------------------|
| **Root Port** | **One per nonroot switch** | **Forwarding** | Provides best path to root bridge | Port receiving best BPDU (lowest root path cost) |
| **Designated Port** | One per segment | Forwarding | Forwards traffic toward root bridge | Port with best path to root on a given segment |
| **Alternate Port** | Zero or more | Blocking | Provides alternate path to root | Receives less favorable BPDUs to root bridge |
| **Backup Port** | Zero or more | Blocking | Redundant connection to same segment | Additional ports on same switch to same segment |
| **Disabled Port** | Zero or more | Disabled | Not participating in STP | Administratively shut down |

**Root Bridge Ports:**
- All ports on the root bridge are designated ports
- The root bridge does not have a root port

**Port Selection Process:**
1. Lowest root bridge ID (Priority + MAC address)
2. Lowest root path cost to root bridge
3. Lowest sender bridge ID
4. Lowest sender port ID

**Bridge ID Components:**
- 2-byte bridge priority (default: 32768, configurable in multiples of 4096)
- 6-byte MAC address
- When comparing, priority is checked first, then MAC address if tied
- With MAC addresses, numerically lower values win (0-9 < A-F)

**STP Port States Memory Aid: "LBLFD"**

- **L**isten: Collecting information, no data forwarding
- **B**locking: Prevents loops, only processes BPDUs
- **L**earning: Building MAC table, no data forwarding
- **F**orwarding: Normal operation, forwards traffic
- **D**isabled: Admin down, not participating

**Port Roles Memory Aid: "RADAR"**

- **R**oot Port: **R**oute to root bridge (one per nonroot switch)
- **A**lternate Port: **A**lternative path to root (blocking)
- **D**esignated Port: **D**irects traffic to root on each segment
- **A**ll ports on root: **A**ll are designated ports
- **R**edundant backup: **R**eserve connection to same segment




> 💡 **Exam Focus:** Know **Port Roles** (RP, DP, Blocked/Alt), **802.1D States** (Block, Listen, Learn, Forward) & timers, **RSTP** differences (Discarding, Edge/P2P, Speed), **Protection Features** (PortFast, BPDU Guard, Root Guard, Loop Guard) purpose & use cases. Understand **Root Election** (Priority+MAC). Know **Rapid PVST+** is the common Cisco implementation.

### **2.5 Wireless Principles**

**Wireless Standards for Roaming & Management**

These standards help improve client roaming experience and network management:

- **802.11w (Protected Management Frames - PMF):**
  - *Mnemonic: "W for Watchguard/Wall"* - Protects management frames
  - Encrypts critical management frames (like deauthentication/disassociation) to prevent spoofing attacks
  - Increases overall WLAN security

- **802.11r (Fast BSS Transition - FT):**
  - *Mnemonic: "R for Rapid Roaming"* - Speeds up handoffs
  - Allows clients to pre-authenticate with nearby APs *before* actually roaming
  - Significantly reduces roaming delay, crucial for voice/video calls

- **802.11k (Radio Resource Management - RRM):**
  - *Mnemonic: "K for Knowledge"* - Provides neighbor info
  - Allows APs to provide clients with lists of neighboring APs and their channel information
  - Helps clients make smarter roaming decisions (find the best AP faster)

- **802.11v (Wireless Network Management - WNM):**
  - *Mnemonic: "V for Versatile Management"* - Various management tools
  - Provides mechanisms for network-assisted power saving, BSS transition management (guiding clients to roam), and client steering

**OFDMA (Orthogonal Frequency Division Multiple Access):** Key Wi-Fi 6 feature. Allows an AP to talk to multiple clients *simultaneously* within the same channel transmission by dividing the channel into smaller sub-carriers (Resource Units). Improves efficiency, especially in dense environments with small packet traffic.

> 💡 **Exam Focus:** Understand the purpose of **802.11w, r, k, v** standards in improving security and roaming. Recognize **OFDMA** as a key efficiency feature of **Wi-Fi 6 (802.11ax)**.

### **2.6 Wireless LAN Controllers (WLC) & APs**

**WLC Architecture (Split-MAC)**

- **Concept:** WLAN functions are split between the lightweight Access Point (AP) and the Wireless LAN Controller (WLC)
- **AP Responsibilities (Real-time):** Beacons, Probe responses, Packet acknowledgments, Frame buffering, Transmissions
- **WLC Responsibilities (Management):** Authentication, Association/Roaming management, QoS enforcement, Security policies, Radio Resource Management (RRM)
- **CAPWAP Tunnel:** Control and Data traffic between AP and WLC is encapsulated within a **CAPWAP (Control and Provisioning of Wireless Access Points)** tunnel. Control traffic is DTLS encrypted; data traffic can be optionally encrypted. (UDP Ports 5246 & 5247). *Replaced older LWAPP protocol*



| **Interface Type** | **Primary Functions** | **Protocol Support** | **Special Characteristics** | **Common Use Cases** |
|-------------------|------------------------|---------------------|----------------------------|---------------------|
| **Management Interface** | • Network management<br>• SNMP polling<br>• Layer 2 LWAPP communications | • SNMP<br>• HTTP/HTTPS<br>• Telnet/SSH | • Must be assigned to an active port<br>• Required for operation | • Continuous monitoring<br>• Controller administration<br>• Network management system integration |
| **AP-Manager Interface** | • CAPWAP control channel<br>• Layer 3 communications | • LWAPP/CAPWAP<br>• Layer 3 control | • Contains source IP for AP communication<br>• Must be unique on network | • AP discovery and join process<br>• AP control and configuration |
| **Service Port Interface** | • Out-of-band management<br>• Controller recovery | • Telnet/SSH<br>• TFTP | • Physical interface<br>• Only available during boot | • Maintenance operations<br>• WLC recovery<br>• Initial setup |
| **Virtual Interface** | • Mobility management<br>• Web authentication<br>• DHCP relay | • HTTP/HTTPS<br>• Layer 3 security protocols | • Not mapped to physical port<br>• Used across controller cluster | • Client roaming<br>• Guest access<br>• Authentication redirection |
| **Dynamic Interface** | • Client data traffic<br>• VLAN segmentation | • User data protocols | • Up to 512 interfaces<br>• User-defined | • Traffic segmentation<br>• SSID-to-VLAN mapping<br>• Network isolation |

**Management Interface Detailed Functions**

- Acts as the primary interface for controller administration and monitoring
- **Used for continuous SNMP polling** by network management systems
- Provides in-band management access for configuration and monitoring
- Used for Layer 2 communications between controller and APs
- Serves as communication path between multiple WLCs in a network
- Handles inter-controller roaming and mobility

**AP-Manager Interface Detailed Functions**

- Manages all Layer 3 communications with lightweight APs
- Contains the IP address used as the source for APs to communicate with the WLC
- Must have a unique IP address on the network
- After configuration, listens for LWAPP/CAPWAP traffic from APs
- Controls AP discovery, join, and configuration processes
- Multiple AP-manager interfaces can be used for load balancing

**Service Port Interface Detailed Functions**

- Used specifically for out-of-band maintenance and recovery operations
- Physical interface on the WLC that can be used to recover a failed controller
- Only interface available during WLC boot process
- Can be accessed using Telnet or SSH during maintenance
- Cannot be in the same subnet as the management interface
- Doesn't support routing; no default gateway configuration

**Virtual Interface Detailed Functions**

- Provides mobility management with consistent IP across multiple controllers
- Used for client redirection during web authentication
- Supports embedded Layer 3 security processes
- Serves as DHCP relay address for wireless clients when enabled
- Enables seamless roaming between controllers in a mobility group
- Used for Layer 3 security operations

**Dynamic Interface Detailed Functions**

- User-defined interfaces for wireless client data traffic
- Function similarly to VLANs for traffic segmentation
- Up to 512 dynamic interfaces supported on enterprise WLCs
- Used to map SSIDs to specific VLANs
- Enable network segmentation and isolation
- Can be configured similarly to virtual LANs (VLANs)

> 💡 **Exam Focus:** Understand that the **Management Interface** is typically used for **continuous SNMP polling**. Know the distinct purposes of each interface type, particularly how the **Management Interface** handles in-band management, the **AP-Manager Interface** manages Layer 3 communications with APs, the **Service Port Interface** provides out-of-band maintenance, the **Virtual Interface** enables mobility, and **Dynamic Interfaces** segment client traffic.
**AP Discovery & Join Process**

1. AP boots up, needs an IP address (usually via DHCP)
2. AP needs to discover the WLC's Management IP address. Methods:
   - DHCP Option 43 (vendor-specific)
   - DNS lookup for CISCO-CAPWAP-CONTROLLER.localdomain
   - Local subnet broadcast
   - Statically configured primary/secondary/tertiary WLC IPs
   - Previously known WLC IP
3. AP attempts to build a secure DTLS connection to the WLC's Management IP for CAPWAP control
4. WLC authenticates the AP (certificate check)
5. AP joins the WLC. Downloads firmware and configuration from the WLC if necessary
6. AP becomes operational and starts serving clients according to the WLC's configuration

**AP Modes**

Determines the function of the Access Point.

- **Local:** Default mode. Serves clients on assigned channels. Also performs background scanning (off-channel) for RRM and rogue detection. **Standard production mode**
- **FlexConnect:** For remote/branch offices with potentially unreliable WAN links to the central WLC
  - Can **switch traffic locally** at the branch for specific WLANs (instead of tunneling everything back to the WLC)
  - Can operate **autonomously** (standalone) if the WLC connection is lost (provides basic connectivity, local authentication options)
  - Requires careful design for local VLANs and DHCP
- **Monitor:** Dedicated monitoring mode. **Does not serve clients.** Continuously scans all channels to detect rogue APs, interference, and for Wireless Intrusion Prevention Systems (wIPS)
- **Sniffer:** Captures raw 802.11 frames from a specific channel and forwards them to a packet analysis tool (like Wireshark) via the wired network. Used for deep troubleshooting. **Does not serve clients**
- **Rogue Detector:** Connects only to the wired network (wireless radios disabled). Listens for MAC addresses of potential rogue APs (APs not managed by the WLC) on the wire to help locate unauthorized devices plugged into the network. **Does not serve clients**
- **Bridge / Mesh:** Used to create wireless backhaul links between APs
  - **Root AP (RAP):** Has a wired connection
  - **Mesh AP (MAP):** Connects wirelessly to a RAP or another MAP
  - Used to extend wireless coverage where running Ethernet is difficult. Can also serve clients

**AP Deployment Models**

- **Cloud-based AP Deployment:**
  - Enables Cisco Meraki APs to **automatically configure themselves** when connected to a network
  - APs connect to a centralized management system (Cisco Meraki Cloud)
  - Deployed at the access layer of the three-tier hierarchical network model
  - Configuration and management through a cloud-based dashboard
  - No on-premises controller required

- **Autonomous AP Deployment:**
  - Connects wireless clients to a wired network without requiring a separate wireless controller
  - AP contains network interfaces for both wireless and wired networks
  - Typically deployed as part of an autonomous AP architecture
  - APs are connected directly to the access layer of the network
  - Each AP must be configured and managed individually
  - Sometimes called "standalone" or "fat" APs

- **Lightweight AP Deployment:**
  - Requires a separate wireless controller (WLC)
  - Uses CAPWAP tunneling protocol for communication between AP and WLC
  - Split-MAC architecture: AP handles frames while WLC handles management functions
  - Connection established using two tunnels (Control and Provisioning of Wireless Access Points)
  - Information encapsulated in Internet Protocol (IP) packets
  - Compatible with centralized management and configuration

- **Embedded AP Deployment:**
  - Requires a separate wireless controller
  - WLC is embedded within a stack of switching hardware (not a separate entity)
  - APs connect to the WLC via switches that directly host the WLC
  - Combines switching and wireless control in one hardware solution

**Physical Connections**

- **APs:** Connect to switch access ports. Usually powered by **PoE/PoE+**. Port config often includes Voice VLAN (if management is tagged), QoS trust settings
- **WLC:**
  - **Management/AP-Manager/Dynamic Interfaces:** Typically connect to **trunk ports** on a switch, allowing traffic from multiple VLANs (Management VLAN + Client VLANs mapped via Dynamic Interfaces)
  - **LAG (Link Aggregation):** WLC ports can often be bundled into an EtherChannel (LAG) group on the WLC and connected to an EtherChannel on the switch for redundancy and increased bandwidth

**Centralized vs. FlexConnect**

| **Feature** | **Centralized (Local Mode)** | **FlexConnect** |
|-------------|------------------------------|-----------------|
| **Traffic Flow** | All traffic tunneled to WLC | Can switch traffic locally |
| **WAN Dependency** | High | Lower (can work standalone) |
| **Latency** | Higher (via WLC) | Lower (for local traffic) |
| **WLC Dependency** | High | Lower |
| **Use Case** | Campus / HQ | Branch / Remote Offices |

> 💡 **Exam Focus:** Understand the **Split-MAC architecture** concept. Know the purpose of key **WLC interfaces** (Management, Virtual, Dynamic). Understand the **AP discovery/join process** basics. Recognize the different **AP Modes** and their primary use cases (especially **Local** vs. **FlexConnect**). Know how WLCs typically connect to the wired network (Trunk ports, optional LAG).

### **2.7 Power over Ethernet (PoE)**

**PoE Standards**

| **Standard** | **Name** | **Power at PSE* (Switch)** | **Power at PD* (Device)** | **Notes** |
|--------------|----------|----------------------------|---------------------------|-----------|
| **IEEE 802.3af** | **PoE** | 15.4 W | 12.95 W | Original standard, basic devices |
| **IEEE 802.3at** | **PoE+** | 30 W | 25.5 W | Higher power APs, PTZ cameras |
| **IEEE 802.3bt Type 3** | **PoE++** | 60 W | 51 W | Uses 4 pairs, high-power APs, displays |
| **IEEE 802.3bt Type 4** | **UPoE+** | 100 W | 71 W | Uses 4 pairs, highest power devices |

*PSE = Power Sourcing Equipment (Switch), PD = Powered Device (AP, Phone, Camera)

*Power at PD is lower due to voltage drop over the cable length.

**PoE Operation**

1. **Detection:** The PSE (switch) sends a small voltage to detect if a valid PD is connected (looks for a specific resistance). Prevents damaging non-PoE devices
2. **Classification (Optional):** PSE determines the PD's power requirement (Class 0-8). Allows the switch to budget power more accurately. If skipped, defaults to max power for the standard (e.g., 15.4W for 802.3af)
3. **Power-Up:** If sufficient power is available in the switch's budget, the PSE provides power to the PD
4. **Operation & Monitoring:** PSE continuously provides power and monitors consumption. Can use CDP or LLDP for more granular power negotiation (PD requests specific amount)
5. **Disconnect:** If PD is unplugged, PSE removes power

**PoE Classes (Simplified)**

| **Class** | **Type** | **Max Power at PD** | **Typical Devices** |
|-----------|----------|---------------------|---------------------|
| 0 | Type 1 | 12.95 W | Default / Legacy |
| 1 | Type 1 | 3.84 W | Basic IP Phones |
| 2 | Type 1 | 6.49 W | IP Cameras |
| 3 | Type 1 | 12.95 W | Basic APs |
| **4** | **Type 2 (PoE+)** | **25.5 W** | **High-power APs, Video Phones** |
| 5/6 | Type 3 (PoE++) | 40W / 51W | High-performance APs, Displays |
| 7/8 | Type 4 (UPoE+) | 62W / 71W | Laptops, TVs, Thin Clients |

**PoE Management**

- **Power Budget:** The total amount of power the switch can supply across all ports (depends on power supplies installed)
- **Power Allocation:** How the switch reserves power (often reserves max class power unless negotiated lower)
- **Power Priority:** Configure ports as critical, high, or low priority. If budget is exceeded, low priority ports lose power first

**PoE Troubleshooting**

- **Check Switch Power Budget:** Is enough power available? (Available vs. Used)
- **Check Port Status:** Is power On? What Class? Any Error status?
- **Insufficient Power:** PD requires more power than the port/switch can provide (e.g., PoE+ device on PoE-only port)
- **Cable Issues:** Cable too long (> 100m), poor quality cable (use Cat5e or better), damaged cable
- **PD Fault:** The powered device itself might be faulty
- **Switch Port Fault:** The switch port might be faulty
- **Error States:** Check logs for specific PoE errors (overload, short circuit, etc.)

> 💡 **Exam Focus:** Know the **different PoE standards (af, at, bt)** and their approximate **power levels (15W, 30W, 60W, 100W)**. Understand the basic **detection and classification** steps. Recognize common troubleshooting issues like **insufficient budget** and **cable problems**.

### **2.8 Network Device Management Access**

**Access Methods**

- **Console:**
  - **Connection:** Direct physical connection using a console cable (Rollover cable - RJ-45 or Serial DB-9 to device Console port, often USB adapter needed on modern laptops)
  - **Pros:** Works even if network connectivity is down. Used for initial setup and recovery
  - **Cons:** Requires physical access
  - **Settings:** 9600 baud, 8 data bits, No parity, 1 stop bit, No flow control (9600 8N1)
  - **Configuration:** line console 0

- **Telnet (Port 23):**
  - **Connection:** Remote access over the network (TCP Port 23)
  - **Pros:** Simple remote access
  - **Cons:** **INSECURE!** Sends username, password, and all session data in **plaintext**. Easily sniffed. **Avoid in production**
  - **Configuration:** line vty 0 <N> (Virtual TeletYpe lines), transport input telnet

- **SSH (Secure Shell - Port 22):**
  - **Connection:** Remote access over the network (TCP Port 22)
  - **Pros:** **SECURE!** Encrypts the entire session, including authentication and data. Industry standard for secure CLI access
  - **Cons:** Requires initial setup on the device
  - **Configuration Steps (Cisco IOS):**
    1. Set hostname: hostname <name>
    2. Set domain name: ip domain-name <domain.com>
    3. Generate RSA crypto keys: crypto key generate rsa modulus <1024_or_higher> (e.g., 2048)
    4. Configure local user accounts: username <user> privilege <0-15> secret <strong_password>
    5. Configure VTY lines for SSH:
       line vty 0 15
       transport input ssh ! Allow only SSH (or 'transport input ssh telnet' for both)
       login local ! Use local user database for authentication
    6. (Optional) Force SSH Version 2: ip ssh version 2

- **HTTP (Port 80) / HTTPS (Port 443):**
  - **Connection:** Web-based GUI access
  - **HTTP:** **Insecure** (plaintext). Enable with ip http server
  - **HTTPS:** **Secure** (uses TLS/SSL encryption). Enable with ip http secure-server. Requires crypto keys (often shared with SSH)
  - **Pros:** Graphical interface, sometimes easier for basic tasks
  - **Cons:** Can be resource-intensive on the device. Security depends on using HTTPS. Limited functionality compared to CLI
  - **Authentication:** Often configured with ip http authentication local (use local users)

**Centralized Authentication (AAA)**

Using external servers (RADIUS or TACACS+) for Authentication, Authorization, and Accounting.

- **RADIUS (Remote Authentication Dial-In User Service):**
  - **Standard:** Open standard
  - **Transport:** UDP (Ports 1812 Auth, 1813 Acct). Considered less reliable
  - **Encryption:** Encrypts **only the password** in the Access-Request packet
  - **AAA:** Combines Authentication and Authorization in the Access-Accept message. Accounting is separate
  - **Use Case:** Common for user network access control (802.1X, VPN), less common for device administration due to limited command authorization

- **TACACS+ (Terminal Access Controller Access-Control System Plus):**
  - **Standard:** **Cisco Proprietary**
  - **Transport:** TCP (Port 49). More reliable
  - **Encryption:** Encrypts the **entire packet body**
  - **AAA:** **Separates** Authentication, Authorization, and Accounting functions into distinct message types
  - **Authorization:** Provides **granular command authorization** (can control exactly which commands a user can run)
  - **Use Case:** Preferred method for **network device administration** due to reliability, full encryption, and granular command control

**Management Security Best Practices**

- **Use Secure Protocols:** SSH and HTTPS ONLY. Disable Telnet and HTTP
- **Strong Authentication:** Use AAA (TACACS+ preferred for devices) or strong local passwords
- **Authorization:** Control *who* can do *what* (privilege levels, command authorization via TACACS+)
- **Access Control Lists (ACLs):** Apply ACLs to VTY lines and management interfaces to restrict access to specific trusted IP addresses/subnets
- **Dedicated Management Network:** Use an out-of-band (OOB) management network if possible
- **Timeouts:** Configure session timeouts for console and VTY lines
- **Logging:** Log access attempts (success and failure) to a syslog server
- **Disable Unused Services:** Turn off unnecessary protocols/services

> 💡 **Exam Focus:** Know the **steps to configure SSH** on a Cisco device. Understand the **key differences between Telnet and SSH** (security!). Differentiate **RADIUS vs. TACACS+** (UDP/TCP, encryption scope, AAA separation, command authorization). Recognize **management security best practices**.

### **2.9 Wireless LAN GUI Configuration (WLC)**

Configuring WLANs using the graphical interface of a Cisco Wireless LAN Controller.

*(Note: Specific GUI layouts vary by WLC model and software version, but the concepts are similar)*

**Accessing the GUI:**

- Open a web browser and navigate to the WLC's Management Interface IP address (using HTTPS)
- Log in with administrative credentials

**Typical GUI Sections:**

- **Monitor:** Dashboard view, client status, AP status, network summary, logs
- **WLANs:** Create, configure, and manage Wireless LANs (SSIDs)
- **Controller:** Configure WLC interfaces, system settings, management options
- **Wireless:** Configure global RF settings, APs, Radio Resource Management (RRM), rogue detection
- **Security:** Configure RADIUS servers, Access Control Lists (ACLs), security policies, web authentication
- **Management:** Configure admin users, SNMP, logging, software updates

**Creating a New WLAN (Typical Workflow)**

1. **Navigate:** Go to the WLANs section and choose Create New or similar
2. **Basic Info:**
   - **Profile Name:** Internal name for the WLAN configuration (e.g., "Corporate_WLAN")
   - **SSID:** The network name broadcast to clients (e.g., "CorporateWiFi")
   - **WLAN ID:** A numerical identifier for the WLAN (e.g., 1, 2, 3...)
3. **General Settings:**
   - **Status:** **Enable** the WLAN to make it active
   - **Radio Policy:** Choose which radios broadcast this SSID (e.g., 2.4 GHz only, 5 GHz only, Both)
   - **Interface/Interface Group:** **Crucial step!** Map this WLAN to a **Dynamic Interface** (which is mapped to a VLAN on the wired side). This links the wireless network to the correct wired subnet
   - **Broadcast SSID:** Checkbox to make the SSID visible or hidden
4. **Security Settings:**
   - **Layer 2 Security:** Select the primary security method:
     - None (Open - Insecure)
     - WPA+WPA2 or WPA2 (Common)
     - WPA3 (Newer standard)
   - **Authentication Key Management (AKM):**
     - PSK (for WPA2/WPA3-Personal): Enter the Pre-Shared Key (password)
     - 802.1X (for WPA2/WPA3-Enterprise): Select configured RADIUS server(s)
     - SAE (for WPA3-Personal): Uses password for secure key exchange
   - **Encryption:** Usually tied to the Layer 2 Security choice (e.g., AES/CCMP for WPA2)
5. **QoS (Quality of Service) Settings:**
   - **Profile:** Assign a QoS profile to prioritize traffic for this WLAN:
     - Platinum (Highest - typically Voice)
     - Gold (High - typically Video)
     - Silver (Normal - Best Effort, often default)
     - Bronze (Low - Background)
   - **WMM (Wi-Fi Multimedia):** Usually enabled to allow QoS tagging over wireless
6. **Advanced Settings (Optional):**
   - Client limits, session timeouts, DHCP requirements, P2P blocking, Band Select (encourage clients to use 5GHz), Fast Roaming (802.11r), PMF (802.11w)
7. **Apply/Save:** Save the configuration

**Key Configuration Areas**

- **WLANs > Edit WLAN:** Modify existing SSIDs
- **Controller > Interfaces:** Configure Management, AP-Manager, Virtual, and Dynamic (VLAN) interfaces
- **Security > AAA > RADIUS:** Configure external RADIUS servers for 802.1X authentication
- **Wireless > Access Points > All APs:** View status and configure individual AP settings (if needed, usually managed globally)

**Verification & Monitoring (GUI)**

- **Monitor Tab:** Check client counts, AP status, traffic levels, interference/noise levels
- **Monitor > Clients:** View detailed information about connected clients (MAC, IP, AP connected to, signal strength, data rates, etc.)
- **Monitor > Logs:** View system event logs

> 💡 **Exam Focus:** Understand the **basic workflow for creating a WLAN** via the GUI (Profile/SSID Name, Interface Mapping, Security Method - PSK vs 802.1X, Enabling). Know where to configure **interfaces** and **RADIUS servers**. Understand the purpose of different **QoS profiles**.

## **3. IP Connectivity**

### **3.1 IP Addressing**

**Private IPv4 Ranges (RFC 1918)**

- Class A: 10.0.0.0/8
- Class B: 172.16.0.0/12
- Class C: 192.168.0.0/16
- Not internet routable; require NAT

**IPv6 Address Types**

- **Unique Local (ULA):** FC00::/7 (Similar to private IPv4, internal use)
- **Link-Local:** FE80::/10 (Single link scope, non-routable, auto-config)
- **Global Unicast (GUA):** 2000::/3 (Internet routable, public)
- **Multicast:** FF00::/8 (Group communication)

**IPv6 EUI-64 Format**

Automatically generates 64-bit interface ID from 48-bit MAC address.

**Process:**
1. Split MAC in half
2. Insert FFFE in the middle
3. Flip the 7th bit (U/L bit) of the first byte

**Example:**
- MAC: 00:0C:29:1D:8A:B5
- Interface ID: 020C:29FF:FE1D:8AB5

> 💡 **Exam Focus:** Know private IPv4 ranges, IPv6 address types, and the EUI-64 process.

### **3.2 Route Selection Process**

Routers select the best path based on:

1. **Longest Prefix Match:** Most specific route wins (e.g., /30 > /24)
2. **Administrative Distance (AD):** Lowest AD wins if prefixes match
3. **Metric:** Lowest metric wins if prefix and AD match
4. **Equal-Cost Load Balancing:** If all above are equal, distribute traffic across multiple paths

**Administrative Distance Values**

| **Protocol** | **AD Value** |
|--------------|--------------|
| Directly connected | 0 |
| Static route | 1 |
| EIGRP summary | 5 |
| eBGP | 20 |
| Internal EIGRP | 90 |
| OSPF | 110 |
| IS-IS | 115 |
| RIP | 120 |
| External EIGRP | 170 |
| iBGP | 200 |
| Unknown | 255 |

> 💡 **Exam Focus:** Understand the complete route selection order, memorize key AD values (connected, static, EIGRP, OSPF, RIP).

### **3.3 Static Routes**

There are different types of static routes for different use cases:

- **Fully Specified:** Specifies both exit interface AND next hop IP address
  - Most explicit, avoids recursive lookups
  - Example: ip route 10.0.0.0 255.0.0.0 GigabitEthernet0/1 192.168.1.2

- **Directly Attached:** Specifies only the exit interface
  - Used when the next hop is directly connected
  - Example: ip route 10.0.0.0 255.0.0.0 GigabitEthernet0/1

- **Recursive:** Specifies only the next hop IP address
  - Router must perform a recursive lookup to find the exit interface
  - Example: ip route 10.0.0.0 255.0.0.0 192.168.1.2

- **Floating Static Route:** Standard static route with a higher Administrative Distance
  - Used as a backup route when the primary route fails
  - Example: ip route 10.0.0.0 255.0.0.0 Serial0/0/1 172.16.2.2 120

**IPv6 Static Route Examples**

- **Fully Specified:**
  - ipv6 route 2001:db8:a::/32 fastethernet 0/1 2001:db8:b::1

- **Directly Attached:**
  - ipv6 route 2001:db8::/32 gigabitethernet 0/0

- **Recursive:**
  - ipv6 route 2001:db8::/32 2001:db8:c::1

- **Floating:**
  - ipv6 route 2001:db8::/32 gigabitethernet 0/1 2001:db8:d::1 5

> 💡 **Exam Focus:** Understand the different types of static routes and when to use each.

### **3.4 OSPF (Open Shortest Path First)**

**Key Concepts**

- Link-state protocol
- Uses Dijkstra algorithm
- Forms neighbor adjacencies
- Hierarchical design with areas

**Cost Calculation**

- Cost = Reference Bandwidth / Interface Bandwidth
- Default Ref BW = 100 Mbps
- Common Costs (100M Ref):
  - 10G = 1
  - 1G = 1
  - 100M = 1
  - 10M = 10
  - T1 = 64

**Load Balancing**

- Supports equal-cost paths (default max 4, configurable)

**OSPF States**

1. Down
2. Init
3. 2-Way
4. ExStart
5. Exchange
6. Loading
7. Full

**OSPF Packets**

- Hello
- DBD (Database Description)
- LSR (Link State Request)
- LSU (Link State Update)
- LSAck (Link State Acknowledgment)

**Router Roles**

- **DR (Designated Router):** Elected on multi-access networks
- **BDR (Backup DR):** Backup for DR
- **DRother:** Non-DR/BDR routers
- **ABR (Area Border Router):** Connects areas to Area 0
- **ASBR (Autonomous System Boundary Router):** Connects OSPF to external networks

**Router ID Selection**

1. Manual config
2. Highest Loopback IP
3. Highest Active Physical IP

**Network Types & Behavior**

| **Network Type** | **Default Interfaces** | **DR/BDR** | **Multicast** | **Hello/Dead** | **Neighbor Config** |
|------------------|------------------------|------------|---------------|----------------|---------------------|
| Broadcast | Ethernet, FDDI | Yes | Yes | 10/40s | Not required |
| Point-to-point | HDLC, PPP serial | No | Yes | 10/40s | Not required |
| Non-broadcast (NBMA) | Frame Relay, X.25 | Yes | No | 30/120s | Required |
| Point-to-multipoint | Manual config | No | Yes | 30/120s | Not required |
| Point-to-multipoint non-bcast | Manual config | No | No | 30/120s | Required |

**Adjacency Requirements**

- Matching Area ID
- Subnet Mask
- Hello/Dead Timers
- MTU
- Authentication
- Unique Router IDs

> 💡 **Exam Focus:** Know OSPF states, packet types, router roles, and adjacency requirements.

### **3.5 EIGRP (Enhanced Interior Gateway Routing Protocol)**

**Key Concepts**

- Advanced distance-vector protocol
- Uses DUAL algorithm
- Forms neighbor adjacencies
- Uses composite metric (Bandwidth, Delay by default)

**Important Terms**

- **Feasible Distance (FD):** Best metric to destination
- **Advertised Distance (AD):** Neighbor's metric to destination
- **Successor:** Best route (lowest FD), in routing table
- **Feasible Successor:** Backup route; must meet feasibility condition (Neighbor's AD < Current FD)

**Configuration Requirements**

- Matching AS numbers (process IDs)
- Compatible K-values (metric weights)
- Network statement inclusion
- Valid neighbor relationship

**Features**

- Supports unequal-cost load balancing
- Rapid convergence
- Classless with VLSM support
- Manual route summarization

> 💡 **Exam Focus:** Understand successor vs. feasible successor concepts and the feasibility condition.

### **3.6 Important Network Tables**

| **Table Name** | **Primary Purpose** | **Key Information** | **View Command** | **Layer** |
|----------------|---------------------|---------------------|------------------|-----------|
| CAM Table | L2 Switching | MAC-to-port mapping | show mac address-table | Layer 2 |
| ARP Table | Address Resolution | IP-to-MAC mapping | show ip arp | Layer 3 |
| Routing Table | Route Selection | Best path info | show ip route | Layer 3 |
| FIB Table | Route Forwarding | CEF routing info | show ip cef | Layer 3 |
| Adjacency Table | Next-hop Info | Layer 2 next-hop | show adjacency | Layer 3 |
| VLAN Table | VLAN Management | VLAN configurations | show vlan | Layer 2 |

> 💡 **Exam Focus:** Know what each table stores and how to view it.

## **4. IP Services**

### **4.1 First Hop Redundancy Protocols (FHRP)**

Provide default gateway redundancy by sharing a virtual IP and MAC address among a group of routers.

**HSRP (Hot Standby Router Protocol)**

- Cisco proprietary
- Roles: Active, Standby
- Highest priority wins (0-255, default 100); highest IP breaks ties
- One Standby router, others in Listen state
- MAC: 0000.0C07.ACxx (v1), 0000.0C9F.Fxxx (v2)

**VRRP (Virtual Router Redundancy Protocol)**

- Industry standard (RFC 3768)
- Roles: Master, Backup
- Highest priority wins (1-254, default 100); highest IP breaks ties
- MAC: 0000.5E00.01xx

**GLBP (Gateway Load Balancing Protocol)**

- Cisco proprietary
- Provides redundancy AND load balancing
- Roles: Active Virtual Gateway (AVG) assigns virtual MACs to Active Virtual Forwarders (AVFs)
- Single virtual IP, multiple virtual MACs (up to 4 AVFs)
- Supports weighted load balancing

**Comparison Table**

| **Feature** | **HSRP** | **VRRP** | **GLBP** |
|-------------|----------|----------|----------|
| Standard | Cisco Proprietary | RFC 3768 | Cisco Proprietary |
| Load Balancing | No (active/standby) | No (master/backup) | Yes (multiple AVFs) |
| Virtual Router | Active + Standby | Master + Backup | AVG + AVFs |
| Priority Range | 0-255 (default 100) | 1-254 (default 100) | 1-255 (default 100) |
| Hello Timer | 3 seconds | 1 second | 3 seconds |
| Hold Timer | 10 seconds | 3 seconds | 10 seconds |
| Virtual MAC | 0000.0C07.ACxx | 0000.5E00.01xx | 0007.B400.xxyy |

> 💡 **Exam Focus:** Know the differences between FHRP protocols, especially regarding load balancing capabilities.

### **4.2 NAT (Network Address Translation)**

**Address Classifications**

- **Inside Local:** Private IP of internal host (e.g., 10.1.1.10)
- **Inside Global:** Public IP representing internal host (e.g., 203.0.113.5)
- **Outside Local:** IP of external host as seen internally (usually same as Outside Global)
- **Outside Global:** Actual public IP of external host (e.g., 8.8.8.8)

**NAT Types**

- **Static NAT:** One-to-one, persistent mapping (for servers)
- **Dynamic NAT:** Many-to-many mapping from a pool (first come, first served)
- **PAT (Port Address Translation / NAT Overload):** Many-to-one mapping using ports (most common)

**NAT Configuration Example**

```
! Define inside and outside interfaces
interface GigabitEthernet0/0
 ip address 192.168.1.1 255.255.255.0
 ip nat inside
interface GigabitEthernet0/1
 ip address 203.0.113.2 255.255.255.252
 ip nat outside

! Configure PAT (NAT Overload)
ip nat inside source list 1 interface GigabitEthernet0/1 overload
access-list 1 permit 192.168.1.0 0.0.0.255
```

> 💡 **Exam Focus:** Understand NAT address terminology and the differences between NAT types.

### **4.3 Quality of Service (QoS)**

**QoS Components and Mechanisms**

QoS implementations rely on four primary mechanisms that work together:

- **Queuing:**
  - Process of buffering packets in a software queue on a QoS-enabled interface
  - Two types of queues: software queue and hardware queue
  - Software queues implement various QoS controls
  - Hardware queue typically functions as first-in-first-out (FIFO)
  - Packets flow through the hardware queue before transmission to the physical medium
  - Each packet is assigned to a traffic class and placed in the corresponding queue

- **Classification:**
  - Process of dividing packets into categories based on predefined attributes
  - Not the actual buffering process
  - Inspects packet's Data Link layer and Network layer traffic descriptors
  - Common classification criteria:
    - Application protocol
    - Destination IP address
    - Layer 4 port numbers
    - DSCP/ToS values
  - Each traffic class is assigned its own queue
  - Different classifications are placed into separate queues

- **Scheduling:**
  - Process of determining when and in what order queued packets are transmitted
  - Not the actual buffering process
  - Handles packets according to configured QoS algorithms
  - Examples include:
    - Custom queuing (CQ): Each queue can send a fixed number of bytes before the next queue can send traffic
    - Priority queuing: Higher priority queues always serviced first
    - Weighted fair queuing: Balances resources among different traffic types

- **Traffic Policing:**
  - Process of regulating the rate of traffic flow
  - Not the process of buffering packets
  - Enforces limits by discarding traffic that exceeds configured thresholds
  - Works with classification, queuing, and scheduling
  - Common techniques:
    - Rate limiting
    - Token bucket algorithms
    - Traffic shaping (smooths traffic by buffering excess packets)


**Tail Drop**

- Default behavior
- Drops arriving packets when queue is full
- Can cause TCP global synchronization

**WRED (Weighted Random Early Detection)**

- Proactive approach
- Monitors average queue depth
- Drops packets probabilistically *before* queue is full
- Prevents synchronization
- Fairer to TCP flows

**QoS Models**

- **Best-Effort:** No QoS (default)
- **Integrated Services (IntServ):** Resource reservation (RSVP)
- **Differentiated Services (DiffServ):** Class-based traffic management

> 💡 **Exam Focus:** Understand the drawbacks of tail drop and how WRED addresses them.

**QoS Per-Hop Behaviors (PHBs)**

QoS implementation relies on several mechanisms that work together:

- **Classification:** Process of identifying and categorizing packets based on specific criteria (source/destination IP, ports, DSCP values, CoS values). Classification happens at network edge and determines which traffic gets preferential treatment.

- **Marking:** After classification, packets are "marked" with specific values (DSCP in the IP header or CoS in 802.1Q tag) to indicate priority throughout the network path. These markings allow downstream devices to identify traffic classes without deep packet inspection.

- **Queuing:** The process of buffering packets when network congestion occurs. Different queuing algorithms determine treatment:
  - Priority Queuing (PQ): Highest priority queue always serviced first
  - Fair Queuing (FQ): Bandwidth shared equally
  - Weighted Fair Queuing (WFQ): Bandwidth allocated proportionally
  - Class-Based Weighted Fair Queuing (CBWFQ): Minimum bandwidth guarantees per class
  - Low Latency Queuing (LLQ): Combines CBWFQ with strict priority queue for real-time traffic

- **Congestion Management:** Techniques to handle network saturation:
  - Tail Drop: Default behavior, simply drops new packets when queue is full
  - WRED: Selectively drops lower-priority packets before congestion becomes severe
  - ECN: Marks packets instead of dropping them to signal congestion

- **Policing:** Monitors traffic rate and drops packets exceeding specified threshold. Unlike shaping, policing doesn't buffer excess traffic, resulting in TCP retransmissions.

- **Shaping:** Controls traffic flow by buffering excess packets and releasing them later. Maintains specified rate without dropping packets unless buffer overflows, causing less TCP retransmissions than policing.




### **4.4 Network Time Protocol (NTP)**

- Synchronizes time across devices
- Uses UDP port 123
- Stratum levels indicate distance from authoritative source (Stratum 0)
- Modes: Client, Server, Symmetric active/passive (peer)

**Configuration Concepts**

- Set timezone
- Configure NTP server
- Configure as NTP client
- Configure NTP master

> 💡 **Exam Focus:** Understand NTP stratum levels and basic configuration.

### **4.4 SNMP (Simple Network Management Protocol)**

- **Purpose:** Framework for monitoring and managing network devices
- **Components:**
  - **Managed Devices:** Network elements with SNMP agents (routers, switches, servers)
  - **Agents:** Software modules running on managed devices
  - **NMS (Network Management Station):** Server running applications to monitor/control managed devices
- **Operations:**
  - **GET:** Retrieve specific values from a device
  - **SET:** Change configuration values on a device
  - **TRAP/INFORM:** Unsolicited notifications from agents to NMS
- **MIB (Management Information Base):** Hierarchical database of managed objects
- **OID (Object Identifier):** Unique identifier for each managed object in the MIB
- **Versions:**
  - **SNMPv1:** Original version, simple authentication (community strings), no encryption
  - **SNMPv2c:** Enhanced performance, improved error handling, still uses community strings
  - **SNMPv3:** Adds authentication (MD5/SHA), encryption (DES/AES), and access control
- **Common Uses:**
  - Network device discovery
  - Performance monitoring
  - Fault detection and alerting
  - Configuration backups and changes


### **4.5 DHCP (Dynamic Host Configuration Protocol)**

- Dynamically assigns IP configuration
- Uses UDP ports 67 (server) / 68 (client)
- Process: Discover, Offer, Request, Acknowledge (DORA)

**DHCP Configuration Concepts**

- Create DHCP pool
- Define network range
- Configure default gateway
- Configure DNS servers
- Set lease time
- Exclude specific addresses

> 💡 **Exam Focus:** Know the DORA process and basic DHCP configuration.

### **4.6 DNS (Domain Name System)**

- Resolves hostnames to IP addresses
- Hierarchical distributed database
- Uses UDP/TCP port 53
- Record types: A (IPv4), AAAA (IPv6), MX (Mail), CNAME (Alias), NS (Name Server)

**DNS Configuration Concepts**

- Configure DNS servers
- Enable DNS lookup
- Set domain name

> 💡 **Exam Focus:** Know common DNS record types and configuration commands.

### **4.7 Syslog**

- Standard for message logging
- Uses UDP port 514
- Centralized log management

**Severity Levels**

| **Level** | **Severity** | **Description** | **Action Required** |
|-----------|--------------|-----------------|---------------------|
| 0 | Emergencies | System unusable | Immediate action required |
| 1 | Alerts | Critical threat | Immediate response needed |
| 2 | Critical | Hardware/software failure | Urgent attention required |
| 3 | Errors | Non-urgent failures | Should be investigated |
| 4 | Warnings | Warning conditions | Monitor for escalation |
| 5 | Notifications | Normal but significant | Information only |
| 6 | Informational | Normal operations | No action needed |
| 7 | Debugging | Troubleshooting data | Used for diagnostics |

**Syslog Configuration Concepts**

- Configure syslog server
- Set logging level (trap)
- Specify source interface
- Enable logging

> 💡 **Exam Focus:** Know the syslog severity levels, especially 0-3.

**Syslog Facilities**

Besides severity levels, syslog uses "facilities" to categorize message sources:

| **Facility Code** | **Facility Name** | **Description** |
|-----------------|------------------|----------------|
| 0 | kern | Kernel messages |
| 1 | user | User-level messages |
| 2 | mail | Mail system |
| 3 | daemon | System daemons |
| 4 | auth | Security/authorization messages |
| 5 | syslog | Messages generated by syslogd |
| 6 | lpr | Line printer subsystem |
| 7 | news | Network news subsystem |
| 8 | uucp | UUCP subsystem |
| 9-15 | cron, local0-local7 | Clock daemon and locally used facilities |
| 16-23 | local0-local7 | Locally defined purposes |

**Syslog Message Format:**
`<PRI>TIMESTAMP HOSTNAME TAG: MESSAGE`

Where PRI (Priority) = Facility × 8 + Severity

This allows filtering and routing messages based on both source and severity.



### **4.8 SSH Configuration**

**Basic Setup Steps**

1. Set hostname
2. Configure domain name
3. Generate RSA keys
4. Configure VTY lines for SSH
5. Create user accounts
6. (Optional) Specify SSH version 2

> 💡 **Exam Focus:** Know the steps required to enable SSH access.

### **4.9 TFTP/FTP Capabilities in Networks**

**TFTP (Trivial File Transfer Protocol):**
- **Port:** UDP 69
- **Characteristics:**
  - Simple, lightweight file transfer protocol with minimal features
  - No authentication mechanism
  - No directory listing capability
  - No encryption
  - Uses UDP (connectionless)
- **Common Network Uses:**
  - IOS image transfers
  - Configuration file backups/restores
  - Router/switch boot files
  - DHCP server delivering boot files

**FTP (File Transfer Protocol):**
- **Port:** TCP 20 (data), TCP 21 (control)
- **Characteristics:**
  - Full-featured file transfer protocol
  - Username/password authentication
  - Directory navigation and listing
  - Multiple file transfer modes (ASCII, binary)
  - Uses TCP (connection-oriented)
- **Common Network Uses:**
  - Larger file transfers (IOS images)
  - Configuration archive management
  - More secure file operations when using FTPS (FTP Secure)
  - User file transfers

**Comparison and Best Practices:**
- TFTP is preferred for simple, quick transfers within secure networks
- FTP is better for larger files, when authentication is needed
- Both protocols send data in cleartext; consider SFTP or FTPS for secure transfers
- FTP active mode may have issues with firewalls (uses inbound connection)
- FTP passive mode is generally more firewall-friendly


## **5. Security Fundamentals**

### **5.1 Security Concepts & Threats**

**Terminology**

- **Threat:** Potential danger
- **Vulnerability:** Weakness
- **Exploit:** Method to use vulnerability
- **Mitigation:** Countermeasures

**Common Threats**

- **Reconnaissance:** Information gathering
- **Access Attacks:** Unauthorized access
- **Denial of Service (DoS):** Service disruption
- **Malware:** Malicious software
- **Social Engineering:** Human manipulation
- **Man-in-the-Middle:** Traffic interception

**Mitigation Techniques**

- Patching
- Segmentation
- Firewalls
- IDS/IPS
- Encryption
- User Training
- Assessments

> 💡 **Exam Focus:** Understand common threat types and their mitigations.

### **5.2 AAA (Authentication, Authorization, Accounting)**

Framework for controlling access, enforcing policies, auditing usage.

**Components**

- **Authentication:** Verify identity (Who are you?)
- **Authorization:** Determine privileges (What can you do?)
- **Accounting:** Track actions (What did you do?)


**Privilege Level Overview**
Cisco devices use privilege levels to control command access and authorization.

| **Level** | **Name** | **Default Access** | **Purpose** |
|-----------|----------|---------------------|-------------|
| **0** | Limited | Very restricted access | Extremely limited functionality (connect, logout, enable) |
| **1** | User EXEC | Default login level | Basic monitoring commands |
| **2-14** | Custom | User-defined | Customizable access levels (rarely used) |
| **15** | Privileged EXEC | Full administrative access | Complete device control |

**Default Command Availability**

- **Level 15 (Privileged):**
  - All configuration and management commands
  - Access to configuration mode
  - System-wide changes and security settings
  
- **Level 1 (User EXEC):**
  - Show commands (limited)
  - Basic connectivity testing (ping, traceroute)
  - Terminal settings
  - By default: `disable`, `enable`, `exit`, `help`, `logout`
  
- **Level 0 (Limited):**
  - Extremely restricted
  - By default only: `logout`, `enable`, `disable`

**Modifying Command Privileges**

- **Command:** `privilege exec level <level> <command>`
- **Purpose:** Moves a command to a specific privilege level
- **Effect:** Command becomes available only to users at that level or higher
- **Example:** `privilege exec level 1 help` moves the help command to level 1




**Implementation Protocols**

| **Feature** | **RADIUS** | **TACACS+** |
|-------------|------------|-------------|
| Standard | Open (IETF) | Cisco Proprietary |
| Protocol | UDP (1812/1813, 1645/1646) | TCP (49) |
| Encryption | Password only (in request) | Full packet encryption |
| AAA Steps | Combines AuthN/AuthZ | Separates AuthN/AuthZ/Acct |
| Customization | Limited | Granular control |
| Use Case | Multi-vendor | Cisco-centric |

**Authentication Factors**

- Something you know (password)
- Something you have (token)
- Something you are (biometric)

> 💡 **Exam Focus:** Know the differences between RADIUS and TACACS+, particularly encryption and protocol.


ryption types, each with different security characteristics.

| **Type** | **Algorithm** | **Command Example** | **Security Level** | **Reversible** | **IOS Version** |
|----------|---------------|---------------------|-------------------|----------------|-----------------|
| **Type 0** | Plaintext | `enable password cisco123` | None | N/A | All |
| **Type 4** | SHA-256 (older) | N/A (deprecated) | Medium | No | Pre-15.3 |
| **Type 5** | SHA-256 | `enable secret cisco123` | Good | No | Default in 15.3+ |
| **Type 7** | Vigenere | Used with `service password-encryption` | Weak | Yes (easily) | All |
| **Type 8** | PBKDF2 with SHA-256 | `enable algorithm-type sha256 secret cisco123` | Strong | No | 15.3+ |
| **Type 9** | Scrypt | `enable algorithm-type scrypt secret cisco123` | Strongest | No | 15.3+ |

**Password Commands and Their Effects**

- **enable secret** (Default Type 5):
  - Creates an encrypted password for privileged EXEC mode access
  - Stores as SHA-256 hash in the running configuration
  - Takes precedence over "enable password" when both exist
  
- **service password-encryption** (Type 7):
  - Encrypts all unencrypted passwords in the configuration
  - Uses weak Vigenere cipher (easily reversed)
  - Better than plaintext but not truly secure
  - Prevents shoulder-surfing only

- **username** with **secret**:
  - Creates a user with an encrypted password (Type 5 by default)
  - Example: `username admin secret cisco123`

**Algorithm Enhancement Commands**

- **enable algorithm-type sha256 secret** _password_:
  - Creates a Type 8 password using PBKDF2 with SHA-256
  - Stronger than the default Type 5
  
- **enable algorithm-type scrypt secret** _password_:
  - Creates a Type 9 password using the scrypt algorithm
  - Offers the strongest available encryption

**Password Type Identification**

 - enable secret 5 11
1mERr$hx5rVt7rPNoS4wqbXKX7m0    ! Type 5
- enable secret 8 88
8TgmTcbJ5$GsiWQ0qZRdCbN3Egw/5TT2hkpYPajC93    ! Type 8
- enable secret 9 9$2dYYk1zOX/UZk
S8JW4DbLiUfV0AiQ2/5EvhWpyUeGkN.MZe    ! Type 9


**Password Management Best Practices**

- Use Type 8 or Type 9 passwords when possible (strongest encryption)
- If downgrading IOS, reapply passwords as older devices won't recognize newer types
- Never rely on Type 7 encryption for sensitive passwords
- Configure `no service password-recovery` for physical security (caution: can lock you out permanently)
- Use AAA with external authentication servers for enterprise environments

**Version Compatibility Considerations**

- When downgrading from 15.3+ to earlier versions:
  - Type 8/9 passwords will not work
  - Must reissue passwords using compatible encryption types
  - Use `enable algorithm-type md5 command` in IOS 15.3/15.4
  - Or reconfigure with standard `enable secret` after downgrade

> 💡 **Exam Focus:** Know the differences between password types, especially Type 5 (default for `enable secret`), Type 7 (used with `service password-encryption`), and the stronger Types 8 and 9. Understand that Type 7 encryption is easily cracked, while Types 5, 8, and 9 are hashed and more secure. Remember that `enable secret` takes precedence over `enable password`.


### **5.3 Access Control Lists (ACLs)**

Packet filters used to control traffic flow based on defined criteria.

**Types**

- **Standard:** Numbers 1-99 / 1300-1999
  - Filters based on *source IP only*
  - Place close to destination

- **Extended:** Numbers 100-199 / 2000-2699
  - Filters based on source/destination IP, protocol, ports
  - Place close to source

- **Named:** Use descriptive names instead of numbers (can be standard or extended)

**Wildcard Masks**

- Used in ACLs to specify which IP address bits must match
- 0 = must match, 1 = don't care
- Inverse of subnet mask

**ACL Configuration Concepts**

- Create ACL with permit/deny statements
- Apply ACL to interface in specific direction (in/out)
- Consider implicit deny at end of every ACL
- Order matters (processed top-down)

**ACL Application Commands**

When configuring ACLs, it's important to understand the commands used to apply them to interfaces and lines:

- **IPv4 Interface ACL Application:**
  - **ip access-group** *list-number-or-name* **in|out**
  - Applied in interface configuration mode
  - **in** keyword applies ACL to inbound traffic (entering the interface)
  - **out** keyword applies ACL to outbound traffic (leaving the interface)
  - Example: `ip access-group 101 in`

- **IPv6 Interface ACL Application:**
  - **ipv6 traffic-filter** *name* **in|out**
  - Applied in interface configuration mode
  - **in** keyword configures ACL to apply to inbound traffic
  - **out** keyword configures ACL to apply to outbound traffic
  - Example: `ipv6 traffic-filter BLOCK_TELNET out`

- **IPv4 VTY Line ACL Application:**
  - **access-class** *acl-name-or-number* **in|out**
  - Applied in line configuration mode (vty, console, aux)
  - Controls Telnet/SSH access to the device itself
  - **in** keyword filters incoming connections
  - **out** keyword filters outgoing connections
  - Example: `access-class ADMIN_ONLY in`

- **IPv6 VTY Line ACL Application:**
  - **ipv6 access-class** *ipv6-acl-name* **in|out**
  - Applied in line configuration mode
  - Controls IPv6 Telnet/SSH access to the device
  - **in** and **out** keywords function the same as IPv4 access-class
  - Example: `ipv6 access-class IPV6_ADMIN in`

**Key Differences:**
- Interface ACLs (access-group/traffic-filter) filter transit traffic through the device
- VTY ACLs (access-class) filter administrative access to the device itself
- IPv4 uses "access-group" for interfaces and "access-class" for VTY lines
- IPv6 uses "traffic-filter" for interfaces and "access-class" for VTY lines



> 💡 **Exam Focus:** Understand ACL types, wildcard masks, and placement best practices.

### **5.4 Layer 2 Security Features**

**Port Security**

Limits MAC addresses per port to prevent unauthorized access and MAC flooding.

**Operation:**
- Enabled via switchport port-security
- Defaults: Max 1 MAC, violation shutdown, aging disabled

**Violation Modes:**
- **shutdown** (default): Err-disables port, logs, increments counter. Manual recovery needed
- **restrict:** Drops violating packets, logs, increments counter, sends SNMP trap
- **protect:** Silently drops violating packets. No log, no counter increment

**DHCP Snooping**

Prevents rogue DHCP servers by validating DHCP messages on untrusted ports.
- Builds binding table (IP-MAC-Port)
- Ports are trusted (to server) or untrusted (to clients)
- Configured per VLAN

**Dynamic ARP Inspection (DAI)**

Prevents ARP poisoning/spoofing by validating ARP packets against DHCP Snooping binding table.
- Drops invalid ARPs
- Configured per VLAN

**Best Practices**
- Disable unused ports
- Use dedicated VLANs
- Disable DTP on access ports
- Explicitly configure trunk modes
- Limit allowed VLANs on trunks
- Use native VLAN security

> 💡 **Exam Focus:** Understand port security violation modes and how DHCP snooping and DAI work together.

### **5.5 Wireless Security**

**Authentication Methods**

- **WPA/WPA2 Personal (PSK):** Pre-Shared Key, common for home/small business
- **WPA/WPA2 Enterprise (802.1X):** Uses RADIUS server for authentication (EAP methods)
- **CCKM (Cisco Centralized Key Management):** Cisco proprietary for fast secure roaming
- **802.1X with CCKM:** Hybrid for faster roaming with 802.1X

**WPA3**

Latest standard with:
- Stronger encryption
- Protection against offline attacks
- Forward secrecy
- Simplified onboarding

**Security Protocols Comparison**

| **Protocol** | **Authentication** | **Encryption** | **Key Management** | **Suitable For** |
|--------------|-------------------|----------------|-------------------|-----------------|
| WEP | Pre-shared key | RC4 (weak) | Static keys | Not recommended |
| WPA | PSK or 802.1X | TKIP | Per-session keys | Legacy devices |
| WPA2-Personal | Pre-shared key | AES-CCMP | 4-way handshake | Home/Small office |
| WPA2-Enterprise | 802.1X (EAP) | AES-CCMP | Dynamic key dist. | Enterprise |
| WPA3-Personal | SAE (Dragonfly) | AES-CCMP | Forward secrecy | Enhanced security |
| WPA3-Enterprise | 802.1X (EAP) | AES-GCMP-256 | 192-bit security | High security |


> 💡 **Exam Focus:** Know the differences between Personal and Enterprise authentication and WPA2 vs WPA3.


## **Wireless LAN Controller Security Layers**

**WLC Security Architecture**

- **Multi-layered approach:** Wireless networks use both Layer 2 and Layer 3 security mechanisms
- **Implementation order:** Must configure Layer 2 security before Layer 3 security
- **Network types:** Different options available for WLANs vs Guest LANs

**Layer 2 Security Options (WLAN)**

| **Option** | **Description** | **Use Case** |
|------------|-----------------|--------------|
| **None** | Disables Layer 2 security | Testing, public hotspots (not recommended) |
| **WPA+WPA2** | Enables Wi-Fi Protected Access | Standard enterprise/home security |
| **802.1X** | Uses Extensible Authentication Protocol (EAP) | Enterprise with RADIUS server |
| **Static WEP** | Uses static shared WEP key | Legacy systems only (insecure) |
| **Static WEP + 802.1X** | Combines static key with dynamic authentication | Mixed legacy environments |
| **CKIP** | Cisco Key Integrity Protocol | Cisco-proprietary alternative to WEP |
| **None + EAP Passthrough** | Open with remote EAP authentication | Special deployment scenarios |

**Layer 3 Security Options**

| **Option** | **Description** | **Applicability** | **Common Use** |
|------------|-----------------|-------------------|----------------|
| **None** | Disables Layer 3 security | WLAN & Guest LAN | When Layer 2 is sufficient |
| **IPsec** | Internet Protocol Security | WLAN only | Corporate secure access |
| **VPN Pass Through** | Allows client-to-VPN server connections | WLAN only | Remote access to corporate networks |
| **Web Authentication** | Prompts for credentials in web portal | WLAN & Guest LAN | Guest/visitor access with tracking |
| **Web Passthrough** | Direct access without credentials | WLAN & Guest LAN | Guest/visitor access without tracking |

**Network Type Security Matrix**

- **WLAN networks:**
  - Support both Layer 2 and Layer 3 security options
  - Typically use Layer 2 (WPA2/WPA3) with optional Layer 3

- **Guest LANs:**
  - **Cannot** use Layer 2 security
  - Typically use Layer 3 security only
  - **Primary options:** Web Authentication or Web Passthrough

**WLC Security Configuration Workflow**

1. Determine network type (WLAN vs Guest LAN)
2. For WLANs, select appropriate Layer 2 security first
3. Configure compatible Layer 3 security if needed
4. For Guest LANs, configure Layer 3 security only

**Security Tab Navigation in WLC GUI**

- Layer settings are accessed through the Security tab
- Layer 2 tab selected by default for WLANs
- Security configuration differs based on network type

> 💡 **Exam Focus:** Understand the difference between Layer 2 and Layer 3 security options and which apply to WLANs vs Guest LANs. Know that Guest LANs can only use Layer 3 security (typically Web Authentication or Web Passthrough). Remember that Layer 2 security must be configured before Layer 3 security, and not all combinations are compatible.


### **5.6 IPsec (Internet Protocol Security)**

Suite of protocols for secure IP communication (encryption, authentication, integrity).

**Core Functions**

- Confidentiality
- Integrity
- Origin Authentication
- Anti-Replay Protection

**Key Components**

- **ESP (Encapsulating Security Payload):** Provides encryption, integrity, optional authentication (Protocol 50)
- **AH (Authentication Header):** Provides integrity and authentication (Protocol 51). *Cannot* traverse NAT

**Modes**

- **Transport Mode:** Encrypts only payload; original IP header intact. Less overhead, end-to-end use
- **Tunnel Mode:** Encrypts entire original packet, adds new IP header. More secure, better NAT compatibility, site-to-site VPNs

**GRE over IPsec**

- GRE provides tunneling (routing protocols, multicast)
- IPsec provides security
- Common for site-to-site VPNs

> 💡 **Exam Focus:** Understand ESP vs. AH and transport vs. tunnel mode.

### **5.7 Intrusion Detection & Prevention (IDS/IPS)**

**IDS (Intrusion Detection System)**

- Passively monitors traffic/systems
- Generates alerts *only*
- Types:
  - Network-based (NIDS)
  - Host-based (HIDS)
- Methods:
  - Signature-based
  - Anomaly-based

**IPS (Intrusion Prevention System)**

- Active; sits inline
- Monitors and *blocks* detected threats automatically
- Higher potential for false positives

**Comparison**

| **Feature** | **IDS** | **IPS** |
|-------------|---------|---------|
| Deployment | Passive (monitoring) | Active (inline) |
| Response | Alerts only | Blocks threats |
| Performance Impact | Lower | Higher |
| False Positive Risk | Lower impact | Can block legitimate traffic |
| Latency | Minimal | Some processing delay |

> 💡 **Exam Focus:** Know the difference between passive detection (IDS) and active prevention (IPS).

### **5.8 Security Best Practices**

**Password Security**

- Use strong policies (length, complexity, history, aging)
- Consider MFA, certificates, biometrics

**User Awareness**

- Train users to mitigate phishing, social engineering

**Physical Access Control**

- First line of defense

**General**

- Defense in depth
- Least privilege
- Patching
- Monitoring
- Encryption
- Access controls
- Assessments
- Incident response plan

> 💡 **Exam Focus:** Understand the concept of defense in depth and basic security principles.

## **6. Automation and Programmability**

### **6.1 Network Automation Benefits**

- Reduced costs
- Faster deployment
- Increased reliability
- Reduced human error
- Improved compliance
- Scalability
- Consistent configuration

> 💡 **Exam Focus:** Understand how automation addresses traditional networking challenges.

### **6.2 Traditional vs Controller-Based Networking**

**Traditional**

- Device-by-device CLI management
- Distributed control plane
- Protocol-driven
- Manual operations

**Controller-Based (SDN)**

- Centralized management
- Policy-based
- Abstracted view
- Programmable interfaces
- Automation

> 💡 **Exam Focus:** Know the key differences between traditional and controller-based approaches.

### **6.3 Software-Defined Architecture (SDN)**

Separates control logic from hardware forwarding.

**Network Planes**

- **Data Plane:** Packet forwarding (switching, routing, NAT, ACLs). Distributed
- **Control Plane:** Decision-making (routing tables, forwarding logic). Centralized in SDN
- **Management Plane:** Device configuration & monitoring (SNMP, Syslog, SSH). Often separate
- **Application Plane:** Network applications leveraging SDN

**Components**

- Controllers
- Network Elements (devices)
- Applications
- APIs

**Underlay vs Overlay**

- **Underlay:** Physical infrastructure
- **Overlay:** Virtual network on top
- **Fabric:** Combined infrastructure

**API Directionality**

- **Northbound:** Controller <-> Applications (REST). High-level policy
- **Southbound:** Controller <-> Devices (OpenFlow, NETCONF, RESTCONF). Device-level control

> 💡 **Exam Focus:** Understand the separation of planes in SDN and API directionality.

### **6.4 Cisco Network Management Solutions**

**Cisco DNA Center / Catalyst Center**

- Modern controller for intent-based networking
- Automation, assurance, security policy
- Fabric provisioning via GUI and REST APIs

## **6.4 Cisco Network Management Solutions - DNA Center Architecture**

**Cisco DNA Center / Catalyst Center Overview**

- **Core Function:** Centralized controller providing a graphical user interface (GUI) to automate network configuration and management
- **Evolution:** Originally launched as DNA Center, now rebranded as Cisco Catalyst Center
- **Architecture:** Based on intent-based networking principles
- **Primary Value:** Abstracts and simplifies network complexity through a centralized controller

**DNA Center Architectural Components**

- **Controller Layer:** Central management engine
- **API Layer:** Programming interfaces for automation and integration
- **Network Layer:** Divided into overlay and underlay networks

**DNA Center API Framework**

| **API Type** | **Direction** | **Technology** | **Primary Function** | **Data Format** |
|--------------|---------------|----------------|----------------------|-----------------|
| **Northbound API** | Controller ↔ Applications | **REST** | Application integration | XML/JSON |
| **Southbound API** | Controller ↔ Devices | NETCONF | Device configuration | XML/RPC |
| **East-West API** | Controller ↔ Other Systems | Various | Cross-system integration | Various |

**Northbound API Details**

- **Implementation:** Representational State Transfer (REST)
- **Architecture:** Uses HTTP/HTTPS for transport
- **Protocol:** Hypertext Transfer Protocol (HTTP) or HTTP Secure (HTTPS)
- **Access Method:** Programmatic methods exposed by the API
- **Data Format:** Extensible Markup Language (XML) or JavaScript Object Notation (JSON)
- **Primary Use Case:** Enables Software-Defined Networking (SDN) applications to communicate with and send instructions to the DNA Center controller

**Southbound API Details**

- **Implementation:** Network Configuration Protocol (NETCONF)
- **Communication:** Two communication paths:
  - Controller to applications (northbound)
  - Controller to network devices (southbound)
- **Format:** Uses XML for data encoding
- **Method:** Remote Procedure Calls (RPCs)
- **Transport:** Typically relies on Secure Shell (SSH)
- **Purpose:** Configures and manages network devices directly

**Network Infrastructure Components**

- **Overlay Network:**
  - Software-Defined Access (SDA) component
  - Creates Virtual Extensible LAN (VXLAN) tunnels between SDA switches
  - Handles traffic between fabric endpoints

- **Underlay Network:**
  - Traditional physical network infrastructure
  - Collection of devices, interfaces, and media
  - Connects each fabric node
  - Supports the overlay network operation

**Fabric Architecture**

- **Components:** Overlay + Underlay networks working together
- **Traffic Flow:** 
  1. Endpoint connects to SDA network
  2. Traffic flows through overlay network's VXLAN tunnels
  3. Underlay provides physical connectivity between fabric nodes
- **Implementation:** The fabric is the entirety of both overlay and underlay networks working as a unified SDA network

**DNA Center Integration Capabilities**

- **Automation:** Network device provisioning and configuration
- **Assurance:** Network monitoring and troubleshooting
- **Security:** Policy creation and enforcement
- **Analytics:** Insights into network performance and usage

> 💡 **Exam Focus:** Remember that the **northbound API** uses **REST** to enable communication between applications and the DNA Center controller. Understand the different roles of northbound (REST, application integration) vs. southbound (NETCONF, device configuration) APIs. Know that the overlay uses VXLAN tunnels while the underlay is the physical infrastructure.

**Cisco Prime Infrastructure (PI)**

- Legacy GUI (Java-based) for device management
- Monitoring, reporting
- Being replaced by DNA Center

> 💡 **Exam Focus:** Understand basic DNA Center capabilities and its role in SDA.

### **6.5 REST APIs**

Representational State Transfer - architectural style for web services.

**Characteristics**

- Stateless
- Client-server
- Cacheable
- Layered system
- Uniform interface

**CRUD Operations & HTTP Methods**

| **CRUD Operation** | **HTTP Method** | **Description** | **Idempotent?** |
|-------------------|----------------|-----------------|----------------|
| Create | POST | Creates new resource | No |
| Read | GET | Retrieves resources | Yes |
| Update | PUT | Replaces resource fully | Yes |
| Update | PATCH | Modifies resource partly | No |
| Delete | DELETE | Removes resource | Yes |

**Authentication**

- Basic HTTP
- API Keys
- OAuth
- Session/Cookie
- Certificates

**Data Encoding**

- JSON
- XML
- YAML

> 💡 **Exam Focus:** Know the HTTP methods and their corresponding CRUD operations.


### **6.5.1 NETCONF and RESTCONF Protocols**

**NETCONF (Network Configuration Protocol):**
- **Standardization:** IETF standard (RFC 6241)
- **Transport:** Uses SSH (port 830) typically
- **Data Format:** XML-encoded data
- **Operations:**
  - `<get>`: Retrieve running configuration and device state
  - `<get-config>`: Retrieve configuration data only
  - `<edit-config>`: Modify configuration
  - `<copy-config>`: Replace entire configuration
  - `<delete-config>`: Delete configuration datastore
  - `<lock>/<unlock>`: Lock/unlock configuration datastore
  - `<close-session>`: Gracefully close session
  - `<kill-session>`: Force session termination
- **Key Features:**
  - Transaction-based changes
  - Configuration validation
  - Configuration rollback
  - Partial and selective configuration changes
  - Multiple configuration datastores (running, startup, candidate)
  - Supports filtering with XPath expressions

**RESTCONF (REST Configuration Protocol):**
- **Standardization:** IETF standard (RFC 8040)
- **Transport:** Uses HTTPS (typically port 443)
- **Data Format:** JSON or XML
- **Operations:** Maps HTTP methods to configuration operations
  - GET: Retrieve data
  - POST: Create resource
  - PUT: Replace resource
  - PATCH: Modify resource
  - DELETE: Remove resource
- **Key Features:**
  - Simpler than NETCONF
  - RESTful interface
  - HTTP-based operations
  - Partial subset of NETCONF functionality
  - Easier integration with web-based applications
  - Uses YANG data models (same as NETCONF)

**YANG (Yet Another Next Generation):**
- Modeling language for defining data models
- Used by both NETCONF and RESTCONF
- Describes how data is represented and accessed
- Provides constraints and relationships between data
- Structured and hierarchical
- Enables consistent device management

**Comparison:**

| **Feature** | **NETCONF** | **RESTCONF** |
|------------|-------------|--------------|
| **Protocol** | RPC-based | REST-based |
| **Transport** | SSH | HTTPS |
| **Data Format** | XML only | JSON or XML |
| **Complexity** | Higher | Lower |
| **Transactions** | Full support | Limited support |
| **Datastores** | Multiple | Only running |
| **API Style** | Procedure-oriented | Resource-oriented |
| **Integration** | Complex systems | Web applications |
| **Use Case** | Full network automation | Simpler API access |

**Example NETCONF Operation (XML):**
```xml
<rpc message-id="101" xmlns="urn:ietf:params:xml:ns:netconf:base:1.0">
  <get-config>
    <source>
      <running/>
    </source>
    <filter type="subtree">
      <interfaces xmlns="urn:ietf:params:xml:ns:yang:ietf-interfaces"/>
    </filter>
  </get-config>
</rpc>



### **6.6 Configuration Management Tools**

Automate infrastructure setup and maintenance.

**Ansible**

- Agentless (uses SSH)
- Push model
- Uses YAML Playbooks for tasks
- Idempotent operations
- Large module library

**Terraform**

- Infrastructure as Code (IaC) for provisioning/lifecycle management
- Declarative language (HCL)
- State-based (compares desired vs actual state)
- Uses provider APIs
- Plan/Apply workflow

> 💡 **Exam Focus:** Understand the basics of Ansible (agentless, YAML playbooks).

### **6.7 JSON (JavaScript Object Notation)**

Lightweight data-interchange format.

**Structure**

- Key-value pairs
- Objects ({})
- Arrays ([])

**Data Types**

- String (in double quotes)
- Number
- Boolean (true/false)
- null
- Object
- Array

**Example**

```json
{
  "device": {
    "name": "Router1",
    "model": "Cisco ISR 4351",
    "interfaces": [
      {
        "name": "GigabitEthernet0/0",
        "ip": "192.168.1.1",
        "mask": "255.255.255.0",
        "enabled": true
      },
      {
        "name": "GigabitEthernet0/1",
        "ip": "10.0.0.1",
        "mask": "255.255.255.0",
        "enabled": false
      }
    ]
  }
}
```

> 💡 **Exam Focus:** Be able to read basic JSON structure and identify key components.

### **6.8 AI and Machine Learning in Networking**

**Generative AI**

- Network config generation
- Automated documentation
- Troubleshooting script generation
- Natural language interfaces

**Predictive AI**

- Anomaly detection
- Capacity planning
- Failure prediction
- Traffic analysis
- Security threat detection

> 💡 **Exam Focus:** Understand basic use cases for AI in networking.

## **CCNA Exam Preparation Tips**

### **Study Strategy**

1. **Understand concepts first**, then memorize details
2. **Practice configurations** in a lab environment (physical or virtual)
3. **Review topics regularly** using spaced repetition
4. **Take practice exams** to identify weak areas

### **Key Areas to Focus On**

- **Subnetting**: Practice until you can do it quickly
- **Routing protocols**: OSPF and EIGRP configuration and troubleshooting
- **Security**: ACLs, port security, wireless security
- **Automation**: REST APIs, JSON, YAML
- **Troubleshooting methodology**: Systematic approach

### **Lab Resources**

- Cisco Packet Tracer
- GNS3
- EVE-NG
- CML (Cisco Modeling Labs)
- DevNet Sandboxes

### **Exam Day Tips**

1. Review key concepts the day before
2. Get a good night's sleep
3. Read questions carefully
4. Manage your time (average 1-1.5 minutes per question)
5. Mark and return to difficult questions
6. Trust your preparation
