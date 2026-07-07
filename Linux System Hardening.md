# Linux System Hardening: Physical Security, Disk Encryption & Host Firewall Configuration

## Overview

This project demonstrates the implementation of foundational Linux system hardening techniques used to secure enterprise Linux environments against physical attacks, unauthorized access, network-based threats, and data compromise.

The project focuses on strengthening a Linux system through multiple layers of defense, including physical security controls, GRUB bootloader protection, full disk encryption with Linux Unified Key Setup (LUKS), host-based firewall configuration, and secure network traffic filtering. These security controls follow the Defense-in-Depth strategy by ensuring that the compromise of one security layer does not expose the entire system.

Throughout this project, I configured and evaluated Linux security mechanisms commonly deployed by system administrators and security engineers to reduce the attack surface, enforce secure access, and improve the confidentiality, integrity, and availability of enterprise systems.

---

# Objectives

- Implement physical security controls for Linux systems
- Protect the bootloader against unauthorized modification
- Configure GRUB password protection
- Encrypt storage using Linux Unified Key Setup (LUKS)
- Understand Linux disk encryption architecture
- Configure encrypted filesystem mappings
- Implement host-based firewall protection
- Configure packet filtering using iptables
- Configure packet filtering using nftables
- Configure firewall rules using UFW
- Design secure firewall policies
- Apply Defense-in-Depth principles to Linux systems

---

# Lab Environment

| Component | Technology |
|-----------|------------|
| Operating System | Linux |
| Bootloader | GRUB2 |
| Encryption | LUKS |
| Encryption Utility | cryptsetup |
| Firewall Framework | Netfilter |
| Firewall Tools | iptables, nftables, UFW |
| Storage | Encrypted Linux Partition |
| Terminal | Bash |

---

# Technologies Used

- Linux
- GRUB2
- LUKS
- cryptsetup
- PBKDF2
- Argon2id
- AES-XTS Encryption
- Netfilter
- iptables
- nftables
- UFW
- SSH
- ext4 Filesystem
- Bash

---

# Skills Demonstrated

- Linux System Hardening
- Enterprise Linux Administration
- Physical Security Controls
- Bootloader Security
- Full Disk Encryption
- LUKS Administration
- Linux Filesystem Security
- Host-Based Firewall Configuration
- Packet Filtering
- Firewall Policy Design
- Defense-in-Depth
- Secure Infrastructure Design
- Security Engineering
- Risk Reduction

---

# Project Implementation

## 1. Physical Security

Security begins with protecting the physical system. Regardless of how secure a Linux installation is, an attacker with unrestricted physical access can potentially compromise the operating system.

To reduce this risk, I evaluated several physical security controls commonly implemented in enterprise environments.

These included:

- Restricting physical access to servers
- Preventing unauthorized boot media usage
- Protecting BIOS/UEFI configuration
- Preventing bootloader manipulation
- Securing storage devices against theft

One important security principle reinforced during this project was:

> **Boot Access = Root Access**

Without additional protections, an attacker can interrupt the boot process, modify GRUB parameters, and reset the root password.

Because of this, physical security forms the first layer of any Defense-in-Depth strategy.

---

## 2. GRUB Bootloader Protection

To prevent unauthorized users from modifying boot parameters or resetting the root password, I configured GRUB password protection.

GRUB passwords are stored as PBKDF2 hashes rather than plaintext passwords.

I generated the password hash using:

```bash
grub2-mkpasswd-pbkdf2
```

Example output:

```text
PBKDF2 hash of your password is
grub.pbkdf2.sha512...
```

The generated hash can then be added to the GRUB configuration, preventing unauthorized access to advanced boot options.

Implementing GRUB authentication significantly reduces the likelihood of privilege escalation through bootloader manipulation.

---

## 3. Filesystem Encryption with LUKS

To protect sensitive data against physical theft, I implemented full partition encryption using Linux Unified Key Setup (LUKS).

Unlike traditional filesystem permissions, encryption protects the data itself.

Even if an attacker removes the storage device, the encrypted contents remain inaccessible without the decryption key.

LUKS protects:

- User files
- System data
- Configuration files
- Sensitive organizational information

---

## 4. Understanding the LUKS Architecture

During implementation, I examined the internal structure of an encrypted LUKS partition.

A LUKS-encrypted partition consists of three primary components:

- LUKS Partition Header
- Key Material Slots
- Encrypted Bulk Data

The partition header stores metadata including:

- UUID
- Cipher
- Cipher Mode
- Key Length
- Master Key Checksum

Each Key Material (KM) slot stores an encrypted version of the master key, allowing multiple authorized users to unlock the same encrypted volume using different passwords.

The actual filesystem data is encrypted using the master encryption key.

This architecture provides secure key management while allowing password rotation without re-encrypting the entire disk.

---

## 5. Creating an Encrypted Partition

To configure an encrypted partition, I first identified the target storage device.

Example:

```bash
lsblk
```

After confirming the partition, I initialized it using:

```bash
cryptsetup luksFormat /dev/sdb1
```

Once encryption was configured, I opened the encrypted volume.

```bash
cryptsetup luksOpen /dev/sdb1 EDCdrive
```

The encrypted partition became available through the Linux Device Mapper.

---

## 6. Formatting and Mounting the Encrypted Volume

After opening the encrypted device, I created an ext4 filesystem.

```bash
mkfs.ext4 /dev/mapper/EDCdrive
```

Finally, I mounted the encrypted partition.

```bash
mount /dev/mapper/EDCdrive /media/secure-USB
```

Once mounted, the encrypted volume behaves like any standard Linux filesystem while transparently encrypting all stored data.

---

## 7. Reviewing Encryption Parameters

After configuring the encrypted partition, I reviewed the LUKS configuration.

```bash
cryptsetup luksDump /dev/sdb1
```

The configuration displayed important security information including:

- Encryption algorithm
- Cipher mode
- Key size
- PBKDF configuration
- Salt
- UUID
- Key slots

The implementation used:

- AES-XTS encryption
- SHA-256 hashing
- Argon2id key derivation
- PBKDF2 digest verification

These mechanisms significantly strengthen resistance against brute-force attacks.

---

# Host-Based Firewall Configuration

## 8. Linux Firewall Fundamentals

A host-based firewall controls which packets may enter or leave an individual Linux system.

Unlike perimeter firewalls, host firewalls enforce security directly on the protected machine.

I evaluated Linux firewall technologies used across modern enterprise environments, including:

- Netfilter
- iptables
- nftables
- UFW

The firewall implementation followed a **default-deny** strategy, allowing only explicitly authorized traffic.

---

## 9. Netfilter

Netfilter provides the packet filtering framework built directly into the Linux kernel.

Rather than configuring Netfilter directly, administrators use front-end utilities that translate firewall rules into kernel-level packet filtering logic.

Netfilter forms the foundation for both:

- iptables
- nftables

---

## 10. Configuring iptables

I configured firewall rules using iptables to permit Secure Shell (SSH) traffic while blocking unauthorized communications.

Incoming SSH traffic:

```bash
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

Outgoing SSH traffic:

```bash
iptables -A OUTPUT -p tcp --sport 22 -j ACCEPT
```

To strengthen security, I implemented a default-deny policy.

```bash
iptables -A INPUT -j DROP

iptables -A OUTPUT -j DROP
```

This configuration ensures that only explicitly approved traffic can enter or leave the system.

---

## 11. Configuring nftables

I also evaluated nftables, the modern successor to iptables.

Unlike iptables, nftables requires administrators to create firewall tables and chains before defining filtering rules.

First, I created a firewall table.

```bash
nft add table fwfilter
```

Next, I created input and output chains.

```bash
nft add chain fwfilter fwinput { type filter hook input priority 0 \; }

nft add chain fwfilter fwoutput { type filter hook output priority 0 \; }
```

Finally, I allowed SSH traffic.

```bash
nft add rule fwfilter fwinput tcp dport 22 accept

nft add rule fwfilter fwoutput tcp sport 22 accept
```

The resulting configuration enforced controlled access while benefiting from improved scalability and performance over legacy iptables implementations.

---

## 12. Configuring UFW

To simplify firewall administration, I configured firewall rules using UFW (Uncomplicated Firewall).

Allowing SSH required only a single command.

```bash
ufw allow 22/tcp
```

Firewall status can be verified using:

```bash
ufw status
```

Example output:

```text
22/tcp ALLOW Anywhere
```

UFW abstracts complex firewall syntax while still leveraging the Netfilter framework underneath.

---

## 13. Firewall Policy Design

Rather than allowing unrestricted communication, I designed firewall policies using the Principle of Least Privilege.

Two common approaches were evaluated.

### Default Allow

- Permit all traffic
- Block selected traffic

Advantages:

- Simpler configuration

Disadvantages:

- Larger attack surface

---

### Default Deny

- Block all traffic
- Explicitly allow required services

Advantages:

- Stronger security
- Reduced attack surface
- Better compliance

Disadvantages:

- Requires careful planning

For this project, I implemented the **Default Deny** model to maximize security while allowing only approved services such as SSH.

---

# Security Principles Applied

- Defense-in-Depth
- Least Privilege
- Secure by Default
- Default Deny
- Data Confidentiality
- Layered Security
- Physical Security
- Secure Boot Protection
- Encryption at Rest
- Host-Based Access Control
- Attack Surface Reduction

---

# Key Outcomes

- Hardened Linux systems against physical attacks
- Protected GRUB from unauthorized modification
- Implemented full disk encryption using LUKS
- Configured secure encrypted filesystem mappings
- Applied enterprise-grade encryption standards
- Implemented host-based firewall protection
- Configured packet filtering with iptables
- Configured packet filtering with nftables
- Simplified firewall administration using UFW
- Designed firewall policies using the Principle of Least Privilege
- Reduced the overall system attack surface through layered security controls

---

# Lessons Learned

This project demonstrated that Linux security extends well beyond user authentication and software updates. Effective system hardening requires securing every stage of the system lifecycle—from physical access and the boot process to data storage and network communications.

Implementing GRUB protection, LUKS encryption, and host-based firewall policies significantly strengthened the system's resistance against unauthorized access, data theft, and network-based attacks. Additionally, comparing multiple Linux firewall technologies provided practical insight into selecting the appropriate solution based on administrative complexity, scalability, and operational requirements.

Overall, this project reinforced the importance of applying multiple complementary security controls rather than relying on a single defensive mechanism, resulting in a more resilient and enterprise-ready Linux environment.

---


# Disclaimer

> **Disclaimer:** This project was completed in an authorized lab and training environment for educational and defensive cybersecurity purposes. All configurations, testing activities, and security implementations were performed on systems where explicit authorization was granted. No testing or modifications were conducted against unauthorized systems.
