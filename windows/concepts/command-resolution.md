## Overview

This note covers how Windows resolves commands using PATH. 
When you run a command, the OS determines what executable to run. 
If you don't give it a full path, Windows walks through the directories listed in PATH until it finds a matching executable. 
These are known as unqualified commands, where no full path is provided and PATH is used to locate the executable.
Essentially, PATH defines where the system searches for executables.

This creates a distinction between qualified commands (explicit paths) and unqualified commands, which depend entirely on PATH.

## Tools Used

- CMD
- Regedit
- NotebookLM (for the diagram)

## Environment

- HackTheBox Windows Environment

## What I Learned

- When a command is entered without a full path, such as backup.exe, the operating system does not have an explicit path to the executable.
Instead, it searches through the directories listed in PATH to find it.
Windows searches this list in order and executes the first match it finds.
- PATH exists as a string in the registry, but at runtime it becomes a search mechanism used by Windows to locate and execute commands.
- Windows is designed to support user-level customization through PATH, allowing user-defined directories to take precedence in command resolution.
This means user-defined directories can take precedence in command resolution, allowing user-installed tools to override system defaults.
This flexibility is useful for legitimate customization, such as running one's own Python executable instead of the one installed by the System, but it also introduces risk when PATH order can be influenced. 

- When a full path is provided, such as C:\Windows\System32\backup.exe, PATH is not used.
The operating system goes directly to that location and executes the file.
This means unqualified commands rely on PATH, while qualified commands bypass PATH.
Because of this, the order of directories in PATH determines which executable is run when multiple versions exist.

- Windows uses a "first match wins" rule when scanning PATH — whichever matching executable it finds first is the one it runs, without further validation. 
It doesn't stop to verify whether that file is actually the intended program. 

## Example

PATH is stored at both the user and system level in the Windows Registry.
These values are combined at runtime, forming the final PATH order that Windows uses when resolving commands.
That combined result is what determines the actual search order whenever a command is resolved.

<img width="900" height="900" alt="image" src="https://github.com/user-attachments/assets/812e70d2-8e99-46fa-acba-35678f812ece" />


## How Unqualified Commands are Introduced

Unqualified commands often exist due to common system and development practices, not necessarily malicious intent.
- Developer convenience
  - Developers may use commands like backup.exe without a full path because it is faster and works in their environment.
- Misconfiguration
  - Scheduled tasks or services may be configured without full paths, unintentionally relying on PATH.
- Installer behavior
  - Some software registers executables and relies on PATH instead of using explicit file paths.

To visualize how this process works in practice:

<img width="900" height="900" alt="image" src="https://github.com/user-attachments/assets/d199bd60-56cd-47ed-9161-217cd432d978" />


## Security Implication
- Because PATH is both configurable data and part of command execution logic, modifying it can directly influence which executables are run. 
- An attacker can place a malicious executable in a directory that appears earlier in PATH.
- Because windows executes the first match without validating its origin, **control over PATH can become control over execution.**
This enables PATH hijacking: if an attacker places a malicious executable in a directory that appears earlier in PATH, it can be executed instead of the legitimate binary.
nm
## Key Takeaway
Windows trusts PATH order when resolving commands, making search order a critical factor in both system behavior and potential exploitation.
