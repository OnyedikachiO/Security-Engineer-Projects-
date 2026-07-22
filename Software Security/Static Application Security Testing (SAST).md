# Static Application Security Testing (SAST) for Secure Code Review

Automated and manual source code security analysis using **Psalm**, **Semgrep**, and secure code review techniques to identify **SQL Injection**, **Local File Inclusion (LFI)**, **Cross-Site Scripting (XSS)**, **Command Injection**, and insecure coding practices.

---

# Overview

This project demonstrates the application of **Static Application Security Testing (SAST)** to identify security vulnerabilities in a PHP web application before deployment.

The assessment combined **manual code review** with **automated SAST tooling** to evaluate source code for common web application vulnerabilities, compare detection accuracy, and understand how SAST integrates into a **Secure Software Development Lifecycle (SSDLC)**.

The exercise also explored multiple static analysis techniques including:

- Semantic Analysis
- Data Flow Analysis
- Structural Analysis
- Configuration Analysis
- Control Flow Analysis

---

# Objectives

- Perform manual security-focused code reviews
- Identify SQL Injection vulnerabilities
- Detect Local File Inclusion (LFI)
- Understand data flow from user input to vulnerable sinks
- Use Psalm for automated static analysis
- Use Semgrep for IDE-based security scanning
- Compare manual findings with automated SAST results
- Evaluate false positives and false negatives
- Understand SAST integration within CI/CD pipelines

---

# Lab Environment

| Component | Details |
|-----------|---------|
| Platform | TryHackMe |
| Operating System | Linux |
| Language | PHP |
| Database | MySQL |
| Static Analysis Tools | Psalm, Semgrep |
| IDE | Visual Studio Code |
| Methodology | Manual Code Review + SAST |

---

# Skills Demonstrated

- Secure Code Review
- Static Application Security Testing (SAST)
- Source Code Analysis
- SQL Injection Detection
- Local File Inclusion Detection
- Cross-Site Scripting Detection
- Command Injection Analysis
- Data Flow Analysis
- Security Validation
- Secure SDLC
- Secure Development Practices
- DevSecOps Fundamentals

---

# Manual Code Review

The first phase involved manually reviewing the application's PHP source code to identify vulnerable code paths.

The review followed three primary steps:

1. Identify dangerous functions
2. Trace user-controlled input
3. Determine whether sanitization is sufficient

---

## Identifying Dangerous Functions

Using recursive `grep` searches, database query functions were identified throughout the project.

```bash
grep -r -n 'mysqli_query('
```

This located the application's database wrapper function:

```php
function db_query($conn, $query){
    $result = mysqli_query($conn, $query);
    return $result;
}
```

Since raw SQL queries eventually reached `mysqli_query()`, further tracing was required.

---

## SQL Injection Discovery

Tracing application input revealed multiple SQL queries constructed from HTTP GET parameters.

### Vulnerable Query

```php
$sql = "SELECT id, firstname, lastname FROM MyGuests WHERE id=".$_GET['guest_id'];
```

User-controlled input was concatenated directly into the SQL statement without validation or parameterization.

### Impact

- SQL Injection
- Database manipulation
- Authentication bypass
- Data disclosure

---

## Input Validation Review

Additional SQL queries were manually inspected.

### Safe Example

```php
preg_replace('/[^a-z0-9A-Z"]/', "", $_GET['log_id'])
```

The whitelist effectively restricted characters, preventing SQL Injection.

**Result**

> Not Vulnerable

---

### Vulnerable Example

```php
preg_replace("/[^0-9]/", "", $_GET['art_id'], 1)
```

Only the first invalid character was removed because the replacement limit was set to `1`, allowing malicious payloads after the first replacement.

**Result**

> SQL Injection

---

# Local File Inclusion Discovery

Potential LFI sinks were identified by searching for include-related functions.

```bash
grep -r -n 'include('
```

Nine `include()` statements were found.

The vulnerable code was:

```php
include('./gallery-files/'.$_GET['img']);
```

Since the filename was fully controlled by user input, an attacker could manipulate included files.

### Potential Impact

- Local File Inclusion (LFI)
- Source code disclosure
- Sensitive file access
- Possible Remote Code Execution (depending on server configuration)

---

# Automated Static Analysis with Psalm

Psalm was executed against the project.

```bash
./vendor/bin/psalm --no-cache
```

The initial scan reported structural programming issues including:

- Invalid operands
- Incorrect assignments
- Redundant conditions
- Unsafe variable handling
- Coding best-practice violations

Example:

```php
if ($result->num_rows = 0)
```

The assignment operator (`=`) was mistakenly used instead of the comparison operator (`==`), causing the condition to always evaluate as `false`.

---

# Taint Analysis

Psalm's taint analysis was enabled.

```bash
./vendor/bin/psalm --no-cache --taint-analysis
```

This identified data flowing from user-controlled sources (`$_GET`) into security-sensitive sinks.

Detected vulnerabilities included:

- SQL Injection
- Local File Inclusion
- Cross-Site Scripting (XSS)
- Command Injection
- Unsafe HTML Output

---

## Example SQL Injection Trace

Psalm successfully traced untrusted input through multiple function calls:

```text
$_GET['guest_id']
        ↓
SQL Query
        ↓
db_query()
        ↓
mysqli_query()
```

This demonstrated how tainted user input propagated into a dangerous database function.

---

# Improving Detection with Custom Sink Annotations

To improve accuracy, Psalm annotations were added to the application's database wrapper.

```php
/**
 * @psalm-taint-sink sql $query
 * @psalm-taint-specialize
 */
function db_query($conn, $query){
    $result = mysqli_query($conn, $query);
    return $result;
}
```

These annotations instructed Psalm to:

- Treat `db_query()` as a SQL sink
- Analyze each function invocation independently

This significantly improved SQL Injection detection coverage.

---

# Semgrep Analysis

Semgrep was integrated within Visual Studio Code to provide real-time security feedback.

Findings included:

- SQL Injection
- Cross-Site Scripting (XSS)
- Unsafe request handling
- Insecure coding patterns

### Project Statistics

- **27 total issues detected**
- **8 issues identified in `showrecipe.inc.php`**

### Detected Rule Identifiers

- `tainted-sql-string`
- `echoed-request`

---

# Manual Review vs SAST

| Finding | Manual Review | Psalm |
|----------|--------------|--------|
| SQL Injection (`$sql`) | ✅ Detected | ✅ Detected |
| SQL Injection (`$sql2`) | ❌ Not Vulnerable | ⚠ False Positive |
| SQL Injection (`$sql3`) | ✅ Detected | ❌ False Negative |
| Local File Inclusion | ✅ Detected | ✅ Detected |
| Structural Errors | Limited | ✅ Extensive |

---

# SAST Analysis Techniques Explored

| Technique | Purpose |
|-----------|----------|
| Semantic Analysis | Detect insecure function usage |
| Data Flow Analysis | Track user-controlled input to sensitive sinks |
| Structural Analysis | Identify programming mistakes and insecure implementations |
| Configuration Analysis | Detect insecure application settings |
| Control Flow Analysis | Discover logic flaws, dead code, and unsafe execution paths |

---

# Key Findings

- Multiple SQL Injection vulnerabilities were identified.
- A Local File Inclusion vulnerability allowed user-controlled file inclusion.
- Psalm successfully detected data-flow vulnerabilities through taint analysis.
- Structural analysis uncovered several programming logic errors.
- Semgrep provided effective IDE-based security feedback.
- Custom taint annotations improved SAST detection accuracy.
- Automated scanning produced both false positives and false negatives, reinforcing the need for manual validation.

---

# Lessons Learned

- Manual reviews remain essential for identifying context-specific vulnerabilities.
- SAST significantly reduces review time by automating repetitive analysis.
- Data Flow Analysis provides deeper insight than simple pattern matching.
- IDE-integrated scanning enables developers to identify issues earlier in the development lifecycle.
- Combining manual reviews with SAST tools yields stronger security coverage than relying on either approach alone.

---

# Tools Used

- Psalm
- Semgrep
- Visual Studio Code
- Linux
- PHP
- MySQL
- Grep

---

# Disclaimer

This project was completed in an authorized training environment using intentionally vulnerable applications for educational purposes. All testing and analysis were conducted in a controlled lab environment following responsible security practices.
