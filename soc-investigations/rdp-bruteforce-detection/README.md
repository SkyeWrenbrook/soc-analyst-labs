# Detecting RDP Brute Force Attempts in Windows Security Logs

## Overview
This investigation simulates repeated failed Remote Desktop Protocol (RDP) login attempts from a Kali Linux VM to a Windows VM and analyzes Windows Security logs to identify brute-force behavior.

The goal is to understand how authentication activity appears in logs and how repeated failures from a single source can indicate suspicious activity.

---

## Lab Setup
- Kali Linux VM (attacker)
- Windows VM (target)
- VirtualBox with Host-only networking
- RDP enabled on Windows
- Windows Event Viewer → Security Logs

---

## Scenario
A remote system attempts to authenticate to a Windows machine multiple times using incorrect credentials over RDP.

These repeated failures generate security events that can be analyzed to detect potential brute-force activity.

---

## Detection Logic
If a source IP generates **≥5 failed login attempts within 15 minutes**, flag it as suspicious.

This threshold is based on observed behavior during testing.

---

## Evidence

<img width="634" height="302" alt="rdp-failed-login" src="https://github.com/user-attachments/assets/9acbc28a-9e72-4d8f-a754-367bac0b4266" />

### Key Event Details
- **Event ID:** 4625 (Failed login)
- **Account Name:** user
- **Source Network Address:** 192.168.x.x (Kali VM)
- **Logon Type:** 3 (Network logon)

### Observed Pattern
- 6 failed login attempts
- Same source IP
- Occurred within approximately 15 minutes

### Sample Events

| Time         | Event ID | Account | Source IP     | Logon Type |
|--------------|----------|---------|---------------|------------|
| 3:32:27 PM   | 4625     | user    | 192.168.x.x   | 3          |
| 3:34:10 PM   | 4625     | user    | 192.168.x.x   | 3          |
| 3:36:02 PM   | 4625     | user    | 192.168.x.x   | 3          |
| ...          | ...      | ...     | ...           | ...        |

---

## Analysis

The repeated failed login attempts from a single IP address within a short time window indicate a potential brute-force or password spraying attempt.

Key indicators:
- Multiple authentication failures
- Consistent source IP
- Short time interval between attempts

This pattern suggests automated or persistent login attempts rather than normal user behavior.

---

## SOC Takeaway

Authentication logs provide critical visibility into potential attack activity.

Repeated failed logins from a single source IP should be investigated as they may indicate:
- Brute force attacks
- Password spraying
- Unauthorized access attempts

This investigation demonstrates how raw log data can be used to identify suspicious patterns before a successful compromise occurs.

---

## Next Steps

- Automate detection using SQL queries on structured log data
- Expand detection to include:
  - Successful login after multiple failures
  - Multiple usernames targeted by a single IP
- Integrate with SIEM tools for real-time alerting
