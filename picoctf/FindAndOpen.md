# FindAndOpen

We received a locked file and a pcap file that might contain the password. So let's open the pcap file in wireshark. After some time looking through the packets, I saw this

<img width="1025" alt="Pasted Graphic 4" src="https://github.com/sesiliafenina/CTFs/assets/44059409/d48f9064-6cc0-4494-8ee2-1e312c56a77f">

This indicates that the flag might've been splitted.

The next packet after that, packet 48 contains the following:

<img width="1021" alt="Pasted Graphic 5" src="https://github.com/sesiliafenina/CTFs/assets/44059409/5c7797ca-2be5-4973-b2d2-2e1b94e887a1">

The `=` at the end tells me that this is likely to be Base64 Encoded and converting it to ASCII gives us:
```
picoCTF{R34DING_LOKd_
```

This is the first part of the flag!
After more checking, I came across this packet:

<img width="1022" alt="Pasted Graphic 6" src="https://github.com/sesiliafenina/CTFs/assets/44059409/ce9706e8-6baa-489c-8108-5865f2068eec">

So I tried to use this first half of the flag as the password to unlock the file, and then I used hexdump on the file to get the flag.
```
00000000  70 69 63 6f 43 54 46 7b  52 33 34 44 49 4e 47 5f  |picoCTF{R34DING_|
00000010  4c 4f 4b 64 5f 66 69 6c  35 36 5f 73 75 63 63 33  |LOKd_fil56_succ3|
00000020  73 73 5f 63 32 65 36 64  39 34 39 7d 0a           |ss_c2e6d949}.|
0000002d
```

picoCTF{R34DING_LOKd_fil56_succ3ss_c2e6d949}
