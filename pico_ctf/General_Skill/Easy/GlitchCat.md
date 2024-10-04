
### Glitch Cat

Author: LT 'syreal' Jones
#easy #General-skills #picomini2022   #nc #shell #python 
#### Description

Our flag printing service has started glitching! `$ nc saturn.picoctf.net 58107`

##### Solution:
```css
nc saturn.picoctf.net 58107
'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'


>>> print(chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35))
bda68f75
```

final output is `picoCTF{gl17ch_m3_n07_bda68f75}`