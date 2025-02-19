### rotation

#Medium #Cryptography #picoCTF2023

Author: Loic Shema

#### Description

You will find the flag after decrypting this fileDownload the encrypted flag [here](https://artifacts.picoctf.net/c/391/encrypted.txt).

##### Solution:
1st method

using cyber chef choose `ROT13`
now here is a catch we have text `xqkwKBN{z0bib1wv_l3kzgxb3l_7l140864}`
we have to convert this text into `picoCTF{}`
`B` to `T` it take 18 shift so modify `ROT13` to `ROT18`
you will get flag `picoCTF{r0tat1on_d3crypt3d_7d140864}`

2nd method
use cyber chef again this time choose `ROT13 Brute Force`
