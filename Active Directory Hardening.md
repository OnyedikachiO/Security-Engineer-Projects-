# Active Directory Hardening

A hands-on Security Engineering project focused on strengthening Microsoft Active Directory environments against common enterprise attack techniques by implementing secure authentication methods, enforcing least privilege, applying Group Policy security configurations, and following Microsoft's recommended security baselines.

This project demonstrates practical Active Directory hardening techniques performed in a controlled Windows Server laboratory environment.

---

# Project Overview

Microsoft Active Directory (AD) is the backbone of identity and access management in many enterprise environments. Because Active Directory stores user identities, authentication mechanisms, authorization policies, and critical infrastructure components, it remains one of the most targeted technologies during cyber attacks.

This project explores defensive strategies for securing Active Directory against credential theft, privilege escalation, lateral movement, password attacks, Kerberos abuse, and misconfigurations using native Microsoft security features and administrative best practices.

The project emphasizes proactive security through authentication hardening, access control, password management, policy enforcement, auditing, and Microsoft's Security Compliance Toolkit.

---

# Objectives

- Strengthen Active Directory authentication security
- Reduce opportunities for privilege escalation
- Implement secure password policies
- Apply Least Privilege principles
- Secure communication protocols
- Deploy Microsoft security baselines
- Protect against common Active Directory attacks
- Improve enterprise identity security posture

---

# Lab Environment

| Component | Details |
|-----------|---------|
| Platform | TryHackMe |
| Environment | Microsoft Windows Server Active Directory Lab |
| Technologies | Active Directory Domain Services (AD DS) |
| Tools Used | Group Policy Management Editor, Local Security Policy, Active Directory Domains and Trusts, Microsoft Security Compliance Toolkit, Policy Analyzer, PowerShell |

---

# Skills Demonstrated

- Active Directory Administration
- Active Directory Security Hardening
- Group Policy Management
- Authentication Security
- Password Policy Management
- Kerberos Security
- LDAP Security
- SMB Security
- Least Privilege Implementation
- Role-Based Access Control (RBAC)
- Tiered Administration
- Enterprise Identity Management
- Security Baseline Deployment
- Policy Analysis
- Windows Server Administration
- Security Auditing
- Active Directory Trust Management

---

# Active Directory Fundamentals

## Domain

Reviewed the role of the Active Directory domain as the central administrative boundary responsible for storing users, groups, computers, policies, and security information.

Key concepts:

- Centralized authentication
- Resource management
- Security policy enforcement
- Identity management

---

## Domain Controllers

Studied Domain Controllers as the authentication and authorization servers responsible for managing:

- User logons
- Kerberos authentication
- Group Policy distribution
- Active Directory replication
- Domain resource access

Security considerations included protecting Domain Controllers as Tier 0 assets.

---

## Trees and Forests

Explored Active Directory's logical structure.

### Trees

Reviewed domain relationships within a tree, including:

- Parent domains
- Child domains
- Shared namespaces
- Trust relationships

### Forests

Studied forest architecture, including:

- Shared schema
- Global Catalog
- Forest-wide trust
- Enterprise administration

---

## Active Directory Trusts

Reviewed how trust relationships enable secure resource sharing between domains.

Trust models studied included:

### Based on Characteristics

- Transitive Trust
- Non-Transitive Trust

### Based on Direction

- One-Way Trust
- Two-Way Trust

Security focus:

- Minimize unnecessary trust relationships
- Monitor cross-domain access
- Reduce attack paths

---

## Containers and Leaf Objects

Explored the hierarchical structure of Active Directory objects.

Reviewed:

- Organizational Containers
- Leaf Objects
- Users
- Groups
- Computers
- Services

---

# Authentication Hardening

## LAN Manager (LM) Hash Protection

Studied legacy LM hash storage and its security risks.

Implemented Group Policy settings to:

- Prevent storage of LM hashes
- Reduce password cracking risk
- Improve credential protection

Security benefit:

- Eliminates weak password hash storage
- Improves resistance against offline attacks

---

## SMB Signing

Configured SMB packet signing through Group Policy.

Benefits include:

- Integrity verification
- Detection of Man-in-the-Middle attacks
- Secure file sharing communications

---

## LDAP Signing

Configured LDAP signing requirements to enforce authenticated LDAP communication.

Benefits:

- Prevent replay attacks
- Protect directory communications
- Reduce LDAP relay attacks

---

## Password Rotation

Reviewed enterprise password rotation strategies.

Approaches studied:

- PowerShell automation
- Multi-Factor Authentication (MFA)
- Group Managed Service Accounts (gMSA)

Security objective:

- Reduce credential reuse
- Limit password exposure
- Improve operational security

---

# Password Policy Hardening

Configured password policies through Group Policy Management.

Security controls reviewed included:

- Password history enforcement
- Minimum password length
- Complexity requirements
- Password expiration
- Password reuse prevention

These policies significantly increase resistance against:

- Brute-force attacks
- Dictionary attacks
- Password spraying
- Credential stuffing

---

# Least Privilege Implementation

## Principle of Least Privilege

Applied the principle that users, applications, and services should receive only the permissions required to perform legitimate tasks.

Security benefits include:

- Reduced attack surface
- Limited privilege escalation
- Improved containment
- Better accountability

---

## Account Types

Reviewed secure account separation.

### Standard User Accounts

Used for:

- Daily productivity
- Email
- Browsing
- Office applications

### Privileged Accounts

Reserved for:

- System administration
- Active Directory management
- Server maintenance

### Shared Accounts

Reviewed risks associated with shared accounts and situations where limited temporary access may be required.

---

## Role-Based Access Control (RBAC)

Studied Role-Based Access Control implementation for enterprise environments.

Reviewed permission assignment based on:

- Job function
- Organizational role
- Administrative responsibility

Benefits:

- Simplified administration
- Reduced excessive permissions
- Improved auditing

---

# Tiered Administrative Model

Reviewed Microsoft's Tiered Administration Model.

## Tier 0

Critical infrastructure including:

- Domain Controllers
- Enterprise Admins
- Domain Admins
- Forest-wide administrative accounts

---

## Tier 1

Includes:

- Member servers
- Enterprise applications
- Administrative services

---

## Tier 2

Includes:

- End-user devices
- Standard user workstations
- Office productivity systems

---

## Security Goal

Prevent privileged credentials from crossing security boundaries to reduce credential theft and lateral movement.

---

# Account Auditing

Reviewed three critical audit categories.

## Usage Audits

Monitor:

- Account activity
- Login behavior
- Resource access

---

## Privilege Audits

Review:

- Administrative rights
- Excessive permissions
- Group memberships

---

## Change Audits

Track:

- Password modifications
- Permission changes
- Policy updates
- Account configuration

---

# Microsoft Security Compliance Toolkit (MSCT)

Implemented Microsoft's recommended security baseline approach.

Components studied:

- Security Baselines
- Group Policy backups
- Security templates
- Baseline deployment

Benefits:

- Faster hardening
- Consistent configuration
- Microsoft best practices
- Standardized enterprise security

---

# Policy Analyzer

Explored Microsoft's Policy Analyzer utility.

Capabilities include:

- Compare Group Policies
- Detect conflicting settings
- Identify redundant policies
- Validate security baselines

Use cases:

- Enterprise policy reviews
- Configuration validation
- Security assessments

---

# Defending Against Common Active Directory Attacks

## Kerberoasting

Studied how attackers abuse Kerberos Ticket Granting Service (TGS) requests to obtain service account hashes for offline cracking.

Mitigation strategies reviewed:

- Strong service account passwords
- Frequent password rotation
- Multi-Factor Authentication
- Monitoring Kerberos activity

---

## Weak Password Attacks

Reviewed common password attacks including:

- Brute Force
- Dictionary Attacks
- Password Spraying
- Credential Reuse

Mitigations implemented:

- Strong password policies
- Complexity enforcement
- Password history
- Account lockout

---

## RDP Brute Force

Reviewed risks associated with exposing Remote Desktop Protocol.

Best practices:

- Restrict RDP exposure
- Monitor authentication attempts
- Enforce MFA
- Apply network segmentation

---

## Insecure Network Shares

Reviewed risks of publicly accessible SMB shares.

PowerShell command studied:

```powershell
Get-SmbOpenFile
```

Security recommendations:

- Remove unnecessary shares
- Restrict permissions
- Apply least privilege
- Audit shared resources

---

# Security Best Practices Implemented

- Disable LAN Manager hash storage
- Enable SMB Signing
- Require LDAP Signing
- Enforce password complexity
- Configure password history
- Rotate privileged credentials
- Implement Least Privilege
- Separate administrative accounts
- Apply Tiered Administration
- Audit privileged accounts
- Deploy Microsoft Security Baselines
- Review Group Policies regularly
- Protect Domain Controllers
- Secure authentication mechanisms
- Monitor trust relationships

---

# Key Takeaways

This project reinforced that securing Active Directory extends far beyond configuring users and groups. Effective enterprise identity protection requires layered defenses that combine secure authentication, strong password policies, least privilege, administrative tiering, protocol hardening, continuous auditing, and Microsoft's recommended security baselines.

The implementation of Group Policy security settings, SMB and LDAP signing, password controls, Microsoft Security Compliance Toolkit, and Active Directory administrative best practices significantly improves resilience against credential theft, privilege escalation, Kerberoasting, password attacks, and lateral movement.

---

# Technologies Used

- Microsoft Active Directory
- Windows Server
- Group Policy Management
- Active Directory Domains and Trusts
- PowerShell
- Microsoft Security Compliance Toolkit
- Policy Analyzer
- LDAP
- SMB
- Kerberos

---

# Disclaimer

All activities documented in this repository were performed in authorized laboratory environments for educational and defensive cybersecurity purposes only. No attacks were performed against systems without explicit authorization.
