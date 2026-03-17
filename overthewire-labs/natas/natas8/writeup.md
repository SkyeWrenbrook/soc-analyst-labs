# overthewire-labs-natas8

## Overview

This challenge involves analyzing source code to identify how a secret value is encoded and then reversing the encoding process to retrieve the correct input.

By inspecting the application logic, the goal is to decode a given hexadecimal string using multiple transformations.

## Tools Used

- Linux command line
- echo
- xxd (hex decoding)
- rev (string reversal)
- base64 (decoding)

## Steps

### 1. Inspect Source Code

The first step is to analyze the application by viewing the page source. This can be done by right-clicking the page and selecting "View Page Source", or by using developer tools.


<img width="800" height="800" alt="01 natas8-secret-input" src="https://github.com/user-attachments/assets/e588f30e-d9a5-4015-aa4c-1c6c972a89bb" />


Viewing the page source shows an encoded string and a function that encodes it.


<img width="1000" height="1000" alt="02 natas8-source-code-analysis" src="https://github.com/user-attachments/assets/92ef48b2-421b-499a-aec4-4911a1d1d530" />

The function does the following:

1. Convert string to hexadecimal
2. Reverse the string
3. Encode using Base64

To retrieve the original secret, these steps must be reversed.


### 2. Identify the Encoded String

The following hexadecimal string is provided:

```
3d3d516343746d4d6d6c315669563362
```
### 3. Reverse the Encoding Process

Step 1: Convert hex to ASCII

```
echo "3d3d516343746d4d6d6c315669563362" | xxd -r -p
```

Step 2: Reverse the string

```
echo "<output>" | rev
```

Step 3: Decode Base64

```
echo "<reversed_output>" | base64 -d
```

### 4. Result

The decoded output is:

```
oubWYf2kBq
```

The value is submitted as the secret to complete the challenge.

<img width="800" height="800" alt="03 natas8-secret-submission" src="https://github.com/user-attachments/assets/311417e4-ea3f-4b29-b577-d25738e1ab31" />


The password for Natas 9 is shown

<img width="800" height="800" alt="04 natas8-access-granted" src="https://github.com/user-attachments/assets/e343ca8e-5392-43e9-82a6-f51cc6ea3ec4" />

## Takeaways

- Encoding problems can be layered so they must be reversed step-by-step
- Reading source code carefully can help with understanding application logic
- Common transformations in challenges include:
  - Hex encoding
  - String reversal
  - Base64 encoding
- Being able to recognize encoding patterns is an essential skill in web security and CTF challenges






