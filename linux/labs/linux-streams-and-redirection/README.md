# Linux Streams and Redirection

## Overview

This project explores how Linux programs use stdin, stdout, stderr, redirection, and pipes. It was created as part of my Linux and SOC analyst learning journey.

---

# Concepts Covered

- stdin (0)
- stdout (1)
- stderr (2)
- redirection
- pipes

---

# Tools Used
- Ubuntu Linux
- Bash
- ls
- cat
- grep


# Lab 1 — Separating stdout and stderr

## Command

```bash
ls fakefile > out.txt 2> err.txt
```
![Lab 1 Screenshot](screenshots/lab1-stream-separation.png)

Result:
- stdout was redirected to out.txt
- stderr was redirected to err.txt
- out.txt remained empty because only an error was generated

# Lab 2 - Redirecting both streams

## Command

```bash
ls fakefile > both.txt 2>&1
```

![Lab 2 Screenshot](screenshots/lab2-both-streams.png)

Result:
Both stdout and stderr were redirected into the same file.

# Lab 3 - Writing input to a file

## Command

```bash
cat > notes.txt
```
![Lab 3 Screenshot](screenshots/lab3-stdin.png)

Result:
Keyboard input was sent into notes.txt through stdin.

# Lab 4 - Using Pipes

## Command

```bash
ls /etc | grep ssh
```
![Lab 4 Screenshot](screenshots/lab4-pipes.png)

Result:
The stdout of `ls` became the stdin of grep.

# Security Relevance

Understanding Linux streams is useful for:
- log analysis
- shell scripting
- troubleshooting
- command-line automation

# Key Takeaway
This lab helped reinforce how Linux programs communicate through streams and how shell redirection can be used to control and process output efficiently. 
