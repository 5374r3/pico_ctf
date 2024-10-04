### Blame Game

Author: Jeffery John
#easy #General-skills #picoCTF2024 #browser_web_shell #git
#### Description

Someone's commits seems to be preventing the program from working. Who is it? You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/158/challenge.zip)
##### Solution:
```css
┌──(kali㉿kali)-[~/Downloads/drop-in]± master
└─╼ $ git log message.py 
commit 8c83358c32daee3f8b597d2b853c1d1966b23f0a
Author: picoCTF{@sk_th3_1nt3rn_2c6bf174} <ops@picoctf.com>
Date:   Tue Mar 12 00:07:11 2024 +0000

    optimize file size of prod code

commit caa945839a2fc0fb52584b559b4e89ac7c46bf54
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:11 2024 +0000

    create top secret project
```
flag is `picoCTF{@sk_th3_1nt3rn_2c6bf174}`
Note using git hidden folder you can find the flag in log file