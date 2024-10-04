### endianness

Author: Nana Ama Atombo-Sackey
#easy #General-skills #picoCTF2024 #browser_web_shell 
#### Description

Know of little and big endian? [Source](https://artifacts.picoctf.net/c_titan/80/flag.c)

Additional details will be available after launching your challenge instance.

`nc titan.picoctf.net 63908`


##### Solution :
convert string to hex using python
```python
>>> "fpktx".encode("utf-8").hex()
'66706b7478' #big Endian format
```

```python
"fpktx".encode("utf-8")[::-1].hex()
'78746b7066' # little endian
```

```python
 hex(ord("f"))
'0x66'
```

we have source code and after running output is 
```css
└─╼ $ ./a.out     
Welcome to the Endian CTF!
You need to find both the little endian and big endian representations of a word.
If you get both correct, you will receive the flag.
Word: rmtug
Enter the Little Endian representation: 6775746d72
Correct Little Endian representation!
Enter the Big Endian representation: 726d747567
Correct Big Endian representation!
Flag not found. Please run this on the server
```

```python
>>> "rmtug".encode("utf-8")[::-1].hex()
'6775746d72' # Little Endian
>>> "rmtug".encode("utf-8").hex()
'726d747567' # Big Endian
```

on server
```css
Welcome to the Endian CTF!
You need to find both the little endian and big endian representations of a word.
If you get both correct, you will receive the flag.
Word: qbdmf
Enter the Little Endian representation: 666d646271
Correct Little Endian representation!
Enter the Big Endian representation: 7162646d66
Correct Big Endian representation!
Congratulations! You found both endian representations correctly!
Your Flag is: picoCTF{3ndi4n_sw4p_su33ess_02999450}

```

```python
>>> "qbdmf".encode("utf-8")[::-1].hex()
'666d646271' # Little Endian
>>> "qbdmf".encode("utf-8").hex()
'7162646d66' # Big Endian
```