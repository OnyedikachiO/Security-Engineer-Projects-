# OWASP API Security Top 10 (Part 2) – Secure API Development & API Security Assessment

## Overview

This project demonstrates the identification, exploitation, and remediation of the remaining five vulnerabilities from the **OWASP API Security Top 10**. The assessment was conducted within a controlled lab environment using intentionally vulnerable REST APIs to understand how insecure API implementations can lead to privilege escalation, data tampering, injection attacks, information disclosure, legacy API abuse, and inadequate incident detection.

Throughout the assessment, vulnerable API endpoints were analyzed, crafted HTTP requests were used to validate security weaknesses, and secure implementations were verified by comparing vulnerable and remediated API versions.

---

# Objectives

- Understand the remaining OWASP API Security Top 10 vulnerabilities.
- Analyze insecure API implementations.
- Exploit vulnerable endpoints in a controlled environment.
- Validate secure implementations after remediation.
- Learn secure API development best practices.
- Strengthen practical API security assessment skills.

---

# Skills Demonstrated

- API Security Testing
- REST API Analysis
- Secure API Development
- Authorization Validation
- Input Validation Testing
- SQL Injection Analysis
- Rate Limiting Verification
- API Version Management
- Logging & Monitoring Assessment
- OWASP API Security Top 10

---

# Tools & Technologies

- Talend API Tester
- Google Chrome Developer Tools
- REST APIs
- HTTP GET & POST Requests
- Authorization Tokens
- JSON Responses
- Local Vulnerable Web Application

---

# Lab Environment

- **Platform:** TryHackMe
- **Environment:** Controlled Virtual Machine
- **API Type:** REST
- **Authentication:** Authorization Tokens
- **Response Format:** JSON
- **Testing Tool:** Talend API Tester

---

# Project Scenarios

## 1. Mass Assignment

### Objective

Assess whether client-controlled input can modify server-side object properties that should remain protected.

### Vulnerability

The vulnerable registration endpoint automatically mapped all client-supplied fields directly to database objects using mass assignment.

Example:

```http
POST /apirule6/user
```

Although the application intended every new user to receive a default credit value of **50**, an attacker could include a custom `credit` field during registration.

Example malicious request:

```json
{
  "name": "Alice",
  "username": "alice",
  "password": "Password123!",
  "credit": 1000
}
```

Without server-side filtering, the application accepted and stored the attacker-controlled value.

---

### Security Impact

Successful exploitation could result in:

- Data tampering
- Privilege escalation
- Unauthorized account modifications
- Business logic abuse

---

### Secure Implementation

The remediated endpoint enforced server-side validation by allowing only approved fields while automatically assigning the default credit value.

Regardless of the submitted input, every new user received:

```text
Credit = 50
```

---

### Key Findings

- Never trust client-supplied object properties.
- Allowlist acceptable fields during object creation.
- Enforce business rules on the server.
- Prevent automatic object binding without validation.

---

# 2. Security Misconfiguration

### Objective

Identify insecure configurations that expose internal application details.

### Vulnerability

The vulnerable health-check endpoint returned full application stack traces whenever an error occurred.

Example:

```http
GET /apirule7/ping_v
```

Instead of displaying a generic error message, the API exposed:

- Internal file paths
- Function names
- Route information
- Controller details
- Debugging information

---

### Security Impact

Information disclosure enabled attackers to:

- Profile the application
- Discover internal architecture
- Identify technology stack
- Prepare targeted attacks

---

### Secure Implementation

The remediated endpoint implemented centralized error handling and returned only generic responses while hiding internal application details.

---

### Key Findings

- Disable debugging in production.
- Never expose stack traces publicly.
- Restrict access to administrative interfaces.
- Remove unnecessary diagnostic information.

---

# 3. Injection

### Objective

Evaluate whether user input was properly validated before interacting with backend components.

### Vulnerability

The vulnerable login endpoint processed user input directly within SQL queries.

Example:

```http
POST /apirule8/user/login_v
```

An attacker supplied the following SQL injection payload:

```sql
' OR 1=1--
```

The application interpreted the payload as part of the SQL query and authenticated the attacker without valid credentials.

---

### Security Impact

Injection vulnerabilities may result in:

- Authentication bypass
- Database compromise
- Information disclosure
- Data manipulation
- Remote Code Execution (RCE)
- Denial of Service (DoS)

---

### Secure Implementation

The secure endpoint implemented:

- Parameterized queries
- Server-side input validation
- Input sanitization
- Framework security protections

Invalid credentials correctly returned:

```http
HTTP 403 Forbidden
```

---

### Key Findings

- Never concatenate user input into SQL queries.
- Validate and sanitize all inputs.
- Use prepared statements.
- Apply Web Application Firewall (WAF) protections where appropriate.

---

# 4. Improper Asset Management

### Objective

Determine whether deprecated API versions remained publicly accessible.

### Vulnerability

The organization deployed a newer API version while leaving the legacy version available.

Example:

```http
POST /apirule9/v1/user/login
```

The obsolete endpoint exposed additional sensitive information that had been removed from the current API version.

Leaked information included:

- User balance
- Address information
- Country
- Additional profile data

---

### Security Impact

Legacy APIs may expose:

- Unpatched vulnerabilities
- Sensitive information
- Outdated authentication mechanisms
- Expanded attack surfaces

---

### Secure Implementation

The updated implementation:

- Disabled obsolete API versions
- Restricted access to deprecated endpoints
- Migrated users to supported versions
- Reduced unnecessary data exposure

---

### Key Findings

- Maintain a complete API inventory.
- Remove deprecated endpoints.
- Separate development, testing, and production APIs.
- Continuously review exposed API assets.

---

# 5. Insufficient Logging & Monitoring

### Objective

Assess whether API activity was adequately logged to support security monitoring and incident response.

### Vulnerability

The organization lacked sufficient API logging, making malicious activity difficult to investigate after an incident.

The solution introduced centralized logging for:

- Client IP addresses
- Browser information
- Accessed endpoints
- Request timestamps
- Authentication events

---

### Security Impact

Without proper logging:

- Attack attribution becomes difficult.
- Incident response is delayed.
- Malicious activity may remain undetected.
- Forensic investigations lack evidence.

---

### Secure Implementation

The updated endpoint recorded user activity and prepared logs for forwarding into a Security Information and Event Management (SIEM) platform.

Successful logging returned:

```http
HTTP 200 OK
```

---

### Key Findings

- Log authentication failures.
- Record denied access attempts.
- Protect log integrity.
- Integrate API logs with SIEM solutions.
- Monitor suspicious activity using automated alerts.

---

# API Security Principles Learned

Throughout this project, I reinforced several secure API development principles:

- Never trust client-controlled input.
- Validate all incoming data.
- Enforce authorization on the server.
- Use parameterized database queries.
- Disable debugging in production.
- Remove deprecated API versions.
- Maintain accurate API inventories.
- Log security-relevant events.
- Integrate monitoring with SIEM platforms.
- Build APIs following secure-by-default principles.

---

# Key Outcomes

Successfully identified and analyzed:

- Mass Assignment
- Security Misconfiguration
- Injection
- Improper Asset Management
- Insufficient Logging & Monitoring

Validated secure implementations introducing:

- Server-side input validation
- Allowlisted object properties
- Parameterized SQL queries
- Secure error handling
- API version management
- Centralized logging
- SIEM integration
- Secure development best practices

---

# Lessons Learned

This project demonstrated how insecure API implementations extend beyond authentication and authorization flaws. Weak input validation, exposed debugging information, legacy API versions, and insufficient monitoring all introduce opportunities for attackers to compromise applications.

By comparing vulnerable and remediated implementations, I gained practical experience in securing REST APIs through proper input validation, secure error handling, lifecycle management of API assets, and comprehensive logging. These exercises reinforced the importance of integrating security throughout the API development lifecycle rather than treating it as an afterthought.

---

# Disclaimer

This project was completed within an authorized cybersecurity training environment using intentionally vulnerable applications. All testing activities were performed in a controlled lab for educational purposes. No unauthorized systems or production environments were targeted.
