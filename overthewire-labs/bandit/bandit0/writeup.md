# overthewire-labs-bandit0  

## Overview
Practice Unix/Linux basics. The password is found in a file called readme in the home directory
## Tools Used
- Linux commands: ls, cd, cat, file, du, find
- VirtualBox
- Kali Linux

## Steps

### 1. Log into the machine
```
ssh bandit0@bandit.labs.overthewire.org -p 2220
```
```
password: bandit0
```

<img width="800" height="800" alt="ssh_bandit0" src="https://github.com/user-attachments/assets/0120dafb-243c-42e2-81ab-f88832363fef" />


### 2. Find the password in the file called readme in the homedirectory by executing the command ls to confirm the file is in the current working directory, and the following command:

```
cat readme
```

<img width="800" height="800" alt="read_file_home_directory_bandit_0" src="https://github.com/user-attachments/assets/d0dd02ab-aca5-4681-893f-7fe96af87281" />


to read the file. 

## Takeaways

Being able to navigate the linux terminal is fundamental to cybersecurity. Knowing linux commands like cat and ls can assist the soc analyst in completing many security tasks such as reading files and listing contents in a directory.

