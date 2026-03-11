# PicoCTF — Ph4nt0m-1ntrud3r (Phantom Intruder) Write-Up

## Overview
A network traffic capture (PCAP) was provided. The goal was to analyze it in Wireshark, find encoded data in the packet payloads, and recover the flag.

## Tools Used
- Wireshark
- CyberChef 
- picoCTF PCAP file

---

## Steps

### 1. Load & Review
Opened the PCAP in Wireshark and reviewed overall traffic flow and protocol distribution.

> <img width="700" height="700" alt="payloadview" src="https://github.com/user-attachments/assets/8df27e14-d967-4da7-a574-3a5b4a3198cb" />


### 2. Filter for Encoded Data
Used display filters to surface packets with Base64 payloads. Since Base64 strings often end in `=` or `==`, this filter was a quick win:

```wireshark
frame contains "=="
```
Also saved handshake filter tcp.flags.syn == 1 || tcp.flags.ack == 1 for later reference as handshake-related packets

> <img width="700" height="700" ![Filtered traffic showing Base64 indicators](https://github.com/user-attachments/assets/9d417ae6-bef7-4df6-a09e-1a9fd062240b)

### 3. Inspect Payloads
Located Base64-like strings across multiple packets using Wireshark's search. Verified their order and continuity.

> <img width="1269" height="1045" alt="payload" src="https://github.com/user-attachments/assets/4a91557a-a198-4c11-bbb1-18d4ffdfb74a" />

### 4. Decode
Extracted and reassembled the Base64 fragments in sequence.

<img width="650" height="516" alt="final" src="https://github.com/user-attachments/assets/36fd9e2d-67e8-41bc-80d4-d99849f4344b" />

Then I decoded them in CyberChef using **From Base64**.



---

## Recovered Flag

<img width="711" height="826" alt="challenge-flag-recovered png" src="https://github.com/user-attachments/assets/a2a5b171-2acf-4860-903d-b02c202ef503" />

<img width="962" height="929" alt="cyberchef-base64-decode-flag png" src="https://github.com/user-attachments/assets/6174edb5-f387-4631-af43-41bb96f6b01a" />


---

## Takeaways
Practiced traffic filtering, payload inspection, and Base64 extraction in Wireshark. Also noted repeated SYN retransmissions consistent with SYN flood-like traffic — not needed to solve the challenge, but a useful observation for understanding abnormal TCP patterns.


