### CanYouSee

Author: Mubarak Mikail
#easy #forensics #picoCTF2024 #browser_web_shell 
#### Description

How about some hide and seek? Download this file [here](https://artifacts.picoctf.net/c_titan/129/unknown.zip).

##### Solution:
use tools exiftool to get information of image
```css
┌──(kali㉿kali)-[~/Downloads]
└─╼ $ exiftool ukn_reality.jpg 
ExifTool Version Number         : 12.76
File Name                       : ukn_reality.jpg
Directory                       : .
File Size                       : 2.3 MB
File Modification Date/Time     : 2024:03:11 20:05:53-04:00
File Access Date/Time           : 2024:09:12 11:18:24-04:00
File Inode Change Date/Time     : 2024:09:12 11:18:24-04:00
File Permissions                : -rw-r--r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
Resolution Unit                 : inches
X Resolution                    : 72
Y Resolution                    : 72
XMP Toolkit                     : Image::ExifTool 11.88
Attribution URL                 : cGljb0NURntNRTc0RDQ3QV9ISUREM05fYjMyMDQwYjh9Cg==
Image Width                     : 4308
Image Height                    : 2875
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 4308x2875
Megapixels                      : 12.4  
```

```css
Attribution URL                 : cGljb0NURntNRTc0RDQ3QV9ISUREM05fYjMyMDQwYjh9Cg==
```
use cyberchef to decode from base64 text `cGljb0NURntNRTc0RDQ3QV9ISUREM05fYjMyMDQwYjh9Cg==`
`picoCTF{ME74D47A_HIDD3N_b32040b8}`

or using terminal
```css
┌──(kali㉿kali)-[~/Downloads]
└─╼ $ echo cGljb0NURntNRTc0RDQ3QV9ISUREM05fYjMyMDQwYjh9Cg== | base64 --decode
picoCTF{ME74D47A_HIDD3N_b32040b8}

```