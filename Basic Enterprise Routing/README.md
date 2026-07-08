# 🌍 Basic Enterprise Routing using OSPF | Cisco Packet Tracer

A beginner-friendly networking project that demonstrates how to connect two branch offices using **Dynamic Routing** in **Cisco Packet Tracer**. This project simulates a real-world enterprise network where two separate office LANs communicate through routers using the **Open Shortest Path First (OSPF)** routing protocol.

Instead of manually configuring static routes, OSPF automatically discovers and exchanges routing information, making the network more scalable, efficient, and easier to manage.

---

## 📖 Project Overview

Enterprise organizations often have multiple office locations that need to communicate securely and efficiently. Dynamic routing protocols like **OSPF** allow routers to automatically learn and update routes between different networks.

In this project, two offices are connected through routers, enabling seamless communication between devices in separate LANs without configuring static routes.

---

## 🎯 Objectives

- Design a multi-office enterprise network
- Configure LAN connectivity for each office
- Connect routers using Ethernet or Serial links
- Configure Dynamic Routing using OSPF
- Advertise connected networks
- Verify automatic route learning
- Test end-to-end communication between offices

---

## 🏗️ Network Topology

The network consists of:

- 2 Cisco Routers
- 2 Cisco Layer 2 Switches
- 4 Desktop PCs
  - Office A
    - PC1
    - PC2
  - Office B
    - PC3
    - PC4

---

## ⚙️ Technologies Used

- Cisco Packet Tracer
- Cisco Routers
- Cisco Switches
- OSPF Routing Protocol
- IPv4 Addressing
- Subnetting
- Ethernet / Serial WAN Links
- Cisco IOS CLI

---

## ✨ Features

- Multi-Office Network Design
- Dynamic Route Discovery
- OSPF Configuration
- Automatic Route Updates
- End-to-End Connectivity
- Scalable Enterprise Routing
- Router-to-Router Communication

---

## 🌍 IP Addressing

Example addressing scheme:

| Network | Address |
|----------|----------|
| Office A LAN | 192.168.10.0/24 |
| Office B LAN | 192.168.20.0/24 |
| Router Link | 10.10.10.0/30 |

---

## 🖧 Network Topology Diagram

```
        OFFICE A                          OFFICE B

    PC1        PC2                  PC3         PC4
      │          │                    │           │
      └──────┬───┘                    └────┬──────┘
             │                             │
          Switch A                     Switch B
             │                             │
          Router A =================== Router B
                Ethernet / Serial Link
```

---

## 🔧 Configuration Included

- Basic Router Configuration
- Basic Switch Configuration
- Interface IP Address Configuration
- OSPF Process Configuration
- Network Advertisement
- Router-to-Router Connectivity
- LAN Configuration
- Default Gateway Configuration
- Connectivity Verification

---

## 🛣️ OSPF Configuration

The following OSPF concepts are implemented:

- OSPF Process ID
- Network Statements
- Wildcard Masks
- Neighbor Discovery
- Route Advertisement
- Automatic Route Learning
- Routing Table Updates

---

## 🔄 Communication Flow

Before OSPF:

```
Office A ❌ Office B

No route available between networks.
```

After OSPF Configuration:

```
Office A
     │
 Router A
     │
===== OSPF =====
     │
 Router B
     │
Office B

Communication Successful ✅
```

---

## 🧪 Testing

The following tests were completed successfully:

✅ Router-to-Router Connectivity

✅ OSPF Neighbor Relationship

✅ Automatic Route Learning

✅ Routing Table Verification (`show ip route`)

✅ OSPF Neighbor Verification (`show ip ospf neighbor`)

✅ PC-to-PC Communication

✅ Successful Ping between Office A and Office B

---

## 📸 Project Screenshots

Store screenshots inside the **images/** directory.

Example:

```
images/
│
├── topology.png
├── ospf-config-router1.png
├── ospf-config-router2.png
├── show-ip-route.png
├── show-ip-ospf-neighbor.png
├── ping-test.png
└── network-topology.png
```

---

## 📁 Repository Structure

```
Basic-Enterprise-Routing/
│
├── Enterprise-Routing.pkt
├── README.md
├── configurations/
│   ├── RouterA-config.txt
│   ├── RouterB-config.txt
│
├── images/
│   ├── topology.png
│   ├── ospf-router1.png
│   ├── ospf-router2.png
│   ├── routing-table.png
│   └── ping-success.png
│
└── documentation/
    └── Network-Design.pdf
```

---

## 📚 Concepts Practiced

- Enterprise Network Design
- Dynamic Routing
- OSPF Fundamentals
- Router Configuration
- Switch Configuration
- IPv4 Addressing
- Subnetting
- Routing Tables
- OSPF Neighbor Discovery
- Cisco IOS CLI
- Network Troubleshooting

---

## 🚀 Learning Outcomes

Through this project, I gained hands-on experience in:

- Designing a multi-office enterprise network
- Configuring routers and switches
- Implementing OSPF dynamic routing
- Advertising connected networks
- Verifying routing tables and OSPF neighbors
- Understanding automatic route learning
- Troubleshooting routing and connectivity issues
- Simulating enterprise-level routing scenarios

---

## 🛠️ Future Improvements

- Multi-Area OSPF
- EIGRP Implementation
- Route Summarization
- Route Redistribution
- Access Control Lists (ACLs)
- DHCP Configuration
- NAT/PAT
- HSRP for Redundancy
- WAN Redundancy
- IPv6 Routing
- Network Monitoring using SNMP

---

## 💼 Real-World Applications

This project demonstrates networking concepts commonly used in enterprise environments, including:

- Enterprise Branch Office Connectivity
- Corporate WAN Networks
- Campus Networks
- Dynamic Route Management
- Scalable Network Infrastructure
- ISP and Enterprise Routing
- Multi-Site Business Networks

---

## 👨‍💻 Author

**Tushar Patel**

### Connect with me

- **LinkedIn:** https://www.linkedin.com/in/tushar-patel-s/
- **GitHub:** https://github.com/Tushar0589

---

## ⭐ Support

If you found this project useful, consider giving this repository a ⭐ on GitHub.

Suggestions, feedback, and contributions are always welcome!
