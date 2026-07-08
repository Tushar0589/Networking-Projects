# 🌐 Enterprise Network Infrastructure | CCNA Capstone Project

> **A comprehensive enterprise network simulation built using Cisco Packet Tracer that integrates routing, switching, network services, security, and monitoring technologies into a scalable hierarchical network architecture.**

![Cisco](https://img.shields.io/badge/Cisco-Packet%20Tracer-blue)
![CCNA](https://img.shields.io/badge/Level-CCNA-success)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)
![License](https://img.shields.io/badge/License-MIT-orange)

---

# 📖 Overview

This project simulates a **real-world enterprise network** based on Cisco's **Three-Tier Hierarchical Network Design Model**. It combines almost every major CCNA networking technology into a single production-like infrastructure.

The network includes:

- Internet (ISP) connectivity
- Enterprise routing
- Layer-3 switching
- Department-based VLAN segmentation
- Dynamic routing
- Network services
- Enterprise security
- Centralized monitoring
- Secure device management

This project was created to demonstrate practical networking skills expected from an entry-level **Network Engineer**, **NOC Engineer**, or **Infrastructure Engineer**.

---

# 🏢 Network Architecture

```
                          Internet
                              │
                             ISP
                              │
                             BGP
                              │
                       Edge Router
                              │
                     Firewall (ACL)
                              │
                     Core Layer Switch (L3)
                ┌──────────┼──────────┐
                │          │          │
         Distribution Distribution Distribution
             Switch       Switch        Switch
                │            │            │
            Access       Access      Access
            Switch       Switch      Switch
                │            │            │
      PCs • Laptops • Printers • Servers
```

---

# 🎯 Project Objectives

- Design an enterprise network architecture
- Implement VLAN-based network segmentation
- Configure Layer 2 and Layer 3 switching
- Configure OSPF dynamic routing
- Simulate ISP connectivity using BGP
- Configure DHCP and DHCP Relay
- Implement DNS services
- Configure NAT and PAT
- Secure the network using ACLs
- Configure SSH for secure remote access
- Enable Syslog for centralized logging
- Configure CDP and LLDP
- Verify complete network connectivity

---

# 🖥️ Network Devices

| Device | Quantity |
|---------|---------:|
| ISP Router | 1 |
| Edge Router | 1 |
| Core Layer 3 Switch | 1 |
| Distribution Switches | 3 |
| Access Switches | Multiple |
| DHCP Server | 1 |
| DNS Server | 1 |
| Syslog Server | 1 |
| PCs | Multiple |
| Servers | Multiple |

---

# ⚙️ Technologies Implemented

## Layer 2 Technologies

- VLANs
- VLSM
- 802.1Q Trunking
- Spanning Tree Protocol (STP)

---

## Layer 3 Technologies

- Inter-VLAN Routing
- OSPF
- BGP
- Default Routing

---

## Network Services

- DHCP
- DHCP Relay
- DNS

---

## Security

- ACL
- SSH
- NAT
- PAT

---

## Monitoring & Management

- Syslog
- CDP
- LLDP

---

# 🏢 VLAN Design

| VLAN ID | Department |
|----------|------------|
| 10 | HR |
| 20 | Sales |
| 30 | Finance |
| 40 | IT |
| 50 | Management |
| 60 | Servers |
| 99 | Management VLAN |

---

# 🌍 IP Addressing Plan

Example addressing scheme:

| Department | Network |
|------------|----------------|
| HR | 192.168.10.0/24 |
| Sales | 192.168.20.0/24 |
| Finance | 192.168.30.0/24 |
| IT | 192.168.40.0/24 |
| Servers | 192.168.50.0/24 |
| Management | 192.168.99.0/24 |
| WAN | 10.10.10.0/30 |

---

# 🔧 Features

## Routing

- OSPF Dynamic Routing
- BGP Internet Connectivity
- Default Routes
- Inter-VLAN Routing

---

## Switching

- VLAN Configuration
- Access Ports
- Trunk Ports
- STP
- Broadcast Domain Segmentation

---

## Services

- DHCP Pools
- DHCP Relay
- DNS Server

---

## Security

- Standard ACLs
- Extended ACLs
- NAT
- PAT
- SSH Remote Login

---

## Monitoring

- Centralized Syslog Server
- Cisco Discovery Protocol (CDP)
- Link Layer Discovery Protocol (LLDP)

---

# 🛠️ Configurations Included

### Layer 2

- VLAN Creation
- Trunk Configuration
- Access Port Assignment
- STP Configuration

### Layer 3

- OSPF Configuration
- BGP Configuration
- Inter-VLAN Routing

### Services

- DHCP
- DHCP Relay
- DNS

### Security

- ACL Configuration
- NAT
- PAT
- SSH

### Monitoring

- Syslog
- CDP
- LLDP

---

# 🧪 Verification

## Routing

```bash
show ip route
show ip ospf neighbor
show ip bgp summary
```

---

## Switching

```bash
show vlan brief
show interfaces trunk
show spanning-tree
```

---

## DHCP

```bash
show ip dhcp binding
show ip dhcp pool
```

---

## NAT

```bash
show ip nat translations
show ip nat statistics
```

---

## SSH

```bash
show ip ssh
show users
```

---

## Syslog

Verified:

- Interface Up Events
- Interface Down Events
- Login Attempts
- Configuration Changes

---

## CDP

```bash
show cdp neighbors
show cdp neighbors detail
```

---

## LLDP

```bash
show lldp neighbors
show lldp neighbors detail
```

---

# 📂 Repository Structure

```
Enterprise-Network/
│
├── Enterprise-Network.pkt
├── README.md
├── LICENSE
│
├── configs/
│   ├── Edge-Router.txt
│   ├── Core-L3-Switch.txt
│   ├── Distribution-Switches.txt
│   ├── Access-Switches.txt
│   ├── DHCP-Server.txt
│   ├── DNS-Server.txt
│   └── Syslog-Server.txt
│
├── images/
│   ├── network-topology.png
│   ├── vlan-config.png
│   ├── ospf-neighbor.png
│   ├── bgp-summary.png
│   ├── dhcp.png
│   ├── nat.png
│   ├── acl.png
│   ├── ssh.png
│   ├── syslog.png
│   ├── cdp.png
│   ├── lldp.png
│   └── ping-test.png
│
└── documentation/
    ├── Enterprise-Network-Design.pdf
    ├── IP-Addressing.xlsx
    └── Network-Diagram.pdf
```

---

# 📸 Suggested Screenshots

Include screenshots of:

- Enterprise Network Topology
- VLAN Configuration
- Trunk Configuration
- OSPF Neighbors
- BGP Summary
- Routing Table
- DHCP Lease Table
- NAT Translation Table
- ACL Configuration
- SSH Login
- Syslog Server Logs
- CDP Neighbors
- LLDP Neighbors
- Successful End-to-End Ping Tests

---

# 📚 CCNA Concepts Covered

### Routing

- OSPF
- BGP
- Default Routing
- Route Advertisement

### Switching

- VLANs
- VLSM
- Trunking
- STP
- Inter-VLAN Routing

### Infrastructure Services

- DHCP
- DHCP Relay
- DNS

### Security

- ACL
- NAT
- PAT
- SSH

### Monitoring

- Syslog
- CDP
- LLDP

### Troubleshooting

- Connectivity Testing
- Route Verification
- VLAN Troubleshooting
- DHCP Validation
- NAT Verification
- Syslog Analysis
- SSH Connectivity

---

# 🎓 Learning Outcomes

By completing this project, I gained hands-on experience in:

- Designing enterprise-scale network infrastructures
- Implementing Cisco's hierarchical network model
- Configuring enterprise routing and switching
- Deploying OSPF and BGP for dynamic routing
- Segmenting networks using VLANs and VLSM
- Configuring essential network services such as DHCP, DHCP Relay, and DNS
- Securing networks with ACLs, NAT/PAT, and SSH
- Monitoring and troubleshooting enterprise devices using Syslog, CDP, and LLDP
- Validating end-to-end connectivity and resolving network issues

---

# 💼 Skills Demonstrated

- Enterprise Network Design
- Routing & Switching
- Cisco IOS CLI
- VLAN Implementation
- OSPF
- BGP
- DHCP
- DNS
- NAT & PAT
- ACL Configuration
- STP
- SSH
- Syslog
- CDP
- LLDP
- Network Troubleshooting
- Infrastructure Management

---

# 🚀 Future Enhancements

- HSRP Gateway Redundancy
- EtherChannel
- IPv6 Deployment
- SNMP Monitoring
- NetFlow Analysis
- QoS Implementation
- VPN Connectivity
- Cisco ASA Firewall
- Wireless LAN Controller (WLC)
- MPLS
- SD-WAN
- AAA Authentication (RADIUS/TACACS+)

---

# 👨‍💻 Author

**Tushar Patel**

### 📫 Connect with Me

- **LinkedIn:** https://www.linkedin.com/in/tushar-patel-s/
- **GitHub:** https://github.com/Tushar0589

---

# ⭐ If you found this project useful

If this project helped you or inspired your learning, please consider giving it a ⭐ on GitHub.

Contributions, suggestions, and feedback are always welcome!
