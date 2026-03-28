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

## 🧭 Lab Overview

📸 **Virtual Environment:**

<img width="526" height="280" alt="Screenshot 2026-03-27 204106" src="https://github.com/user-attachments/assets/f2878335-e6d7-4956-bf8e-24ef4cc7767e" />

## 🛠️ Tools Used

- Nmap
- enum4linux-ng
- smbclient
- rpcclient
- Kali Linux
- Windows Server 2022

# 🔍 Phase 1: Service Discovery

Key Findings:
445/tcp → SMB (microsoft-ds)
389/tcp → LDAP
88/tcp → Kerberos

👉 These services confirm the target is an Active Directory Domain Controller

📸 **Nmap Scan Results:**

<img width="1280" height="765" alt="nmap" src="https://github.com/user-attachments/assets/80c77c75-2194-425a-9ff7-c14568355c13" />

**Analysis:**
- Port 445 confirms SMB is enabled
- Port 389 confirms LDAP is running
- Port 88 indicates Kerberos authentication

👉 These services confirm the system is a Domain Controller.


🔎 Phase 2: SMB Enumeration

Command:
smbclient -L //192.168.56.10 -N
Findings:
Attempted anonymous SMB share enumeration
Limited or restricted access observed

👉 Indicates basic access controls are in place

📸 SMB Share Enumeration:
<img width="1280" height="765" alt="smb-shares" src="https://github.com/user-attachments/assets/a3421aa5-9df3-4372-b162-f75d42126ef5" />

🔍 Phase 3: Advanced Enumeration (enum4linux-ng)

Command:
enum4linux-ng 192.168.56.10
Key Findings:
Domain Name: LAB
Hostname: DC01
Domain SID identified
System confirmed as part of Active Directory

📸 Enumeration Output:
<img width="1280" height="765" alt="enum-ng" src="https://github.com/user-attachments/assets/3e3ebd36-e859-436b-a857-f0032a3d9c10" />

🔍 Phase 4: RPC Enumeration Attempt

Command:
rpcclient -U "" -N 192.168.56.10

Inside rpcclient:
enumdomusers
Result:
NT_STATUS_ACCESS_DENIED
Analysis:
User enumeration blocked
Indicates hardened configuration against anonymous access

# 🧠 Attacker Perspective

From this enumeration, an attacker can identify:

- Domain name (LAB)
- Domain controller hostname (DC01)
- Active Directory services 
- Potential null session access

👉 This information can be used for:
- Credential attacks
- Kerberos attacks
- Lateral movement




