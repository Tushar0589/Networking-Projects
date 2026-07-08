# 📡 Network Monitoring Lab using Cisco Packet Tracer

A hands-on networking project that demonstrates how to implement **network monitoring, device discovery, secure remote management, and centralized logging** using **Cisco Packet Tracer**. This lab focuses on configuring **Syslog**, **CDP**, **LLDP**, and **SSH** to simulate real-world network monitoring and management in an enterprise environment.

---

## 📖 Project Overview

Modern enterprise networks rely on monitoring and management protocols to ensure network availability, troubleshoot issues, and maintain security.

In this project, network devices are configured to:

- Send logs to a centralized **Syslog Server**
- Discover neighboring devices using **CDP** and **LLDP**
- Allow secure remote administration through **SSH**
- Monitor interface status, login attempts, and configuration changes

This project demonstrates essential networking concepts commonly used by **Network Engineers**, **NOC Engineers**, and **System Administrators**.

---

## 🎯 Objectives

- Configure centralized Syslog logging
- Enable Cisco Discovery Protocol (CDP)
- Configure Link Layer Discovery Protocol (LLDP)
- Secure devices using SSH
- Monitor network events
- Verify log generation and collection
- Practice enterprise network monitoring

---

## 🏗️ Network Topology

The network consists of:

- 2 Cisco Routers
- 2 Cisco Layer 2 Switches
- Syslog Server
- Management PC
- Multiple End Devices

---

## ⚙️ Technologies Used

- Cisco Packet Tracer
- Cisco IOS CLI
- Syslog
- SSH
- CDP
- LLDP
- IPv4 Addressing
- Layer 2 Switching
- Router Configuration

---

## ✨ Features

- Centralized Syslog Server
- Secure Remote Login using SSH
- Automatic Neighbor Discovery
- Network Device Monitoring
- Event Logging
- Configuration Change Tracking
- Interface Status Monitoring

---

# 🔧 Technologies Implemented

## 📄 Syslog

Configured network devices to send logs to a centralized Syslog server.

### Logs Captured

- Interface Up Events
- Interface Down Events
- Device Startup
- Configuration Changes
- Login Attempts
- Security Notifications
- System Messages

---

## 🔍 Cisco Discovery Protocol (CDP)

Configured CDP to automatically discover directly connected Cisco devices.

### Verified

- Device Name
- Platform
- Interface Information
- IP Address
- Connected Port

Commands Used

```bash
show cdp neighbors
show cdp neighbors detail
```

---

## 🌐 Link Layer Discovery Protocol (LLDP)

Configured LLDP for vendor-neutral device discovery.

### Verified

- Neighbor Information
- Device Capabilities
- Interface Details
- Management Address

Commands Used

```bash
show lldp neighbors
show lldp neighbors detail
```

---

## 🔐 Secure Shell (SSH)

Configured secure remote device management.

### Configuration Includes

- Hostname
- Domain Name
- RSA Key Generation
- Local User Database
- SSH Version 2
- VTY Configuration

Verified

- Successful Remote Login
- Authentication
- Secure CLI Access

---

## 🌍 Example IP Addressing

| Device | IP Address |
|----------|------------|
| Router 1 | 192.168.10.1 |
| Router 2 | 192.168.20.1 |
| Switch 1 | 192.168.10.2 |
| Switch 2 | 192.168.20.2 |
| Syslog Server | 192.168.10.100 |
| Management PC | 192.168.10.101 |

---

## 🧪 Verification Performed

### ✅ Syslog

- Interface Up Event Logged
- Interface Down Event Logged
- Login Success Logged
- Login Failure Logged
- Configuration Changes Logged
- Device Startup Logged

---

### ✅ SSH

- Remote Login Successful
- Authentication Verified
- Secure CLI Access

---

### ✅ CDP

Verified Neighbor Discovery

```bash
show cdp neighbors
show cdp neighbors detail
```

---

### ✅ LLDP

Verified Neighbor Discovery

```bash
show lldp neighbors
show lldp neighbors detail
```

---

## 📸 Project Screenshots

Store screenshots inside the **images/** directory.

Example:

```
images/
│
├── topology.png
├── ssh-login.png
├── syslog-server.png
├── show-cdp-neighbors.png
├── show-lldp-neighbors.png
├── login-attempts.png
├── interface-events.png
└── configuration-change-log.png
```

---

## 📁 Repository Structure

```
Network-Monitoring-Lab/
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
│   ├── syslog.png
│   ├── ssh.png
│   ├── cdp.png
│   ├── lldp.png
│   └── logs.png
│
└── documentation/
    └── Network-Design.pdf
```

---

## 📚 Concepts Practiced

- Enterprise Network Monitoring
- Syslog Configuration
- Centralized Logging
- SSH Remote Access
- Cisco Discovery Protocol (CDP)
- Link Layer Discovery Protocol (LLDP)
- Cisco IOS CLI
- Device Management
- Network Troubleshooting
- Secure Administration

---

## 🚀 Learning Outcomes

Through this project, I gained hands-on experience in:

- Configuring centralized Syslog logging
- Monitoring network events and device activity
- Securing remote device access using SSH
- Discovering neighboring devices with CDP and LLDP
- Verifying interface status and configuration changes
- Troubleshooting network connectivity and management services
- Applying enterprise network monitoring best practices

---

## 💼 Real-World Applications

This project demonstrates technologies commonly used in production enterprise networks for:

- Network Operations Center (NOC)
- Enterprise Network Monitoring
- Infrastructure Management
- Security Auditing
- Remote Device Administration
- Incident Investigation
- Configuration Management
- Fault Detection and Troubleshooting

---

## 🛠️ Future Improvements

- SNMP Monitoring
- NTP Configuration
- Syslog Severity Levels
- AAA Authentication (RADIUS/TACACS+)
- Email Alerts
- Network Time Synchronization
- Syslog Log Rotation
- Syslog over TLS
- NetFlow Traffic Analysis
- Network Monitoring Dashboard

---

## 👨‍💻 Author

**Tushar Patel**

### Connect with me

- **LinkedIn:** *https://www.linkedin.com/in/tushar-patel-s/*
- **GitHub:** https://github.com/Tushar0589

---

## ⭐ Support

If you found this project useful, consider giving this repository a ⭐ on GitHub.

Feedback, suggestions, and contributions are always welcome!
