### Wave a flag

Author: syreal
#easy #General-skills #picoCTF2021 
#### Description

Can you invoke help flags for a tool or binary? [This program](https://mercury.picoctf.net/static/fc1d77192c544314efece5dd309092e3/warm) has extraordinarily helpful information...

##### Solution:
```css
┌──(kali㉿kali)-[~/Downloads]
└─╼ $ file warm   
warm: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=7b3da2efd83a2b9154697b6c7f6474042e1fd033, with debug_info, not stripped

┌──(kali㉿kali)-[~/Downloads]
└─╼ $ chmod +x warm           

┌──(kali㉿kali)-[~/Downloads]
└─╼ $ ./warm                 
Hello user! Pass me a -h to learn what I can do!
    
┌──(kali㉿kali)-[~/Downloads]
└─╼ $ ./warm -h
Oh, help? I actually don't do much, but I do have this flag here: picoCTF{b1scu1ts_4nd_gr4vy_6635aa47}
```