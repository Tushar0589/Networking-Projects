# 📡 Network Monitoring Lab using Cisco Packet Tracer

A hands-on **Network Monitoring and Secure Device Management Lab** built using **Cisco Packet Tracer**. This project demonstrates centralized network logging, Cisco and vendor-neutral neighbor discovery, secure remote administration, IP connectivity, and network-event monitoring using **Syslog, CDP, LLDP, and SSH**.

The lab simulates a small enterprise network environment and focuses on practical skills required for **Network Engineers, NOC Engineers, Network Support Engineers, and System Administrators**.

---

## 🎯 Project Objectives

The main objectives of this project are to:

* Configure a multi-router and multi-switch enterprise-style network
* Configure IPv4 addressing and static routing
* Implement centralized Syslog logging
* Configure Cisco Discovery Protocol (CDP)
* Configure Link Layer Discovery Protocol (LLDP)
* Secure network-device management using SSH
* Monitor interface status and configuration events
* Verify network connectivity and device reachability
* Practice Cisco IOS CLI configuration and troubleshooting
* Document network configurations and verification results

---

# 🏗️ Network Topology

The topology consists of:

* 2 × Cisco Routers
* 2 × Cisco Layer 2 Switches
* 1 × Syslog Server
* 1 × Management PC
* 4 × End Devices

### Logical Topology

```text
                         ┌─────────────────┐
                         │     Router 1    │
                         │    R1-CORE      │
                         │ 192.168.10.1    │
                         └────────┬────────┘
                                  │
                            10.0.0.1/30
                                  │
                            10.0.0.2/30
                                  │
                         ┌────────┴────────┐
                         │     Router 2    │
                         │    R2-EDGE      │
                         │ 192.168.20.1    │
                         └────────┬────────┘
                                  │
                         ┌────────┴────────┐
                         │    Switch 2     │
                         │   SW2-EDGE      │
                         │ 192.168.20.2    │
                         └───────┬─┬───────┘
                                 │ │
                               PC3 PC4


       ┌─────────────────────────────────────┐
       │              Switch 1               │
       │             SW1-MGMT                │
       │           192.168.10.2              │
       └──────┬────────┬────────┬────────────┘
              │        │        │
             PC1      PC2    Syslog Server
                              192.168.10.100

                              │
                        Management PC
                        192.168.10.101
```

---

# 🌐 IP Addressing Plan

## LAN 1 — 192.168.10.0/24

| Device        | Interface | IP Address     | Subnet Mask   | Default Gateway |
| ------------- | --------- | -------------- | ------------- | --------------- |
| R1-CORE       | G0/0      | 192.168.10.1   | 255.255.255.0 | —               |
| SW1-MGMT      | VLAN 1    | 192.168.10.2   | 255.255.255.0 | 192.168.10.1    |
| Syslog Server | NIC       | 192.168.10.100 | 255.255.255.0 | 192.168.10.1    |
| Management PC | NIC       | 192.168.10.101 | 255.255.255.0 | 192.168.10.1    |
| PC1           | NIC       | 192.168.10.10  | 255.255.255.0 | 192.168.10.1    |
| PC2           | NIC       | 192.168.10.11  | 255.255.255.0 | 192.168.10.1    |

## LAN 2 — 192.168.20.0/24

| Device   | Interface | IP Address    | Subnet Mask   | Default Gateway |
| -------- | --------- | ------------- | ------------- | --------------- |
| R2-EDGE  | G0/0      | 192.168.20.1  | 255.255.255.0 | —               |
| SW2-EDGE | VLAN 1    | 192.168.20.2  | 255.255.255.0 | 192.168.20.1    |
| PC3      | NIC       | 192.168.20.10 | 255.255.255.0 | 192.168.20.1    |
| PC4      | NIC       | 192.168.20.11 | 255.255.255.0 | 192.168.20.1    |

## Router-to-Router Transit Network

| Device  | Interface | IP Address  |
| ------- | --------- | ----------- |
| R1-CORE | G0/1      | 10.0.0.1/30 |
| R2-EDGE | G0/1      | 10.0.0.2/30 |

---

# 🔌 Physical Connections

| Source   | Interface | Destination   | Interface |
| -------- | --------- | ------------- | --------- |
| R1-CORE  | G0/0      | SW1-MGMT      | G0/1      |
| R1-CORE  | G0/1      | R2-EDGE       | G0/1      |
| R2-EDGE  | G0/0      | SW2-EDGE      | G0/1      |
| SW1-MGMT | Fa0/1     | PC1           | NIC       |
| SW1-MGMT | Fa0/2     | PC2           | NIC       |
| SW1-MGMT | Fa0/3     | Syslog Server | NIC       |
| SW1-MGMT | Fa0/4     | Management PC | NIC       |
| SW2-EDGE | Fa0/1     | PC3           | NIC       |
| SW2-EDGE | Fa0/2     | PC4           | NIC       |

---

# ⚙️ Technologies Used

* Cisco Packet Tracer
* Cisco IOS CLI
* IPv4
* Static Routing
* Layer 2 Switching
* Syslog
* CDP
* LLDP
* SSH
* Remote Device Management
* Network Monitoring
* Network Troubleshooting

---

# 🔧 Network Configuration

## 1. Router 1 — R1-CORE

### Basic Configuration

```cisco
enable
configure terminal

hostname R1-CORE

interface gigabitEthernet 0/0
ip address 192.168.10.1 255.255.255.0
no shutdown
exit

interface gigabitEthernet 0/1
ip address 10.0.0.1 255.255.255.252
no shutdown
exit
```

### Static Route

```cisco
ip route 192.168.20.0 255.255.255.0 10.0.0.2
```

---

## 2. Router 2 — R2-EDGE

```cisco
enable
configure terminal

hostname R2-EDGE

interface gigabitEthernet 0/0
ip address 192.168.20.1 255.255.255.0
no shutdown
exit

interface gigabitEthernet 0/1
ip address 10.0.0.2 255.255.255.252
no shutdown
exit
```

### Static Route

```cisco
ip route 192.168.10.0 255.255.255.0 10.0.0.1
```

---

# 🔀 Switch Configuration

## Switch 1 — SW1-MGMT

```cisco
enable
configure terminal

hostname SW1-MGMT

interface vlan 1
ip address 192.168.10.2 255.255.255.0
no shutdown
exit

ip default-gateway 192.168.10.1

end
copy running-config startup-config
```

---

## Switch 2 — SW2-EDGE

```cisco
enable
configure terminal

hostname SW2-EDGE

interface vlan 1
ip address 192.168.20.2 255.255.255.0
no shutdown
exit

ip default-gateway 192.168.20.1

end
copy running-config startup-config
```

---

# 📄 Syslog Configuration

A centralized Syslog Server is used to collect system messages from network devices.

### Syslog Server

Configure the server with:

```text
IP Address:      192.168.10.100
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.10.1
```

Navigate to:

```text
Server
   ↓
Services
   ↓
SYSLOG
   ↓
ON
```

### Configure Network Devices

Run on R1, R2, SW1 and SW2:

```cisco
logging 192.168.10.100
logging trap informational
logging buffered 16384
```

### Verification

```cisco
show logging
```

The Syslog server is used to monitor events such as:

* Interface status changes
* Configuration changes
* System messages
* Device startup events
* Network events

---

# 🔍 Cisco Discovery Protocol — CDP

CDP is used to discover directly connected Cisco devices.

### Enable CDP

```cisco
enable
configure terminal
cdp run
end
```

Run on all Cisco routers and switches.

### Verification

```cisco
show cdp neighbors
```

Detailed information:

```cisco
show cdp neighbors detail
```

### Information Verified

* Neighbor device name
* Device platform
* Local interface
* Remote interface
* IP address
* Device capabilities

---

# 🌐 Link Layer Discovery Protocol — LLDP

LLDP provides vendor-neutral neighbor discovery.

### Enable LLDP

Run on all supported Cisco devices:

```cisco
enable
configure terminal
lldp run
end
```

### Verification

```cisco
show lldp neighbors
```

Detailed information:

```cisco
show lldp neighbors detail
```

### Information Verified

* Neighbor device
* Local interface
* Remote interface
* Device capabilities
* Management information

---

# 🔐 Secure Shell — SSH

SSH is configured to provide secure remote administration of network devices.

## Step 1 — Configure Domain Name

```cisco
ip domain-name networklab.local
```

## Step 2 — Create Local User

```cisco
username admin privilege 15 secret Cisco@123
```

## Step 3 — Generate RSA Keys

```cisco
crypto key generate rsa
```

Use:

```text
1024
```

when prompted for the modulus size.

## Step 4 — Enable SSH Version 2

```cisco
ip ssh version 2
```

## Step 5 — Configure VTY Lines

```cisco
line vty 0 4
login local
transport input ssh
exit
```

Save configuration:

```cisco
end
copy running-config startup-config
```

Repeat the SSH configuration on:

* R1-CORE
* R2-EDGE
* SW1-MGMT
* SW2-EDGE

---

# 🖥️ SSH Verification

From the Management PC:

```text
Desktop
   ↓
Command Prompt
```

Test connectivity:

```text
ping 192.168.10.1
```

Then connect using SSH:

```text
ssh -l admin 192.168.10.1
```

Enter the configured password.

Successful access should provide:

```text
R1-CORE#
```

Test switch management:

```text
ssh -l admin 192.168.10.2
```

Expected prompt:

```text
SW1-MGMT#
```

---

# 🧪 Network Connectivity Testing

Connectivity was verified between the two LANs.

### From Management PC

```text
ping 192.168.10.1
ping 192.168.10.2
ping 192.168.10.100
ping 192.168.20.1
ping 192.168.20.2
ping 192.168.20.10
ping 192.168.20.11
```

Successful responses confirm:

* Local LAN connectivity
* Router connectivity
* Inter-router connectivity
* Static routing
* Remote LAN reachability

---

# 🧪 Syslog Event Testing

To verify that centralized logging is working, network events were deliberately generated.

## Interface Down Event

On R1:

```cisco
configure terminal

interface gigabitEthernet 0/0
shutdown

end
```

The interface-down event should appear in the Syslog Server.

## Interface Up Event

```cisco
configure terminal

interface gigabitEthernet 0/0
no shutdown

end
```

The interface-up event should then be logged.

---

# 📝 Configuration Change Testing

A harmless configuration change can be used to generate a configuration event.

Example:

```cisco
configure terminal

interface gigabitEthernet 0/0
description LAN-to-SW1

end
```

Verify local logging:

```cisco
show logging
```

The configuration-related Syslog message can then be observed on the centralized Syslog Server.

---

# 🔎 Verification Commands

The following Cisco IOS commands were used during the project.

### Interface Status

```cisco
show ip interface brief
```

### Routing Table

```cisco
show ip route
```

### CDP

```cisco
show cdp neighbors
show cdp neighbors detail
```

### LLDP

```cisco
show lldp neighbors
show lldp neighbors detail
```

### Syslog

```cisco
show logging
```

### SSH

```cisco
show ip ssh
```

### Running Configuration

```cisco
show running-config
```

---

# ✅ Project Verification

| Test                          | Result     |
| ----------------------------- | ---------- |
| Router-to-router connectivity | ✅ Verified |
| LAN connectivity              | ✅ Verified |
| Inter-LAN connectivity        | ✅ Verified |
| Static routing                | ✅ Verified |
| Switch management IP          | ✅ Verified |
| Centralized Syslog            | ✅ Verified |
| Interface UP event            | ✅ Verified |
| Interface DOWN event          | ✅ Verified |
| Configuration-change logging  | ✅ Verified |
| CDP neighbor discovery        | ✅ Verified |
| LLDP neighbor discovery       | ✅ Verified |
| SSH remote login              | ✅ Verified |
| Cisco IOS verification        | ✅ Verified |

---

# 📸 Project Screenshots

The following screenshots document the implementation and verification of the project.

Store all screenshots inside the `images/` directory.

## Required Screenshots

### 1. Network Topology

```text
images/topology.png
```

Show the complete Packet Tracer topology with all devices and connections.

---

### 2. IP Interface Status

```text
images/ip-addressing.png
```

Show:

```cisco
show ip interface brief
```

The screenshot should clearly show the configured interfaces and their `up/up` status.

---

### 3. Connectivity Test

```text
images/connectivity-test.png
```

Show successful ping results from the Management PC to devices on both networks.

---

### 4. Syslog Server

```text
images/syslog-server.png
```

Show:

```text
Server → Services → SYSLOG
```

with received network messages visible.

---

### 5. Interface Events

```text
images/interface-events.png
```

Show Syslog messages generated by:

```text
Interface Down
Interface Up
```

---

### 6. Configuration Change Log

```text
images/configuration-change-log.png
```

Show the Syslog message generated after a configuration change.

---

### 7. Local Logging

```text
images/show-logging.png
```

Show:

```cisco
show logging
```

on a router.

---

### 8. CDP Neighbor Discovery

```text
images/cdp.png
```

Show:

```cisco
show cdp neighbors
```

and, preferably, detailed neighbor information.

---

### 9. LLDP Neighbor Discovery

```text
images/lldp.png
```

Show:

```cisco
show lldp neighbors
```

---

### 10. SSH Login

```text
images/ssh-login.png
```

Show a successful SSH login from the Management PC:

```text
ssh -l admin 192.168.10.1
```

with the resulting:

```text
R1-CORE#
```

prompt visible.

---

# 📁 Repository Structure

```text
Network Monitoring Lab/
│
├── Network-Monitoring.pkt
├── README.md
│
├── configurations/
│   ├── Router1-config.txt
│   ├── Router2-config.txt
│   ├── Switch1-config.txt
│   └── Switch2-config.txt
│
├── images/
│   ├── topology.png
│   ├── ip-addressing.png
│   ├── connectivity-test.png
│   ├── syslog-server.png
│   ├── interface-events.png
│   ├── configuration-change-log.png
│   ├── show-logging.png
│   ├── cdp.png
│   ├── lldp.png
│   └── ssh-login.png
│
└── documentation/
    └── Network-Design.pdf
```

---

# 📚 Concepts Practiced

This project provided hands-on practice with:

* IPv4 addressing
* Subnetting
* Static routing
* Layer 2 switching
* Cisco IOS CLI
* Network device management
* Centralized logging
* Syslog
* CDP
* LLDP
* SSH
* Remote device administration
* Network troubleshooting
* Interface monitoring
* Configuration monitoring
* Enterprise network operations

---

# 💡 Real-World Applications

The technologies implemented in this lab are commonly associated with:

### 🖥️ Network Operations Center — NOC

* Device monitoring
* Event monitoring
* Fault detection
* Troubleshooting

### 🔐 Network Security

* Secure remote administration
* Login monitoring
* Configuration monitoring
* Security event logging

### 🌐 Enterprise Networking

* Device discovery
* Network management
* Centralized logging
* Infrastructure monitoring

### 🛠️ Network Administration

* Remote device access
* Configuration management
* Troubleshooting
* Operational monitoring

---

# 🚀 Future Improvements

The project can be expanded with additional enterprise networking and monitoring technologies.

### Monitoring

* SNMP
* SNMPv3
* Network monitoring dashboard
* Interface utilization monitoring
* Network performance monitoring

### Time Synchronization

* NTP
* Centralized time synchronization

### Security

* AAA
* RADIUS
* TACACS+
* SSH hardening
* Login blocking
* Password policies

### Logging

* Syslog severity levels
* Centralized log management
* Log filtering
* Syslog over TLS
* Log retention and rotation

### Traffic Analysis

* NetFlow
* Traffic monitoring
* Bandwidth analysis

---

# 🎓 Learning Outcomes

After completing this project, I gained practical experience in:

* Designing a small enterprise network topology
* Configuring Cisco routers and switches
* Implementing IPv4 addressing
* Configuring static routing
* Configuring centralized Syslog logging
* Monitoring network events
* Using CDP for Cisco device discovery
* Using LLDP for neighbor discovery
* Securing remote administration with SSH
* Generating and analyzing network events
* Verifying network connectivity
* Troubleshooting network-device communication
* Using Cisco IOS verification commands
* Documenting a network infrastructure project

---

# 👨‍💻 Author

## Tushar Patel

Aspiring **Network & Cloud Engineer** with hands-on experience in Cisco networking, network troubleshooting, infrastructure technologies, and cloud fundamentals.

### 🔗 Connect With Me

* **LinkedIn:** [Tushar Patel](https://www.linkedin.com/in/tushar-patel-s/)
* **GitHub:** [Tushar0589](https://github.com/Tushar0589)

---

# ⭐ Support

If you found this project useful, consider giving the repository a ⭐ on GitHub.

Feedback, suggestions, and contributions are welcome!

---

## 📌 Project Status

**Status:** ✅ Completed

**Platform:** Cisco Packet Tracer

**Project Type:** Network Monitoring / Network Administration

**Level:** CCNA / Entry-Level Network Engineer

**Primary Technologies:** Syslog • CDP • LLDP • SSH • IPv4 • Static Routing • Cisco IOS
