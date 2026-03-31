# PowerShell Basic Enumeration Lab

## Objective

The purpose of this lab is to practice using a few basic PowerShell commands to understand what is happening on a Windows system.

The goal isn't to memorize commands, but to start getting comfortable looking at a system and asking simple questions like:
	•	who is logged in
	•	what is running
	•	what services are active

⸻

## Commands I ran

## 1. Check current user

whoami

This shows the user currently logged in.

⸻

## 2. View running processes

Get-Process


This shows what is currently running on the system.

⸻

## 3. View services

Get-Service


This shows background services.

⸻

## 4. Show only running services


Get-Service | Where-Object {$_.Status -eq "Running"}


This filters the output so I only see what is actually running.

⸻

## 5. View local users


Get-LocalUser


This shows the users on the system.

⸻

## Key Takeaways
- PowerShell helps me quickly look at what is happening on a system
- Even simple commands can give useful information
- Filtering output makes it easier to focus
- This is similar to how I would start looking at a system during an investigation

⸻

## Why this matters

These commands help with basic system visibility.

In a real environment, this could help identify:
- unexpected processes
- unknown user accounts
- services that shouldn’t be running

⸻

## Reflection

This felt simple, but it helped me start thinking differently.

Instead of just running commands, I started asking:

what am I actually looking for?

⸻

