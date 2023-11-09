# hideme

exiftools says that there are extra metadata at the end of the file
```
ExifTool Version Number         : 12.65
File Name                       : flag (1).png
Directory                       : .
File Size                       : 43 kB
File Modification Date/Time     : 2023:11:09 10:41:08+08:00
File Access Date/Time           : 2023:11:09 10:41:10+08:00
File Inode Change Date/Time     : 2023:11:09 10:41:08+08:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 512
Image Height                    : 504
Bit Depth                       : 8
Color Type                      : RGB with Alpha
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Warning                         : [minor] Trailer data after PNG IEND chunk
Image Size                      : 512x504
Megapixels                      : 0.258
```

So lets do a hexdump
```
00009b30  00 00 00 49 45 4e 44 ae  42 60 82 50 4b 03 04 0a  |...IEND.B`.PK...|
00009b40  00 00 00 00 00 3b 10 70  56 00 00 00 00 00 00 00  |.....;.pV.......|
00009b50  00 00 00 00 00 07 00 1c  00 73 65 63 72 65 74 2f  |.........secret/|
00009b60  55 54 09 00 03 91 78 12  64 91 78 12 64 75 78 0b  |UT....x.d.x.dux.|
00009b70  00 01 04 00 00 00 00 04  00 00 00 00 50 4b 03 04  |............PK..|
00009b80  14 00 00 00 08 00 3b 10  70 56 9e b1 e9 3a 80 0b  |......;.pV...:..|
00009b90  00 00 17 0c 00 00 0f 00  1c 00 73 65 63 72 65 74  |..........secret|
00009ba0  2f 66 6c 61 67 2e 70 6e  67 55 54 09 00 03 91 78  |/flag.pngUT....x|
```

We see a `PK` at the end which shows that there is a zip file hidden inside this png. So lets extract that zip file.
```
dd if=flag.png of=test.zip skip=39739 bs=1
```

After that we just need to unzip the file and we will get a `secret/flag.png` directory. Opening this png file will give us
<img width="604" alt="image" src="https://github.com/sesiliafenina/CTFs/assets/44059409/ebd75499-8452-4d86-a6bb-7acfc387fb99">

picoCTF{Hiddinng_An_imag3_within_@n_ima9e_ad9f6587}
