# 🧠 Active Directory Enumeration Lab

> 🚀 Hands-on cybersecurity lab demonstrating enumeration of an Active Directory Domain Controller using Kali Linux.

---

## 👨‍💻 About This Project

This project simulates a real-world internal network where an attacker performs reconnaissance against a Windows Domain Controller.

The objective was to:
- Identify domain infrastructure
- Enumerate system information
- Attempt unauthenticated access
- Analyze exposed services

---

## 🖥️ Lab Environment

| Role              | Machine |
|------------------|--------|
| Attacker         | Kali Linux |
| Domain Controller| Windows Server (DC01) |
| Client Machine   | Windows 10 (Domain Joined) |
| Network          | Host-only (192.168.56.0/24) |

---

## 🔍 Phase 1: Target Discovery

### Command:
```bash
nmap -p 445 192.168.56.10
