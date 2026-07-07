# Network Security Protocols

## Project Overview

This project explores the implementation and operation of secure network protocols across multiple layers of the OSI model. The focus was on understanding how modern protocols protect network communications through encryption, authentication, integrity verification, and secure tunneling.

The project covered secure web communication, secure file transfer, secure email protocols, DNS security, encrypted remote administration, SSL/TLS encryption, SOCKS5 proxying, IPsec, and VPN technologies. Practical exercises reinforced the role each protocol plays in protecting enterprise communications from interception, tampering, spoofing, and unauthorized access.

---

## Objectives

- Understand secure network protocols across the OSI model
- Compare secure protocols with their insecure counterparts
- Learn how HTTPS protects web communications
- Explore secure file transfer using FTPS
- Understand secure email protocols (SMTPS and POP3S)
- Learn DNS integrity protection using DNSSEC
- Study end-to-end email encryption with OpenPGP
- Understand secure remote administration using SSH
- Examine SSL/TLS handshake operations
- Explore SOCKS5 proxy communications
- Understand IPsec architecture and VPN technologies

---

# Skills Demonstrated

- Network Security
- Secure Communications
- Network Protocol Analysis
- SSL/TLS Fundamentals
- HTTPS Security
- FTPS Administration
- Secure Email Protocols
- DNS Security
- Public Key Cryptography
- VPN Security
- IPsec Fundamentals
- SSH Administration
- Secure Remote Access
- Proxy Technologies
- Protocol Hardening
- Encryption Concepts

---

# Technologies & Tools

- HTTPS
- HTTP
- SSL/TLS
- FTPS
- FTP
- SMTPS
- SMTP
- POP3S
- POP3
- DNSSEC
- OpenPGP
- GnuPG (GPG)
- SSH
- Telnet
- SOCKS5
- IPsec
- ESP
- OpenVPN
- Wireshark
- Tshark
- SSL Shopper
- MXToolbox SuperTool

---

# Lab Environment

- TryHackMe Network Security Protocols Lab
- Linux
- Ubuntu
- Web Browser
- Wireshark
- Tshark
- OpenVPN
- GnuPG
- SSL/TLS Testing Tools

---

# Project Tasks

## 1. Understanding Secure Network Protocols

Studied how secure protocols operate across the OSI model and how encryption protects communications between clients and servers.

Covered:

- OSI Layer responsibilities
- TCP and UDP protocol usage
- Default protocol ports
- Secure vs insecure communications
- Encryption and authentication concepts

### Outcome

Developed a strong understanding of protocol layering and the role secure protocols play in protecting enterprise communications.

---

## 2. Securing Web Communications with HTTPS

Explored HTTPS as the secure version of HTTP.

Studied:

- Client-server communication
- HTTP request and response model
- HTTPS encryption
- TLS integration
- Public and private key cryptography
- Symmetric session key negotiation
- Port 443

### Practical Activities

- Compared HTTP and HTTPS traffic
- Reviewed encrypted communications
- Examined HTTPS workflow
- Verified SSL certificates using SSL Shopper

### Outcome

Learned how HTTPS protects confidentiality and integrity during web browsing and online transactions.

---

## 3. Secure File Transfer Using FTPS

Studied how FTPS secures traditional FTP communications.

Covered:

- FTP architecture
- Control channel
- Data channel
- Active mode
- Passive mode
- Explicit FTPS
- Implicit FTPS
- TLS encryption
- FTP ports 21 and 990

### Practical Activities

- Reviewed FTP connection workflows
- Compared FTP and FTPS
- Studied encrypted file transfers

### Outcome

Understood how FTPS protects authentication credentials and transferred files from interception.

---

## 4. Securing Email Communications

Explored secure email transmission and retrieval protocols.

Covered:

- SMTP
- SMTPS
- POP3
- POP3S
- STARTTLS
- Email encryption
- Secure authentication
- Ports 465, 587, and 995

### Practical Activities

- Reviewed SMTP workflows
- Examined STARTTLS negotiation
- Tested SMTP security

### Outcome

Learned how TLS secures email delivery and retrieval while reducing exposure to credential theft and message interception.

---

## 5. DNS Security with DNSSEC

Studied how DNSSEC protects DNS integrity and authenticity.

Covered:

- DNS record signing
- Public/private key cryptography
- Digital signatures
- Record validation
- DNS authenticity
- DNS integrity

### Practical Activities

- Examined DNS query responses
- Reviewed signed DNS records
- Studied DNS spoofing mitigation

### Outcome

Developed an understanding of how DNSSEC prevents forged DNS responses and cache poisoning attacks.

---

## 6. End-to-End Email Encryption Using OpenPGP

Implemented secure email encryption concepts using OpenPGP.

Studied:

- Pretty Good Privacy (PGP)
- Gnu Privacy Guard (GPG)
- Public key cryptography
- Private key cryptography
- Message signing
- Message encryption
- Message verification

### Practical Activities

Generated encryption keys using:

```bash
gpg --gen-key
```

Encrypted and signed messages using:

```bash
gpg --encrypt --sign --armor -r recipient@example.com message.txt
```

### Outcome

Learned how end-to-end encryption protects email contents even from mail servers.

---

## 7. Secure Remote Administration with SSH

Compared legacy remote administration protocols with SSH.

Reviewed:

- Telnet
- Rlogin
- SSH
- Encrypted sessions
- Secure authentication
- Secure command execution

### Practical Activities

- Compared Telnet traffic in Wireshark
- Observed encrypted SSH sessions
- Reviewed SSH protocol behavior

### Outcome

Understood why SSH replaces Telnet for secure remote administration.

---

## 8. Understanding SSL/TLS

Studied the SSL/TLS protocol and handshake process.

Covered:

- Client Hello
- Server Hello
- Certificate validation
- Public key exchange
- Premaster secret
- Session key generation
- Secure communication

### Practical Activities

- Completed SSL handshake exercises
- Observed encrypted communication
- Reviewed certificate validation

### Outcome

Developed an understanding of how SSL/TLS establishes trusted encrypted sessions.

---

## 9. Exploring SOCKS5 Proxy Communications

Studied the SOCKS5 protocol and proxy architecture.

Covered:

- Client initiation
- Authentication negotiation
- Proxy routing
- Secure data forwarding
- Firewall traversal
- IP masking

### Practical Activities

- Reviewed SOCKS5 handshake
- Examined proxy communication workflow

### Outcome

Learned how SOCKS5 enables secure proxy communications while hiding internal network details.

---

## 10. Securing Network Traffic with IPsec

Studied IPsec architecture and secure tunneling.

Covered:

- Authentication Header (AH)
- Encapsulating Security Payload (ESP)
- Security Associations (SA)
- Tunnel mode
- Transport mode
- Authentication
- Integrity
- Confidentiality

### Practical Activities

Reviewed:

- AH packet protection
- ESP encryption
- Tunnel mode
- Transport mode

### Outcome

Developed an understanding of how IPsec secures network-layer communications.

---

## 11. Understanding VPN Technologies

Explored Virtual Private Network technologies.

Covered:

- Site-to-site VPNs
- Remote access VPNs
- VPN concentrators
- IPsec VPNs
- OpenVPN
- SSL/TLS VPNs
- Secure tunneling

### Practical Activities

Compared:

- Cisco IPsec VPN
- OpenVPN
- SSL/TLS VPN implementation
- PPTP limitations

### Outcome

Learned how VPNs securely connect users and branch offices across public networks.

---

# Key Security Concepts Learned

- HTTPS
- SSL/TLS
- FTPS
- SMTPS
- POP3S
- DNSSEC
- OpenPGP
- GPG
- SSH
- SOCKS5
- IPsec
- VPN Security
- Public Key Cryptography
- Session Key Negotiation
- Secure Authentication
- Secure Communications
- Data Confidentiality
- Data Integrity
- Digital Signatures

---

# Practical Exercises Completed

Successfully completed practical exercises including:

- Identified HTTPS default port (443)
- Examined FTP active and passive modes
- Tested SSL certificates using SSL Shopper
- Verified SMTP security using MXToolbox SuperTool
- Generated GPG key pairs
- Encrypted and signed messages with GPG
- Compared Telnet and SSH communications
- Completed SSL/TLS handshake exercises
- Explored SOCKS5 proxy negotiation
- Studied IPsec transport and tunnel modes
- Compared OpenVPN and Cisco IPsec VPN implementations

---

# Security Best Practices Applied

- Use HTTPS instead of HTTP
- Replace FTP with FTPS
- Use SMTPS and POP3S for email security
- Secure DNS using DNSSEC
- Implement end-to-end encryption with OpenPGP
- Replace Telnet with SSH
- Validate SSL/TLS certificates
- Encrypt remote communications
- Use IPsec or TLS-based VPNs
- Protect confidentiality, integrity, and authenticity
- Utilize strong public key cryptography
- Enforce encrypted administrative access

---

# Lessons Learned

This project demonstrated that modern network security depends heavily on secure communication protocols operating across multiple layers of the OSI model. Protocols such as HTTPS, FTPS, SMTPS, POP3S, SSH, DNSSEC, SSL/TLS, OpenPGP, IPsec, and VPN technologies work together to provide confidentiality, integrity, authentication, and secure remote access. Understanding how these protocols function and where they operate enables security professionals to design resilient network architectures capable of protecting sensitive communications against interception, spoofing, tampering, and unauthorized access.

---

# Disclaimer

This project was completed within an authorized TryHackMe training environment for educational purposes. All protocol analysis, configuration reviews, encryption exercises, and security demonstrations were performed on controlled lab systems designed for cybersecurity training. No testing was conducted against production or unauthorized systems.
