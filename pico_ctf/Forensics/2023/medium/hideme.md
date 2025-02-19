### hideme

#Medium #forensics #picoCT2023 #steganography 
Author: Geoffrey Njogu

#### Description

Every file gets a flag. The SOC analyst saw one image been sent back and forth between two people. They decided to investigate and found out that there was more than what meets the eye [here](https://artifacts.picoctf.net/c/257/flag.png)

##### Solution:
```css
┌──(kali㉿kali)-[~/Downloads/pico_ctf_lab]
└─$ binwalk -e flag.png 

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
41            0x29            Zlib compressed data, compressed
39739         0x9B3B          Zip archive data, at least v1.0 to extract, name: secret/
39804         0x9B7C          Zip archive data, at least v2.0 to extract, compressed size: 2959, uncompressed size: 3108, name: secret/flag.png
```

just go to extract folder you will see another png file which contain flag

![](hideme/hideme_flag.png)

flag is `picoCTF{Hiddinng_An_imag3_within_@n_ima9e_dc2ab58f}`