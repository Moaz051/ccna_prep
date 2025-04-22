# Cisco IOS Command Reference Guide

## Table of Contents
1. [Network Fundamentals](#network-fundamentals)
   - [IPv4 Configuration](#ipv4-configuration)
   - [IPv6 Configuration](#ipv6-configuration)
   - [Interface Management](#interface-management)
   - [MAC Address Table](#mac-address-table)
   - [Basic System Management](#basic-system-management)

2. [Network Access](#network-access)
   - [VLAN Configuration](#vlan-configuration)
   - [Trunk Configuration](#trunk-configuration)
   - [EtherChannel Configuration](#etherchannel-configuration)
   - [STP (Spanning Tree Protocol)](#stp-spanning-tree-protocol)
   - [Port Security](#port-security)
   - [LLDP and CDP](#lldp-and-cdp)

3. [IP Connectivity](#ip-connectivity)
   - [Static Routing](#static-routing)
   - [OSPF Configuration](#ospf-configuration) 
   - [EIGRP Configuration](#eigrp-configuration)
   - [RIP Configuration](#rip-configuration)
   - [First Hop Redundancy Protocols](#first-hop-redundancy-protocols)

4. [IP Services](#ip-services)
   - [NAT Configuration](#nat-configuration)
   - [DHCP Configuration](#dhcp-configuration)
   - [NTP Configuration](#ntp-configuration)
   - [PoE (Power over Ethernet)](#poe-power-over-ethernet)

5. [Security Fundamentals](#security-fundamentals)
   - [Device Security Configuration](#device-security-configuration)
   - [Layer 2 Security Features](#layer-2-security-features)
   
6. [System Management and Recovery](#system-management-and-recovery)
   - [File Management](#file-management)
   - [Password Recovery](#password-recovery)
   - [IOS Management](#ios-management)

---

## Network Fundamentals

### IPv4 Configuration
*Commands for configuring and verifying IPv4 addressing on Cisco devices*

```
# Interface IP Configuration
Router(config)# interface GigabitEthernet0/0              # Enter interface configuration mode
Router(config-if)# ip address 192.168.1.1 255.255.255.0   # Configure static IP address and subnet mask
Router(config-if)# no shutdown                            # Enable the interface

# Layer 3 Switch Configuration
Switch(config)# ip routing                                # Enable IP routing on a switch
Switch(config)# interface vlan 10                         # Enter VLAN interface configuration
Switch(config-if)# ip address 10.10.10.1 255.255.255.0    # Configure SVI IP address
Switch(config-if)# no shutdown                            # Enable the SVI

# IP Management (Layer 2 Switch)
Switch(config)# interface vlan 1                          # Enter management VLAN interface
Switch(config-if)# ip address 192.168.1.10 255.255.255.0  # Set management IP
Switch(config-if)# no shutdown                            # Enable interface
Switch(config)# ip default-gateway 192.168.1.1            # Set default gateway

# Verification Commands
Router# show ip interface brief                           # Quick status of all IP interfaces
Router# show ip interface gigabitEthernet 0/0             # Detailed IP info for specific interface
Router# show running-config interface gigabitEthernet 0/0 # Config for specific interface
Router# ping 192.168.1.2                                  # Test connectivity
```

### IPv6 Configuration
*Commands for configuring and verifying IPv6 addressing on Cisco devices*

```
# Basic IPv6 Configuration
Router(config)# ipv6 unicast-routing                      # Enable IPv6 routing (global command)
Router(config-if)# ipv6 address 2001:db8:0:1::1/64        # Configure global unicast address
Router(config-if)# ipv6 address fe80::1 link-local        # Configure explicit link-local address
Router(config-if)# ipv6 address 2001:db8::/64 eui-64      # Use EUI-64 format (derived from MAC)

# IPv6 Address Types
# Global Unicast: 2000::/3 (routable public addresses)
# Unique Local: fc00::/7 (private addresses, similar to IPv4 private)
# Link Local: fe80::/10 (non-routable, auto-configured on interfaces)

# Additional IPv6 Configuration
Router(config-if)# ipv6 enable                            # Enable IPv6 and auto-configure link-local
Router(config)# ipv6 unicast-routing                      # Enable IPv6 packet forwarding

# Verification Commands
Router# show ipv6 interface brief                         # Quick status of IPv6 interfaces
Router# show ipv6 interface gigabitEthernet 0/0           # Detailed IPv6 info for interface
Router# show ipv6 neighbors                               # IPv6 neighbor table (similar to ARP)
Router# ping ipv6 2001:db8:0:1::2                         # Test IPv6 connectivity
```

### Interface Management
*Commands for managing physical and virtual interfaces*

```
# Basic Interface Configuration
Router(config)# interface GigabitEthernet0/0              # Enter interface configuration
Router(config-if)# description Link to Core Switch        # Set interface description
Router(config-if)# speed {10 | 100 | 1000 | auto}         # Set interface speed
Router(config-if)# duplex {half | full | auto}            # Set duplex mode
Router(config-if)# mtu 1500                               # Set Maximum Transmission Unit
Router(config-if)# shutdown                               # Disable interface
Router(config-if)# no shutdown                            # Enable interface

# Interface Range Configuration
Switch(config)# interface range GigabitEthernet0/1 - 12   # Configure multiple interfaces
Switch(config-if-range)# shutdown                         # Disable all in range
Switch(config)# interface range g0/1 - 12, g0/20 - 24     # Configure multiple ranges
Switch(config-if-range)# description User Ports           # Apply description to all

# Loopback Interface
Router(config)# interface loopback 0                      # Create virtual loopback interface
Router(config-if)# ip address 10.255.255.1 255.255.255.255 # Assign IP address

# Verification and Troubleshooting
Router# show interfaces                                   # Details of all interfaces
Router# show interfaces status                            # Status of all interfaces
Router# show ip interface brief                           # Summary of interface states
Router# show interfaces GigabitEthernet0/0                # Specific interface details
Router# show controllers GigabitEthernet0/0               # Hardware status (detect cable issues)
```

### MAC Address Table
*Commands for managing and viewing the MAC address table on switches*

```
# MAC Address Table Configuration
Switch(config)# mac address-table aging-time 300          # Set aging time in seconds (default: 300)
Switch(config)# mac address-table static 1122.3344.5566 vlan 10 interface g0/1  # Add static entry

# Clear MAC Address Table
Switch# clear mac address-table dynamic                   # Clear all dynamic entries
Switch# clear mac address-table dynamic interface g0/1    # Clear entries for specific interface
Switch# clear mac address-table dynamic vlan 10           # Clear entries for specific VLAN

# Verification Commands
Switch# show mac address-table                            # Show MAC address table
Switch# show mac address-table count                      # Show MAC address count
Switch# show mac address-table aging-time                 # Show aging time
Switch# show mac address-table vlan 10                    # Show MAC addresses in specific VLAN
Switch# show mac address-table interface g0/1             # Show MAC addresses on specific interface
Switch# show mac address-table static                     # Show static MAC addresses
```

### Basic System Management
*Commands for basic device configuration and management*

```
# Hostname and Banner Configuration
Router(config)# hostname Core-Router                      # Set device hostname
Router(config)# banner login "Authorized Access Only"     # Set login banner
Router(config)# banner motd "Maintenance Window Sunday"   # Set Message of the Day banner

# Time and Clock Configuration
Router(config)# clock timezone EST -5                     # Set timezone (EST, -5 hours from UTC)
Router(config)# clock summer-time EDT recurring           # Configure Daylight Saving Time
Router# clock set 14:30:00 15 March 2023                  # Set system clock manually

# Basic System Verification
Router# show version                                      # Show IOS version and hardware info
Router# show running-config                               # Show current active configuration
Router# show startup-config                               # Show saved configuration in NVRAM
Router# show processes cpu                                # Show CPU utilization
Router# show memory                                       # Show memory usage
Router# show clock                                        # Show current system time
```

---

## Network Access

### VLAN Configuration
*Commands for creating and configuring VLANs on switches*

```
# VLAN Creation and Management
Switch(config)# vlan 10                                   # Create VLAN or enter VLAN config mode
Switch(config-vlan)# name Engineering                     # Assign name to VLAN
Switch(config-vlan)# state active                         # Set VLAN state to active (default)
Switch(config)# no vlan 10                                # Delete VLAN

# Access Port Configuration
Switch(config)# interface GigabitEthernet0/1              # Enter interface configuration
Switch(config-if)# switchport mode access                 # Set interface as access port
Switch(config-if)# switchport access vlan 10              # Assign port to VLAN 10
Switch(config-if)# switchport voice vlan 20               # Assign voice VLAN (for IP phones)

# Default VLAN (VLAN 1)
# Avoid using VLAN 1 for user traffic (security best practice)
# VLAN 1 cannot be deleted or renamed

# Verification Commands
Switch# show vlan                                         # Display all VLANs and ports
Switch# show vlan brief                                   # Summary view of all VLANs
Switch# show vlan id 10                                   # Show specific VLAN details
Switch# show interfaces GigabitEthernet0/1 switchport     # Show switchport configuration
```

### Trunk Configuration
*Commands for configuring VLAN trunks between switches*

```
# Trunk Port Configuration
Switch(config)# interface GigabitEthernet0/1              # Enter interface configuration
Switch(config-if)# switchport mode trunk                  # Set interface as trunk port
Switch(config-if)# switchport trunk encapsulation dot1q   # Set 802.1Q encapsulation (some models)
Switch(config-if)# switchport trunk native vlan 99        # Set native VLAN (untagged traffic)
Switch(config-if)# switchport trunk allowed vlan 10,20,30 # Restrict VLANs on trunk
Switch(config-if)# switchport trunk allowed vlan add 40   # Add VLAN to allowed list
Switch(config-if)# switchport trunk allowed vlan remove 30 # Remove VLAN from allowed list
Switch(config-if)# switchport trunk allowed vlan all      # Allow all VLANs on trunk
Switch(config-if)# switchport nonegotiate                 # Disable DTP (Dynamic Trunking Protocol)

# Verification Commands
Switch# show interfaces trunk                             # Display all trunk ports
Switch# show interface GigabitEthernet0/1 trunk           # Show specific trunk port
Switch# show interfaces GigabitEthernet0/1 switchport     # Show detailed switchport information

# Native VLAN Mismatch Detection
Switch# show interfaces trunk                             # Check for "Native VLAN Mismatch" warning

# Best Practices
# - Change native VLAN from default (VLAN 1) to unused VLAN (security)
# - Explicitly specify allowed VLANs on trunk (don't use "all")
# - Disable DTP when connecting to other vendors or secure environments
```

### EtherChannel Configuration
*Commands for bundling multiple physical links into a logical channel*

```
# LACP EtherChannel (802.3ad) - Recommended
Switch(config)# interface range GigabitEthernet0/1-2      # Select interfaces for channel
Switch(config-if-range)# channel-protocol lacp            # Specify LACP protocol
Switch(config-if-range)# channel-group 1 mode active      # Create group 1 and set LACP active
Switch(config-if-range)# no shutdown                      # Ensure interfaces are enabled
Switch(config)# interface port-channel 1                  # Configure the logical interface
Switch(config-if)# switchport mode trunk                  # Configure as trunk (if needed)
Switch(config-if)# switchport trunk native vlan 99        # Set native VLAN

# PAgP EtherChannel (Cisco Proprietary)
Switch(config)# interface range GigabitEthernet0/3-4      # Select interfaces for channel  
Switch(config-if-range)# channel-protocol pagp            # Specify PAgP protocol
Switch(config-if-range)# channel-group 2 mode desirable   # Create group 2 and set PAgP desirable
Switch(config)# interface port-channel 2                  # Configure the logical interface

# Static EtherChannel (No Protocol)
Switch(config)# interface range GigabitEthernet0/5-6      # Select interfaces for channel
Switch(config-if-range)# channel-group 3 mode on          # Create static EtherChannel
Switch(config)# interface port-channel 3                  # Configure the logical interface

# Layer 3 EtherChannel
Switch(config)# interface range GigabitEthernet0/7-8      # Select interfaces for channel
Switch(config-if-range)# no switchport                    # Convert to routed ports
Switch(config-if-range)# channel-group 4 mode active      # Create LACP EtherChannel
Switch(config)# interface port-channel 4                  # Configure the logical interface
Switch(config-if)# ip address 10.1.1.1 255.255.255.252    # Assign IP address

# Verification Commands
Switch# show etherchannel summary                         # Quick status of all EtherChannels
Switch# show etherchannel 1 detail                        # Detailed info for specific group
Switch# show etherchannel port-channel                    # Show port-channel interfaces
Switch# show interfaces port-channel 1                    # Show specific port-channel details
Switch# show spanning-tree                                # Verify STP treats group as one link
```

### STP (Spanning Tree Protocol)
*Commands for configuring and monitoring Spanning Tree Protocol*

```
# STP Mode Configuration
Switch(config)# spanning-tree mode rapid-pvst             # Set to Rapid PVST+ (recommended)
Switch(config)# spanning-tree mode mst                    # Set to Multiple Spanning Tree
Switch(config)# spanning-tree mode pvst                   # Set to Per-VLAN Spanning Tree

# Root Bridge Configuration
Switch(config)# spanning-tree vlan 10 root primary        # Set as primary root for VLAN 10
Switch(config)# spanning-tree vlan 20 root secondary      # Set as backup root for VLAN 20
Switch(config)# spanning-tree vlan 30 priority 4096       # Set bridge priority manually
                                                          # Valid values: 0-61440 in increments of 4096

# STP Port Configuration
Switch(config-if)# spanning-tree portfast                 # Enable PortFast on access port
Switch(config-if)# spanning-tree bpduguard enable         # Enable BPDU Guard on port
Switch(config-if)# spanning-tree cost 100                 # Manually set port cost
Switch(config-if)# spanning-tree port-priority 64         # Set port priority (0-240, multiple of 16)

# Global STP Features
Switch(config)# spanning-tree portfast default            # Enable PortFast on all access ports
Switch(config)# spanning-tree portfast bpduguard default  # Enable BPDU Guard on all PortFast ports
Switch(config)# spanning-tree loopguard default           # Enable Loop Guard globally
Switch(config)# spanning-tree extend system-id            # Use extended system IDs (enables VLAN IDs)

# Verification Commands
Switch# show spanning-tree                                # Show STP for all VLANs
Switch# show spanning-tree vlan 10                        # Show STP for specific VLAN
Switch# show spanning-tree interface GigabitEthernet0/1   # Show STP for specific interface
Switch# show spanning-tree summary                        # Show STP global settings
Switch# show spanning-tree detail                         # Show detailed STP information
Switch# show spanning-tree root                           # Show root bridge information

# STP Troubleshooting
# Check for ports in "BLK" (blocking) or "LIS" (listening) states
# Verify consistent STP mode across switches
# Ensure no unintended bridge priorities are set
```

### Port Security
*Commands for restricting input to an interface by limiting MAC addresses*

```
# Basic Port Security Configuration
Switch(config)# interface GigabitEthernet0/1              # Enter interface configuration
Switch(config-if)# switchport mode access                 # Set as access port (required)
Switch(config-if)# switchport port-security               # Enable port security
Switch(config-if)# switchport port-security maximum 3     # Set maximum MAC addresses (default: 1)

# MAC Address Configuration Options
Switch(config-if)# switchport port-security mac-address 000A.1111.2222  # Set static MAC
Switch(config-if)# switchport port-security mac-address sticky          # Enable sticky learning
                                                          # Dynamically learned MACs added to config

# Violation Mode Configuration
Switch(config-if)# switchport port-security violation shutdown  # Disable port on violation (default)
Switch(config-if)# switchport port-security violation restrict  # Log violation, drop excess traffic
Switch(config-if)# switchport port-security violation protect   # Silently drop excess traffic

# Aging Configuration
Switch(config-if)# switchport port-security aging time 60       # Set aging time in minutes
Switch(config-if)# switchport port-security aging type inactivity # Age only if inactive
Switch(config-if)# switchport port-security aging type absolute  # Age regardless of activity
Switch(config-if)# switchport port-security aging static        # Apply aging to static addresses

# Recovery from Security Violation
Switch# interface GigabitEthernet0/1                      # Enter interface configuration
Switch(config-if)# shutdown                               # Shutdown the interface
Switch(config-if)# no shutdown                            # Re-enable the interface
Switch(config)# errdisable recovery cause psecure-violation # Enable auto recovery
Switch(config)# errdisable recovery interval 300          # Set recovery interval (seconds)

# Verification Commands
Switch# show port-security                                # Show port security status for all ports
Switch# show port-security interface GigabitEthernet0/1   # Show specific interface security
Switch# show port-security address                        # Show secured MAC addresses
Switch# show errdisable recovery                          # Show recovery configuration
```

### LLDP and CDP
*Commands for Link Layer Discovery Protocol and Cisco Discovery Protocol*

```
# CDP Configuration (Cisco Proprietary)
Switch(config)# cdp run                                   # Enable CDP globally (default enabled)
Switch(config)# no cdp run                                # Disable CDP globally
Switch(config-if)# cdp enable                             # Enable CDP on interface (default)
Switch(config-if)# no cdp enable                          # Disable CDP on interface
Switch(config)# cdp timer 60                              # Set CDP update timer (seconds)
Switch(config)# cdp holdtime 180                          # Set CDP hold time (seconds)

# LLDP Configuration (IEEE 802.1AB Standard)
Switch(config)# lldp run                                  # Enable LLDP globally (default disabled)
Switch(config)# no lldp run                               # Disable LLDP globally
Switch(config-if)# lldp transmit                          # Enable LLDP transmit on interface
Switch(config-if)# no lldp transmit                       # Disable LLDP transmit on interface
Switch(config-if)# lldp receive                           # Enable LLDP receive on interface
Switch(config-if)# no lldp receive                        # Disable LLDP receive on interface
Switch(config)# lldp timer 30                             # Set LLDP update timer (seconds)
Switch(config)# lldp holdtime 120                         # Set LLDP hold time (seconds)

# Verification Commands
Switch# show cdp neighbors                                # Show CDP neighbor summary
Switch# show cdp neighbors detail                         # Show detailed CDP neighbor info
Switch# show cdp interface                                # Show interfaces with CDP enabled
Switch# show lldp neighbors                               # Show LLDP neighbor summary
Switch# show lldp neighbors detail                        # Show detailed LLDP neighbor info
Switch# show lldp interface                               # Show interfaces with LLDP enabled

# Security Best Practice
# Disable CDP/LLDP on interfaces connecting to untrusted networks
```

---

## IP Connectivity

### Static Routing
*Commands for configuring static routes on Cisco routers*

```
# Basic Static Route Configuration
Router(config)# ip route 10.0.0.0 255.0.0.0 192.168.1.2         # Network route via next-hop IP
Router(config)# ip route 172.16.0.0 255.255.0.0 GigabitEthernet0/0 # Network route via exit interface
Router(config)# ip route 172.16.0.0 255.255.0.0 GigabitEthernet0/0 192.168.1.2 # Fully specified

# Default Route Configuration
Router(config)# ip route 0.0.0.0 0.0.0.0 192.168.1.2            # Default route via next-hop
Router(config)# ip route 0.0.0.0 0.0.0.0 GigabitEthernet0/0     # Default route via exit interface

# Host Route Configuration
Router(config)# ip route 10.10.10.10 255.255.255.255 192.168.1.2 # Host route (for specific host)

# Floating Static Route (Backup Route)
Router(config)# ip route 10.0.0.0 255.0.0.0 192.168.2.2 200     # Higher AD (less preferred)
                                                                # Default AD for static route: 1

# IPv6 Static Routes
Router(config)# ipv6 route 2001:db8::/64 2001:db8:0:1::2        # IPv6 route via next-hop
Router(config)# ipv6 route 2001:db8::/64 GigabitEthernet0/0     # IPv6 route via exit interface
Router(config)# ipv6 route ::/0 2001:db8:0:1::1                 # IPv6 default route

# Static Route with Description
Router(config)# ip route 10.1.0.0 255.255.0.0 192.168.1.2 name "Route to Branch Office"

# Verification Commands
Router# show ip route                                      # Show IPv4 routing table
Router# show ip route static                               # Show only static routes
Router# show ipv6 route                                    # Show IPv6 routing table 
Router# show ipv6 route static                             # Show only IPv6 static routes
Router# show running-config | include ip route             # Show static routes in config
```

### OSPF Configuration
*Commands for configuring Open Shortest Path First routing protocol*

```
# Basic OSPF Configuration
Router(config)# router ospf 1                              # Enter OSPF process 1 configuration
Router(config-router)# network 10.0.0.0 0.255.255.255 area 0 # Add networks to OSPF area 0
Router(config-router)# network 192.168.1.0 0.0.0.255 area 0 # Add another network to area 0

# OSPF Router ID Configuration
Router(config-router)# router-id 1.1.1.1                   # Set OSPF router ID manually
Router(config)# interface loopback 0                       # Create loopback interface
Router(config-if)# ip address 1.1.1.1 255.255.255.255      # Assign IP (used as router ID)

# Interface-Specific OSPF Configuration
Router(config)# interface GigabitEthernet0/0               # Enter interface configuration
Router(config-if)# ip ospf 1 area 0                        # Enable OSPF directly on interface
Router(config-if)# ip ospf cost 100                        # Set OSPF cost for interface
Router(config-if)# ip ospf priority 255                    # Set priority (for DR/BDR election)
Router(config-if)# ip ospf network point-to-point          # Set network type to point-to-point

# OSPF Authentication
Router(config-if)# ip ospf authentication message-digest    # Enable MD5 authentication
Router(config-if)# ip ospf message-digest-key 1 md5 CISCO   # Set key ID 1 with password CISCO
Router(config-router)# area 0 authentication message-digest # Enable MD5 auth for area 0

# Passive Interfaces
Router(config-router)# passive-interface GigabitEthernet0/1 # No OSPF packets, but advertise network
Router(config-router)# passive-interface default            # Make all interfaces passive
Router(config-router)# no passive-interface GigabitEthernet0/0 # Make specific interface active

# OSPF Timers Configuration
Router(config-if)# ip ospf hello-interval 5                # Set hello timer (seconds)
Router(config-if)# ip ospf dead-interval 20                # Set dead timer (seconds)

# Route Summarization
Router(config-router)# area 1 range 10.1.0.0 255.255.0.0   # Summarize within area
Router(config-router)# summary-address 10.0.0.0 255.0.0.0  # Summarize at ASBR (external)

# Default Route Advertisement
Router(config-router)# default-information originate        # Advertise default if exists
Router(config-router)# default-information originate always # Advertise default always

# Verification Commands
Router# show ip ospf neighbor                              # Show OSPF neighbors
Router# show ip ospf interface                             # Show OSPF interface details
Router# show ip ospf database                              # Show OSPF database (LSAs)
Router# show ip route ospf                                 # Show OSPF routes
Router# show ip protocols                                  # Show routing protocol info
Router# clear ip ospf process                              # Reset OSPF process
```

### EIGRP Configuration
*Commands for configuring Enhanced Interior Gateway Routing Protocol*

```
# Basic EIGRP Configuration
Router(config)# router eigrp 100                           # Enter EIGRP AS 100 configuration
Router(config-router)# network 10.0.0.0 0.255.255.255      # Add networks to EIGRP
Router(config-router)# network 192.168.1.0 0.0.0.255       # Add another network
Router(config-router)# no auto-summary                     # Disable auto-summary (recommended)

# EIGRP Router ID
Router(config-router)# eigrp router-id 1.1.1.1             # Set EIGRP router ID manually

# Interface-Specific EIGRP Configuration
Router(config)# interface GigabitEthernet0/0               # Enter interface configuration
Router(config-if)# ip hello-interval eigrp 100 5           # Set hello timer (seconds)
Router(config-if)# ip hold-time eigrp 100 15               # Set hold timer (seconds)
Router(config-if)# ip bandwidth-percent eigrp 100 75       # Limit bandwidth usage to 75%
Router(config-if)# ip summary-address eigrp 100 10.1.0.0 255.255.0.0 # Interface summarization

# EIGRP Authentication
Router(config)# key chain EIGRP-KEY                        # Create key chain
Router(config-keychain)# key 1                             # Create key 1
Router(config-keychain-key)# key-string CISCO              # Set key value
Router(config)# interface GigabitEthernet0/0               # Enter interface configuration
Router(config-if)# ip authentication mode eigrp 100 md5     # Enable MD5 authentication
Router(config-if)# ip authentication key-chain eigrp 100 EIGRP-KEY # Apply key chain

# Passive Interfaces
Router(config-router)# passive-interface GigabitEthernet0/1 # No EIGRP packets, advertise network
Router(config-router)# passive-interface default            # Make all interfaces passive
Router(config-router)# no passive-interface GigabitEthernet0/0 # Make specific interface active

# Adjusting EIGRP Metrics
Router(config-if)# delay 100                               # Set delay value (tens of microseconds)
Router(config-if)# bandwidth 1544                          # Set bandwidth (Kbps)

# Default Route Advertisement
Router(config-router)# redistribute static                 # Redistribute static routes
Router(config-router)# default-metric 10000 100 255 1 1500 # Set metric for redistributed routes

# Verification Commands
Router# show ip eigrp neighbors                            # Show EIGRP neighbors
Router# show ip eigrp interfaces                           # Show interfaces running EIGRP
Router# show ip eigrp topology                             # Show EIGRP topology table
Router# show ip route eigrp                                # Show EIGRP routes
Router# show ip protocols                                  # Show routing protocol info
Router# clear ip eigrp neighbors                           # Reset EIGRP neighbors
```

### RIP Configuration
*Commands for configuring Routing Information Protocol*

```
# Basic RIP Configuration
Router(config)# router rip                                 # Enter RIP configuration mode
Router(config-router)# version 2                           # Use RIPv2 (supports VLSM and CIDR)
Router(config-router)# network 10.0.0.0                    # Advertise network in RIP
Router(config-router)# network 192.168.1.0                 # Advertise another network
Router(config-router)# no auto-summary                     # Disable auto summarization (recommended)

# RIP Timers
Router(config-router)# timers basic 30 180 180 240         # Update, invalid, hold, flush timers

# RIP Authentication
Router(config)# interface GigabitEthernet0/0               # Enter interface configuration
Router(config-if)# ip rip authentication mode md5          # Enable MD5 authentication
Router(config-if)# ip rip authentication key-chain RIP-KEY # Apply key chain
Router(config)# key chain RIP-KEY                          # Create key chain
Router(config-keychain)# key 1                             # Create key 1
Router(config-keychain-key)# key-string CISCO              # Set key value

# Passive Interfaces
Router(config-router)# passive-interface GigabitEthernet0/1 # No RIP updates, advertise network
Router(config-router)# passive-interface default            # Make all interfaces passive
Router(config-router)# no passive-interface GigabitEthernet0/0 # Make specific interface active

# Default Route Advertisement
Router(config-router)# default-information originate       # Advertise default route in RIP

# Verification Commands
Router# show ip rip database                               # Show RIP database
Router# show ip protocols                                  # Show routing protocol info
Router# show ip route rip                                  # Show RIP routes
Router# debug ip rip                                       # Debug RIP updates
Router# undebug all                                        # Turn off all debugging
```

### First Hop Redundancy Protocols
*HSRP, VRRP, and GLBP commands for router redundancy*

```
# HSRP Configuration (Hot Standby Router Protocol)
Router(config)# interface GigabitEthernet0/0               # Enter interface configuration
Router(config-if)# standby 1 ip 10.10.10.1                 # Create group 1 with virtual IP
Router(config-if)# standby 1 priority 110                  # Set priority (higher is preferred)
Router(config-if)# standby 1 preempt                       # Enable preemption (return to active)
Router(config-if)# standby 1 preempt delay minimum 60      # Delay preemption by 60 seconds
Router(config-if)# standby 1 timers 5 15                   # Hello and dead timers (seconds)
Router(config-if)# standby 1 track 1 decrement 20          # Track object 1, reduce priority by 20
Router(config-if)# standby 1 authentication md5 key-string HSRP-KEY # MD5 authentication

# VRRP Configuration (Virtual Router Redundancy Protocol)
Router(config)# interface GigabitEthernet0/0               # Enter interface configuration
Router(config-if)# vrrp 1 ip 10.10.10.1                    # Create group 1 with virtual IP
Router(config-if)# vrrp 1 priority 110                     # Set priority (higher is preferred)
Router(config-if)# vrrp 1 preempt                          # Enable preemption
Router(config-if)# vrrp 1 timers advertise 5               # Advertisement timer (seconds)
Router(config-if)# vrrp 1 authentication md5 key-string VRRP-KEY # MD5 authentication

# GLBP Configuration (Gateway Load Balancing Protocol)
Router(config)# interface GigabitEthernet0/0               # Enter interface configuration
Router(config-if)# glbp 1 ip 10.10.10.1                    # Create group 1 with virtual IP
Router(config-if)# glbp 1 priority 110                     # Set priority (higher is preferred)
Router(config-if)# glbp 1 preempt                          # Enable preemption
Router(config-if)# glbp 1 timers 5 15                      # Hello and dead timers (seconds)
Router(config-if)# glbp 1 load-balancing round-robin       # Set load-balancing method
                                                           # Options: round-robin, weighted, host-dependent
Router(config-if)# glbp 1 weighting 100                    # Set weighting for load-balancing
Router(config-if)# glbp 1 authentication md5 key-string GLBP-KEY # MD5 authentication

# Object Tracking Configuration
Router(config)# track 1 interface GigabitEthernet0/1 line-protocol # Track interface status
Router(config)# track 2 ip route 0.0.0.0/0 reachability    # Track default route

# Verification Commands
Router# show standby                                       # Show HSRP status
Router# show standby brief                                 # Show HSRP summary
Router# show vrrp                                          # Show VRRP status
Router# show vrrp brief                                    # Show VRRP summary
Router# show glbp                                          # Show GLBP status
Router# show glbp brief                                    # Show GLBP summary
Router# show track                                         # Show tracked objects
```

---

## IP Services

### NAT Configuration
*Commands for Network Address Translation*

```
# Static NAT Configuration
Router(config)# interface GigabitEthernet0/0               # Outside interface
Router(config-if)# ip address 203.0.113.2 255.255.255.0    # Public IP address
Router(config-if)# ip nat outside                          # Designate as outside interface
Router(config)# interface GigabitEthernet0/1               # Inside interface
Router(config-if)# ip address 192.168.1.1 255.255.255.0    # Private IP address
Router(config-if)# ip nat inside                           # Designate as inside interface
Router(config)# ip nat inside source static 192.168.1.10 203.0.113.10  # One-to-one mapping

# Dynamic NAT Configuration
Router(config)# interface GigabitEthernet0/0               # Outside interface
Router(config-if)# ip nat outside                          # Designate as outside interface
Router(config)# interface GigabitEthernet0/1               # Inside interface
Router(config-if)# ip nat inside                           # Designate as inside interface
Router(config)# ip nat pool PUBLIC-POOL 203.0.113.20 203.0.113.30 netmask 255.255.255.0  # Define pool
Router(config)# access-list 1 permit 192.168.1.0 0.0.0.255  # Define ACL for translation
Router(config)# ip nat inside source list 1 pool PUBLIC-POOL  # Associate ACL with pool

# PAT (NAT Overload) Configuration
Router(config)# interface GigabitEthernet0/0               # Outside interface
Router(config-if)# ip nat outside                          # Designate as outside interface
Router(config)# interface GigabitEthernet0/1               # Inside interface
Router(config-if)# ip nat inside                           # Designate as inside interface
Router(config)# access-list 1 permit 192.168.1.0 0.0.0.255  # Define ACL for translation
Router(config)# ip nat inside source list 1 interface GigabitEthernet0/0 overload  # PAT config

# NAT for Overlapping Networks
Router(config)# ip nat inside source static network 10.1.1.0 10.2.2.0 /24  # Statically map network

# Verification and Troubleshooting Commands
Router# show ip nat translations                           # Show active translations
Router# show ip nat statistics                             # Show NAT statistics
Router# clear ip nat translation *                         # Clear all dynamic translations
Router# debug ip nat                                       # Enable NAT debugging
Router# undebug all                                        # Turn off all debugging

# Remove NAT Configuration
Router(config-if)# no ip nat outside                       # Remove outside designation
Router(config-if)# no ip nat inside                        # Remove inside designation
Router(config)# no ip nat inside source static 192.168.1.10 203.0.113.10  # Remove static NAT
Router(config)# no ip nat inside source list 1 pool PUBLIC-POOL  # Remove dynamic NAT
Router(config)# no ip nat inside source list 1 interface GigabitEthernet0/0 overload  # Remove PAT
```

### DHCP Configuration
*Commands for Dynamic Host Configuration Protocol*

```
# DHCP Server Configuration
Router(config)# ip dhcp excluded-address 192.168.1.1 192.168.1.10  # Exclude addresses from pool
Router(config)# ip dhcp pool MAIN-POOL                     # Create DHCP pool
Router(dhcp-config)# network 192.168.1.0 255.255.255.0     # Define network and subnet mask
Router(dhcp-config)# default-router 192.168.1.1            # Define default gateway
Router(dhcp-config)# dns-server 8.8.8.8 8.8.4.4            # Define DNS servers
Router(dhcp-config)# domain-name example.com               # Define domain name
Router(dhcp-config)# lease 7                               # Set lease time (days)
                                                           # Alternative formats: lease 0 12 30 (days hours minutes)

# Additional DHCP Options
Router(dhcp-config)# option 150 ip 192.168.1.10            # TFTP server (for VoIP)
Router(dhcp-config)# option 66 ascii "192.168.1.11"        # TFTP server name
Router(dhcp-config)# netbios-name-server 192.168.1.15      # WINS server
Router(dhcp-config)# netbios-node-type h-node              # NetBIOS node type

# DHCP Relay Configuration
Router(config)# interface GigabitEthernet0/1               # Client-facing interface
Router(config-if)# ip helper-address 10.1.1.10             # Forward DHCP to server

# DHCP Client Configuration
Router(config)# interface GigabitEthernet0/0               # WAN interface 
Router(config-if)# ip address dhcp                         # Obtain IP via DHCP
Router(config-if)# ip dhcp client client-id ascii "Router1" # Set client identifier 

# DHCP Verification and Troubleshooting
Router# show ip dhcp binding                               # Show address assignments
Router# show ip dhcp server statistics                     # Show DHCP statistics
Router# show ip dhcp pool                                  # Show pool configuration
Router# debug ip dhcp server events                        # Debug DHCP server
Router# undebug all                                        # Turn off debugging

# Client Verification
Router# show dhcp lease                                    # Show obtained DHCP lease
Router# show ip interface                                  # Verify interface configuration
Router# release dhcp interface GigabitEthernet0/0          # Release DHCP lease
Router# renew dhcp interface GigabitEthernet0/0            # Renew DHCP lease
```

### NTP Configuration
*Network Time Protocol configuration for time synchronization*

```
# NTP Server Configuration
Router(config)# ntp master 3                              # Configure as NTP server (stratum 3)
                                                          # Lower stratum = higher precedence

# NTP Client Configuration
Router(config)# ntp server 10.1.1.1                       # Configure primary NTP server
Router(config)# ntp server 10.1.1.2                       # Configure secondary NTP server
Router(config)# ntp update-calendar                       # Update hardware calendar
Router(config)# ntp authenticate                          # Enable NTP authentication
Router(config)# ntp authentication-key 1 md5 NTP-KEY      # Define authentication key
Router(config)# ntp trusted-key 1                         # Specify trusted key
Router(config)# ntp access-group serve-only 10            # Restrict NTP access
Router(config)# access-list 10 permit 10.1.0.0 0.0.255.255 # Define allowed networks

# Clock and Timezone Configuration
Router(config)# clock timezone EST -5                     # Set timezone (EST, -5 hours from UTC)
Router(config)# clock summer-time EDT recurring           # Configure Daylight Saving Time
Router# clock set 14:30:00 15 March 2023                  # Set system clock manually

# NTP Verification Commands
Router# show ntp associations                             # Show NTP peers
Router# show ntp status                                   # Show NTP synchronization status
Router# show clock                                        # Show current system time
Router# show calendar                                     # Show hardware calendar time
Router# debug ntp all                                     # Debug NTP operations
Router# undebug all                                       # Turn off debugging
```

### PoE (Power over Ethernet)
*Commands for configuring and managing Power over Ethernet*

```
# Basic PoE Configuration
Switch(config)# interface GigabitEthernet0/1              # Enter interface configuration
Switch(config-if)# power inline auto                      # Auto-detect and power devices (default)
Switch(config-if)# power inline never                     # Disable PoE on interface
Switch(config-if)# power inline consumption 8000          # Set max power (milliwatts)

# PoE Prioritization
Switch(config-if)# power inline port priority critical    # Set high priority
Switch(config-if)# power inline port priority high        # Set medium priority
Switch(config-if)# power inline port priority low         # Set low priority (default)

# PoE Policing Configuration
Switch(config-if)# power inline police                    # Enable power policing
Switch(config-if)# power inline police action log         # Log when power exceeds limit
Switch(config-if)# power inline police action errdisable  # Disable port when power exceeds
Switch(config)# errdisable recovery cause inline-power    # Enable auto recovery for violations
Switch(config)# errdisable recovery interval 300          # Set recovery interval (seconds)

# PoE Management
Switch(config)# power inline priority critical port       # Global port priority on power loss
Switch(config)# power inline power-management multi-mode  # Advanced power management
Switch(config)# power inline usage-threshold 85           # Set power usage threshold (%)

# PoE Verification Commands
Switch# show power inline                                 # Show all PoE interfaces
Switch# show power inline GigabitEthernet0/1              # Show specific interface
Switch# show power inline priority                        # Show by priority
Switch# show power inline consumption                     # Show actual power usage
Switch# show power inline policing                        # Show policing statistics
Switch# show errdisable recovery                          # Show recovery configuration
```

---

## Security Fundamentals

### Device Security Configuration
*Basic security configuration for Cisco devices*

```
# Privileged EXEC (Enable) Mode Security
Router(config)# enable secret Str0ngP@ss                 # Set encrypted enable password (recommended)
Router(config)# service password-encryption              # Encrypt other passwords in config
Router(config)# no service password-recovery             # Disable password recovery (caution!)

# Line Security Configuration
Router(config)# line console 0                           # Enter console line configuration
Router(config-line)# password Str0ngP@ss                 # Set console password
Router(config-line)# login                               # Enable password checking
Router(config-line)# exec-timeout 10 0                   # Timeout after 10 minutes, 0 seconds
Router(config-line)# logging synchronous                 # Prevent log messages disrupting input

# VTY (Telnet/SSH) Line Security
Router(config)# line vty 0 15                            # Configure all VTY lines
Router(config-line)# transport input ssh                 # Allow only SSH connections
Router(config-line)# transport output none               # Prevent outbound connections
Router(config-line)# access-class 10 in                  # Apply ACL for VTY access
Router(config-line)# login local                         # Use local user database
Router(config-line)# exec-timeout 5 0                    # Timeout after 5 minutes

# Local User Configuration
Router(config)# username admin privilege 15 secret Str0ngP@ss  # Create privileged user
Router(config)# username operator privilege 5 secret Op3r@t0r  # Create limited-privilege user
Router(config)# privilege exec level 5 show running-config     # Allow specific commands

# SSH Configuration
Router(config)# hostname Router1                         # Set hostname (required for SSH)
Router(config)# ip domain-name example.com               # Set domain name
Router(config)# crypto key generate rsa modulus 2048     # Generate RSA key (2048+ bits recommended)
Router(config)# ip ssh version 2                         # Use SSH version 2 only
Router(config)# ip ssh authentication-retries 3          # Set authentication retry limit
Router(config)# ip ssh time-out 60                       # Set authentication timeout

# AAA Configuration (Basic)
Router(config)# aaa new-model                            # Enable AAA
Router(config)# aaa authentication login default local    # Use local database for authentication
Router(config)# aaa authorization exec default local      # Use local database for authorization

# Secure Access Warnings
Router(config)# banner login #                          # Start login banner
Unauthorized access is prohibited and will be prosecuted.
#                                                        # End banner with same character

# Verification Commands
Router# show users                                       # Show connected users
Router# show ip ssh                                      # Show SSH server configuration
Router# show line                                        # Show line settings
Router# show running-config                              # Show current configuration
```

### Layer 2 Security Features
*Security features for Layer 2 switching*

```
# DHCP Snooping Configuration
Switch(config)# ip dhcp snooping                         # Enable DHCP snooping globally
Switch(config)# ip dhcp snooping vlan 10,20              # Enable for specific VLANs
Switch(config)# no ip dhcp snooping information option   # Disable option 82 (if needed)
Switch(config)# interface GigabitEthernet0/1             # Enter interface configuration
Switch(config-if)# ip dhcp snooping trust                # Configure as trusted interface

# Dynamic ARP Inspection (DAI)
Switch(config)# ip arp inspection vlan 10,20             # Enable ARP inspection for VLANs
Switch(config)# interface GigabitEthernet0/1             # Enter interface configuration
Switch(config-if)# ip arp inspection trust               # Configure as trusted interface
Switch(config)# ip arp inspection validate src-mac dst-mac ip # Validate ARP packets

# IP Source Guard
Switch(config)# interface GigabitEthernet0/2             # Enter interface configuration
Switch(config-if)# ip verify source                      # Enable source IP verification
Switch(config-if)# ip verify source port-security        # Enable source IP and MAC verification

# Storm Control
Switch(config)# interface GigabitEthernet0/2             # Enter interface configuration
Switch(config-if)# storm-control broadcast level 50.00    # Set broadcast threshold to 50%
Switch(config-if)# storm-control multicast level 40.00    # Set multicast threshold to 40%
Switch(config-if)# storm-control unicast level 30.00      # Set unknown unicast threshold to 30%
Switch(config-if)# storm-control action shutdown          # Shutdown port when threshold exceeded

# Private VLANs (Basic)
Switch(config)# vlan 100                                 # Create primary VLAN
Switch(config-vlan)# private-vlan primary                # Designate as primary VLAN
Switch(config)# vlan 101                                 # Create secondary VLAN
Switch(config-vlan)# private-vlan isolated               # Set as isolated VLAN
Switch(config)# vlan 102                                 # Create another secondary VLAN
Switch(config-vlan)# private-vlan community              # Set as community VLAN
Switch(config)# vlan 100                                 # Enter primary VLAN configuration
Switch(config-vlan)# private-vlan association 101,102    # Associate secondary VLANs

# VTP Security
Switch(config)# vtp mode transparent                      # Set to transparent mode (safest)
Switch(config)# vtp password StrongVTPPass                # Set VTP password if using server mode
Switch(config)# vtp version 3                             # Use VTP version 3 (more secure)

# Verification Commands
Switch# show ip dhcp snooping                            # Show DHCP snooping configuration
Switch# show ip dhcp snooping binding                    # Show DHCP bindings
Switch# show ip arp inspection                           # Show ARP inspection configuration
Switch# show ip verify source                            # Show IP source guard configuration
Switch# show storm-control                               # Show storm control configuration
Switch# show vlan private-vlan                           # Show private VLAN configuration
```

---

## System Management and Recovery

### File Management
*Commands for file operations and system management*

```
# File System Navigation
Router# dir                                              # List files in current directory
Router# dir flash:                                       # List files in flash memory
Router# cd flash:                                        # Change to flash directory
Router# pwd                                              # Show current directory
Router# show file systems                                # Show available file systems

# File Operations
Router# copy running-config startup-config               # Save current config to NVRAM
Router# copy running-config flash:backup-config          # Backup config to flash
Router# copy startup-config flash:backup-config          # Backup startup config to flash
Router# copy flash:backup-config running-config          # Restore config from flash
Router# delete flash:old-config                          # Delete file from flash
Router# rename flash:old-config flash:archive-config     # Rename file
Router# verify flash:ios-image                           # Verify file integrity

# File Transfer
Router# copy running-config tftp://10.1.1.1/router1-config  # Copy config to TFTP server
Router# copy tftp://10.1.1.1/router1-config running-config  # Restore from TFTP server
Router# copy flash:ios-image tftp://10.1.1.1/ios-image     # Backup IOS to TFTP
Router# copy tftp://10.1.1.1/new-ios-image flash:          # Download new IOS

# Configuration Management
Router# show running-config                              # Show current configuration
Router# show startup-config                              # Show saved configuration
Router# erase startup-config                             # Delete saved configuration
Router# copy running-config startup-config               # Save configuration
Router# write memory                                     # Save configuration (alternative)
Router# write erase                                      # Erase startup configuration
Router# reload                                           # Reboot the device
Router# reload in 10                                     # Schedule reload in 10 minutes
Router# reload cancel                                    # Cancel scheduled reload
```

### Password Recovery
*Commands and procedures for password recovery*

```
# Password Recovery Procedure
# Step 1: Connect console cable and restart router
# Press Ctrl+Break during boot to enter ROMMON mode

# Step 2: ROMMON Commands
rommon 1> confreg 0x2142                                # Set register to ignore startup config
rommon 2> reset                                         # Reboot the router

# Step 3: After Reboot
Router> enable                                          # Enter privileged mode (no password needed)
Router# copy startup-config running-config              # Load saved config (without passwords)
Router# configure terminal                              # Enter global config mode
Router(config)# enable secret new-password              # Set new enable password
Router(config)# line console 0                          # Enter console config
Router(config-line)# password new-console-password      # Set new console password
Router(config-line)# exit                               # Exit line config
Router(config)# line vty 0 15                           # Enter VTY config
Router(config-line)# password new-vty-password          # Set new VTY password
Router(config-line)# exit                               # Exit line config

# Step 4: Save Changes and Restore Normal Boot
Router(config)# config-register 0x2102                  # Restore normal boot mode
Router(config)# end                                     # Exit config mode
Router# copy running-config startup-config              # Save changes
Router# reload                                          # Reboot with normal settings

# Config Register Values
# 0x2102 - Normal boot mode (default)
# 0x2142 - Ignore startup-config on boot
# 0x2100 - Boot to ROM monitor
# 0x2101 - Boot from ROM
```

### IOS Management
*Commands for managing the Cisco IOS software*

```
# IOS Information
Router# show version                                    # Show IOS version and hardware info
Router# show flash:                                     # Show flash contents
Router# show bootvar                                    # Show boot variables
Router# show processes cpu                              # Show CPU utilization
Router# show processes memory                           # Show memory utilization

# Boot System Configuration
Router(config)# boot system flash:c2900-universalk9-mz.SPA.152-4.M3.bin  # Primary IOS
Router(config)# boot system flash:c2900-universalk9-mz.SPA.152-3.M2.bin  # Backup IOS
Router(config)# boot system tftp://10.1.1.1/ios-backup.bin               # TFTP backup

# IOS Installation and Upgrade
Router# copy tftp://10.1.1.1/new-ios.bin flash:         # Download new IOS
Router# verify /md5 flash:new-ios.bin                   # Verify MD5 checksum
Router(config)# boot system flash:new-ios.bin           # Set boot variable
Router# copy running-config startup-config              # Save configuration
Router# reload                                          # Reboot with new IOS

# License Management (IOS 15.x and later)
Router# show license                                    # Show license information
Router# license install stored-location-url             # Install license from file
Router# license boot module module-name technology-name # Activate license

# ROMMON Recovery (If Device Won't Boot)
# Connect console and enter ROMMON mode
rommon> IP_ADDRESS=10.1.1.2                            # Set temporary IP address
rommon> IP_SUBNET_MASK=255.255.255.0                   # Set subnet mask
rommon> DEFAULT_GATEWAY=10.1.1.1                       # Set default gateway
rommon> TFTP_SERVER=10.1.1.10                          # Set TFTP server IP
rommon> TFTP_FILE=ios-image.bin                        # Set IOS filename
rommon> tftpdnld                                       # Download and install IOS
```
