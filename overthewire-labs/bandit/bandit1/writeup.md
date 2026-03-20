overthewire-labs-bandit1  

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
````
### 2. Find the password in the file called readme in the homedirectory by executing the command ls to confirm the file is in the current working directory, and the following command:

```
cat readme
```
to read the file. 

## Takeaways

Being able to navigate the linux terminal is fundamental to cybersecurity. Knowing linux commands like cat and ls can assist the soc analyst in completing many security tasks such as reading files. 

