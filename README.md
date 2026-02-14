## Table of Contents

- [Objective](#objective)
- [Lab Architecture](#lab-architecture)
- [Implemented Labs](#implemented-labs)
- [Password Spraying Detection](#password-spraying-detection)
- [Future Labs](#future-labs)



# SOC Home Lab – Active Directory

This project documents the creation of a hands-on Active Directory lab designed to simulate real-world enterprise environments from a defensive (SOC) perspective.

The objective is to understand authentication flows, privilege escalation risks, attack paths, and detection strategies inside a Windows domain environment.

---

## 🎯 Objectives

- Install and configure a Domain Controller
- Deploy Active Directory (AD)
- Join a Windows client to the domain
- Generate authentication events
- Analyze Windows Security logs
- Simulate suspicious activity for detection practice

---

## 🏗️ Lab Architecture (Phase 1)

- Windows Server 2022 (Domain Controller)
- Windows 10/11 Client (Domain-joined machine)
- VMware Workstation (Virtualization)
- Windows 11 Host Machine
- Isolated Host-Only Network

---

## 🔐 Focus Areas

- Kerberos authentication
- NTLM vs Kerberos analysis
- Windows Event ID monitoring (4768, 4769, 4771, 4624, 4625)
- Privilege escalation scenarios
- Defensive detection mindset
- Active Directory security fundamentals

---

## 🧪 Implemented Labs

### 🔎 Kerberos Password Spraying Detection

- Simulated fast password spraying attack
- Generated multiple Event ID 4771 entries
- Analyzed source IP correlation
- Evaluated authentication method and failure codes
- Developed detection logic and mitigation recommendations

More attack simulations and defensive detection use cases will be added as the project evolves.
