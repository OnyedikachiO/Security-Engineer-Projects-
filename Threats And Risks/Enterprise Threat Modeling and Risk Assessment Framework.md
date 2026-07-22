# Enterprise Threat Modeling and Risk Assessment Framework

## Overview

This project demonstrates the application of enterprise threat modeling methodologies to identify, analyze, prioritize, and mitigate cybersecurity risks across organizational infrastructure.

The assessment combines multiple industry-standard frameworks—including **MITRE ATT&CK**, **STRIDE**, and **DREAD**—to evaluate attack paths, assess business risk, and recommend security controls aligned with secure system design and organizational resilience.

The project simulates the responsibilities of a Security Engineer during the security architecture review phase of the Secure Development Lifecycle (SDL).

---

# Objectives

- Perform structured threat modeling
- Identify organizational assets and attack surfaces
- Analyze threats using MITRE ATT&CK
- Prioritize risks using DREAD
- Categorize threats using STRIDE
- Develop practical security recommendations
- Improve organizational cyber resilience

---

# Skills Demonstrated

- Threat Modeling
- Security Architecture Review
- Risk Assessment
- Attack Surface Analysis
- Security Design
- Secure Development Lifecycle (SDL)
- Enterprise Security Engineering
- MITRE ATT&CK Mapping
- STRIDE Analysis
- DREAD Risk Scoring
- Security Documentation

---

# Tools & Frameworks

- MITRE ATT&CK
- ATT&CK Navigator
- STRIDE
- DREAD
- Risk Assessment Matrix
- Threat Trees
- Security Architecture Diagrams

---

# Project Scenario

An enterprise organization requested a comprehensive threat modeling assessment before deploying a new cloud-hosted application.

The engagement focused on:

- Customer Personally Identifiable Information (PII)
- Financial records
- Cloud infrastructure
- Internal web applications
- Customer Relationship Management (CRM) systems

The objective was to identify realistic attack scenarios before production deployment.

---

# Phase 1 — Scope Definition

The assessment began by defining critical assets and trust boundaries.

## Critical Assets

- Customer PII
- Financial transactions
- Authentication systems
- Web applications
- Cloud storage
- Internal APIs
- CRM platform

## Trust Boundaries

- Internet
- Load Balancer
- Web Application
- Authentication Service
- Internal API
- Database
- Cloud Storage

---

# Phase 2 — Asset Identification

Each component was evaluated for:

- Confidentiality requirements
- Integrity requirements
- Availability requirements

### Example

| Asset | CIA Priority |
|--------|--------------|
| Customer Database | High |
| Payment Gateway | High |
| CRM | Medium |
| Cloud Storage | High |
| Internal API | High |

---

# Phase 3 — Threat Identification

Potential threats were identified across multiple categories.

Examples include:

- Credential Theft
- Phishing
- SQL Injection
- Remote Code Execution (RCE)
- Insider Threats
- Privilege Escalation
- Cloud Misconfiguration
- Denial of Service (DoS)
- Data Exfiltration
- Session Hijacking

---

# Phase 4 — Threat Tree Construction

Threat trees were created to visualize attack paths.

### Example Attack Tree

```text
Steal Customer Data
│
├── Exploit Web Application
│      ├── SQL Injection
│      ├── RCE
│      └── Authentication Bypass
│
├── Compromise Cloud Storage
│      ├── Weak IAM
│      ├── Public Bucket
│      └── Stolen Credentials
│
└── Phishing Campaign
       ├── Credential Theft
       └── MFA Fatigue
```

---

# Phase 5 — MITRE ATT&CK Mapping

Relevant adversary techniques were mapped to enterprise assets.

### Example Techniques

| Technique | ATT&CK ID |
|-----------|-----------|
| Exploit Public-Facing Application | T1190 |
| Exploitation for Privilege Escalation | T1068 |
| Data from Cloud Storage | T1530 |
| Valid Accounts | T1078 |
| Credential Dumping | T1003 |
| Phishing | T1566 |
| Network Denial of Service | T1498 |

---

## ATT&CK Navigator Usage

Threat techniques were visualized using ATT&CK Navigator.

Activities included:

- Creating enterprise layers
- Selecting threat groups
- Filtering techniques
- Annotating high-risk techniques
- Scoring attack methods
- Exporting threat matrices

---

## Threat Group Research

Threat actor techniques were reviewed for groups known to target enterprise environments.

Examples included:

- APT28
- APT29
- FIN7
- Carbanak
- Lazarus Group

The associated tactics and techniques informed risk prioritization and defensive planning.

---

# Phase 6 — STRIDE Threat Analysis

Threats were categorized using Microsoft's STRIDE framework.

| STRIDE Category | Example Threat |
|-----------------|----------------|
| Spoofing | Credential Theft |
| Tampering | SQL Injection |
| Repudiation | Missing Audit Logs |
| Information Disclosure | Public Cloud Storage |
| Denial of Service | DDoS Attack |
| Elevation of Privilege | Local Privilege Escalation |

### STRIDE Assessment Example

| System Component | Threat Category |
|------------------|-----------------|
| Login Portal | Spoofing |
| Database | Tampering |
| Audit Logs | Repudiation |
| Cloud Storage | Information Disclosure |
| Web Server | Denial of Service |
| Admin Console | Elevation of Privilege |

---

# Phase 7 — DREAD Risk Assessment

Each vulnerability was scored using Microsoft's DREAD methodology.

### Criteria

- Damage
- Reproducibility
- Exploitability
- Affected Users
- Discoverability

### Example Risk Scores

| Vulnerability | DREAD Score |
|---------------|------------:|
| Remote Code Execution | 8.0 |
| SQL Injection | 7.5 |
| Cloud Misconfiguration | 7.0 |
| Insecure Direct Object Reference (IDOR) | 6.5 |
| Information Disclosure | 5.0 |

---

# Phase 8 — Risk Prioritization

High-priority findings included:

- Public-facing application exposure
- Weak IAM permissions
- Cloud storage exposure
- Missing MFA enforcement
- Privilege escalation paths
- Sensitive data exposure

---

# Security Recommendations

## Identity Security

- Enforce Multi-Factor Authentication (MFA)
- Apply Least Privilege
- Review IAM Roles
- Monitor Privileged Accounts

### Application Security

- Adopt Secure Coding Practices
- Perform Input Validation
- Conduct Regular Vulnerability Scanning
- Implement Patch Management

### Cloud Security

- Restrict Public Storage Access
- Encrypt Sensitive Data
- Enable Audit Logging
- Implement Continuous Cloud Monitoring

### Monitoring

- Deploy SIEM
- Centralize Logging
- Configure Anomaly Detection
- Improve Incident Response Workflows

---

# Governance Alignment

The assessment aligns with recognized industry standards including:

- NIST SP 800-53
- NIST Cybersecurity Framework (CSF)
- MITRE ATT&CK
- STRIDE
- DREAD
- ISO/IEC 27001

---

# Key Outcomes

- Identified enterprise attack paths
- Prioritized critical security risks
- Applied multiple threat modeling methodologies
- Improved visibility into attack surfaces
- Strengthened cloud and application security posture
- Produced actionable mitigation recommendations

---

# Technologies & Frameworks

- MITRE ATT&CK
- ATT&CK Navigator
- STRIDE
- DREAD
- NIST SP 800-53
- NIST Cybersecurity Framework
- ISO/IEC 27001

---


# ⚠️ Disclaimer

This project was completed in an authorized cybersecurity training environment for educational and portfolio purposes. All threat modeling, risk assessments, and security analyses were performed on simulated enterprise scenarios and do not represent assessments of production systems.
