# Web Application Security Assessment & Website Recovery (Traverse)

## Overview

This project documents a hands-on security assessment of the **Traverse** tourism web application conducted within the TryHackMe training environment.

The objective was to identify the root causes behind repeated website compromises after deployment to production. The assessment involved web application reconnaissance, JavaScript analysis, endpoint enumeration, API testing, administrative interface assessment, web shell detection, and website recovery.

The exercise simulated the responsibilities of an Application Security Engineer investigating a compromised production web application and restoring it to a secure operational state.

---

## Objectives

- Investigate recurring web application compromises
- Analyze client-side JavaScript
- Identify hidden application resources
- Enumerate application endpoints
- Assess exposed APIs
- Discover sensitive information leakage
- Identify unauthorized administrative functionality
- Detect malicious web shells
- Restore the compromised website

---

## Lab Environment

| Component | Details |
|-----------|---------|
| Platform | TryHackMe |
| Room | Traverse |
| Target | Traverse Tourism Web Application |
| Environment | AttackBox |
| Assessment Type | Web Application Security Assessment |

---

# Tools Used

- Browser Developer Tools
- OWASP ZAP Spider
- CyberChef
- Browser Network Inspector
- HTTP Requests
- Manual API Testing

---

# Methodology

## Phase 1 — Application Reconnaissance

The assessment began with manual exploration of the deployed tourism website to understand available functionality and identify potential indicators of compromise.

Initial reconnaissance included:

- Reviewing available pages
- Inspecting client-side resources
- Monitoring network requests
- Identifying JavaScript assets

---

## Phase 2 — JavaScript Analysis

The application's JavaScript resources were inspected using browser developer tools.

A compressed JavaScript file (`custom.min.js`) contained obfuscated content left behind by the attacker.

The encoded data was extracted and analyzed using CyberChef.

### Findings

- Hexadecimal encoding identified
- Hidden attacker message recovered
- Evidence of client-side obfuscation discovered

Recovered message:

```
DIRECTORY LISTING IS THE ONLY WAY
```

---

## Phase 3 — Endpoint Enumeration

To discover hidden resources not visible through the application interface, automated crawling was performed using OWASP ZAP Spider.

The spider recursively enumerated application routes and exposed several hidden resources, including:

- Log directories
- Administrative files
- Email dump files
- Internal application resources

Sensitive file discovered:

```
email_dump.txt
```

---

## Phase 4 — Information Disclosure Analysis

The exposed logs contained sensitive operational information intended for internal personnel.

Analysis revealed:

- Internal directory names
- Administrative references
- Access information
- Operational notes

This demonstrated improper exposure of sensitive internal resources.

---

## Phase 5 — API Security Assessment

Application APIs were manually explored to identify insecure object references and improperly exposed functionality.

The assessment successfully enumerated user records and extracted information associated with user identifiers.

Security issues identified included:

- Predictable object identifiers
- Sensitive data exposure
- Insecure API design

---

## Phase 6 — Administrative Interface Discovery

Further enumeration uncovered a hidden administrative login endpoint.

Discovered endpoint:

```
/realadmin
```

Access to this interface provided elevated administrative functionality used to manage the application.

---

## Phase 7 — Web Shell Detection

Inspection of the administration interface revealed command execution functionality.

Using browser developer tools, additional command options were manually introduced into the available HTML elements, allowing execution of additional operating system commands.

Directory listing revealed the presence of a malicious web shell uploaded by the attacker.

Identified malicious file:

```
thm_shell.php
```

Additional investigation identified a renamed server management file:

```
renamed_file_manager.php
```

This demonstrated successful attacker persistence through server-side web shell deployment.

---

## Phase 8 — Website Recovery

The recovered file manager was used to inspect the application's source files.

The homepage (`index.php`) contained malicious modifications displaying:

```
FINALLY HACKED
```

The injected condition responsible for displaying the attacker message was removed.

After saving the corrected file and reloading the application, the website was successfully restored.


---

# Vulnerabilities Identified

- Sensitive Information Disclosure
- Client-side Information Leakage
- JavaScript Obfuscation
- Directory Enumeration Exposure
- Insecure API Exposure
- Broken Access Control
- Administrative Endpoint Disclosure
- Command Execution Functionality
- Web Shell Deployment
- Website Defacement

---

# Security Concepts Demonstrated

- Application Reconnaissance
- Secure Code Review
- JavaScript Analysis
- Web Enumeration
- OWASP ZAP Spider
- API Security Testing
- Information Disclosure Assessment
- Administrative Interface Discovery
- Web Shell Detection
- Incident Investigation
- Website Recovery
- Manual Web Application Testing

---

# Skills Developed

- Web application assessment
- JavaScript deobfuscation
- API enumeration
- Hidden endpoint discovery
- Directory enumeration
- Information disclosure analysis
- Administrative interface assessment
- Web shell identification
- Incident response
- Website restoration

---

# Key Takeaways

- Client-side JavaScript can unintentionally expose sensitive information.
- Hidden administrative endpoints should never rely on obscurity for protection.
- Directory listing and exposed log files can significantly increase attacker knowledge.
- APIs should enforce proper authorization for every request.
- Administrative functionality must never expose unrestricted command execution.
- Early detection of web shells is essential for limiting attacker persistence.
- Secure recovery includes removing malicious modifications while preserving application functionality.

---

## Disclaimer

This project was completed within an authorized TryHackMe laboratory environment designed for cybersecurity training. All testing, exploitation, and remediation activities were performed against intentionally vulnerable systems in a controlled environment.
