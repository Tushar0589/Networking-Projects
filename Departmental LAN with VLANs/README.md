# 🏢 Departmental LAN with VLANs using Cisco Packet Tracer

![Cisco Packet Tracer](https://img.shields.io/badge/Cisco%20Packet%20Tracer-1BA0D7?style=for-the-badge\&logo=cisco\&logoColor=white)
![Networking](https://img.shields.io/badge/Networking-VLAN%20%7C%20ROAS-blue?style=for-the-badge)
![IPv4](https://img.shields.io/badge/IPv4-Addressing-orange?style=for-the-badge)
![CCNA](https://img.shields.io/badge/CCNA-Lab-red?style=for-the-badge)

A hands-on Cisco Packet Tracer project demonstrating the design and configuration of a small **departmental enterprise LAN** using **VLAN segmentation, IEEE 802.1Q trunking, and Router-on-a-Stick (ROAS)** for Inter-VLAN Routing.

The lab models two departments — **HR** and **Sales** — on a Layer 2 switch. Devices are placed into separate VLANs and IP subnets, while a Cisco router provides Layer 3 communication between the networks.

> 🎯 **Project Goal:** Build a segmented departmental LAN, configure VLANs and trunking, implement Router-on-a-Stick, and verify end-to-end connectivity using Cisco IOS and ping tests.

---

## 📖 Project Overview

In an enterprise LAN, different departments are commonly separated into logical networks to create independent broadcast domains and simplify network administration.

This project implements:

* **VLAN 10 — HR Department**
* **VLAN 20 — Sales Department**
* A **Cisco 2960 Layer 2 switch**
* A **Cisco router** using Router-on-a-Stick
* **IEEE 802.1Q trunking** between the switch and router
* Static IPv4 addressing for end devices
* Connectivity and configuration verification using Cisco IOS commands

Each VLAN represents a separate **broadcast domain**. Communication between VLANs requires a Layer 3 device, which in this project is the Cisco router.

---

## 🎯 Objectives

* Design a departmental LAN topology
* Create and name multiple VLANs
* Assign switch access ports to departments
* Configure an IEEE 802.1Q trunk link
* Configure Router-on-a-Stick
* Configure router subinterfaces
* Configure default gateways
* Enable Inter-VLAN Routing
* Verify Layer 2 and Layer 3 connectivity
* Practice Cisco IOS configuration
* Troubleshoot VLAN and routing connectivity

---

## 🏗️ Network Topology

### Logical Topology

```text
                              ┌──────────────────┐
                              │       R1         │
                              │  Cisco Router    │
                              │                  │
                              │ G0/0.10  VLAN10 │
                              │ G0/0.20  VLAN20 │
                              └────────┬─────────┘
                                       │
                              802.1Q TRUNK
                                       │
                              ┌────────┴────────┐
                              │       SW1       │
                              │  Cisco 2960     │
                              └─┬────┬────┬────┬┘
                                │    │    │    │
                               PC1  PC2  PC3  PC4
                                │    │    │    │
                               HR   HR Sales Sales
                                │    │    │    │
                              VLAN 10      VLAN 20
```

### Network Components

| Device         | Quantity | Model      | Purpose            |
| -------------- | -------: | ---------- | ------------------ |
| Router         |        1 | Cisco 1941 | Inter-VLAN Routing |
| Layer 2 Switch |        1 | Cisco 2960 | VLAN segmentation  |
| Desktop PC     |        4 | PC-PT      | End-user devices   |

---

## 🔌 Port Mapping

| Device | Interface | Connected To | Role           |
| ------ | --------- | ------------ | -------------- |
| R1     | G0/0      | SW1 G0/1     | Router trunk   |
| SW1    | G0/1      | R1 G0/0      | 802.1Q trunk   |
| SW1    | fa0/2     | PC1          | VLAN 10 access |
| SW1    | fa0/3     | PC2          | VLAN 10 access |
| SW1    | fa0/4     | PC3          | VLAN 20 access |
| SW1    | Fa0/5     | PC4          | VLAN 20 access |

---

## 📂 VLAN Structure

| VLAN ID | Department | Purpose            | Network         |
| ------: | ---------- | ------------------ | --------------- |
|      10 | HR         | HR user devices    | 192.168.10.0/24 |
|      20 | Sales      | Sales user devices | 192.168.20.0/24 |

### VLAN Design

```text
VLAN 10
   │
   └── HR Department
       192.168.10.0/24


VLAN 20
   │
   └── Sales Department
       192.168.20.0/24
```

---

## 🌍 IP Addressing Plan

| Device | Department | VLAN | IP Address    | Subnet Mask   | Default Gateway |
| ------ | ---------- | ---: | ------------- | ------------- | --------------- |
| PC1    | HR         |   10 | 192.168.10.11 | 255.255.255.0 | 192.168.10.1    |
| PC2    | HR         |   10 | 192.168.10.12 | 255.255.255.0 | 192.168.10.1    |
| PC3    | Sales      |   20 | 192.168.20.11 | 255.255.255.0 | 192.168.20.1    |
| PC4    | Sales      |   20 | 192.168.20.12 | 255.255.255.0 | 192.168.20.1    |

### Router Gateway Addresses

| Router Interface | VLAN | IP Address      |
| ---------------- | ---: | --------------- |
| G0/0.10          |   10 | 192.168.10.1/24 |
| G0/0.20          |   20 | 192.168.20.1/24 |

---

## ⚙️ Technologies Used

* Cisco Packet Tracer
* Cisco IOS CLI
* VLANs
* IEEE 802.1Q Trunking
* Router-on-a-Stick
* Inter-VLAN Routing
* IPv4 Addressing
* /24 Subnetting
* Access Ports
* Broadcast Domain Segmentation
* Network Troubleshooting

---

# 🔧 Configuration Walkthrough

## 1. Create the Topology

Place the following devices in Cisco Packet Tracer:

* 1 × Cisco 1941 Router
* 1 × Cisco 2960 Switch
* 4 × PCs

Rename them:

```text
R1
SW1
PC1
PC2
PC3
PC4
```

Connect them using **Copper Straight-Through** cables:

```text
R1 G0/0    → SW1 G0/1

SW1 fa0/2  → PC1
SW1 fa0/3  → PC2
SW1 fa0/4  → PC3
SW1 fa0/5  → PC4
```

---

# 2. Configure PC IP Addresses

Navigate to:

```text
PC
→ Desktop
→ IP Configuration
```

### PC1 — HR

```text
IP Address:      192.168.10.11
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.10.1
```

### PC2 — HR

```text
IP Address:      192.168.10.12
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.10.1
```

### PC3 — Sales

```text
IP Address:      192.168.20.11
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.20.1
```

### PC4 — Sales

```text
IP Address:      192.168.20.12
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.20.1
```

---

# 3. Configure the Switch

Open:

```text
SW1 → CLI
```

Enter privileged mode:

```cisco
enable
```

Enter configuration mode:

```cisco
configure terminal
```

Set hostname:

```cisco
hostname SW1
```

---

## Create VLAN 10 — HR

```cisco
vlan 10
name HR
exit
```

---

## Create VLAN 20 — Sales

```cisco
vlan 20
name SALES
exit
```

---

## Assign HR Ports

PC1 and PC2 are connected to fa0/2 and fa0/3.

```cisco
interface range fa0/2-3
switchport mode access
switchport access vlan 10
exit
```

---

## Assign Sales Ports

PC3 and PC4 are connected to fa0/4 and fa0/5.

```cisco
interface range fa0/4-5
switchport mode access
switchport access vlan 20
exit
```

---

## Configure Trunk Port

The switch connects to the router through G0/1.

```cisco
interface gigabitEthernet 0/1
switchport mode trunk
exit
```

---

## Save Switch Configuration

```cisco
end
copy running-config startup-config
```

Press **Enter** when prompted for the destination filename.

---

# 4. Verify Switch Configuration

### Verify VLANs

```cisco
show vlan brief
```

Expected:

```text
VLAN 10 → fa0/2, fa0/3
VLAN 20 → fa0/4, fa0/5
```

### Verify Trunk

```cisco
show interfaces trunk
```

Expected:

```text
Gi0/1
```

should be operating as a trunk.

### Verify MAC Address Table

```cisco
show mac address-table
```

---

# 5. Configure Router-on-a-Stick

Open:

```text
R1 → CLI
```

Enter:

```cisco
enable
configure terminal
hostname R1
```

---

## Enable Router Interface

```cisco
interface gigabitEthernet 0/0
no shutdown
exit
```

The physical interface acts as the parent interface for the VLAN subinterfaces.

---

## Configure VLAN 10 Subinterface

```cisco
interface gigabitEthernet 0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0
exit
```

This interface acts as the default gateway for HR.

```text
G0/0.10
     │
     └── VLAN 10
          192.168.10.1
```

---

## Configure VLAN 20 Subinterface

```cisco
interface gigabitEthernet 0/0.20
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0
exit
```

This interface acts as the default gateway for Sales.

```text
G0/0.20
     │
     └── VLAN 20
          192.168.20.1
```

---

## Save Router Configuration

```cisco
end
copy running-config startup-config
```

---

# 6. Verify Router Configuration

### Check Interface Status

```cisco
show ip interface brief
```

Expected:

```text
GigabitEthernet0/0.10
192.168.10.1

GigabitEthernet0/0.20
192.168.20.1
```

### Check Routing Table

```cisco
show ip route
```

Expected connected networks:

```text
192.168.10.0/24
192.168.20.0/24
```

### Check Running Configuration

```cisco
show running-config
```

Look for:

```cisco
interface GigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0

interface GigabitEthernet0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0
```

---

# 🔄 Inter-VLAN Routing

## Before Router-on-a-Stick

```text
PC1 - VLAN 10
     │
     │
    SW1
     │
     X
     │
PC3 - VLAN 20
```

The Layer 2 switch keeps VLAN 10 and VLAN 20 separate.

---

## After Router-on-a-Stick

```text
PC1
 │
 │ VLAN 10
 ▼
SW1
 │
 │ 802.1Q Trunk
 ▼
R1 G0/0.10
 │
 │ Layer 3 Routing
 ▼
R1 G0/0.20
 │
 │ 802.1Q Trunk
 ▼
SW1
 │
 │ VLAN 20
 ▼
PC3
```

Traffic between the two VLANs is routed through R1.

---

# 🧪 Connectivity Testing

## Test 1 — HR to HR

From PC1:

```cmd
ping 192.168.10.12
```

Expected:

```text
PC1 → PC2
VLAN 10 → VLAN 10
```

Result:

```text
✅ Successful
```

---

## Test 2 — Sales to Sales

From PC3:

```cmd
ping 192.168.20.12
```

Expected:

```text
PC3 → PC4
VLAN 20 → VLAN 20
```

Result:

```text
✅ Successful
```

---

## Test 3 — HR Gateway

From PC1:

```cmd
ping 192.168.10.1
```

Result:

```text
✅ Successful
```

---

## Test 4 — Sales Gateway

From PC3:

```cmd
ping 192.168.20.1
```

Result:

```text
✅ Successful
```

---

## Test 5 — Inter-VLAN Routing

From PC1:

```cmd
ping 192.168.20.11
```

This tests:

```text
VLAN 10 → Router → VLAN 20
```

Result:

```text
✅ Successful
```

---

## Test 6 — Reverse Inter-VLAN Routing

From PC3:

```cmd
ping 192.168.10.11
```

This tests:

```text
VLAN 20 → Router → VLAN 10
```

Result:

```text
✅ Successful
```

---

# 🔍 Verification Commands

## Switch Commands

```cisco
show vlan brief
```

```cisco
show interfaces trunk
```

```cisco
show interfaces status
```

```cisco
show mac address-table
```

```cisco
show running-config
```

---

## Router Commands

```cisco
show ip interface brief
```

```cisco
show ip route
```

```cisco
show running-config
```

---

## PC Commands

```cmd
ipconfig
```

```cmd
ping <destination-ip>
```

---

# 🛠️ Troubleshooting

| Problem                   | Possible Cause               | Solution                      |
| ------------------------- | ---------------------------- | ----------------------------- |
| PC cannot reach gateway   | Incorrect IP/gateway         | Check PC IP configuration     |
| VLAN missing              | VLAN not created             | Run `show vlan brief`         |
| PC assigned to wrong VLAN | Incorrect access port        | Check `show vlan brief`       |
| Trunk not working         | Port not configured as trunk | Check `show interfaces trunk` |
| Router subinterface down  | Parent interface disabled    | Use `no shutdown` on G0/0     |
| Inter-VLAN ping fails     | Incorrect VLAN ID            | Check `encapsulation dot1Q`   |
| Inter-VLAN ping fails     | Wrong gateway                | Verify PC default gateway     |
| Same-VLAN ping fails      | Wrong IP/subnet              | Check PC addressing           |
| No MAC address learned    | Link/traffic issue           | Check cables and interfaces   |

---

# 📸 Project Screenshots

The following screenshots are recommended for documenting the project.

## 1. Network Topology

/images/Topology.png
```text
R1
SW1
PC1
PC2
PC3
PC4
```

Recommended filename:

```text
images/topology.png
```

---

## 2. VLAN Configuration

Run:

```cisco
show vlan brief
```

Capture VLAN 10 and VLAN 20.

Recommended filename:

```text
images/vlan-config.png
```

---

## 3. Switch Port Assignment

Capture the output showing:

```text
VLAN 10 → fa0/3, fa0/3
VLAN 20 → fa0/4, fa0/5
```

Recommended filename:

```text
images/switch-vlan-ports.png
```

---

## 4. Trunk Configuration

Run:

```cisco
show interfaces trunk
```

Capture the trunk interface:

```text
Gi0/1
```

Recommended filename:

```text
images/trunk-port.png
```

---

## 5. Router-on-a-Stick Configuration

Run:

```cisco
show running-config
```

Capture:

```text
G0/0.10
encapsulation dot1Q 10

G0/0.20
encapsulation dot1Q 20
```

Recommended filename:

```text
images/router-cli.png
```

---

## 6. Router Interface Verification

Run:

```cisco
show ip interface brief
```

Capture:

```text
G0/0.10 → 192.168.10.1
G0/0.20 → 192.168.20.1
```

Recommended filename:

```text
images/router-interface.png
```

---

## 7. Inter-VLAN Ping

From PC1:

```cmd
ping 192.168.20.11
```

Capture the successful replies.

Recommended filename:

```text
images/inter-vlan-ping.png
```

⭐ **This is one of the most important screenshots.**

---

## 8. Packet Flow

Use **Simulation Mode** in Packet Tracer and generate traffic from PC1 to PC3.

Show the packet traveling through:

```text
PC1
 ↓
SW1
 ↓
R1
 ↓
SW1
 ↓
PC3
```

Recommended filename:

```text
images/inter-vlan-routing.png
```

---

# 📁 Recommended Repository Structure

```text
Departmental LAN with VLANs/
│
├── Departmental-LAN.pkt
├── README.md
│
├── configurations/
│   ├── router-config.txt
│   └── switch-config.txt
│
├── images/
│   ├── topology.png
│   ├── vlan-config.png
│   ├── switch-vlan-ports.png
│   ├── trunk-port.png
│   ├── router-cli.png
│   ├── router-interface.png
│   ├── inter-vlan-ping.png
│   └── inter-vlan-routing.png
│
└── documentation/
    └── Network-Design.pdf
```

---

# 📄 Router Configuration

The complete router configuration can be saved as:

`configurations/router-config.txt`

```cisco
enable
configure terminal

hostname R1

interface gigabitEthernet 0/0
no shutdown
exit

interface gigabitEthernet 0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0
exit

interface gigabitEthernet 0/0.20
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0
exit

end
copy running-config startup-config
```

---

# 📄 Switch Configuration

The complete switch configuration can be saved as:

`configurations/switch-config.txt`

```cisco
enable
configure terminal

hostname SW1

vlan 10
name HR
exit

vlan 20
name SALES
exit

interface range fa0/3-2
switchport mode access
switchport access vlan 10
exit

interface range fa0/4-4
switchport mode access
switchport access vlan 20
exit

interface gigabitEthernet 0/1
switchport mode trunk
exit

end
copy running-config startup-config
```

---

# 📚 Concepts Practiced

* VLAN Fundamentals
* Broadcast Domains
* Access Ports
* Trunk Ports
* IEEE 802.1Q
* Router-on-a-Stick
* Inter-VLAN Routing
* IPv4 Addressing
* /24 Subnetting
* Default Gateways
* Network Segmentation
* Cisco IOS Configuration
* MAC Address Learning
* Routing Table Verification
* Network Troubleshooting

---

# 🎓 Learning Outcomes

Through this project, I gained hands-on experience in:

* Designing a small enterprise departmental LAN
* Creating and configuring VLANs
* Assigning switch access ports
* Configuring IEEE 802.1Q trunking
* Implementing Router-on-a-Stick
* Configuring router subinterfaces
* Configuring IPv4 addressing and default gateways
* Understanding broadcast-domain separation
* Enabling communication between VLANs
* Verifying Layer 2 and Layer 3 connectivity
* Using Cisco IOS commands for network troubleshooting

---

# 🚀 Future Improvements

This project can be extended into a more realistic enterprise network by implementing:

* 🔹 DHCP for automatic IP assignment
* 🔹 ACLs for department-level traffic control
* 🔹 Port Security
* 🔹 SSH for secure remote management
* 🔹 Management VLAN
* 🔹 Multiple switches
* 🔹 EtherChannel
* 🔹 OSPF Dynamic Routing
* 🔹 Layer 3 Switching
* 🔹 Wireless VLAN Integration
* 🔹 SNMP Network Monitoring

---

# 💼 Real-World Applications

The concepts demonstrated in this project are commonly used in enterprise networks for:

* Office network segmentation
* Department-based network design
* Broadcast-domain management
* Enterprise VLAN deployment
* Access-layer switching
* Inter-VLAN communication
* Network administration
* Network troubleshooting

---

# ⭐ Project Completion Checklist

### Network Design

* [x] Network topology designed
* [x] Router and switch configured
* [x] Four end devices connected
* [x] IP addressing plan created

### VLAN Configuration

* [x] VLAN 10 created for HR
* [x] VLAN 20 created for Sales
* [x] HR access ports configured
* [x] Sales access ports configured

### Routing

* [x] Trunk link configured
* [x] Router subinterfaces configured
* [x] IEEE 802.1Q encapsulation configured
* [x] Default gateways configured
* [x] Inter-VLAN Routing enabled

### Verification

* [x] VLAN configuration verified
* [x] Trunk configuration verified
* [x] Router interfaces verified
* [x] Routing table verified
* [x] Same-VLAN connectivity tested
* [x] Inter-VLAN connectivity tested

### Future Enhancements

* [ ] DHCP
* [ ] ACL
* [ ] SSH
* [ ] Port Security
* [ ] Multiple Switches
* [ ] EtherChannel
* [ ] OSPF
* [ ] Network Monitoring

---

# 👨‍💻 Author

## Tushar Patel

Aspiring **Network & Cloud Engineer** with hands-on experience in networking concepts, Cisco technologies, troubleshooting, and enterprise network design.

### Connect with me

* 💼 **LinkedIn:** [Tushar Patel](https://www.linkedin.com/in/tushar-patel-s/)
* 💻 **GitHub:** [Tushar0589](https://github.com/Tushar0589)

---

# ⭐ Support

If you found this project useful, consider giving the repository a ⭐ on GitHub.

Suggestions, feedback, and contributions are always welcome! 🚀
