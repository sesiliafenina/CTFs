# MSB

The description says that the image passes the LSB analysis. For those who doesn't know what the LSB steganography technique is, you can read this [link](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwjslK_W-LWCAxVb3TgGHUQ6BoEQFnoECCQQAQ&url=https%3A%2F%2Fmedium.com%2F%40renantkn%2Flsb-steganography-hiding-a-message-in-the-pixels-of-an-image-4722a8567046&usg=AOvVaw2fe5curOZveD5DdY8bi1O4&opi=89978449).

Basically it is the technique of hiding information on the LSB of the file as the changes made to the LSB will not be visually visible.

When we download the image we see this:

<img width="501" alt="image" src="https://github.com/sesiliafenina/CTFs/assets/44059409/f5fc9dec-73f6-4615-931d-e801a4905a7c">

This image looks quite distorted and does not look like the normal LSB image. From here we can deduce that the message must've been stored in another bit and the title hints that it is being stored in the MSB.

I don't have a tool to extract bits from an image but let's find an online tool. After some searching I found this tool: https://stegonline.georgeom.net/extract

<img width="776" alt="Pasted Graphic 7" src="https://github.com/sesiliafenina/CTFs/assets/44059409/c3fe0374-af28-4f0e-b7b8-74b548a6b383">

Get the data on the most significant bit and download. It seems like a long text so let's use grep to quickly find the flag.
```
cat Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisadaflag.dat | grep pico
picoCTF{15_y0ur_que57_qu1x071c_0r_h3r01c_24d55bee}
```

