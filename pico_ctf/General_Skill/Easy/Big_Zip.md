### Big Zip

Author: LT 'syreal' Jones
#easy #General-skills #picoGym 
#### Description

Unzip this archive and find the flag.

- [Download zip file](https://artifacts.picoctf.net/c/504/big-zip-files.zip)

##### Solution:
To find the word "pico" in files across multiple folders and subfolders, you can use `grep` with the `-r` (recursive) option. Here's the command:
`grep -r "pico" /path/to/search`
```css
 grep -r "pico"                
folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt:information on the record will last a billion years. Genes and brains and books encode picoCTF{gr3p_15_m4g1c_ef8790dc}
```

```css
The command `grep -lir pico` will do the following:

- `-l`: Only list the filenames of files that contain the word "pico".
- `-i`: Perform a case-insensitive search (so it will match "pico", "Pico", "PICO", etc.).
- `-r`: Recursively search through all files and directories.

So, `grep -lir pico /path/to/search` will give you a list of files that contain the word "pico" (ignoring case), recursively searching through the specified directory and subdirectories. Replace `/path/to/search` with the directory you want to search in (e.g., `.` for the current directory).
```

```css
┌──(kali㉿kali)-[~/Downloads/big-zip-files]
└─╼ $ grep -lir pico
folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt

┌──(kali㉿kali)-[~/Downloads/big-zip-files]
└─╼ $ cat folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt
information on the record will last a billion years. Genes and brains and books encode picoCTF{gr3p_15_m4g1c_ef8790dc}
```
