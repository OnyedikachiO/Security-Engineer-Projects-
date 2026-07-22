# Implementing Cloud Security Controls in AWS

## Project Overview

Cloud environments require multiple layers of security to protect workloads, identities, networks, storage, and applications from unauthorized access and cyber threats. Cloud providers offer native security services that enable organizations to implement defense-in-depth strategies while maintaining scalability and operational efficiency.

In this project, I implemented core AWS security controls within a controlled cloud lab environment. The implementation focused on securing network access, protecting cloud storage, improving visibility through monitoring and logging, understanding disaster recovery strategies, and automating patch management using AWS-native security services.

The project demonstrates practical cloud security implementation by configuring AWS services that strengthen the confidentiality, integrity, and availability of cloud resources.

---

# Objectives

- Implement network security controls in AWS.
- Configure secure access to cloud resources using Network ACLs.
- Understand the purpose of Security Groups and AWS firewalls.
- Secure cloud storage using server-side encryption.
- Explore AWS monitoring and logging services.
- Generate and review IAM credential reports.
- Understand disaster recovery strategies in cloud environments.
- Explore automated patch management using AWS Systems Manager.
- Apply cloud security best practices using AWS native services.

---

# Skills Learned

- AWS Security Fundamentals
- Cloud Network Security
- Network Access Control Lists (NACLs)
- Security Groups
- AWS Virtual Private Cloud (VPC)
- Amazon S3 Security
- Data Encryption
- AWS Identity and Access Management (IAM)
- Cloud Monitoring
- Security Logging
- Disaster Recovery Planning
- Patch Management
- Cloud Hardening
- Defense in Depth

---

# Tools & Technologies

- Amazon Web Services (AWS)
- Amazon VPC
- Security Groups
- Network ACLs (NACL)
- Amazon S3
- AWS Identity and Access Management (IAM)
- AWS CloudTrail
- AWS CloudWatch
- AWS GuardDuty
- AWS Systems Manager
- AWS Patch Manager
- Server-Side Encryption (SSE)

---

# Project Tasks

## Task 1: Implemented Network Security Controls

The first phase of the project focused on securing cloud networking using AWS native security services.

AWS provides multiple layers of protection that work together to reduce the attack surface of cloud resources.

These layers include:

- Security Groups
- Network Access Control Lists (NACLs)
- DNS Firewall
- Network Firewall

This layered approach ensures traffic is filtered before reaching cloud workloads.

---

## Task 2: Studied AWS Security Groups

Security Groups act as stateful virtual firewalls attached directly to AWS resources such as EC2 instances.

Unlike traditional firewalls, Security Groups only contain **Allow** rules.

Traffic that is not explicitly permitted is automatically denied.

Key characteristics include:

- Stateful inspection
- Instance-level protection
- Default deny behavior
- Granular inbound and outbound rules

This follows the security principle:

> **Deny all traffic unless explicitly allowed.**

Implementing this model significantly reduces unnecessary network exposure.

---

## Task 3: Configured Network Access Control Lists (NACLs)

Unlike Security Groups, Network ACLs operate at the subnet level and provide both **Allow** and **Deny** rules.

NACLs provide an additional layer of network filtering before traffic reaches cloud resources.

Capabilities include:

- Stateless packet filtering
- Explicit allow rules
- Explicit deny rules
- IP-based filtering
- Subnet-level protection

Combining Security Groups with NACLs creates a defense-in-depth architecture that limits unauthorized network access.

---

## Task 4: Implemented a Network ACL Rule to Block SSH

To strengthen remote access security, I configured a Network ACL to deny inbound SSH traffic on TCP port **22**.

### Implementation Steps

- Navigated to the AWS VPC console.
- Created a new Network ACL.
- Associated the ACL with the target VPC.
- Edited inbound rules.
- Added a deny rule for TCP Port 22.
- Applied the updated rule set.

### Security Benefit

Blocking unnecessary remote administration ports reduces the attack surface and limits opportunities for brute-force attacks or unauthorized remote access.

---

## Task 5: Explored AWS Network Protection Services

AWS provides additional security services beyond Security Groups and NACLs.

### AWS DNS Firewall

Protects cloud workloads from communicating with malicious domains by filtering DNS requests.

Benefits include:

- Blocking malicious domains
- Preventing command-and-control communication
- Reducing malware activity

---

### AWS Network Firewall

Provides centralized network traffic inspection across AWS environments.

Capabilities include:

- Stateful inspection
- Intrusion prevention
- Traffic filtering
- Policy enforcement

Together, these services improve visibility and strengthen network defenses.

---

## Task 6: Secured Cloud Storage

Protecting stored data is a critical component of cloud security.

The project explored storage security principles including:

- Encryption at rest
- Geographic restrictions
- Role-Based Access Control (RBAC)
- Secure connection strings
- Physical security considerations

These controls help preserve the confidentiality and integrity of sensitive cloud data.

---

## Task 7: Created an Encrypted Amazon S3 Bucket

To improve storage security, I created an Amazon S3 bucket with Server-Side Encryption enabled.

### Implementation Steps

- Navigated to Amazon S3.
- Created a new S3 bucket.
- Configured a globally unique bucket name.
- Selected the AWS region.
- Enabled Server-Side Encryption (SSE).
- Selected Amazon S3 managed encryption keys.
- Created the encrypted bucket.

### Security Benefit

Server-side encryption protects data stored in S3 by encrypting objects before they are written to disk, helping safeguard sensitive information if storage media is compromised.

---

## Task 8: Explored Disaster Recovery Strategies

Business continuity depends on maintaining reliable backup and disaster recovery processes.

I examined three cloud disaster recovery models.

### Cold Disaster Recovery

Characteristics:

- Lowest implementation cost
- Longest Recovery Time Objective (RTO)
- Requires restoration of backups before operations resume

---

### Warm Disaster Recovery

Characteristics:

- Near real-time synchronization
- Faster recovery
- Moderate operational cost

---

### Hot Disaster Recovery

Characteristics:

- Active-active infrastructure
- Near-zero downtime
- Highest availability
- Highest implementation cost

Selecting the appropriate disaster recovery model depends on business requirements, acceptable downtime, and budget.

---

## Task 9: Implemented Monitoring and Logging Concepts

Continuous monitoring enables organizations to detect suspicious activity and maintain visibility across cloud environments.

AWS provides several services for centralized monitoring and auditing.

---

### AWS Identity and Access Management (IAM)

IAM provides visibility into user accounts and credential usage.

I explored the generation of credential reports containing information such as:

- User creation dates
- Password age
- Password usage
- MFA status
- Credential lifecycle

Credential reports assist with security auditing and identity governance.

---

### AWS CloudTrail

CloudTrail records API activity across AWS services.

Captured information includes:

- API requests
- User activity
- Source IP addresses
- Event timestamps

CloudTrail provides a detailed audit trail for incident investigations and compliance reporting.

---

### AWS CloudWatch

CloudWatch monitors cloud infrastructure by collecting operational metrics and generating alerts.

Capabilities include:

- Resource monitoring
- Performance metrics
- Alert generation
- Operational visibility

Continuous monitoring helps identify abnormal behavior before it impacts production systems.

---

### AWS GuardDuty

GuardDuty provides intelligent threat detection by continuously monitoring AWS accounts for malicious or unauthorized behavior.

Examples include:

- Suspicious API activity
- Credential compromise
- Reconnaissance attempts
- Unauthorized access

GuardDuty enhances cloud threat detection without requiring extensive manual configuration.

---

## Task 10: Generated an IAM Credential Report

To improve identity visibility, I generated an IAM Credential Report.

### Implementation Steps

- Opened AWS Identity and Access Management (IAM).
- Navigated to Credential Reports.
- Generated a new report.
- Downloaded the report in CSV format.
- Reviewed credential information.

The report provided valuable security information including:

- Password last changed
- Password last used
- User creation time
- MFA status
- Credential age

This process supports identity audits and access reviews.

---

## Task 11: Explored Automated Patch Management

Maintaining secure cloud infrastructure requires continuous operating system and application updates.

AWS Systems Manager simplifies patch management through automation.

Capabilities include:

- Automated patch deployment
- Scheduled maintenance
- Compliance scanning
- Patch reporting

Automated patching reduces administrative effort while minimizing exposure to known vulnerabilities.

---

## Task 12: Explored AWS Patch Manager

Using AWS Systems Manager Patch Manager, I examined how patch policies are configured for cloud resources.

Patch Manager supports:

- Immediate patch installation
- Scheduled patch deployment
- Patch compliance reporting
- Missing patch detection

Implementing structured patch management strengthens infrastructure security and supports organizational compliance requirements.

---

# Key Takeaways

- Defense in depth is essential for securing cloud environments.
- Security Groups and Network ACLs complement one another by providing multiple layers of network protection.
- Restricting unnecessary inbound traffic significantly reduces attack surface.
- Encrypting cloud storage protects sensitive information at rest.
- Monitoring and logging provide essential visibility for threat detection and incident response.
- Identity auditing improves access governance and credential management.
- Disaster recovery planning is critical for maintaining business continuity.
- Automated patch management helps reduce vulnerabilities and improve overall cloud security posture.

---

# Conclusion

This project provided practical experience implementing foundational AWS security controls within a controlled laboratory environment. By configuring network protections, securing cloud storage, exploring disaster recovery strategies, reviewing identity security, enabling monitoring capabilities, and studying automated patch management, I developed hands-on experience with the native security services used to protect modern cloud environments.

These implementations reinforce the importance of layered security, continuous monitoring, strong identity management, and proactive maintenance in building resilient cloud infrastructures.

---

# Disclaimer

This project was completed in an authorized training and laboratory environment for educational purposes. All AWS resources, configurations, and security implementations were performed within controlled cloud environments to demonstrate defensive security concepts and best practices. No unauthorized systems or production environments were accessed during this project.
