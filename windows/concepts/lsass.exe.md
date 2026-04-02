# lsass.exe

## Overview

lsass.exe is a core Windows system process located in the System32 directory that is responsible for handling authentication and enforcing security policies. 
It is critical to system security because it manages user credentials in memory, making it a high-value target for attackers seeking unauthorized access.

## Objective
- Observe lsass.exe in a real Windows environment
- Identify its expected location and behavior (e.g., System32, SYSTEM privileges)
- Understand how to verify normal vs abnormal process characteristics
- Develop awareness of suspicious indicators, such as unexpected file paths (e.g., user or Temp directories)

## What I learned
- lsass.exe is a single, critical Windows process responsible for authentication and security policy enforcement
- It runs continuously after system boot under SYSTEM privileges
- Its expected location is C:\Windows\System32\lsass.exe
- Any instance outside this path is highly suspicious and likely masquerading malware
- LSASS is typically initialized during the Windows boot process and should not be spawned by user-level applications
- Attackers commonly target the real LSASS process to extract credentials from memory

## Example

## Key Takeaways
- Verify both process path and parent process to detect anomalies
- Multiple instances of LSASS should be treated as a high-priority alert
- Focus detection on interaction with LSASS, not just its existence
- Credential access behavior is often more important than process creation events
- High-value system processes require behavioral monitoring, not just signature checks
