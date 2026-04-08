## Overview

When a command is executed without a full path, Windows must determine which executable to run.
Rather than searching the entire system, Windows follows a defined search order. 

This means execution depends not only on what files exist, but on where Windows is configured to look. 

## Tools Used

- CMD

## Environment

-Windows Environment

# Viewing %PATH%

The %PATH% environment variable contains a list of directories that Windows searches to locate executables when a command is run without a full path.

You can inspect the current %PATH% using:

```echo %PATH%```

Example output:

```C:\Windows\System32;C:\Windows;C:\Windows\System32\wbem;C:\Windows\System32\WindowsPowerShell\v1.0\;C:\Windows\System32\OpenSSH\;c:\Program files\Git\cmd;C:\Program Files\PowerShell\7\;C:\Users\htb-student\AppData\Local\Microsoft\WindowsApps;```

Each directory is separated by a semicolon (;) and is searched in order from left to right.

# Command Resolution Order

When a command is entered without a full path (e.g., ipconfig, backup, sample), Windows searches in the following order: 
1. Current working Directory
2. C:\Windows\System32
3. C:\Windows
4. Directories listed in %PATH% (in order)

Windows stops searching as soon as it finds the first matching executable. 

This means that if a malicious executable exists earlier in the search path--such as in the current working directory--it will be executed instead of the legitimate one located later (e.g., in System32).

# Qualified vs Unqualified Commands

Unqualified Command:

```ipconfig```

Windows searches according to the resolution order.

Unqualified commands rely on this search process, while qualified commands bypass it entirely.

# How %PATH% Influences Execution

%PATH% affects command resolution only after the current directory and system directories have been checked. 

This means:

- %PATH% can influence which executable is run
- But it does not override system directories or the current working directory

If multiple directories in %PATH% contain the same executable name, the first match (from left to right) is used.

# Modifying %PATH% (Session Example)

%PATH% can be modified within a session:

```set PATH=C:\LabPath;%PATH%```

This prepends a user-controlled directory to the beginning of %PATH%, causing Windows to search it before other %PATH% entries. 

# Key Insight

Windows uses a "first match wins" rule when resolving commands.

Because of this:

- Execution depends on search order
- The same command can produce different results depending on context
- Changing directories or %PATH% can change which executable runs

# Security Implication

Command resolution is based on where Windows looks, not just what exists.

This means:
- A different executable may run than expected
- Behavior can change depending on environment configuration
- Systems that rely on unqualified commands may execute unintended binaries

# Final Takeaway

Windows does not search everywhere, it follows a defined order.
Understanding that order is key to understanding how commands are executed. 
