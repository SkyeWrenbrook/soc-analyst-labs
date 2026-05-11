# Linux Streams and Redirection

## Overview

This lab explores how Linux programs communicate using standard streams. The purpose of this project was to better understand how command-line tools handle input, normal output, errors, redirection, and pipes.

While working through Linux fundamentals, I noticed that many tools are designed to work together by passing data through streams. Understanding this helped me better understand how administrators and security analysts interact with logs, scripts, and terminal output.

---

# Concepts Covered

- stdin (standard input)
- stdout (standard output)
- stderr (standard error)
- file descriptors
- output redirection
- error redirection
- pipes

---

# Standard Streams

| Stream | File Descriptor | Purpose |
|---|---|---|
| stdin | 0 | Input sent into a program |
| stdout | 1 | Normal program output |
| stderr | 2 | Error and diagnostic output |

---

# Lab 1 — Separating stdout and stderr

## Command

```bash
ls fakefile > out.txt 2> err.txt
