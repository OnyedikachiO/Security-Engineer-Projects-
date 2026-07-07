# Secure Key Exchange with Diffie-Hellman

> A hands-on Security Engineering project demonstrating the implementation of the Diffie-Hellman key exchange protocol using OpenSSL. This project explores secure key establishment over untrusted networks, practical parameter generation, protocol security, and the importance of authentication in defending against Man-in-the-Middle (MITM) attacks.

---

# Project Overview

Secure communication depends not only on strong encryption algorithms but also on the ability of communicating parties to establish a shared secret securely. One of the most significant breakthroughs in modern cryptography is the **Diffie-Hellman Key Exchange**, which allows two parties to agree on a common secret over an insecure communication channel.

In this project, I explored the mathematical principles behind the Diffie-Hellman algorithm, generated real-world Diffie-Hellman parameters using OpenSSL, inspected cryptographic parameter files, validated prime sizes, and examined why the protocol alone cannot guarantee authentication.

Additionally, I analyzed how a Man-in-the-Middle (MITM) attack compromises unauthenticated Diffie-Hellman exchanges and why modern secure communication protocols integrate authentication mechanisms alongside key exchange.

All activities were completed within an authorized Security Engineering laboratory environment using OpenSSL and Linux command-line tools.

---

# Objectives

- Understand the purpose of secure key exchange
- Explore the Diffie-Hellman algorithm
- Understand public and private key generation
- Learn how shared secrets are established
- Generate Diffie-Hellman parameters with OpenSSL
- Inspect Diffie-Hellman parameter files
- Validate prime sizes and generators
- Understand the Discrete Logarithm Problem
- Analyze Man-in-the-Middle attacks
- Understand why authentication is required in modern cryptographic protocols

---

# Technologies & Tools

| Category | Technology |
|----------|------------|
| Operating System | Kali Linux |
| Cryptography Toolkit | OpenSSL |
| Shell | Bash |
| Key Exchange Protocol | Diffie-Hellman |
| Cryptographic Concepts | Modular Arithmetic |

---

# Skills Demonstrated

- Security Engineering
- Cryptographic Engineering
- Diffie-Hellman Key Exchange
- OpenSSL Administration
- Linux Security
- Cryptographic Parameter Validation
- Secure Key Establishment
- Cryptographic Analysis
- Threat Modeling
- Network Security Fundamentals

---

# Introduction

Encryption algorithms such as AES require both communicating parties to possess the same secret key before encrypted communication can begin.

The challenge is how two users can establish this shared secret without exposing it to attackers monitoring the communication channel.

The Diffie-Hellman Key Exchange protocol solves this problem by allowing both parties to independently calculate the same shared secret without ever transmitting that secret across the network.

Even if an attacker intercepts every exchanged message, deriving the shared secret remains computationally infeasible when secure parameters are used.

---

# Understanding Diffie-Hellman

The Diffie-Hellman algorithm relies on two publicly known values:

- A large prime number (q)
- A generator (g)

Each participant independently selects a private value.

Using these values, each participant calculates a corresponding public value which is exchanged across the network.

Despite exchanging only public information, both participants ultimately compute the exact same shared secret.

---

# Diffie-Hellman Workflow

```mermaid
flowchart LR

A[Alice]

B[Bob]

A -->|Public Value A| B

B -->|Public Value B| A

A --> C[Shared Secret]

B --> C
```

---

# Key Exchange Process

## Step 1 — Public Parameters

Both communicating parties first agree on two public values.

- Prime Number (q)
- Generator (g)

These values are not secret and may be transmitted openly.

Example:

```
Prime (q): 29
Generator (g): 3
```

---

## Step 2 — Private Key Selection

Each participant generates a random private number.

Example:

**Alice**

```
Private Key = 13
```

**Bob**

```
Private Key = 15
```

These values never leave their respective systems.

---

## Step 3 — Public Key Generation

Using the agreed parameters, each participant computes a public value.

Alice computes:

```
A = g^a mod q
```

Bob computes:

```
B = g^b mod q
```

Only these public values are exchanged.

---

## Step 4 — Shared Secret Generation

After exchanging public values, both participants independently compute the shared secret.

Alice computes:

```
Shared Secret = B^a mod q
```

Bob computes:

```
Shared Secret = A^b mod q
```

Despite performing different calculations, both obtain the exact same secret key.

```mermaid
flowchart LR

A[Prime q]

B[Generator g]

C[Alice Private Key]

D[Bob Private Key]

A --> E

B --> E

C --> E

E --> F[Alice Public Value]

A --> G

B --> G

D --> G

G --> H[Bob Public Value]

F --> I[Shared Secret]

H --> I
```

---

# Why Diffie-Hellman Is Secure

An attacker monitoring the communication can observe:

- Prime Number
- Generator
- Alice's Public Value
- Bob's Public Value

However, the attacker cannot efficiently recover either participant's private key because doing so requires solving the **Discrete Logarithm Problem**, which becomes computationally infeasible when large cryptographic parameters are used.

Modern implementations typically use prime numbers ranging from **2048 bits** to **4096 bits**, making brute-force recovery impractical with current computing capabilities.

---

# Generating Diffie-Hellman Parameters with OpenSSL

To simulate real-world deployments, I generated Diffie-Hellman parameters using OpenSSL.

Generate a 2048-bit parameter file:

```bash
openssl dhparam -out dhparams.pem 2048
```

Inspect the generated parameters:

```bash
openssl dhparam -in dhparams.pem -text -noout
```

The output exposes:

- Prime Number
- Generator
- Parameter Size

This exercise demonstrates how production systems generate trusted Diffie-Hellman parameters for secure key exchange.

---

# Practical Implementation

## Generating Diffie-Hellman Parameters

To simulate a production-ready key exchange, I generated Diffie-Hellman parameters using OpenSSL.

Generate a 2048-bit parameter file:

```bash
openssl dhparam -out dhparams.pem 2048
```

Inspect the generated parameters:

```bash
openssl dhparam -in dhparams.pem -text -noout
```

The generated parameter file contains:

- Prime Number (P)
- Generator (G)
- Parameter Size

Generating large prime numbers requires significant computational effort because OpenSSL searches for cryptographically secure prime values suitable for Diffie-Hellman key exchange.

---

# Inspecting Diffie-Hellman Parameters

One of the practical tasks involved inspecting an existing Diffie-Hellman parameter file.

```bash
openssl dhparam -in dhparams.pem -text -noout
```

Example output:

```text
DH Parameters: (4096 bit)

prime:
00:c0:10:65:c6:ad...

generator: 2 (0x2)
```

From the generated output I verified:

- Parameter Size: **4096 bits**
- Generator Value: **2**

This confirmed that strong cryptographic parameters had been generated successfully.

---

# Parameter Validation

As part of the laboratory exercise, I validated important characteristics of the generated Diffie-Hellman parameters.

## Prime Size

Verified that the generated prime was:

```
4096 bits
```

Using larger prime values significantly increases resistance against attacks targeting the Discrete Logarithm Problem.

---

## Least Significant Byte

After inspecting the generated prime number, I identified its final byte.

```
4f
```

This exercise demonstrated how to inspect cryptographic parameter files using OpenSSL and verify generated values.

---

# Security Analysis

The Diffie-Hellman protocol successfully enables two parties to establish a shared secret without transmitting that secret across the network.

However, Diffie-Hellman alone provides:

- Confidentiality
- Secure key establishment

It does **not** provide:

- Authentication
- Identity verification

Without authentication, the protocol remains vulnerable to impersonation attacks.

---

# Man-in-the-Middle (MITM) Attack

One of the most significant weaknesses of unauthenticated Diffie-Hellman is its susceptibility to a **Man-in-the-Middle (MITM)** attack.

During this attack, an adversary intercepts the key exchange process and establishes independent shared secrets with both communicating parties.

Instead of Alice and Bob communicating securely with one another, both unknowingly establish encrypted sessions with the attacker.

The attacker can then:

- Read messages
- Modify messages
- Forward altered messages
- Impersonate both parties

without either participant realizing the compromise.

---

# MITM Attack Workflow

```mermaid
flowchart LR

Alice -->|Public Value| Mallory

Mallory -->|Fake Public Value| Bob

Bob -->|Public Value| Mallory

Mallory -->|Fake Public Value| Alice

Mallory --> SharedSecret1

Mallory --> SharedSecret2
```

---

# Engineering Implications

This exercise demonstrates an important engineering principle:

> **Encryption alone does not guarantee secure communication.**

A secure communication protocol must provide:

- Confidentiality
- Authentication
- Integrity

Diffie-Hellman solves only one part of the problem:

**Secure key establishment.**

Authentication must be added separately.

---

# Modern Security Solutions

Modern cryptographic protocols solve the authentication problem by combining Diffie-Hellman with digital certificates and public key infrastructure (PKI).

Examples include:

- TLS
- HTTPS
- SSH
- VPN protocols

These protocols authenticate communicating parties before completing the Diffie-Hellman key exchange, preventing MITM attacks.

---

# Validation & Practical Exercises

During this project, I successfully completed the following practical exercises:

- Generated Diffie-Hellman parameters using OpenSSL
- Inspected generated parameter files
- Verified cryptographic parameter sizes
- Identified generator values
- Validated prime lengths
- Examined prime number structures
- Identified the least significant byte of generated primes
- Explored secure key establishment
- Analyzed Diffie-Hellman security properties
- Investigated Man-in-the-Middle attacks against unauthenticated key exchange

These exercises strengthened my practical understanding of cryptographic key establishment within Security Engineering environments.

---

# Security Engineering Takeaways

- Diffie-Hellman enables secure key exchange over untrusted networks.
- Private keys are never transmitted during the exchange.
- Large prime numbers provide computational security.
- The Discrete Logarithm Problem forms the mathematical foundation of Diffie-Hellman security.
- OpenSSL provides practical tools for generating production-quality Diffie-Hellman parameters.
- Diffie-Hellman alone does not authenticate communicating parties.
- Authentication mechanisms such as PKI are essential to prevent MITM attacks.
- Secure communication protocols combine multiple cryptographic techniques rather than relying on a single algorithm.

---

# Challenges Encountered

- Understanding modular exponentiation concepts.
- Differentiating between public parameters and private values.
- Inspecting and interpreting OpenSSL-generated Diffie-Hellman parameter files.
- Understanding why secure key exchange does not automatically provide authentication.
- Visualizing how Man-in-the-Middle attacks compromise unauthenticated protocols.

---

# Lessons Learned

This project provided practical experience implementing the Diffie-Hellman key exchange protocol and reinforced the importance of secure key establishment in modern cryptographic systems. I gained hands-on experience generating and validating Diffie-Hellman parameters using OpenSSL while developing a deeper understanding of how shared secrets are securely established across untrusted networks. The project also highlighted that encryption alone is insufficient for secure communication and demonstrated why authentication mechanisms such as Public Key Infrastructure (PKI) are critical for defending against Man-in-the-Middle attacks in real-world environments.

---


# Disclaimer

> **Disclaimer:** This project was completed within an authorized training and laboratory environment for educational purposes. All cryptographic analysis, parameter generation, protocol implementation, and security validation activities were performed using controlled lab resources and do not target or expose real-world systems, networks, or sensitive information.
