### Mod 26

Author: Pandu
#easy #forensics #picoCTF2021 
#### Description

Cryptography can be easy, do you know what ROT13 is? `cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_uJdSftmh}`

##### Solution:

```css
┌──(kali㉿kali)-[~/Downloads]
└─$ echo "cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_uJdSftmh}" | tr 'A-Za-z' 'N-ZA-Mn-za-m'
picoCTF{next_time_I'll_try_2_rounds_of_rot13_hWqFsgzu}
```

you can use cyberchef to decode ROT13

important notes #ROT13
```css
ROT13 is a simple letter substitution cipher that replaces a letter with the 13th letter after it in the alphabet. The name stands for "rotate by 13 places." This means that each letter is shifted by 13 positions in the alphabet:

- 'A' becomes 'N'
- 'B' becomes 'O'
- 'C' becomes 'P'
- ...
- 'N' becomes 'A'
- 'O' becomes 'B'
```