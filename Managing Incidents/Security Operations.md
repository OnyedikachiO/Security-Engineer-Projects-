# Becoming a First Responder


---

## Project Overview

This project demonstrates the responsibilities and decision-making process of a cybersecurity first responder during the early stages of a security incident. The focus was on preserving digital evidence, notifying the appropriate stakeholders, supporting containment efforts, understanding business continuity planning, and documenting every action to ensure an effective incident response.

Throughout this project, I applied industry-recognized incident response principles based on guidance from organizations such as **NIST** and the **IETF**, emphasizing evidence preservation, chain of custody, containment strategies, and proper documentation.

---

## Objectives

- Understand the responsibilities of a cybersecurity first responder.
- Learn the correct order of digital evidence preservation.
- Prevent accidental destruction or contamination of forensic evidence.
- Understand stakeholder notification procedures.
- Study containment methods used during active incidents.
- Explore Business Continuity Planning (BCP) concepts.
- Document incident response activities using industry best practices.

---

## Skills Demonstrated

- Incident Response
- Digital Forensics Fundamentals
- Evidence Preservation
- Chain of Custody
- Incident Documentation
- Security Operations (SOC)
- Business Continuity Planning
- Disaster Recovery Planning
- Containment Strategies
- Security Governance
- Blue Team Operations
- Risk Management

---

## Scenario

A production server was suspected of being compromised.

As the first responder, my responsibility was not to immediately remediate the incident, but to preserve evidence, notify the correct personnel, and support the incident response team while ensuring that all actions maintained forensic integrity.

---

# Phase 1 — Preserving Digital Evidence

One of the most important lessons learned was that shutting down an infected system is often the worst possible first action.

Powering off a compromised machine destroys volatile evidence stored in memory and immediately alerts an attacker that they have been discovered.

Instead, I studied the correct evidence preservation order based on volatility.

## Evidence Preservation Priority

| Priority | Evidence |
|----------|----------|
| 1 | Registers and CPU Cache |
| 2 | Routing Table, ARP Cache, Running Processes, Kernel Statistics, RAM |
| 3 | Temporary File Systems |
| 4 | Disk Image |
| 5 | Remote Logs |
| 6 | Physical Configuration & Network Topology |
| 7 | Archival Media / Backups |

### Key Learning

The more volatile the evidence, the sooner it must be collected.

Forensic investigators prioritize RAM before disk because memory contents disappear immediately after power loss.

---

## Evidence Handling Best Practices

I also learned three critical forensic rules.

### Never Power Off the Host

Doing so destroys volatile evidence stored in RAM.

### Never Trust Programs on the Compromised System

Attackers may modify built-in utilities.

Evidence should be collected using trusted forensic tools instead of software installed on the compromised machine.

### Never Modify File Access Times

Simple actions such as copying files can alter metadata.

Forensic tools preserve timestamps to maintain evidence integrity.

---

## Chain of Custody

An important legal concept studied during this project was **Chain of Custody**.

Chain of Custody ensures that digital evidence:

- Remains unaltered
- Is fully documented
- Can be presented in legal proceedings
- Maintains forensic integrity throughout the investigation

Proper documentation ensures investigators can prove that evidence has not been tampered with.

---

# Phase 2 — Incident Escalation

After preserving evidence, the next responsibility is notifying the appropriate stakeholders.

I learned that mature organizations rely on predefined procedures instead of improvisation.

## Incident Playbooks

Playbooks provide standardized response procedures for different incident types, ensuring consistent actions and reducing response time.

### Examples include:

- Phishing
- Malware Infection
- Account Compromise
- Data Exfiltration

---

## Call Trees

A Call Tree defines:

- Who should be notified
- Escalation paths
- Backup contacts
- Management notification process

This structure ensures incidents are communicated quickly and efficiently.

---

## First Responder Responsibilities

Rather than resolving the incident independently, the first responder's responsibilities include:

- Preserving evidence
- Notifying responders
- Avoiding evidence contamination
- Preparing the affected team
- Supporting the incident response process

---

# Phase 3 — Containment

Before eradication or recovery can begin, the incident must first be contained.

Attempting recovery before containment risks reinfection and allows attackers to maintain access.

## Containment Techniques

### Network Segmentation

The compromised host is isolated into a separate network segment to prevent lateral movement.

### Physical Isolation

The infected device is physically removed from users and disconnected from the environment.

### Virtual Isolation

Using **Endpoint Detection and Response (EDR)**, the compromised host is remotely quarantined while remaining powered on.

This method preserves evidence while limiting attacker activity.

---

## Delayed Containment

An interesting defensive strategy involved intentionally slowing an attacker's network connection instead of immediately disconnecting them.

### Benefits include:

- Observing attacker behavior
- Identifying command-and-control infrastructure
- Understanding attack scope
- Collecting additional forensic evidence

---

# Phase 4 — Business Continuity Planning (BCP)

Once containment is established, organizations may invoke a **Business Continuity Plan (BCP).**

A BCP enables critical business operations to continue during major incidents while allowing emergency operational changes outside the normal change management process.

---

## BCP Development Process

I learned the four major phases of Business Continuity Planning:

1. Perform Business Impact Analysis (BIA)
2. Define Recovery Actions
3. Establish Team Responsibilities
4. Test the Plan through Tabletop Exercises

---

## BCP vs DRP

| Business Continuity Plan | Disaster Recovery Plan |
|--------------------------|-------------------------|
| Covers the entire business | Focuses on technical recovery |
| Includes communications | Restores systems and infrastructure |
| Coordinates stakeholders | Restores IT services |

---

## Business Continuity Metrics

Several important recovery metrics were studied.

| Metric | Purpose |
|---------|----------|
| Recovery Point Objective (RPO) | Maximum acceptable data loss |
| Recovery Time Objective (RTO) | Time required to restore hardware |
| Work Recovery Time (WRT) | Time required to restore software and data |
| Maximum Tolerable Downtime (MTD) | Longest acceptable outage |
| Mean Time Between Failures (MTBF) | Average operational time between failures |
| Mean Time To Repair (MTTR) | Average recovery time after failure |

---

# Phase 5 — Incident Documentation

One of the most overlooked responsibilities of a first responder is documentation.

Every action taken during an incident should be recorded.

A proper incident log should include:

- Request Time (UTC)
- Action Performed
- Reason for Action
- Approver
- Person Performing Action
- Completion Time
- Observed Results

Using **UTC** timestamps ensures consistency across systems, log sources, and time zones during investigations.

---

## Key Concepts Learned

- Digital evidence is highly volatile and must be preserved in the correct order.
- Never power off a compromised system unless specifically directed.
- Chain of Custody is essential for legal admissibility.
- Playbooks standardize incident response procedures.
- Call Trees define stakeholder notification and escalation paths.
- Containment must occur before eradication and recovery.
- Business Continuity Plans enable organizations to maintain operations during major incidents.
- Recovery metrics help measure resilience and recovery performance.
- Thorough documentation improves investigations, supports handovers, and captures lessons learned.

---

## Tools & Concepts

- Digital Forensics
- Incident Response Procedures
- Endpoint Detection and Response (EDR)
- Network Segmentation
- Business Continuity Planning (BCP)
- Disaster Recovery Planning (DRP)
- Chain of Custody
- Incident Playbooks
- Call Trees
- Evidence Preservation
- UTC Timekeeping
- NIST Incident Response Lifecycle

---

## Project Outcomes

By completing this project, I strengthened my understanding of how cybersecurity first responders contribute during the critical initial stages of an incident. I practiced forensic evidence preservation principles, learned proper escalation procedures, evaluated containment strategies, explored business continuity planning, and reinforced the importance of detailed documentation for maintaining accountability and supporting successful incident investigations.

---

## Disclaimer

> **Disclaimer:** This project was completed in an authorized cybersecurity training environment for educational purposes. All activities were conducted within controlled lab scenarios designed to simulate real-world incident response workflows. No unauthorized systems or third-party environments were accessed.
