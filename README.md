# 🧠 Active Directory Enumeration Lab (Kali + Windows Server)

> 🚀 Hands-on cybersecurity lab demonstrating enumeration of an Active Directory Domain Controller using Kali Linux.

---

## 👨‍💻 About This Project

This project simulates a real-world internal network where an attacker performs reconnaissance and enumeration against a Windows Active Directory environment.

The objective was to:
- Identify domain infrastructure
- Enumerate services and open ports
- Attempt unauthenticated (null session) enumeration
- Analyze exposed information from the Domain Controller

---

## 🖥️ Lab Environment

| Role              | Machine |
|------------------|--------|
| Attacker         | Kali Linux |
| Domain Controller| Windows Server 2022 (DC01) |
| Client Machine   | Windows 10 (Domain Joined) |
| Network          | Host-only (192.168.56.0/24) |

---

## 🌐 Network Configuration

| Machine        | IP Address       |
|---------------|-----------------|
| DC01          | 192.168.56.10   |
| WIN10-CLIENT  | 192.168.56.20   |
| Kali          | 192.168.56.X    |

---

# 🔍 Phase 1: Service Discovery

Key Findings:
445/tcp → SMB (microsoft-ds)
389/tcp → LDAP
88/tcp → Kerberos

👉 These services confirm the target is an Active Directory Domain Controller
📸 Nmap Scan Results: 
<img width="1280" height="765" alt="nmap" src="https://github.com/user-attachments/assets/80c77c75-2194-425a-9ff7-c14568355c13" />

