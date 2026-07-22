# Microsoft Windows System Hardening

A hands-on cybersecurity project focused on hardening Microsoft Windows systems against common attack vectors using built-in security features, security policies, firewall configurations, endpoint protection, encryption, application control, and update management.

This project demonstrates practical Windows security administration techniques performed in a controlled lab environment using Windows 10.

---

## Project Overview

Windows endpoints are one of the most common targets for attackers because they expose numerous services, applications, authentication mechanisms, and administrative features.

This project explores Microsoft's native security capabilities and documents practical hardening techniques that significantly reduce the attack surface while improving endpoint security.

The project covers multiple security domains including:

- Identity and Access Management
- Network Security
- Application Security
- Storage Protection
- Windows Update Management
- System Logging
- Built-in Windows Security Features

---

## Objectives

- Reduce the Windows attack surface
- Strengthen authentication mechanisms
- Secure network communications
- Protect sensitive data
- Restrict unnecessary services
- Harden Microsoft applications
- Improve endpoint resilience
- Apply security best practices

---

# Lab Environment

| Component | Details |
|-----------|---------|
| Platform | TryHackMe |
| Operating System | Microsoft Windows 10 |
| Tools Used | Services Console, Registry Editor, Event Viewer, Windows Defender Firewall, Local Group Policy, Windows Defender, BitLocker, Microsoft Edge, AppLocker, PowerShell |

---

# Skills Demonstrated

- Windows Security Hardening
- Windows Administration
- Windows Registry Analysis
- Service Management
- User Account Security
- Firewall Configuration
- Microsoft Defender Configuration
- Network Hardening
- DNS Security
- SMB Hardening
- Storage Encryption
- BitLocker
- Windows Sandbox
- Secure Boot
- Application Control
- Microsoft Office Hardening
- Security Policy Implementation
- Windows Update Management
- Event Log Analysis

---

# Project Sections

- Windows Services
- Windows Registry Security
- Event Viewer Analysis
- Windows Telemetry
- Identity & Access Management
- Network Hardening
- Application Security
- Storage Protection
- Windows Updating
- Security Best Practices

---

# Windows Services

## Objective

Understand critical Windows services and identify how attackers abuse running services.

## Activities

- Reviewed Windows Services
- Examined startup types
- Identified service categories
- Studied Service Control Manager
- Investigated service abuse techniques

## Security Considerations

- Disable unnecessary services
- Review startup types
- Remove unused software
- Monitor service changes

---

# Windows Registry

## Objective

Understand registry abuse techniques and secure registry access.

## Activities

- Explored Registry Editor
- Reviewed Run and RunOnce keys
- Investigated persistence locations
- Identified registry-based startup entries

## Security Benefits

- Prevent persistence
- Reduce malware execution
- Protect critical configuration

---

# Event Viewer

## Objective

Learn how Windows records security and operational events.

## Logs Reviewed

- Application
- Security
- System

## Security Value

- Authentication monitoring
- Crash investigation
- Incident response
- Threat hunting
- Audit trail analysis

---

# Windows Telemetry

## Objective

Understand Microsoft's telemetry services.

## Reviewed Components

- DiagTrack
- UTC Service
- Diagnostic Logs
- Local telemetry storage

## Security Considerations

- Understand collected data
- Review privacy implications
- Monitor telemetry behavior

---

# Identity & Access Management

## Administrator vs Standard Accounts

Implemented the Principle of Least Privilege by separating administrative tasks from daily activities.

### Best Practices

- Use Standard Accounts daily
- Reserve Administrator accounts for administrative tasks
- Avoid unnecessary privilege escalation

---

## User Account Control (UAC)

Configured UAC to:

- Always Notify
- Require administrative approval
- Reduce unauthorized privilege escalation

---

## Password Policies

Studied password policy configuration using Local Group Policy.

Implemented concepts including:

- Password complexity
- Password length
- Password history
- Account lockout
- Failed login protection

---

## Account Lockout

Configured account lockout concepts to defend against:

- Password guessing
- Brute-force attacks
- Credential stuffing

---

# Network Hardening

## Windows Defender Firewall

Configured firewall profiles and reviewed:

- Domain Profile
- Private Profile
- Public Profile

Applied a default-deny mindset where appropriate.

---

## Disable Unused Network Devices

Reduced attack surface by disabling unused:

- Network adapters
- Wireless interfaces
- Virtual adapters

---

## SMB Hardening

Disabled SMBv1 using PowerShell.

```powershell
Disable-WindowsOptionalFeature -Online -FeatureName SMB1Protocol
```

Benefits:

- Eliminates legacy protocol risks
- Reduces ransomware attack surface
- Prevents SMB exploitation

---

## DNS Protection

Reviewed:

- Hosts file
- Local name resolution
- DNS manipulation risks

Security focus:

- Prevent malicious host redirection
- Detect unauthorized modifications

---

## ARP Security

Studied Address Resolution Protocol attacks.

Used:

```cmd
arp -a
```

to inspect cached entries.

Reviewed mitigation:

```cmd
arp -d
```

---

## Remote Desktop

Reviewed Remote Desktop security.

Best practice:

- Disable RDP when unnecessary
- Limit remote access exposure

---

# Application Security

## Microsoft Store

Configured Windows to prefer trusted software sources.

Benefits:

- Reduced malware exposure
- Trusted application installation

---

## Microsoft Defender Antivirus

Reviewed built-in protections including:

- Real-time protection
- Browser integration
- Controlled Folder Access
- Application Guard

---

## Microsoft Office Hardening

Applied Microsoft Office hardening recommendations including:

- Restrict macros
- Reduce attack surface
- Apply Microsoft Attack Surface Reduction (ASR) rules

---

## AppLocker

Studied application allowlisting using:

- Publisher Rules
- Executable Rules
- Script Rules
- Installer Rules

Security benefits:

- Prevent unauthorized execution
- Restrict malware
- Control application usage

---

## Microsoft Edge Hardening

Configured:

- SmartScreen
- Tracking Prevention
- Reputation-based Protection

Security improvements:

- Phishing protection
- Malware download prevention
- Enhanced browser privacy

---

# Storage Security

## BitLocker

Studied full-disk encryption using BitLocker.

Topics covered:

- TPM
- Recovery Keys
- Device Encryption
- Recovery Planning

---

## Windows Sandbox

Explored isolated application execution.

Benefits:

- Safe malware testing
- Disposable environment
- No persistence after closing

---

## Secure Boot

Reviewed Secure Boot functionality.

Benefits:

- Prevent bootkits
- Protect boot chain
- Validate trusted firmware

---

## Backup Strategy

Studied Windows backup mechanisms including:

- File History
- Backup Recovery
- Disaster Recovery

---

# Windows Update Management

Reviewed Windows Update best practices.

Topics included:

- Automatic Updates
- Patch Management
- Security Fixes
- Vulnerability Mitigation

---

# Security Best Practices Learned

- Apply Least Privilege
- Keep Windows Updated
- Use Strong Password Policies
- Enable UAC
- Disable SMBv1
- Use BitLocker
- Enable Defender Firewall
- Harden Microsoft Office
- Restrict Application Execution
- Secure Microsoft Edge
- Enable Backups
- Use Secure Boot
- Monitor Event Logs
- Disable Unused Services
- Disable Unused Hardware

---

# Key Takeaways

This project reinforced the importance of endpoint hardening as a layered security strategy. By leveraging native Windows security features—including User Account Control, Windows Defender Firewall, BitLocker, AppLocker, Secure Boot, Microsoft Defender, and Group Policy—a Windows system can be significantly more resilient against privilege escalation, malware, ransomware, credential attacks, and unauthorized access.

The exercises demonstrated that effective hardening is an ongoing process requiring continuous monitoring, regular patch management, least-privilege enforcement, and proactive security configuration.

---

## Disclaimer

All activities documented in this repository were performed in authorized laboratory environments for educational and defensive cybersecurity purposes only. No techniques were used against systems without explicit permission.
