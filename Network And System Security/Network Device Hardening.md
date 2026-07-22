# Network Device Hardening

## Project Overview

This project demonstrates the implementation of industry-standard hardening techniques for network infrastructure components, including routers, firewalls, VPN gateways, and network services. The objective was to reduce the attack surface of critical network devices by applying secure configurations, enforcing strong authentication, implementing secure management protocols, and improving monitoring and logging capabilities.

The project also explores common attack vectors against network devices, VPN hardening using OpenVPN, router security using OpenWrt, enterprise network protection techniques, and network monitoring solutions used to maintain the **Confidentiality, Integrity, and Availability (CIA)** of enterprise environments.

---

## Objectives

- Understand common threats targeting network infrastructure
- Differentiate endpoint devices from network devices
- Apply general network device hardening techniques
- Secure network management protocols
- Harden an OpenVPN deployment
- Secure routers and firewalls using OpenWrt
- Implement firewall traffic controls and monitoring
- Understand enterprise network hardening techniques
- Explore commonly used network monitoring solutions

---

## Skills Demonstrated

- Network Security
- Network Device Hardening
- VPN Hardening
- Router Hardening
- Firewall Configuration
- Secure Protocol Implementation
- OpenVPN Administration
- OpenWrt Administration
- Access Control
- Network Monitoring
- Logging & Auditing
- Threat Mitigation
- Principle of Least Privilege (PoLP)
- Security Configuration Management

---

## Technologies & Tools

- OpenVPN
- OpenWrt
- Linux
- Ubuntu
- Firewall Rules
- SSH
- HTTPS
- TLS
- AES Encryption
- Syslog
- SNMP
- NetFlow
- Wireshark
- Nagios
- SolarWinds Network Performance Monitor
- PRTG
- Zabbix

---

## Lab Environment

- TryHackMe Network Device Hardening Lab
- Ubuntu VPN Server
- OpenVPN
- OpenWrt Router
- Linux Command Line Interface (CLI)
- Web-based Router Administration Interface

---

# Project Tasks

## 1. Understanding Network Device Threats

### Activity

Studied the differences between endpoint devices and network devices while analyzing common attack vectors targeting enterprise network infrastructure.

### Attacks Covered

- Unauthorized access
- Denial of Service (DoS)
- Man-in-the-Middle (MITM)
- Privilege Escalation
- Bandwidth Theft
- Password Attacks
- ARP Spoofing
- DNS Spoofing
- Rogue Access Points
- Remote Code Execution (RCE)
- Social Engineering

### Outcome

Developed an understanding of how attackers compromise networking equipment and the impact these attacks have on enterprise environments.

---

## 2. Applying General Network Hardening Techniques

### Activity

Implemented foundational security controls to reduce the attack surface of network devices.

### Implemented Controls

- Operating system updates and patch management
- Disabling unnecessary services
- Closing unused ports
- Principle of Least Privilege (PoLP)
- Strong password enforcement
- Multi-Factor Authentication (MFA)
- Regular configuration backups
- Continuous log monitoring

### Outcome

Reduced potential attack vectors while improving the resilience of network infrastructure.

---

## 3. Securing Network Management Protocols

### Activity

Reviewed secure protocols used for network administration.

### Secure Protocols

- SSH
- HTTPS
- SSL/TLS
- IPsec

### Insecure Protocols Identified

- FTP
- HTTP
- Telnet
- SMTP (without encryption)

### Outcome

Improved secure remote administration while minimizing credential interception and plaintext communications.

---

## 4. Implementing Network Logging & Monitoring

### Activity

Configured and reviewed centralized logging and monitoring mechanisms.

### Technologies

- Syslog
- SNMP Traps
- NetFlow
- Packet Capture Analysis

### Outcome

Improved visibility into network events and strengthened incident detection capabilities.

---

## 5. Hardening OpenVPN

### Activity

Configured an OpenVPN server using secure cryptographic settings and authentication mechanisms.

### Implemented Security Controls

- AES-128-CBC Encryption
- AES-256-CBC Encryption
- SHA256 Authentication
- SHA512 Authentication
- TLS Crypt
- Perfect Forward Secrecy (PFS)
- TLS Version 1.2
- Dedicated VPN Service Accounts
- Updated VPN Software
- Strong Authentication

### Example Configuration

```conf
cipher AES-256-CBC
auth SHA256
tls-crypt my.key
tls-version-min 1.2
```

### Outcome

Strengthened VPN confidentiality, integrity, authentication, and session security while reducing the risk of interception and replay attacks.

---

## 6. Router Hardening Using OpenWrt

### Activity

Performed administrative hardening using the OpenWrt management interface.

### Implemented

- Changed default administrator credentials
- Verified SSH configuration
- Enabled secure administration
- Reviewed logging settings
- Configured system information
- Secured startup services
- Reviewed Wi-Fi security recommendations

### Outcome

Reduced administrative attack vectors while improving secure management of the router.

---

## 7. Firewall Hardening

### Activity

Reviewed firewall configuration and access control policies.

### Features Reviewed

- Traffic Rules
- Port Forwarding
- Firewall Policies

### Security Controls Examined

- ICMP Filtering
- WAN-to-LAN Forwarding Rules
- Controlled Inbound Access
- Firewall Rule Management

### Outcome

Improved network segmentation while minimizing unnecessary external exposure.

---

## 8. Monitoring Network Activity

### Activity

Reviewed built-in monitoring capabilities provided by network devices.

### Monitoring Features

- Real-time Bandwidth Monitoring
- Upload and Download Statistics
- Network Traffic Visualization
- Scheduled Task Monitoring

### Outcome

Improved operational visibility and enabled early detection of suspicious traffic patterns.

---

## 9. Enterprise Network Hardening

### Activity

Studied enterprise-level protection mechanisms commonly deployed on production networks.

### Security Controls

- Port Security
- Static ARP
- DHCP Protection
- Rogue DHCP Prevention
- IPv6 Security
- MAC Address Filtering

### Outcome

Learned defensive techniques that protect enterprise switching infrastructure against spoofing and lateral movement attacks.

---

## 10. Network Monitoring Solutions

### Activity

Researched commonly used enterprise monitoring platforms.

### Platforms Covered

- Nagios
- SolarWinds Network Performance Monitor
- PRTG
- Zabbix

### Outcome

Developed familiarity with enterprise monitoring platforms used for network visibility, availability monitoring, and security operations.

---

# Key Security Concepts Learned

- Network Device Hardening
- Secure Device Administration
- VPN Security
- Firewall Management
- Router Security
- Secure Network Protocols
- Principle of Least Privilege (PoLP)
- Logging and Monitoring
- Network Visibility
- Enterprise Network Security
- Configuration Hardening
- Threat Detection

---

# Practical Configuration Changes

Successfully performed and validated multiple hardening activities, including:

- Configured AES encryption for OpenVPN
- Updated VPN authentication algorithms
- Enabled TLS protection
- Changed default router credentials
- Reviewed firewall traffic rules
- Examined port forwarding configurations
- Reviewed startup services
- Verified SSH configuration
- Implemented secure management practices
- Reviewed logging and monitoring configurations

---

# Security Best Practices Applied

- Principle of Least Privilege (PoLP)
- Strong Authentication
- Secure Cryptographic Algorithms
- Secure Remote Administration
- Encryption of Network Traffic
- Logging and Auditing
- Configuration Hardening
- Patch Management
- Network Monitoring
- Continuous Security Review

---

# Lessons Learned

This project reinforced that securing network infrastructure requires significantly more than changing default passwords. Effective network device hardening combines secure protocols, strong cryptography, continuous monitoring, least-privilege access, proper firewall configuration, regular software updates, and ongoing configuration reviews. Implementing these layered security controls significantly reduces the attack surface of routers, firewalls, VPN gateways, and other critical network devices while improving the resilience of enterprise environments.

---

# Disclaimer

This project was completed within an authorized **TryHackMe** training environment for educational purposes. All configurations, hardening activities, and security assessments were performed on controlled lab systems designed for cybersecurity training. No testing was conducted against production systems or unauthorized environments.
