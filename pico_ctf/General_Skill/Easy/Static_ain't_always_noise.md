### Static ain't always noise

Author: syreal
#easy #General-skills #picoCTF2021 
#### Description

Can you look at the data in this binary: [static](https://mercury.picoctf.net/static/e9dd71b5d11023873b8abe99cdb45551/static)? This [BASH script](https://mercury.picoctf.net/static/e9dd71b5d11023873b8abe99cdb45551/ltdis.sh) might help!

##### Solution:
```css
ls
ltdis.sh static

┌──(kali㉿kali)-[~/Downloads]
└─$ bash ltdis.sh 
Attempting disassembly of  ...
objdump: 'a.out': No such file
objdump: section '.text' mentioned in a -j option, but not found in any input file
Disassembly failed!
Usage: ltdis.sh <program-file>
Bye!

┌──(kali㉿kali)-[~/Downloads]
└─$ ./static     
zsh: permission denied: ./static

┌──(kali㉿kali)-[~/Downloads]
└─$ chmod +x static 

┌──(kali㉿kali)-[~/Downloads]
└─$ ./static 
Oh hai! Wait what? A flag? Yes, it's around here somewhere!

┌──(kali㉿kali)-[~/Downloads]
└─$ file static 
static: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=7eb9ee1907cc878f15f9949988893b1f0ab1ebdf, not stripped

┌──(kali㉿kali)-[~/Downloads]
└─$ bash ltdis.sh static 
Attempting disassembly of static ...
Disassembly successful! Available at: static.ltdis.x86_64.txt
Ripping strings from binary with file offsets...
Any strings found in static have been written to static.ltdis.strings.txt with file offset

┌──(kali㉿kali)-[~/Downloads]
└─$ cat static.ltdis.strings.txt | grep pico
   1020 picoCTF{d15a5m_t34s3r_ae0b3ef2}
```

search  flag in *static.ltdis.strings.txt* `picoCTF{d15a5m_t34s3r_ae0b3ef2}`