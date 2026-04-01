# SMB (Server Message Block)

## Overview

SMB (Server Message Block) is a protocol used by Windows to connect shared resources such as files, folders, and printers.

## What I learned

- SMB allows a client to request access to shared resources on another system
- A client connects to an SMB server over the network to access shared resources
- The server authenticates the user and checks permissions
- Access is granted or denied based on both share and NTFS permissions
- SMB is commonly used in Windows environments for file and printer sharing
- SMB is commonly used in internal networks, but misconfigured shares or exposed services can create security risks
- Attackers may attempt to access shared resources, move laterally within a network, or exploit vulnerabilities if proper controls are not in place
- SMB commonly operates over port 445
- SMB can be absued for lateral movement if attackers gain access to a system and attempt to reach other systems on the network

## Key Takeaways

- SMB is used to access shared resources over a network, typically within a local environment
- NTFS permissions control file access, while Share permissions control network access
- The most restrictive permission between NTFS and Share determines effective access
- SMB commonly operates over port 445 and should not be exposed to the public internet
- Misconfigured SMB shares can create security risks, including unauthorized access and lateral movement
