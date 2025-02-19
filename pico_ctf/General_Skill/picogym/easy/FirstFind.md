### First Find

Author: LT 'syreal' Jones
#easy #General-skills #picoGym 
#### Description

Unzip this archive and find the file named 'uber-secret.txt'

- [Download zip file](https://artifacts.picoctf.net/c/502/files.zip)

##### Solution:

```css
The command `grep -ri pico` will do the following:

- `-i`: Perform a case-insensitive search (so it will match "pico", "Pico", "PICO", etc.).
- `-r`: Recursively search through all files and directories.
```

```css
 step 1 
 unzip files.zip 
 step 2
 
┌──(kali㉿kali)-[~/Downloads/files]
└─╼ $ grep -ri "pico"                                                                             
adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt:picoCTF{f1nd_15_f457_ab443fd1}
14789.txt.utf-8:brassa un picotin d'orge_. Comme depuis une demi-heure environ c'était

```