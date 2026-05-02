# Detecting RDP Brute Force Attempts in Windows Security Logs

## Overview

This investigation simulates repeated failed Remote Desktop Protocol (RDP) login atetmpts from a Kali Linux VM to a Windows VM and analyzes Windows Security logs to identify brute-force behavior.

The goal is to understand how authentication activity appears in logs and how repeated failures from a single source can indicate suspicious activity.

## Lab Environment
- Kali Linux VM (attacker)
- Windows VM (host)
- VirtualBox with Host-only networking
- RDP enabled on Windows
- Windows Event Viewer → Security Logs

## Scenerio
A remote system attempts to authenticate to a Windows machine multiple times using incorrect credentials over RDP.

These repeated failures generate security events that can be analyzed to detect potential brute-force activity.

## Detection Logic
If a source IP generates **≥5
