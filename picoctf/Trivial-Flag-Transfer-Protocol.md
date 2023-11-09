# Trivial Flag Transfer Protocol

Just from the name, we can get a hint - TFTP

Just by looking at the pcap we can see there are files being transferred using TFTP. Using wireshark we can extract the files that are being transferred:

<img width="744" alt="Pasted Graphic 10" src="https://github.com/sesiliafenina/CTFs/assets/44059409/5a5f4699-fcb4-40a0-97c0-eb5b11f8b396">

Opening the `instruction.txt` i found:
```
GSGCQBRFAGRAPELCGBHEGENSSVPFBJRZHFGQVFTHVFRBHESYNTGENAFSRE.SVTHERBHGNJNLGBUVQRGURSYNTNAQVJVYYPURPXONPXSBEGURCYNA
which translates to (ROT13)
TFTPDOESNTENCRYPTOURTRAFFICSOWEMUSTDISGUISEOURFLAGTRANSFER.FIGUREOUTAWAYTOHIDETHEFLAGANDIWILLCHECKBACKFORTHEPLAN
```

And the plan:
```
VHFRQGURCEBTENZNAQUVQVGJVGU-QHRQVYVTRAPR.PURPXBHGGURCUBGBF
IUSEDTHEPROGRAMANDHIDITWITH-DUEDILIGENCE.CHECKOUTTHEPHOTOS
```

I don't have steghide installed so let's use an online tool for this: https://futureboy.us/stegano/decinput.html

When I first tried to upload the file, I got this error:
```
Error.  This file may not contain steganographic data, or you may have specified an incorrect password.
```

Which implies that the file might need a password to unlock. After some time looking, the `DUEDILIGENCE` in the plan seems a little bit off so let's try to use this as the password.

It gives me the flag:
picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}

