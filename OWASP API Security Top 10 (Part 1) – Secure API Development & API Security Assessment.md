# OWASP API Security Top 10 (Part 1) – Secure API Development & API Security Assessment

## Overview

This project demonstrates the identification, exploitation, and remediation of the first five vulnerabilities from the **OWASP API Security Top 10**. The assessment was performed in a controlled lab environment using intentionally vulnerable APIs to understand how insecure API implementations can expose sensitive data, enable privilege escalation, bypass authentication, and cause denial of service conditions.

Throughout the project, vulnerable endpoints were analyzed, HTTP requests were modified, authorization controls were tested, and secure implementations were validated by comparing vulnerable and remediated API versions.

---

## Objectives

- Understand how modern APIs communicate between applications.
- Analyze common API security vulnerabilities.
- Exploit vulnerable API endpoints in a controlled environment.
- Validate secure implementations after remediation.
- Learn secure API development best practices.
- Strengthen practical API security testing skills.

---

## Skills Demonstrated

- API Security Testing
- REST API Analysis
- Authorization Testing
- Authentication Bypass Analysis
- HTTP Request Manipulation
- Access Control Validation
- Rate Limiting Verification
- Sensitive Data Exposure Assessment
- OWASP API Security Top 10
- Secure API Development

---

## Tools & Technologies

- Talend API Tester
- Google Chrome Developer Tools
- REST APIs
- HTTP GET & POST Requests
- Authorization Tokens
- JSON Responses
- Local Vulnerable Web Application

---

## Lab Environment

| Category | Details |
|----------|---------|
| Platform | TryHackMe |
| Environment | Controlled Virtual Machine |
| API Testing Tool | Talend API Tester |
| API Type | REST |
| Authentication | Authorization Tokens |
| Response Format | JSON |

---

# Project Scenarios

## 1. Understanding API Fundamentals

Studied how APIs function as communication interfaces between applications and why they are fundamental components of modern software architectures.

### Topics Covered

- API requests and responses
- API documentation
- REST architecture
- Authentication headers
- Authorization tokens
- API attack surface

Additionally, real-world API breaches involving major technology platforms were reviewed to understand how insecure APIs have resulted in large-scale data exposure.

---

# Vulnerability 1 — Broken Object Level Authorization (BOLA)

## Objective

Assess whether users can directly access objects they are not authorized to view by manipulating object identifiers.

## Vulnerability

The vulnerable endpoint accepted sequential employee IDs without verifying whether the requester was authorized to access the requested object.

**Example**

```http
GET /apirule1_v/user/1
```

Changing:

```text
/user/1
```

to

```text
/user/2
```

or

```text
/user/3
```

returned other employees' records without any authorization validation.

## Security Impact

Successful exploitation allowed:

- Unauthorized data disclosure
- Employee enumeration
- Information leakage
- Potential account takeover

## Secure Implementation

The secure endpoint introduced:

- Authorization Token validation
- Access control verification
- HTTP 403 Forbidden responses for unauthorized users

**Example**

```http
Authorization-Token: <valid token>
```

## Key Findings

- Object references must always be authorization checked.
- Sequential IDs should never determine access rights.
- Authorization must be enforced server-side.

---

# Vulnerability 2 — Broken User Authentication

## Objective

Evaluate weaknesses in the authentication implementation.

## Vulnerability

The vulnerable login endpoint validated only the user's email address while completely ignoring the supplied password.

**Example**

```http
POST /apirule2/user/login_v
```

Any password combined with a valid email generated a valid authorization token.

## Security Impact

This resulted in:

- Authentication bypass
- Account takeover
- Unauthorized token generation
- Unauthorized access to user profiles

## Secure Implementation

The secure endpoint validated:

- Email
- Password
- Authorization logic

before issuing authentication tokens.

## Security Best Practices

- Validate all authentication factors.
- Store passwords securely.
- Use strong authentication tokens.
- Support Multi-Factor Authentication (MFA) where appropriate.
- Avoid transmitting credentials through GET requests.

---

# Vulnerability 3 — Excessive Data Exposure

## Objective

Identify unnecessary sensitive information exposed through API responses.

## Vulnerability

The vulnerable endpoint returned complete database objects instead of only the fields required by the client.

**Example**

```http
GET /apirule3/comment_v/{id}
```

The response exposed additional sensitive information such as:

- Device identifiers
- Internal usernames
- Metadata
- User information

that was never intended for end users.

## Security Impact

Exposed information may enable:

- User profiling
- Device fingerprinting
- Credential harvesting
- Further targeted attacks

## Secure Implementation

The remediated endpoint only returned the minimum fields required by the client.

## Key Lesson

Data filtering should always occur on the server.

Front-end applications must never be responsible for hiding sensitive information.

---

# Vulnerability 4 — Lack of Resources & Rate Limiting

## Objective

Assess whether APIs restrict abusive request frequency.

## Vulnerability

The password recovery endpoint allowed unlimited OTP requests.

**Example**

```http
POST /apirule4/sendOTP_v
```

No request throttling existed.

Attackers could automate thousands of OTP requests, exhausting system resources.

## Security Impact

Potential consequences included:

- Email service abuse
- Financial loss
- Resource exhaustion
- Denial of Service (DoS)

## Secure Implementation

The remediated endpoint implemented:

- Request throttling
- Waiting periods
- Rate limiting
- Controlled OTP generation

## Security Best Practices

- Apply API rate limits.
- Implement CAPTCHA when appropriate.
- Restrict payload sizes.
- Monitor abusive clients.
- Alert on unusual request volumes.

---

# Vulnerability 5 — Broken Function Level Authorization

## Objective

Determine whether low-privileged users could access administrative functionality.

## Vulnerability

The vulnerable endpoint trusted the client-supplied header:

```http
isAdmin=1
```

An authenticated non-administrative user could simply modify this value and retrieve privileged information.

## Security Impact

Successful exploitation enabled:

- Privilege escalation
- Unauthorized administrative access
- Sensitive employee data exposure
- Administrative function abuse

## Secure Implementation

The secure endpoint validated administrative privileges directly from server-side user roles rather than trusting client-controlled input.

## Key Lesson

Authorization decisions must always be enforced by the server.

Client-controlled values should never determine user privileges.

---

# API Security Principles Learned

During this project, I reinforced several critical secure development concepts:

- Never trust client input.
- Enforce authorization on every request.
- Validate authentication securely.
- Return only necessary data.
- Implement server-side access controls.
- Apply rate limiting to public endpoints.
- Protect administrative functionality.
- Follow least privilege principles.
- Validate every object reference.
- Design APIs with security by default.

---

# Key Outcomes

Successfully identified and analyzed:

- Broken Object Level Authorization (BOLA)
- Broken User Authentication
- Excessive Data Exposure
- Lack of Resources & Rate Limiting
- Broken Function Level Authorization

Validated secure implementations that introduced:

- Authorization Tokens
- Role-Based Access Control (RBAC)
- Secure Authentication
- Data Minimization
- Rate Limiting
- Proper Access Validation

---

# Lessons Learned

This project demonstrated how seemingly minor implementation flaws in APIs can result in severe security consequences, including unauthorized data disclosure, authentication bypass, privilege escalation, and denial of service.

Comparing vulnerable and secure implementations reinforced the importance of enforcing authentication and authorization server-side, minimizing exposed data, and integrating security throughout the API development lifecycle rather than relying on client-side protections.

---

# Disclaimer

This project was completed within an authorized cybersecurity training environment using intentionally vulnerable applications. All testing activities were performed in a controlled lab for educational purposes. No unauthorized systems or production environments were targeted.
