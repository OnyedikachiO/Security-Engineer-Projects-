# Incident Response and Management Fundamentals

Understanding Incident Response (IR) and Incident Management (IM) processes used by security teams to detect, investigate, contain, eradicate, recover from, and learn from cybersecurity incidents.

---

## Overview

This project documents the core principles of Incident Response (IR) and Incident Management (IM) from a Security Engineering perspective.

The project explores how Security Operations Centers (SOCs), Incident Responders, Security Engineers, Digital Forensics teams, and business stakeholders collaborate to identify, investigate, contain, eradicate, recover from, and review cyber incidents while minimizing business impact.

Unlike penetration testing projects, this repository focuses on defensive security operations and incident coordination.

---

## Objectives

- Understand the lifecycle of a cyber incident
- Differentiate Incident Response from Incident Management
- Learn incident severity levels
- Understand roles involved during cyber incidents
- Study the NIST Incident Management process
- Explore common mistakes that weaken incident response
- Understand how Security Engineers contribute during incidents

---

# Skills Demonstrated

- Incident Response (IR)
- Incident Management (IM)
- Security Operations Center (SOC) concepts
- Incident triage
- Digital Forensics fundamentals
- Threat analysis
- Incident containment
- Eradication planning
- Recovery procedures
- Root Cause Analysis
- Security documentation
- Security Engineering
- NIST Incident Response Framework
- Security Operations

---

# Incident Response vs Incident Management

| Incident Response | Incident Management |
|-------------------|---------------------|
| Technical investigation | Coordination of response |
| Determines what happened | Determines how to respond |
| Collects forensic evidence | Coordinates stakeholders |
| Investigates attack scope | Makes containment decisions |
| Supports technical remediation | Manages communication and recovery |

---

# Incident Lifecycle

## 1. Event

Normal system activity or anomaly detected.

↓

## 2. Alert

Security monitoring tools identify suspicious behavior.

Examples include:

- SIEM alerts
- Endpoint Detection & Response (EDR)
- Antivirus detections
- Network monitoring alerts

↓

## 3. Incident

An alert becomes an incident after investigation determines potential business impact or compromise.

↓

## 4. Investigation

The Incident Response team determines:

- What happened
- Who was affected
- How compromise occurred
- Scope of compromise
- Indicators of Compromise (IoCs)

↓

## 5. Containment

Actions are taken to stop the attacker from causing further damage.

↓

## 6. Eradication

The root cause of the incident is removed.

↓

## 7. Recovery

Systems are restored to normal business operations.

↓

## 8. Lessons Learned

Processes, controls, and detections are improved.

---

# Incident Severity Levels

## Level 1 — SOC Incident

Characteristics:

- Isolated event
- Limited impact
- Managed by individual SOC analyst

Example:

- Single phishing email blocked

---

## Level 2 — CERT Incident

Characteristics:

- Multiple analysts involved
- Further investigation required
- Scope still uncertain

Example:

- Multiple employees receive phishing email

---

## Level 3 — CSIRT Incident

Characteristics:

- Entire SOC engaged
- Active containment
- Digital forensics
- Malware analysis
- Recovery planning

Example:

- Malware execution confirmed

---

## Level 4 — Crisis Management Team (CMT)

Characteristics:

- Executive involvement
- Legal teams
- Communications teams
- Regulatory notifications
- Potential business shutdown

Example:

- Enterprise ransomware attack

---

# Roles During an Incident

## SOC Analyst

- Monitors alerts
- Performs investigations
- Conducts initial triage

---

## SOC Lead

- Coordinates analysts
- Escalates incidents
- Assigns investigation tasks

---

## Forensic Analyst

- Examines disks
- Recovers evidence
- Investigates attack timeline

---

## Malware Analyst

- Reverse engineers malware
- Develops Indicators of Compromise (IoCs)
- Supports detection improvements

---

## Threat Hunter

- Searches for hidden threats
- Develops new detection rules
- Improves monitoring

---

## Security Engineer

Responsible for:

- Security architecture
- Log integration
- Security tooling
- Supporting incident investigations
- Implementing remediation

---

## Incident Manager

Coordinates:

- Communication
- Documentation
- Response activities
- Stakeholder engagement
- Decision making

---

## Subject Matter Experts (SMEs)

Provide technical expertise regarding:

- Active Directory
- Cloud platforms
- Applications
- Infrastructure
- Networking

---

## Crisis Management Team

Executive leadership responsible for strategic decisions during major incidents.

---

# NIST Incident Management Lifecycle

## 1. Preparation

Activities include:

- Playbooks
- Incident response plans
- Contact lists
- Threat hunting
- Tabletop exercises

---

## 2. Detection and Analysis

Focus areas:

- Alert validation
- Log analysis
- Malware investigation
- Digital forensics
- Scope determination

---

## 3. Containment

Objectives:

- Stop attacker activity
- Isolate affected systems
- Prevent lateral movement

---

## 4. Eradication

Objectives:

- Remove malware
- Eliminate persistence
- Close attack vectors

---

## 5. Recovery

Objectives:

- Restore systems
- Validate integrity
- Resume business operations

---

## 6. Lessons Learned

Activities:

- Root Cause Analysis
- Process improvements
- Detection tuning
- Documentation updates

---

# Common Incident Response Pitfalls

## Insufficient Hardening

Weak security configurations increase the likelihood of compromise.

---

## Insufficient Logging

Limited visibility delays detection and investigation.

---

## Poor Alert Quality

Too many false positives create alert fatigue.

---

## Incorrect Scope Assessment

Underestimating scope leaves attackers active.

Overestimating scope causes unnecessary business disruption.

---

## Lack of Accountability

Actions discussed but not assigned delay incident resolution.

---

## Poor Backup Strategy

Missing or insecure backups significantly increase recovery time after ransomware or destructive attacks.

---

# Security Engineering Takeaways

This project reinforced several important Security Engineering principles:

- Security monitoring depends on quality logging.
- Incident Response and Incident Management are complementary disciplines.
- Accurate incident scoping is essential for effective containment.
- Preparation significantly improves incident outcomes.
- Documentation and communication are as important as technical investigation.
- Security Engineers play a critical role in enabling visibility, supporting investigations, and implementing long-term improvements.

---

# Technologies & Concepts

- Security Operations Center (SOC)
- Incident Response
- Incident Management
- Digital Forensics
- Malware Analysis
- Threat Hunting
- SIEM
- EDR
- Antivirus
- Indicators of Compromise (IoCs)
- NIST Incident Response Framework

---

# Key Learning Outcomes

- Distinguished Incident Response from Incident Management
- Understood incident severity escalation
- Learned responsibilities of incident response stakeholders
- Studied the NIST Incident Response lifecycle
- Identified common operational pitfalls
- Strengthened understanding of defensive security operations

---

## Disclaimer

This project is based on structured cybersecurity training completed in a controlled lab environment. All activities were conducted within authorized educational systems and are intended solely to demonstrate Incident Response and Security Engineering concepts. No unauthorized systems were accessed or targeted.
