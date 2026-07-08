# 🏢 Departmental LAN with VLANs using Cisco Packet Tracer

A beginner-friendly networking project that demonstrates how to design and configure a **Departmental Local Area Network (LAN)** using **Virtual Local Area Networks (VLANs)** in **Cisco Packet Tracer**. The project simulates a small organization where different departments are logically separated to improve network security, reduce broadcast traffic, and enable controlled communication through Inter-VLAN Routing.

---

## 📖 Project Overview

In modern enterprise networks, departments are often separated into different VLANs to improve security, performance, and network management.

This project creates two departmental VLANs:

- **HR Department**
- **Sales Department**

Each department has its own broadcast domain, preventing direct communication between them unless traffic is routed through a router using **Router-on-a-Stick (ROAS)**.

---

## 🎯 Objectives

- Design a departmental LAN
- Create multiple VLANs
- Assign switch ports to VLANs
- Configure trunk links
- Implement Router-on-a-Stick
- Enable controlled Inter-VLAN communication
- Verify network connectivity
- Understand VLAN security and broadcast domains

---

## 🏗️ Network Topology

The network consists of:

- 1 Cisco Router
- 1 Cisco Layer 2 Switch
- 4 Desktop PCs
  - PC1 (HR)
  - PC2 (HR)
  - PC3 (Sales)
  - PC4 (Sales)

---

## ⚙️ Technologies Used

- Cisco Packet Tracer
- Cisco Router
- Cisco Switch
- VLAN Configuration
- IEEE 802.1Q Trunking
- Router-on-a-Stick (ROAS)
- IPv4 Addressing
- Subnetting
- Inter-VLAN Routing

---

## ✨ Features

- Department-wise VLAN Segmentation
- Access Port Configuration
- Trunk Port Configuration
- Inter-VLAN Routing
- Logical Network Isolation
- Broadcast Domain Separation
- Successful Connectivity Testing

---

## 📂 VLAN Structure

| VLAN ID | Department |
|----------|------------|
| 10 | HR |
| 20 | Sales |

---

## 🌍 IP Addressing

Example IP addressing scheme:

| VLAN | Network | Gateway |
|-------|----------|----------|
| VLAN 10 (HR) | 192.168.10.0/24 | 192.168.10.1 |
| VLAN 20 (Sales) | 192.168.20.0/24 | 192.168.20.1 |

---

## 🔧 Configuration Included

- Basic Router Configuration
- Basic Switch Configuration
- VLAN Creation
- VLAN Port Assignment
- Switchport Access Mode
- Trunk Port Configuration
- Router Sub-Interfaces
- IEEE 802.1Q Encapsulation
- Default Gateway Configuration
- Connectivity Verification

---

## 🔄 Communication Flow

Without Inter-VLAN Routing:

```
HR PC  ❌  Sales PC
```

After Router-on-a-Stick Configuration:

```
HR PC
   │
Switch
   │
Trunk Link
   │
Router
   │
Switch
   │
Sales PC
```

Traffic between departments is only possible after it is routed through the router.

---

## 🧪 Testing

The following tests were performed successfully:

✅ HR PC ↔ HR PC Communication

✅ Sales PC ↔ Sales PC Communication

✅ HR PC → Sales PC (Fails before routing)

✅ HR PC → Sales PC (Succeeds after Router-on-a-Stick configuration)

✅ Gateway Reachability

✅ Ping Verification

---

## 📸 Project Screenshots

Store screenshots inside the **images/** directory.

Example:

```
images/
│
├── topology.png
├── vlan-creation.png
├── switch-config.png
├── router-config.png
├── trunk-port.png
├── ping-success.png
└── inter-vlan-routing.png
```

---

## 📁 Repository Structure

```
Departmental-LAN-VLAN/
│
├── Departmental-LAN.pkt
├── README.md
├── configurations/
│   ├── router-config.txt
│   ├── switch-config.txt
│
├── images/
│   ├── topology.png
│   ├── vlan-config.png
│   ├── router-cli.png
│   ├── switch-cli.png
│   └── ping-test.png
│
└── documentation/
    └── Network-Design.pdf
```

---

## 📚 Concepts Practiced

- VLAN Fundamentals
- Broadcast Domains
- Access Ports
- Trunk Ports
- IEEE 802.1Q
- Router-on-a-Stick
- Inter-VLAN Routing
- IPv4 Addressing
- Subnetting
- Network Segmentation
- Cisco IOS Configuration
- Network Troubleshooting

---

## 🚀 Learning Outcomes

Through this project, I gained hands-on experience in:

- Designing a departmental enterprise network
- Configuring VLANs on Cisco switches
- Assigning switch ports to specific VLANs
- Configuring trunk links using IEEE 802.1Q
- Implementing Router-on-a-Stick (ROAS)
- Understanding broadcast domain isolation
- Enabling communication between VLANs
- Troubleshooting VLAN connectivity issues

---

## 🛠️ Future Improvements

- DHCP for Each VLAN
- Access Control Lists (ACLs)
- Port Security
- SSH Remote Management
- Multiple Switches using VTP
- EtherChannel
- Dynamic Routing
- Wireless VLAN Integration
- Layer 3 Switch Implementation
- Network Monitoring using SNMP

---

## 💼 Real-World Applications

This project demonstrates concepts commonly used in enterprise networks, including:

- Office Network Segmentation
- Department-Based Security
- Enterprise LAN Design
- Campus Networks
- Corporate Network Infrastructure
- Access Layer Switching

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
