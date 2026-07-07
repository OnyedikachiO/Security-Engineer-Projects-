# Secure Network Architecture: Network Segmentation, Traffic Filtering & Defense-in-Depth

## Overview

This project demonstrates the design and implementation of a secure enterprise network architecture using industry best practices for network segmentation, access control, traffic filtering, and layered security.

The environment was designed to minimize the organization's attack surface by implementing VLAN-based segmentation, security zones, stateful firewall policies, Access Control Lists (ACLs), and Layer 2 validation mechanisms such as DHCP Snooping and Dynamic ARP Inspection (DAI). The project also explores modern network protection techniques including SSL/TLS inspection and zone-based firewall architectures.

The implementation follows security engineering principles commonly used in enterprise environments to improve confidentiality, integrity, availability, and overall network resilience.

---

## Objectives

- Design a secure enterprise network architecture
- Implement VLAN-based network segmentation
- Configure secure routing between VLANs
- Apply security zoning principles
- Implement Access Control Lists (ACLs)
- Configure stateful firewall policies using Zone-Pairs
- Inspect encrypted traffic using SSL/TLS inspection
- Validate Layer 2 traffic using DHCP Snooping
- Prevent ARP spoofing attacks using Dynamic ARP Inspection (DAI)
- Apply Defense-in-Depth principles throughout the network

---

## Architecture Overview

The network was designed around multiple security zones to isolate systems based on business function and sensitivity.

```text
                    Internet
                        │
                 External Zone
                        │
                Stateful Firewall
                        │
                    DMZ Network
             ┌──────────┴──────────┐
             │                     │
      Public Web Server       VPN Gateway
                        │
                 Internal Firewall
                        │
        ┌───────────────┼───────────────┐
        │               │               │
     Trusted        Restricted      Management
     Network          Servers          VLAN
        │               │               │
   Employee PCs   Domain Controllers
                  Database Servers
```

Traffic between every security zone follows a **default-deny** model, where only explicitly authorized communications are permitted.

---

## Technologies & Platforms

- Open vSwitch (OVS)
- VyOS Router
- VLAN (IEEE 802.1Q)
- Access Control Lists (ACLs)
- Stateful Firewall Policies
- Zone-Based Firewall
- DHCP Snooping
- Dynamic ARP Inspection (DAI)
- SSL/TLS Inspection
- Enterprise Network Segmentation

---

## Skills Demonstrated

- Enterprise Network Security
- Secure Network Architecture
- VLAN Design & Implementation
- Layer 2 Security
- Layer 3 Routing
- Firewall Policy Design
- Access Control
- Traffic Filtering
- Defense-in-Depth
- Network Hardening
- Secure Infrastructure Design
- Security Policy Enforcement

---

# Project Implementation

## 1. Network Segmentation with VLANs

To reduce lateral movement across the network, I segmented the environment using Virtual LANs (VLANs).

Each department or security zone was assigned its own VLAN, providing logical isolation while sharing the same physical switching infrastructure.

### Example VLAN Assignments

| VLAN | Purpose |
|------|---------|
| VLAN 10 | Trusted Users |
| VLAN 20 | Internal Servers |
| VLAN 30 | DMZ |
| VLAN 40 | Management |

Traffic entering switch ports was tagged using the IEEE 802.1Q standard to preserve VLAN separation across trunk links.

### Example Open vSwitch Configuration

```bash
ovs-vsctl set port eth1 tag=10
```

Unknown traffic was assigned to a Native VLAN to ensure all network traffic remained properly classified.

---

## 2. Router-on-a-Stick (ROAS)

Instead of deploying multiple physical router interfaces, I implemented inter-VLAN routing using a Router-on-a-Stick (ROAS) architecture.

Virtual interfaces were configured for each VLAN.

### Example

```bash
set interfaces ethernet eth0 vif 10 address 192.168.100.1/24
```

This centralized routing while maintaining secure communication between isolated VLANs.

---

## 3. Security Zone Design

The network was organized into dedicated security zones based on business function and system sensitivity.

| Zone | Purpose |
|------|---------|
| External | Internet Users |
| DMZ | Public-Facing Services |
| Trusted | Employee Devices |
| Restricted | Sensitive Servers |
| Management | Infrastructure Administration |
| Audit | Security Monitoring Systems |

This architecture reduced exposure and simplified policy enforcement across the environment.

---

## 4. Access Control Lists (ACLs)

Traffic filtering was implemented using Access Control Lists (ACLs) to define permitted and denied communications.

ACL rules evaluated:

- Source Address
- Destination Address
- Network Prefix
- Host
- Interface

### Example ACL

```bash
set policy access-list 1 rule 1 action permit
set policy access-list 1 rule 1 source 10.10.212.0/24
```

Packets not matching approved criteria were denied by default.

---

## 5. Stateful Firewall Deployment

To improve traffic filtering beyond traditional ACLs, I implemented stateful firewall inspection.

Unlike stateless filtering, stateful firewalls track:

- Session State
- Protocol
- Port
- Connection Direction
- Related Connections

### Default Firewall Policy

**Default Action**

```
DROP
```

**Allowed Traffic**

- Established Connections
- Related Connections
- Explicitly Permitted Services

This approach ensures that only trusted and authorized sessions are allowed through the firewall.

---

## 6. Zone-Pair Policy Implementation

Traffic between every security zone was explicitly controlled using Zone-Pair firewall policies.

### Example Policy

| Source | Destination | Protocol | Action |
|---------|------------|----------|--------|
| LAN | WAN | ICMP | Drop |
| WAN | LAN | ICMP | Allow |
| DMZ | LAN | HTTP | Allow |

### Example Configuration

```bash
set zone-policy zone LAN from WAN firewall name lan-wan
```

Directional policies enforce the principle of least privilege across security boundaries.

---

## 7. SSL/TLS Inspection

Encrypted traffic was inspected using SSL/TLS interception before reaching internal resources.

Traffic passed through an SSL Proxy before being analyzed by Unified Threat Management (UTM) services.

Inspection enabled:

- Malware Detection
- HTTPS Filtering
- Intrusion Prevention
- Threat Intelligence
- Content Inspection

This reduced the risk of malicious encrypted traffic bypassing traditional perimeter defenses.

---

## 8. DHCP Snooping

DHCP Snooping was implemented to defend against rogue DHCP servers.

The switch validated DHCP messages and maintained a trusted DHCP Binding Database containing legitimate IP-to-MAC mappings.

### Protection Against

- Rogue DHCP Servers
- DHCP Starvation Attacks
- Malicious Address Assignment

---

## 9. Dynamic ARP Inspection (DAI)

Dynamic ARP Inspection (DAI) leveraged the DHCP Binding Database to validate ARP packets.

Incoming ARP traffic was checked against known IP-to-MAC bindings.

Packets with mismatched information were discarded automatically.

### Protection Against

- ARP Spoofing
- ARP Poisoning
- Man-in-the-Middle (MitM) Attacks

---

# Security Principles Applied

- Network Segmentation
- Least Privilege
- Defense-in-Depth
- Zero Trust Concepts
- Default Deny
- Layered Security
- Secure Routing
- Traffic Validation
- Continuous Monitoring
- Risk Reduction

---

# Key Outcomes

- Designed a segmented enterprise network architecture using VLAN isolation
- Reduced the attack surface through logical network segmentation
- Controlled inter-zone communication with ACLs and stateful firewall policies
- Implemented Zone-Based Firewall policies following a default-deny approach
- Protected Layer 2 communications using DHCP Snooping and Dynamic ARP Inspection
- Improved visibility into encrypted traffic using SSL/TLS inspection
- Applied enterprise-grade security zoning to strengthen network resilience
- Reinforced Defense-in-Depth through multiple complementary security controls

---

# Lessons Learned

This project reinforced the importance of building security into network architecture rather than relying solely on endpoint protection. Implementing network segmentation, access control, and traffic validation significantly reduces the risk of lateral movement, unauthorized access, and network-based attacks.

By combining VLANs, stateful firewalls, Layer 2 protections, and security zoning, I developed a resilient Defense-in-Depth architecture that aligns with modern enterprise security best practices.

---


# Disclaimer

> **Disclaimer:** This project was completed in an authorized lab and training environment for educational and defensive cybersecurity purposes. All configurations, security assessments, and network implementations were performed on systems where explicit permission was granted. No testing or activity was conducted against unauthorized systems.
