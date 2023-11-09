# Wireshark doo dooo do doo...

We received a pcap file so let's open it using Wireshark. I followed the TCP stream one-by-one and stream 5 looks like a cipher.

<img width="1028" alt="Pasted Graphic 8" src="https://github.com/sesiliafenina/CTFs/assets/44059409/9baeebea-933e-4813-ba0a-46d6f744fb4f">


Since we can clearly see the `{}`, this looks like a Caesar cipher. We can use cyberchef to decrypt this and get the flag

<img width="886" alt="Pasted Graphic 9" src="https://github.com/sesiliafenina/CTFs/assets/44059409/818aa3cc-f6ae-4371-898b-5d990509cd6a">

```
picoCTF{p33kab00_1_s33_u_deadbeef}
```
