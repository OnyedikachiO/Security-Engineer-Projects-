# Linux Security Administration: SSH Hardening, Access Control & System Maintenance

## Overview

This project demonstrates the implementation of Linux security administration best practices to secure user access, strengthen authentication mechanisms, manage privileged accounts, reduce the system attack surface, maintain software security, and improve audit visibility.

The project focuses on securing remote administration through SSH hardening, implementing secure user and privilege management, enforcing strong password policies, minimizing unnecessary services, maintaining system updates, and configuring logging practices for security monitoring and incident response.

These configurations follow industry-standard Linux administration and security engineering practices used to strengthen enterprise systems against unauthorized access, credential attacks, privilege escalation, and outdated software vulnerabilities.

---

# Objectives

- Secure remote administration using SSH
- Harden SSH authentication and configuration
- Configure SSH public key authentication
- Prevent unauthorized root access
- Implement secure user privilege management
- Configure sudo for administrative access
- Enforce strong password policies
- Disable unused user accounts
- Reduce the Linux attack surface
- Remove unnecessary services
- Maintain secure software update practices
- Configure system auditing and log monitoring
- Apply Linux security administration best practices

---

# Lab Environment

| Component | Technology |
|-----------|------------|
| Operating System | Linux |
| Remote Access | OpenSSH |
| Authentication | SSH Keys (RSA) |
| Privilege Management | sudo |
| Password Management | libpwquality |
| Package Managers | APT, DNF, YUM |
| Logging | `/var/log` |
| Shell | Bash |

---

# Technologies Used

- Linux
- OpenSSH
- SSH
- RSA Key Authentication
- sudo
- libpwquality
- PAM (Pluggable Authentication Modules)
- APT
- DNF
- YUM
- Bash
- System Logs
- grep
- tail

---

# Skills Demonstrated

- Linux Administration
- Linux Security Hardening
- SSH Security
- Identity & Access Management (IAM)
- Privileged Access Management
- Password Policy Enforcement
- Patch Management
- Vulnerability Mitigation
- Service Hardening
- Security Monitoring
- Linux Auditing
- Security Operations
- Incident Readiness

---

# Project Implementation

## 1. Secure Remote Access

Remote administration is essential for managing Linux systems, but it also introduces one of the most common attack surfaces within enterprise environments.

To secure remote access, I evaluated common attack techniques against remote administration services, including:

- Password sniffing
- Password guessing
- Brute-force attacks
- Service exploitation

Rather than relying on insecure legacy protocols, I configured Linux systems to use Secure Shell (SSH) for encrypted remote administration.

SSH provides:

- Encrypted communications
- Secure authentication
- Secure file transfers
- Confidential remote administration

This significantly improves the security of remote management compared to legacy protocols such as Telnet.

---

## 2. SSH Hardening

To reduce the likelihood of unauthorized access, I hardened the OpenSSH server configuration.

One of the first security improvements was disabling direct root login.

Inside the SSH server configuration file:

```text
/etc/ssh/sshd_config
```

I configured:

```text
PermitRootLogin no
```

Disabling direct root authentication reduces the likelihood of successful brute-force attacks against privileged accounts while encouraging administrative access through standard user accounts with elevated privileges.

---

## 3. Public Key Authentication

Instead of relying solely on passwords, I configured SSH public key authentication.

I generated an RSA key pair using:

```bash
ssh-keygen -t rsa
```

This generated:

- Private Key

```text
id_rsa
```

- Public Key

```text
id_rsa.pub
```

The public key was copied to the remote server using:

```bash
ssh-copy-id username@server
```

Within the SSH configuration, I enabled public key authentication while disabling password-based authentication.

```text
PubkeyAuthentication yes

PasswordAuthentication no
```

Using SSH key authentication greatly reduces the effectiveness of password guessing and brute-force attacks.

---

## 4. User Privilege Management

To reduce security risks associated with privileged accounts, I implemented least-privilege administration using sudo.

Rather than logging in directly as the root user, administrative users were granted temporary elevated privileges through membership in the sudoers group.

For Debian-based systems:

```bash
usermod -aG sudo username
```

For Red Hat and Fedora systems:

```bash
usermod -aG wheel username
```

This approach improves accountability while minimizing unnecessary root usage.

---

## 5. Root Account Hardening

After configuring administrative users, I hardened the root account by preventing interactive logins.

Inside:

```text
/etc/passwd
```

The root shell was changed from:

```text
/bin/bash
```

to:

```text
/sbin/nologin
```

Disabling direct root logins helps reduce opportunities for privilege abuse and unauthorized administrative access.

---

## 6. Password Policy Enforcement

To improve credential security, I configured Linux password quality policies using the `libpwquality` framework.

Example policy:

```text
difok=5
minlen=10
minclass=3
retry=2
```

These controls enforce:

- Longer passwords
- Character complexity
- Password uniqueness
- Limited retry attempts

Strong password policies reduce the likelihood of successful credential attacks.

---

## 7. Account Hardening

Unused accounts present unnecessary risk.

As part of system hardening, I disabled inactive user accounts by assigning a non-interactive shell.

Example:

```text
/sbin/nologin
```

This prevents interactive logins while preserving the account for auditing purposes.

The same approach can also be applied to service accounts including:

- www-data
- nginx
- mongo

Restricting shell access limits opportunities for attackers to abuse compromised service accounts.

---

## 8. Software & Service Hardening

Every installed package increases the potential attack surface.

To reduce unnecessary exposure, I followed software minimization principles by:

- Removing unused applications
- Disabling unnecessary services
- Reducing listening network services
- Limiting exposed network ports

Systems should only run services that are required for business operations.

---

## 9. Replacing Legacy Protocols

Older protocols transmit sensitive information in plaintext and should no longer be used.

I evaluated secure alternatives for legacy services.

| Legacy Protocol | Secure Alternative |
|----------------|-------------------|
| Telnet | SSH |
| FTP | SFTP |
| TFTP | SFTP |

Replacing insecure protocols significantly improves confidentiality and integrity during remote communications.

---

## 10. Update & Patch Management

Maintaining current software versions is one of the most important aspects of Linux security administration.

I reviewed package management across multiple Linux distributions.

### Debian-Based Systems

Update package information:

```bash
apt update
```

Install updates:

```bash
apt upgrade
```

Combined:

```bash
apt update && apt upgrade
```

---

### Fedora

```bash
dnf update
```

---

### Older Red Hat Systems

```bash
yum update
```

Keeping systems fully updated reduces exposure to publicly known vulnerabilities.

---

## 11. Long-Term Support (LTS) Strategy

I also reviewed operating system lifecycle management.

Enterprise Linux deployments should prioritize supported operating system releases.

Examples include:

- Ubuntu LTS Releases
- Red Hat Enterprise Linux
- Fedora supported releases

Using supported operating systems ensures continued access to:

- Security patches
- Bug fixes
- Vendor support
- Stability updates

---

## 12. Kernel Security

System hardening also requires maintaining an up-to-date Linux kernel.

Kernel vulnerabilities can allow attackers to gain elevated privileges.

One well-known example is the Dirty COW vulnerability, which affected multiple Linux kernel versions through a race condition in the Copy-on-Write (COW) mechanism.

Regular kernel updates significantly reduce exposure to privilege escalation vulnerabilities.

---

## 13. Automatic Updates

Where operationally appropriate, I evaluated the use of automatic updates to ensure systems receive security patches promptly.

Automatic updates help reduce the window of exposure between vulnerability disclosure and remediation.

---

## 14. Linux Audit & Log Management

System logs provide essential visibility into authentication events, system activity, and potential security incidents.

Common Linux log locations include:

| Log File | Purpose |
|----------|---------|
| `/var/log/messages` | General system events |
| `/var/log/auth.log` | Authentication events (Debian) |
| `/var/log/secure` | Authentication events (Red Hat/Fedora) |
| `/var/log/kern.log` | Kernel messages |
| `/var/log/boot.log` | Boot events |
| `/var/log/wtmp` | Login history |
| `/var/log/utmp` | Current logged-in users |

Proper log management improves security monitoring and forensic investigations.

---

## 15. Log Analysis

To efficiently investigate large log files, I used common Linux command-line utilities.

View the most recent entries:

```bash
tail -n 15 kern.log
```

Search for specific events:

```bash
grep denied secure
```

These utilities simplify the identification of authentication failures, configuration issues, and potential indicators of compromise.

---

# Security Principles Applied

- Least Privilege
- Principle of Secure Administration
- Defense-in-Depth
- Identity & Access Management
- Strong Authentication
- Password Security
- Service Minimization
- Secure Remote Administration
- Patch Management
- Continuous Monitoring
- Auditability
- Attack Surface Reduction

---

# Key Outcomes

- Hardened SSH against unauthorized access
- Eliminated direct root login
- Implemented SSH public key authentication
- Configured secure administrative access using sudo
- Enforced enterprise password policies
- Hardened user and service accounts
- Reduced attack surface by removing unnecessary services
- Replaced insecure legacy protocols with encrypted alternatives
- Applied secure software update strategies
- Improved system visibility through centralized log analysis
- Strengthened overall Linux administrative security posture

---

# Lessons Learned

This project demonstrated that Linux security extends beyond operating system hardening and requires continuous administrative controls throughout the system lifecycle. Proper user management, secure authentication, software maintenance, and audit logging are essential components of a secure Linux environment.

By implementing SSH hardening, privilege separation, strong password policies, software minimization, and proactive patch management, I significantly improved the resilience of the system against credential attacks, privilege escalation, and outdated software vulnerabilities. Additionally, strengthening audit capabilities reinforced the importance of monitoring and maintaining visibility into system activity for effective security operations.

---


# Disclaimer

> **Disclaimer:** This project was completed in an authorized lab and training environment for educational and defensive cybersecurity purposes. All configurations, testing activities, and security implementations were performed on systems where explicit authorization was granted. No testing or activity was conducted against unauthorized systems.
