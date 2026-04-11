# Overview

This lab explores how Windows resolves commands when they are executed without a fully qualified path. The goal is to understand search order, %PATH%, %PATHEXT%, and why command resolution behavior matters from a security perspective.

# Objective

- Identify the order Windows uses to resolve unqualified commands
- Understand the role of %PATH% and %PATHEXT%
- Compare qualified and unqualified commands
- Explain how search order can create security risk


# Tools and Environment

- Windows Command Prompt (CMD)
- Test machine: Windows VM
- Built-in commands: echo, where, set, cd

# Key Concepts

- Qualified command: full path provided
- Unqualified command: command entered without full path
- %PATH%: directories Windows searches
- %PATHEXT%: executable extension priority list

# Steps Taken

1. View %PATH%
   - Command: ```echo %PATH%```
   - Output: ```C:\Windows\System32;C:\Windows;C:\Windows\System32\wbem;C:\Windows\System32\WindowsPowerShell\v1.0\;C:\Windows\System32\OpenSSH\;c:\Program files\Git\cmd;C:\Program Files\PowerShell\7\;C:\Users\htb-student\AppData\Local\Microsoft\WindowsApps;```
   - Interpretation: The %PATH% environment variable contains a list of directories that Windows searches to locate executables when a command is run without a full path. Each directory is separated by a semicolon (;) and is searched in order from left to right.

2. Observe command resolution order

    When a command is entered without a full path (e.g., ipconfig, backup, sample), Windows follows this order:
    - Current working directory
    - System directories
    - Directories listed in %PATH% (in order)

   Windows stops searching as soon as it finds the first matching executable.
   This search is performed directory-by-directory, and within each directory, file extensions are evaluated in priority order.

4. Compare qualified vs unqualified commands

   Unqualified command:  ```ipconfig```
   
   Qualified command: ```C:\Windows\System32\ipconfig.exe```

   Unqualified commands rely on resolution order, while qualified commands bypass it entirely.

6. View %PATHEXT%

   When a command is entered without an extension (e.g., sample), Windows determines which file type to execute using %PATHEXT%.
   
      - Command: ```echo %PATHEXT%```
   
      - Output: ```.COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC```

      - Interpretation: When a command is entered without an extension (e.g., sample), Windows determines which file type to execute using %PATHEXT%.

8. Test extension resolution
   If a directory contains three files with different extensions:

        ```
        sample.exe
        sample.bat
        sample.cmd
        ```

   Running: ```sample``` will execute: ```sample.exe```because .EXE has higher priority.

7. Modify %PATH% in session
   
       ``` set PATH=C:\LabPath;%PATH%```
   
    This prepends a user-controlled directory to the beginning of %PATH%, causing Windows to search it before other %PATH% entries.

    So now %PATH% should look something like this:

    ```C:\LabPath;C:\Windows\system32;C:\Windows;C:\Windows\System32\wbem;C:\Windows\System32\WindowsPowerShell\v1.0\;C:\Windows\System32\OpenSSH\;c:\Program files\Git\cmd;C:\Program Files\PowerShell\7\;C:\Users\htb-student\AppData\Local\Microsoft\WindowsApps;```

# Observations

- %PATH% affects command resolution only after the current directory and system directories have been checked.
- %PATHEXT% affects which file executes inside a directory.
- The first matching executable wins.

# Security Implications

Unqualified commands often exist due to common system and development practices, not necessarily malicious intent.
- Developer convenience
  - Developers may use commands like backup.exe without a full path because it is faster and works in their environment.
- Misconfiguration
  - Scheduled tasks or services may be configured without full paths, unintentionally relying on PATH.
- Installer behavior
  - Some software registers executables and relies on PATH instead of using explicit file paths.

- A malicious binary placed earlier in the search order may execute first.
- Using fully qualified paths reduces the risk of search order abuse.

# Key Findings

- Command resolution depends on both directory order and extension priority.
- %PATH% influences execution only after earlier checks.
- %PATHEXT% determines which file type runs first within a directory.
- Fully qualified paths are more predictable and secure.

