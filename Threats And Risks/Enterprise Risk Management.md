# Enterprise Risk Management and Cyber Risk Assessment

## Overview

This project demonstrates the practical application of enterprise risk management principles to identify, assess, analyze, respond to, and continuously monitor cybersecurity risks across organizational environments.

The assessment applies industry-recognized risk management methodologies—including NIST SP 800-30 qualitative and quantitative risk assessment techniques—to evaluate business risks, prioritize mitigation strategies, calculate potential financial impact, and improve organizational resilience against cyber threats.

The project simulates the responsibilities of a Security Engineer or Cyber Risk Analyst performing enterprise information security risk assessments as part of an organization's Governance, Risk, and Compliance (GRC) program.

---

# Objectives

- Perform enterprise cyber risk assessments
- Identify organizational assets, threats, and vulnerabilities
- Analyze business impact and likelihood
- Conduct qualitative and quantitative risk analysis
- Calculate SLE and ALE values
- Develop risk treatment strategies
- Monitor evolving risks
- Evaluate supply chain security risks
- Align security recommendations with industry frameworks

---

# Skills Demonstrated

- Enterprise Risk Management
- Cyber Risk Assessment
- Threat Identification
- Vulnerability Assessment
- Business Impact Analysis
- Qualitative Risk Analysis
- Quantitative Risk Analysis
- Risk Prioritization
- Risk Treatment Planning
- Supply Chain Risk Assessment
- Governance, Risk & Compliance (GRC)
- Security Documentation

---

# Frameworks & Methodologies

- NIST SP 800-30
- NIST Risk Management Framework (RMF)
- NIST Cybersecurity Framework (CSF)
- Qualitative Risk Analysis
- Quantitative Risk Analysis
- Single Loss Expectancy (SLE)
- Annualized Loss Expectancy (ALE)
- Supply Chain Risk Management (SCRM)

---

# Project Scenario

An enterprise organization requested a comprehensive cybersecurity risk assessment to evaluate potential threats against its information systems before expanding business operations and deploying additional cloud services.

The assessment focused on protecting critical business assets while balancing operational costs, regulatory requirements, and acceptable organizational risk.

Critical business assets included:

- Customer information
- Financial records
- Employee data
- Enterprise laptops
- Internal servers
- Cloud infrastructure
- Business applications
- Email services
- Intellectual property

---

# Phase 1 — Risk Framing

The first stage established the organization's overall risk management strategy.

The following elements were defined:

## Risk Assumptions

- Enterprise systems are continuously targeted by cybercriminals.
- Customer information is considered highly valuable.
- Cloud services increase the external attack surface.
- Employees remain susceptible to phishing attacks.
- Ransomware represents a significant business threat.

## Risk Constraints

- Security budget limitations
- Staffing availability
- Regulatory compliance requirements
- Legacy system dependencies
- Operational uptime requirements

## Risk Tolerance

The organization determined:

- Zero tolerance for customer data breaches
- Low tolerance for service outages
- Moderate tolerance for operational disruptions during maintenance
- Acceptable financial risk within predefined thresholds

## Business Priorities

- Protect customer trust
- Maintain business continuity
- Ensure regulatory compliance
- Preserve confidentiality
- Protect financial assets

---

# Phase 2 — Asset Identification

Critical enterprise assets were identified and classified.

| Asset | Business Criticality |
|---------|---------------------|
| Customer Database | High |
| Financial Records | High |
| Cloud Infrastructure | High |
| Email Services | Medium |
| Authentication Systems | High |
| Internal Applications | High |
| Employee Laptops | Medium |
| Backup Infrastructure | High |

Each asset was evaluated based on:

- Confidentiality
- Integrity
- Availability

---

# Phase 3 — Threat Identification

Potential threats were categorized into three major groups.

## Human Threats

- Phishing
- Insider threats
- Credential theft
- Social engineering
- Ransomware
- Unauthorized access
- Malware deployment

## Technical Threats

- Software vulnerabilities
- Hardware failure
- Misconfiguration
- Network outages
- Power failures
- Data corruption

## Natural Threats

- Flooding
- Fire
- Earthquakes
- Storm damage

---

# Phase 4 — Vulnerability Assessment

Security weaknesses affecting enterprise systems were identified.

Examples included:

- Weak passwords
- Missing Multi-Factor Authentication
- Outdated software
- Unpatched operating systems
- Publicly exposed services
- Cloud misconfigurations
- Poor access controls
- Insufficient logging
- Inadequate backups

---

# Phase 5 — Risk Assessment

Each identified risk was analyzed using four key factors:

- Threat
- Vulnerability
- Business Impact
- Likelihood

### Example Assessment

| Threat | Vulnerability | Impact | Likelihood |
|---------|---------------|---------|------------|
| Ransomware | Unpatched Systems | High | High |
| Phishing | Weak Security Awareness | High | High |
| Data Breach | Cloud Misconfiguration | High | Medium |
| Power Failure | No UPS | Medium | Medium |
| Flooding | Office Location | High | Low |

---

# Phase 6 — Qualitative Risk Analysis

Each identified risk received a qualitative rating.

Risk levels included:

- Low
- Medium
- High
- Critical

### Example Risk Matrix

| Likelihood | Impact | Overall Risk |
|------------|--------|--------------|
| High | High | Critical |
| Medium | High | High |
| Medium | Medium | Medium |
| Low | High | Medium |
| Low | Low | Low |

The qualitative assessment assisted in prioritizing security investments and remediation efforts.

---

# Phase 7 — Quantitative Risk Analysis

Financial risk calculations were performed using industry-standard formulas.

## Single Loss Expectancy (SLE)

Formula:

```text
SLE = Asset Value × Exposure Factor
```

### Example

Asset Value:

$10,000

Exposure Factor:

90%

Calculation:

```text
SLE = 10,000 × 0.90
SLE = $9,000
```

---

## Annualized Loss Expectancy (ALE)

Formula:

```text
ALE = SLE × Annualized Rate of Occurrence
```

Example:

```text
SLE = $9,000
ARO = 0.5
```

Calculation:

```text
ALE = 9,000 × 0.5
ALE = $4,500
```

This calculation enabled cost-benefit analysis when selecting security controls.

---

# Phase 8 — Risk Treatment

Appropriate risk responses were selected based on business objectives.

## Risk Avoidance

Examples:

- Disabling vulnerable services
- Removing unsupported software
- Eliminating unnecessary internet exposure

---

## Risk Reduction

Examples:

- Multi-Factor Authentication
- Endpoint Detection & Response (EDR)
- Patch management
- Security awareness training
- Network segmentation
- Regular vulnerability scanning

---

## Risk Acceptance

Examples:

- Low-impact risks
- Low-likelihood threats
- Risks with mitigation costs exceeding potential losses

---

## Risk Transfer

Examples:

- Cyber insurance
- Outsourced managed security services
- Vendor contractual agreements

---

# Phase 9 — Continuous Risk Monitoring

The organization established continuous monitoring procedures.

Monitoring activities included:

- Security control effectiveness
- Emerging cyber threats
- Infrastructure changes
- Business expansion
- Compliance audits
- Regulatory updates
- Vulnerability assessments
- Incident response metrics

Continuous monitoring ensured risks remained within acceptable organizational thresholds.

---

# Phase 10 — Supply Chain Risk Management

Third-party suppliers were evaluated as potential sources of cybersecurity risk.

Supply chain categories included:

## Hardware Suppliers

Potential risks:

- Hardware Trojans
- Counterfeit components
- Firmware compromise

## Software Vendors

Potential risks:

- Malicious updates
- Vulnerable software
- Supply chain malware

## Service Providers

Potential risks:

- Cloud outages
- Data breaches
- Insider threats
- Third-party compromise

Security reviews included evaluating vendor security posture, contractual obligations, compliance certifications, and incident response capabilities.

---

# Security Recommendations

## Identity Security

- Enforce Multi-Factor Authentication
- Apply least privilege
- Implement privileged access management
- Strengthen password policies

## Endpoint Security

- Deploy Endpoint Detection & Response (EDR)
- Encrypt enterprise devices
- Maintain asset inventory
- Perform regular patching

## Infrastructure Security

- Network segmentation
- Firewall hardening
- Secure remote access
- Continuous vulnerability management

## Cloud Security

- Secure cloud configurations
- Encrypt sensitive data
- Monitor cloud activity
- Restrict public access

## Risk Governance

- Perform recurring risk assessments
- Maintain enterprise risk register
- Conduct regular security awareness training
- Review business continuity plans
- Update disaster recovery procedures

---

# Governance Alignment

This assessment aligns with recognized cybersecurity and risk management standards including:

- NIST SP 800-30
- NIST Risk Management Framework (RMF)
- NIST Cybersecurity Framework (CSF)
- ISO/IEC 27001
- ISO 31000 Risk Management
- CIS Critical Security Controls

---

# Key Outcomes

- Identified enterprise cyber risks
- Classified critical business assets
- Assessed threats and vulnerabilities
- Performed qualitative risk analysis
- Calculated quantitative financial impact
- Applied enterprise risk treatment strategies
- Evaluated supply chain cybersecurity risks
- Produced actionable security recommendations
- Improved organizational cyber resilience

---

# Technologies & Frameworks

- NIST SP 800-30
- NIST RMF
- NIST Cybersecurity Framework
- ISO/IEC 27001
- ISO 31000
- SLE
- ALE
- Qualitative Risk Analysis
- Quantitative Risk Analysis
- Supply Chain Risk Management (SCRM)

---


## ⚠️ Disclaimer

This project was completed in an authorized cybersecurity training environment for educational and portfolio purposes. All risk assessments, threat analyses, quantitative calculations, and security recommendations were performed on simulated enterprise scenarios and do not represent assessments of production systems.
