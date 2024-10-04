### binhexa

Author: Nana Ama Atombo-Sackey
#easy #General-skills #picoCTF2024 #browser_web_shell 
#### Description

How well can you perfom basic binary operations?

Additional details will be available after launching your challenge instance.
Start searching for the flag here `nc titan.picoctf.net 52163`

##### Solution:
some tips to solve this challenges using python

```css
$ python3
>>> print(0b11100000 | 0b10010010)
226
>>> print(0b11100000 & 0b10010010)
144
>>> print(0b11100000 * 0b10010010)
513920
>>> print(0b11100000 + 0b10010010)
418
>>> print(0b11100000 << 2) # left shift by 2 bit
896
>>> print(0b11100000 >> 2) # right shift by 2 bit
56
>>> print(bin(0b11100000 >> 1)[2:]) # right shift by 1 bit
110000
>>> print(bin(0b11100000 << 1)[2:]) # left shift by 1 bit
111000000

>>> bin(513920)[2:]
'1111101011110000000'
>>> bin(513920)
'0b1111101011110000000'

>>>print(bin(224 << 1)[2:]) # Outputs: 111000000
>>>print(bin(0b11100000 * 0b10010010)[2:])
111111111000000

print(int('11111001100100000000', 2))  # Outputs: 1022080

```

```css
┌──(kali㉿kali)-[~]
└─╼ $ python3      
Python 3.11.9 (main, Apr 10 2024, 13:16:36) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> print(bin(0b10101110 << 1)[2:])
101011100
>>> print(bin(0b10101110 * 0b00011000))
0b1000001010000
>>> print(bin(0b10101110 & 0b00011000))
0b1000
>>> print(0b10101110 & 0b00011000)
8
>>> print(bin(0b10101110 + 0b00011000))
0b11000110
>>> print(bin(0b10101110 | 0b00011000))
0b10111110
>>> print(bin(0b00011000 >> 1)[2:])
1100
>>> hex(int('1100', 2))
'0xc'
>>> 
```

```css
┌──(kali㉿kali)-[~]
└─╼ $ nc titan.picoctf.net 49634

Welcome to the Binary Challenge!"
Your task is to perform the unique operations in the given order and find the final result in hexadecimal that yields the flag.

Binary Number 1: 10101110
Binary Number 2: 00011000


Question 1/6:
Operation 1: '<<'
Perform a left shift of Binary Number 1 by 1 bits.
Enter the binary result: 101011100
Correct!

Question 2/6:
Operation 2: '*'
Perform the operation on Binary Number 1&2.
Enter the binary result: 01000001010000
Correct!

Question 3/6:
Operation 3: '&'
Perform the operation on Binary Number 1&2.
Enter the binary result: 1000
Correct!

Question 4/6:
Operation 4: '+'
Perform the operation on Binary Number 1&2.
Enter the binary result: 11000110
Correct!

Question 5/6:
Operation 5: '|'
Perform the operation on Binary Number 1&2.
Enter the binary result: 10111110
Correct!

Question 6/6:
Operation 6: '>>'
Perform a right shift of Binary Number 2 by 1 bits .
Enter the binary result: 1100
Correct!

Enter the results of the last operation in hexadecimal: c  

Correct answer!
The flag is: picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_d6f8047e}

```