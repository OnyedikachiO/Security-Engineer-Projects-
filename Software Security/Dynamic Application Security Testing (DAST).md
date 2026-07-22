# Dynamic Application Security Testing (DAST) with OWASP ZAP

Dynamic Application Security Testing (DAST) of web applications and APIs using OWASP ZAP to identify runtime vulnerabilities through spidering, authenticated scanning, API security testing, and CI/CD pipeline integration.

---

# Overview

This project demonstrates the application of **Dynamic Application Security Testing (DAST)** against vulnerable web applications and REST APIs using **OWASP ZAP**.

The assessment combined manual security validation with automated vulnerability scanning to identify exploitable security weaknesses from an attacker's perspective without requiring access to the application's source code.

The project also explored authenticated scanning, API security testing using OpenAPI specifications, scan policy customization, and automated DAST integration within a CI/CD pipeline using Docker and Jenkins.

---

# Objectives

- Understand Dynamic Application Security Testing (DAST)
- Perform black-box security testing against live applications
- Discover application attack surfaces through spidering and crawling
- Configure custom scan policies for targeted assessments
- Perform authenticated vulnerability scanning
- Test REST APIs using OpenAPI (Swagger) specifications
- Detect runtime vulnerabilities in web applications
- Integrate OWASP ZAP into a CI/CD security pipeline
- Compare manual and automated DAST techniques
- Understand DAST's role within the Secure Software Development Lifecycle (SSDLC)

---

# Lab Environment

| Component | Details |
|-----------|---------|
| Platform | TryHackMe |
| Operating System | Linux |
| Web Server | Apache 2.4 |
| Application Language | PHP |
| API Specification | OpenAPI (Swagger) |
| Security Tool | OWASP ZAP |
| Browser | Firefox |
| CI/CD | Jenkins |
| Version Control | Gitea |
| Containers | Docker |
| Methodology | Manual + Automated DAST |

---

# Skills Demonstrated

- Dynamic Application Security Testing (DAST)
- Web Application Security Testing
- Black-Box Security Assessment
- OWASP ZAP
- Spidering & Crawling
- AJAX Spider
- Active Vulnerability Scanning
- Authenticated Scanning
- API Security Testing
- OpenAPI (Swagger) Analysis
- Runtime Vulnerability Detection
- Scan Policy Configuration
- Session Management
- CI/CD Security Integration
- DevSecOps Fundamentals
- Vulnerability Validation

---

# Understanding DAST

Dynamic Application Security Testing evaluates a **running application** by interacting with it just as an external attacker would.

Unlike Static Application Security Testing (SAST), DAST does not inspect source code. Instead, it discovers vulnerabilities by sending requests, manipulating parameters, and analyzing application responses during runtime.

DAST is particularly effective for identifying vulnerabilities introduced during deployment or runtime that static analysis cannot detect.

---

# Manual vs Automated DAST

The assessment explored both manual and automated DAST methodologies.

### Manual DAST

Manual testing involved interacting directly with the application to:

- Explore functionality
- Identify attack surfaces
- Validate vulnerabilities
- Analyze application logic
- Verify scanner findings

### Automated DAST

OWASP ZAP automated the discovery and exploitation process by:

- Crawling application pages
- Identifying attackable parameters
- Launching attack payloads
- Reporting discovered vulnerabilities

Combining both techniques provided broader vulnerability coverage while reducing false positives.

---

# Spidering the Web Application

The first phase involved mapping the application's attack surface using OWASP ZAP's Spider.

The spider recursively discovered:

- Web pages
- Forms
- Parameters
- Input fields
- Navigation paths

This established the application's testing scope.

---

# AJAX Spider

Traditional spiders cannot discover content generated dynamically through JavaScript.

To improve coverage, the assessment utilized the **AJAX Spider**, which controlled a real Firefox browser to execute JavaScript before extracting application links.

Additional resources discovered included:

- `nospiders-gallery.php`
- `view.php`

These resources were invisible to the standard crawler because they were generated dynamically.

---

# Scan Policy Configuration

Before scanning, a custom scan policy was created to improve efficiency.

Disabled categories included:

- SQL Injection
- XML Processing
- DOM-Based Cross-Site Scripting

These checks were excluded because they were irrelevant to the application's architecture, reducing scan duration while minimizing unnecessary testing.

---

# Active Vulnerability Scanning

An Active Scan was performed against the discovered application resources.

OWASP ZAP launched automated payloads against identified parameters to detect runtime vulnerabilities.

Initial findings included:

- Path Traversal
- Reflected Cross-Site Scripting (XSS)

Alerts included detailed request and response pairs, allowing manual validation of scanner findings.

---

# Authenticated Scanning

Unauthenticated scans cannot assess protected functionality.

To improve coverage, authenticated scanning was configured.

Authentication workflow:

- Recorded login sequence using a ZEST script
- Created a testing Context
- Configured script-based authentication
- Defined authenticated users
- Configured login verification indicators
- Excluded logout functionality to maintain active sessions

This allowed OWASP ZAP to continuously authenticate while scanning protected application areas.

---

# Runtime Vulnerability Discovery

Authenticated scanning revealed additional attack surfaces inaccessible during anonymous testing.

A critical vulnerability discovered after authentication:

- Remote OS Command Injection

This demonstrated the importance of scanning authenticated application functionality.

---

# API Security Testing

Modern applications expose APIs that traditional spiders cannot easily enumerate.

Instead of crawling endpoints, OWASP ZAP imported the application's **OpenAPI (Swagger)** specification.

Imported information included:

- API endpoints
- HTTP methods
- Parameters
- Request formats
- Response definitions

Once imported, ZAP treated API endpoints similarly to web application resources.

---

# API Vulnerability Assessment

An Active Scan was executed against the imported API.

High-risk finding:

- Remote OS Command Injection

The assessment also reviewed Path Traversal findings and validated that one reported issue was a false positive based on application behavior.

---

# Vulnerabilities Identified

| Vulnerability | Detection |
|--------------|-----------|
| Path Traversal | ✅ Detected |
| Reflected Cross-Site Scripting (XSS) | ✅ Detected |
| Remote OS Command Injection | ✅ Detected |
| Runtime Configuration Issues | ✅ Detected |
| Authentication-Protected Vulnerabilities | ✅ Detected |

---

# OWASP ZAP Features Explored

The project demonstrated several core OWASP ZAP capabilities.

| Feature | Purpose |
|----------|----------|
| Spider | Crawl application resources |
| AJAX Spider | Discover JavaScript-generated content |
| Active Scan | Launch runtime attack payloads |
| Passive Scan | Analyze HTTP traffic without attacks |
| Authentication Context | Maintain authenticated sessions |
| ZEST Scripts | Automate login workflows |
| Scan Policies | Customize vulnerability testing |
| API Import | Test OpenAPI/Swagger endpoints |

---

# CI/CD Security Integration

The project demonstrated integrating DAST into a DevSecOps pipeline.

Pipeline components included:

- Gitea
- Jenkins
- Docker
- OWASP ZAP Docker (zap2docker)

Each commit triggered:

1. Build Docker image
2. Deploy application
3. Execute automated ZAP Baseline Scan
4. Generate vulnerability reports
5. Fail the pipeline if security issues were detected

This provided developers with immediate security feedback during development.

---

# Automated Scan Profiles

The assessment reviewed three OWASP ZAP automation modes.

### Baseline Scan

- Passive scanning only
- Fast execution
- Suitable for CI/CD pipelines

### Full Scan

- Spidering
- Active vulnerability scanning
- Comprehensive assessment

### API Scan

- Imports OpenAPI specifications
- Tests REST APIs
- Performs active vulnerability analysis

---

# Pipeline Findings

### Simple Web Application

Automated baseline scanning identified:

- **3 Medium-Risk Vulnerabilities**

### Simple API

Pipeline execution identified:

- Remote OS Command Injection

The assessment also reviewed Jenkins build history to analyze pipeline failures and validate automated security reporting.

---

# Key Findings

- Runtime testing successfully identified vulnerabilities inaccessible through static analysis.
- Spidering effectively mapped the application's attack surface.
- AJAX Spider increased coverage by discovering JavaScript-generated resources.
- Authenticated scanning exposed vulnerabilities hidden behind login functionality.
- API testing using OpenAPI specifications simplified endpoint discovery.
- Remote OS Command Injection was detected in both web and API environments.
- CI/CD integration enabled automated security validation on every commit.
- Customized scan policies significantly reduced scanning time while maintaining effective coverage.

---

# Lessons Learned

- DAST complements rather than replaces SAST and Software Composition Analysis (SCA).
- Runtime testing identifies vulnerabilities that source code analysis cannot detect.
- Authenticated scanning greatly improves application security coverage.
- API security testing is essential for modern web applications.
- Scan policies should be customized to reduce unnecessary testing.
- Continuous DAST integration improves security throughout the Software Development Lifecycle.
- Manual validation remains necessary to confirm automated scanner findings and eliminate false positives.

---

# Tools Used

- OWASP ZAP
- Firefox
- OpenAPI (Swagger)
- Jenkins
- Docker
- Gitea
- Linux
- Apache
- PHP

---


# Disclaimer

This project was completed in an authorized training environment using intentionally vulnerable applications within a controlled lab. All testing activities were conducted for educational purposes and followed responsible security and ethical testing practices.
