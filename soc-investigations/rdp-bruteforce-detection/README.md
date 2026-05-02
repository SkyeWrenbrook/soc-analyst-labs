# Detecting RDP Brute Force Attempts in Windows Security Logs

## Overview
This investigation simulates repeated failed Remote Desktop Protocol (RDP) login attempts from a Kali Linux VM to a Windows VM and analyzes Windows Security logs to identify brute-force behavior.

The goal is to validate how repeated authentication failures are recorded in logs and whether they can be reliably measured against a defined threshold.

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

These repeated failures generate security events that can be analyzed to validate how authentication behavior is recorded and measured in logs.

---

## Detection Hypothesis

Hypothesis: Repeated failed authentication attempts from a single source IP should be observable and quantifiable within a defined time window. 

This threshold (≥5 failed authentication attempts within 15 minutes) was used as a test condition to evaluate whether such patterns are clearly visible and traceable in Windows Security logs.

---

## Evidence

<img width="634" height="302" alt="rdp-failed-login" src="https://github.com/user-attachments/assets/9acbc28a-9e72-4d8f-a754-367bac0b4266" />

### Key Event Details
- **Event ID:** 4625 (Failed login)
- **Account Name:** user
- **Source Network Address:** 192.168.x.x (Kali VM)
- **Logon Type:** 3 (Network logon)

Logon Type 3 indicates a network-based authentication attempt. In RDP scenerios, Logon Type 10 may also be osberved depending on the authentication stage.

### Observed Pattern
- 6 failed login attempts
- Same source IP
- Occurred within approximately 15 minutes

### Sample Events

| Time         | Event ID | Account | Source IP     | Logon Type |
|--------------|----------|---------|---------------|------------|
| 3:32:27 PM   | 4625     | user    | 192.168.56.101   | 3          |
| 3:32:26 PM   | 4625     | user    | 192.168.56.101   | 3          |
| 3:32:25 PM   | 4625     | user    | 192.168.56.101   | 3          |
| 3:32:23 PM   | 4625     | user    | 192.168.56.101   | 3          |
| 3:32:20 PM   | 4625     | user    | 192.168.56.101   | 3          |
| 3:32:13 PM   | 4625     | user    | 192.168.56.101   | 3          |

---

## Analysis

This investigation validates that repeated failed authentication attempts from a single source IP are clearly observable in Windows Security logs and can be quantified over a defined time window.

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

- Explore how similar patters appear across different authentication methods
- Refine thresholds to distinguish between brute force and password spraying behavior
