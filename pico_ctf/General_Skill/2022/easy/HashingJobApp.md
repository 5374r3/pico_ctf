### HashingJobApp

Author: LT 'syreal' Jones
#easy #General-skills #picomini2022  #hashing #nc #shell #python 
#### Description

If you want to hash with the best, beat this test! `nc saturn.picoctf.net 63868`

##### Solution:
```css
 nc saturn.picoctf.net 63868
Please md5 hash the text between quotes, excluding the quotes: 'Count Dracula'
Answer: 
aff1b17cdcbc3b40afd42d5fe00297da
aff1b17cdcbc3b40afd42d5fe00297da
Correct.
Please md5 hash the text between quotes, excluding the quotes: 'UV rays'
Answer: 
fa572056bc7677e6104801f2773fcc76
fa572056bc7677e6104801f2773fcc76
Correct.
Please md5 hash the text between quotes, excluding the quotes: 'the sunrise'
Answer: 
3652f115c238da1f79187d39b64e3fa2
3652f115c238da1f79187d39b64e3fa2
Correct.
picoCTF{4ppl1c4710n_r3c31v3d_674c1de2}

```


```c++
The `-n` option in the `echo` command tells it **not** to append a newline (`\n`) at the end of the output. By default, `echo` adds a newline character after printing text, which would affect the result when piping the output to a command like `md5sum`
echo -n Welcome | md5sum
83218ac34c1834c26781fe4bde918ee4  -

```

```css
┌──(kali㉿kali)-[~]
└─╼ $ echo -n Count Dracula | md5sum
aff1b17cdcbc3b40afd42d5fe00297da  -

┌──(kali㉿kali)-[~]
└─╼ $ echo -n UV rays | md5sum
fa572056bc7677e6104801f2773fcc76  -

┌──(kali㉿kali)-[~]
└─╼ $ echo -n the sunrise | md5sum
3652f115c238da1f79187d39b64e3fa2  -
```

another tool we can use is cyberchef  online for md5
