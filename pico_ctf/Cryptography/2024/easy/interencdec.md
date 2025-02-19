### interencdec

Author: NGIRIMANA Schadrack
#easy #cryptography #picoCTF2024 #base64 #browser_web_shell #caesar
#### Description

Can you get the real meaning from this file. Download the file [here](https://artifacts.picoctf.net/c_titan/2/enc_flag).

##### Solution:
the file contain `YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6YzRNalV3YUcxcWZRPT0nCg==`
which is base64
now using cyberchef decode from base64
you will get `b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzc4MjUwaG1qfQ=='`
this file is again in base64
now remove b and decode `d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzc4MjUwaG1qfQ==`
into from base64 you will get `wpjvJAM{jhlzhy_k3jy9wa3k_78250hmj}`
well this look like flag but it is not into correct format use __Caesar Cipher__
to decrypt the text use this [site](https://www.dcode.fr/caesar-cipher) for decryption you will get flag `picoCTF{caesar_d3cr9pt3d_78250afc}`
