# Windows Core Processes

## Overview

Windows uses core system processes to handle authentication, system services, and user logon. Understanding these processes helps identify normal behavior and detect potential security issues.

## What I learned

- lsass.exe handles authentication and enforces security policies on Windows systems
- lsass.exe creates access tokens and stores credential-related information in memory
- svchost.exe is used to run multiple Windows services in the background
- winlogon.exe manages user logon and logoff processes
- These processes are critical to system operation and should not be terminated under normal conditions

## One Example

When a user logs into a system, lsass.exe verifies login attempts and creates an access token based on the user's permissions. 
If this process is compromised, attackers may be able to access sensitive credential information stored in memory.

## Key Takeaways

- lsass.exe is a high-value target because it handles authentication and credentials
- svchost.exe may appears multiple times because it hosts different services
- winlogon.exe is responsible for managing user logon processes
- Understanding normal process behavior helps detect anomalies and potential attacks
