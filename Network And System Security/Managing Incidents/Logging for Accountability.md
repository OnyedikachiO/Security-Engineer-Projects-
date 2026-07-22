# Logging for Accountability

Understanding how logging, Security Information and Event Management (SIEM), and accountability support incident response, forensic investigations, and non-repudiation within enterprise environments.

---

## Overview

This project explores the role of logging in modern Security Operations and Incident Response. It examines how organizations collect, store, correlate, and protect log data to establish accountability and support forensic investigations.

The project also introduces SIEM architecture, log ingestion methods, storage strategies, and practical log analysis using Splunk to investigate security events and validate user activity.

Unlike offensive security projects, this repository focuses on defensive security practices that improve visibility, auditability, and incident response.

---

## Objectives

- Understand accountability within the IAAA security model
- Learn the importance of logging for incident response
- Study non-repudiation and evidentiary integrity
- Understand SIEM architecture and components
- Explore log ingestion and storage methods
- Identify common log sources
- Learn log correlation techniques
- Perform basic security investigations using Splunk

---

# Skills Demonstrated

- Security Logging
- Accountability
- Non-Repudiation
- Security Information and Event Management (SIEM)
- Splunk Fundamentals
- Log Correlation
- Incident Response
- Security Monitoring
- Digital Forensics Fundamentals
- Event Investigation
- Security Operations (SOC)
- Audit Logging
- Security Engineering

---

# Accountability in Security

Accountability is the fourth pillar of the Identification, Authentication, Authorization, and Accountability (IAAA) model.

Its purpose is to ensure that every action performed within an environment can be traced back to an authenticated user or system.

Proper accountability requires:

- Reliable logging
- Secure log storage
- Tamper protection
- Accurate timestamps
- Long-term retention

Without trustworthy logs, organizations cannot confidently determine who performed an action during a security investigation.

---

# Non-Repudiation

Non-repudiation ensures that users cannot deny actions they performed.

Logging supports non-repudiation by providing verifiable records of:

- User logins
- File creation
- Process execution
- Email activity
- Administrative actions
- Network events

Maintaining log integrity is essential because altered or incomplete logs lose their evidentiary value during incident response and compliance audits.

---

# Security Information and Event Management (SIEM)

A SIEM collects, indexes, searches, and analyzes security events from multiple systems across an enterprise.

Core capabilities include:

- Real-time log ingestion
- Centralized log storage
- Event correlation
- Security monitoring
- Threat detection
- Historical investigations
- Dashboard visualization
- Alert generation

Common SIEM platforms include:

- Splunk
- Wazuh
- Elastic (ELK Stack)
- IBM QRadar

---

# SIEM Architecture

A typical SIEM consists of three major components.

## Search Head

Responsible for:

- Searching indexed data
- Running queries
- Creating dashboards
- Displaying investigation results

---

## Indexer

Responsible for:

- Parsing incoming logs
- Indexing data
- Storing searchable events

---

## Forwarder

Responsible for:

- Collecting logs
- Sending events securely to the SIEM
- Supporting centralized logging

---

# Log Ingestion Methods

Common techniques for ingesting security data include:

- Agent / Forwarder
- Syslog
- Port forwarding
- File upload

Reliable log ingestion is essential because incomplete or missing data weakens investigations and accountability.

---

# Log Storage

Security logs often follow a storage lifecycle.

## Hot Storage

Frequently accessed logs stored on high-performance storage.

Typical retention:

- Recent investigations
- Active monitoring

---

## Warm Storage

Less frequently accessed logs retained for medium-term investigations.

---

## Cold Storage

Long-term archival storage optimized for cost rather than speed.

Used for:

- Compliance
- Historical investigations
- Legal requirements
- Regulatory audits

---

# Common Log Sources

## Manual Logs

Created by individuals.

Examples include:

- Change logs
- Maintenance records
- Administrative documentation

---

## Automated Logs

Generated automatically by systems or applications.

Examples include:

- Operating system logs
- Application logs
- Authentication logs
- Firewall logs
- Endpoint logs

---

## Communication Logs

Additional sources that support investigations.

Examples include:

- Email logs
- Messaging platforms
- Collaboration tools

---

# Log Correlation

Log correlation combines multiple data sources to build a complete timeline of an incident.

Examples include correlating:

- Authentication logs
- Email activity
- Browser history
- Firewall events
- Endpoint telemetry
- Process creation logs

Correlation improves visibility and enables investigators to determine how an attack occurred and its overall impact.

---

# Practical SIEM Investigation

A Splunk dataset was analyzed to reinforce core logging and accountability concepts.

The investigation included:

- Reviewing indexed security events
- Filtering events by time range
- Identifying unique users
- Investigating user activity
- Examining process creation events
- Correlating related event IDs
- Tracing system utilities used during execution

---

# Investigation Summary

Key observations included:

- Total indexed events: **12,256**
- Events analyzed for April 15–16, 2022: **12,250**
- Unique users identified: **4**
- User activity investigated for **James**
- Oldest observed utility: **wmic**
- Correlated process creation events using associated Event IDs

---

# Security Engineering Takeaways

This project reinforced several important Security Engineering principles:

- Logging is foundational for effective incident response.
- Accountability depends on trustworthy and tamper-resistant log data.
- SIEM platforms improve visibility by centralizing security events.
- Correlating multiple log sources provides better investigative context.
- Proper log retention supports compliance, audits, and forensic investigations.
- Security monitoring is only as effective as the quality and completeness of collected logs.

---

# Technologies & Concepts

- Splunk
- SIEM
- Security Logging
- Event Correlation
- Security Operations Center (SOC)
- Incident Response
- Audit Logging
- Log Ingestion
- Log Retention
- Hot, Warm, and Cold Storage
- Non-Repudiation
- IAAA Model

---

# Key Learning Outcomes

- Understood the accountability pillar of the IAAA model
- Studied how logging supports non-repudiation
- Learned SIEM architecture and data ingestion methods
- Explored log storage strategies for compliance
- Identified manual and automated log sources
- Applied log correlation during a Splunk investigation
- Strengthened understanding of logging within Security Operations

---

## Disclaimer

This project was completed in an authorized cybersecurity training environment using a simulated SIEM dataset. All activities were conducted within a controlled lab for educational purposes to demonstrate security logging, accountability, and incident response concepts.
