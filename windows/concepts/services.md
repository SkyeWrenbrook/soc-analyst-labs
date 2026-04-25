# Overview
This note covers how to start, stop, and query Windows services locally and remotely using PowerShell.
Understanding service behavior is important for identifying misconfigurations and potential malicious activity.

# What I learned
Using the Get-Service command, I can enumerate running services and gather key details such as service name and status.
Querying remote hosts allows analysts to:
- identify services that should not be running
- detect unauthorized or suspicious services
- validate system configurations across multiple machines

From a blue team perspective, this is useful because malicious services can be used for persistence or unauthorized execution.

# Example
```Invoke-Command -ComputerName [hostname],LOCALHOST -SCRIPTBLOCK {Get-Service -Name 'windefend'}```
Breakdown:
- Invoke-Command → executes commands on local or remote systems
- ComputerName → specifies target systems
- ScriptBlock {} → contains the command to run

This allows centralized monitoring of services across systems

For example:
- If a non-standard service appears on multiple hosts, it may indicate lateral movement or persistence

# Key Takeaways
- Windows services are a common target for attackers
- Service enurmeration helps identify abnormal system behavior
- Remote querying enables scalable monitoring across environments
- Understanding service behavior is critical for detecting persistence mechanisms
