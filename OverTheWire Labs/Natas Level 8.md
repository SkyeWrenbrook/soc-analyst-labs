# OverTheWire-Natas-Level-8

<img width="1920" height="1080" alt="Screenshot_2026-03-06_17_20_31" src="https://github.com/user-attachments/assets/16a948ab-ed61-4c35-a268-0606012fb93d" />

Right click "view source code"

<img width="1920" height="1080" alt="Screenshot_2026-03-06_17_21_45" src="https://github.com/user-attachments/assets/72c50283-7b2d-495b-b062-455fed848d3d" />

Decode the hexadecimal string "3d3d516343746d4d6d6c315669563362" using the details in the function encodeSecret($secret)

Convert hex to binary using hex2bin($encodedSecret),

reverse the string using strrev(),

and decode the final string using base64_decode() in the Linux command line

'''bash
echo "3d3d516343746d4d6d6c315669563362" | xxd -r -p | rev | base64 -d
'''

the result: oubWYf2kBq

Add the output into Input Secret and submit query

<img width="1920" height="1080" alt="Screenshot_2026-03-06_17_29_51" src="https://github.com/user-attachments/assets/8f9c76d5-0b00-42aa-98c2-8f5f1eb673fa" />

Password for Natas 9 is shown

<img width="1920" height="1080" alt="Screenshot_2026-03-06_17_30_37" src="https://github.com/user-attachments/assets/95eeffc6-3366-46bb-8cae-236bfcc4f155" />





