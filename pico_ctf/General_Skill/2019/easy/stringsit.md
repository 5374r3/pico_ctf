### strings it

Author: Sanjay C/Danny Tunitis
#easy #General-skills #picoCTF2019 
#### Description

Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/fae9ac5267cd6e44124e559b901df177/strings) without running it?

##### Solution :
```css
  
┌──(kali㉿kali)-[~/Downloads]
└─$ chmod +x strings       

┌──(kali㉿kali)-[~/Downloads]
└─$ ./strings 
Maybe try the 'strings' function? Take a look at the man page
    
┌──(kali㉿kali)-[~/Downloads]
└─$ strings strings | grep pico
picoCTF{5tRIng5_1T_7f766a23}


```