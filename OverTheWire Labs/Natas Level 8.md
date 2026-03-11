# OverTheWire-Natas-Level-8

<img width="1920" height="919" alt="01 natas8-secret-input" src="https://github.com/user-attachments/assets/e588f30e-d9a5-4015-aa4c-1c6c972a89bb" />

Right click "view source code"

<img width="1920" height="924" alt="02 natas8-source-code-analysis" src="https://github.com/user-attachments/assets/92ef48b2-421b-499a-aec4-4911a1d1d530" />

Decode the hexadecimal string "3d3d516343746d4d6d6c315669563362" using the details in the function encodeSecret($secret)

Convert hex to binary using hex2bin($encodedSecret),

reverse the string using strrev(),

and decode the final string using base64_decode() in the Linux command line

```bash
echo "3d3d516343746d4d6d6c315669563362" | xxd -r -p | rev | base64 -d
```

the result: oubWYf2kBq

Add the output into Input Secret and submit query

<img width="1920" height="921" alt="03 natas8-secret-submission" src="https://github.com/user-attachments/assets/311417e4-ea3f-4b29-b577-d25738e1ab31" />


Password for Natas 9 is shown

<img width="1920" height="924" alt="04 natas8-access-granted" src="https://github.com/user-attachments/assets/e343ca8e-5392-43e9-82a6-f51cc6ea3ec4" />






