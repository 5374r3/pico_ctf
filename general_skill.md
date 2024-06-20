Each **hexadecimal** digit represents **four bits** (binary digits), also known as a nibble (or nybble)

---

### Bases

Tags:  #General-skills

#### Description

What does this `bDNhcm5fdGgzX3IwcDM1` mean? I think it has something to do with bases.

##### Solution:

use command

```shell
echo bDNhcm5fdGgzX3IwcDM1 | base64 --decode
l3arn_th3_r0p35
```

`picoCTF{l3arn_th3_r0p35}`

---

### First Grep

Tags:  #General-skills

#### Description

Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/515f19f3612bfd97cd3f0c0ba32bd864/file)? This would be really tedious to look through manually, something tells me there is a better way.

##### Solution:

```shell
cat file | grep pico
picoCTF{grep_is_good_to_find_things_5af9d829}
```

`picoCTF{grep_is_good_to_find_things_5af9d829}`

---

### Codebook

Tags:  #General-skills #shell #python

#### Description

Run the Python script `code.py` in the same directory as `codebook.txt`.

- [Download code.py](https://artifacts.picoctf.net/c/3/code.py)
- [Download codebook.txt](https://artifacts.picoctf.net/c/3/codebook.txt)

##### Solution:

```shell
python3 code.py
picoCTF{c0d3b00k_455157_197a982c}
```

`picoCTF{c0d3b00k_455157_197a982c}`

---

### convertme.py

Tags: #General-skills #shell #python

#### Description

Run the Python script and convert the given number from decimal to binary to get the flag. [Download Python script](https://artifacts.picoctf.net/c/22/convertme.py)

##### Solution

```shell
python3 convertme.py
If 97 is in decimal base, what is it in binary base?
Answer: 1100001
That is correct! Here's your flag: picoCTF{4ll_y0ur_b4535_762f748e}
```

note: bin(97) => '0b1100001'
`picoCTF{4ll_y0ur_b4535_762f748e}`

---

### fixme1.py

Tags:  #General-skills #shell #python

#### Description

Fix the syntax error in this Python script to print the flag. [Download Python script](https://artifacts.picoctf.net/c/27/fixme1.py)

##### Solution:

```shell
 python3 fixme1.py
  File "/home/alpha/fixme1.py", line 20
    print('That is correct! Here\'s your flag: ' + flag)
IndentationError: unexpected indent
```

fix line 20 print statement
python3 fixme1.py
That is correct! Here's your flag: `picoCTF{1nd3nt1ty_cr1515_182342f7}`

---

### fixme2.py

Tags:  #General-skills #shell #python

#### Description

Fix the syntax error in the Python script to print the flag. [Download Python script](https://artifacts.picoctf.net/c/4/fixme2.py)

##### Solution:

```shell
python3 fixme2.py
  File "/home/alpha/fixme2.py", line 22
    if flag = "":
       ^^^^^^^^^
SyntaxError: invalid syntax. Maybe you meant '==' or ':=' instead of '='?
```

fix line 22
python3 fixme2.py
That is correct! Here's your flag: `picoCTF{3qu4l1ty_n0t_4551gnm3nt_e8814d03}`

---

### Glitch Cat

Tags:  #General-skills #nc #shell #python

#### Description

Our flag printing service has started glitching!
Additional details will be available after launching your challenge instance.

##### Solution:

click on launch instance you will get `$ nc saturn.picoctf.net 59763`

```shell
nc saturn.picoctf.net 59763
'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'
```

open python shell and paste the entire line of flag

```shell
 python3
Python 3.10.12 (main, Nov 20 2023, 15:14:05) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> chr(0x62)
'b'
>>> 'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'
'picoCTF{gl17ch_m3_n07_bda68f75}'
```

`picoCTF{gl17ch_m3_n07_bda68f75}`

---

### HashingJobApp

Tags:  #General-skills #nc #shell #python #hashing

#### Description

If you want to hash with the best, beat this test!
Additional details will be available after launching your challenge instance

##### Solution:

click on launch instance you will get `nc saturn.picoctf.net 58017`

```shell
└──╼ $ nc saturn.picoctf.net 58017
Please md5 hash the text between quotes, excluding the quotes: 'cleaning the bathroom'
Answer:
0c8acab58314dbcf54dbc158470a8047
0c8acab58314dbcf54dbc158470a8047
Correct.
Please md5 hash the text between quotes, excluding the quotes: 'Chinatown'
Answer:
09e49bb61f0323a3bfbe8937e2e031e8
09e49bb61f0323a3bfbe8937e2e031e8
Correct.
Please md5 hash the text between quotes, excluding the quotes: 'Count Dracula'
Answer:
aff1b17cdcbc3b40afd42d5fe00297da
aff1b17cdcbc3b40afd42d5fe00297da
Correct.
picoCTF{4ppl1c4710n_r3c31v3d_674c1de2}
```

Note: you can find md5 online easily
`picoCTF{4ppl1c4710n_r3c31v3d_674c1de2}`

---

### PW Crack 1

Tags: #General-skills #password_cracking #python

#### Description

Can you crack the password to get the flag? Download the password checker [here](https://artifacts.picoctf.net/c/10/level1.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/10/level1.flag.txt.enc) in the same directory too.

##### Solution:

first run the program

```shell
python3 level1.py
Please enter correct password for flag: 123
That password is incorrect
```

now read the code

```python
### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
###############################################################################
flag_enc = open('level1.flag.txt.enc', 'rb').read()
def level_1_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == "691d"):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")
level_1_pw_check()
```

you need to use `691d` to get flag

```shell
python3 level1.py
Please enter correct password for flag: 691d
Welcome back... your flag, user:
picoCTF{545h_r1ng1ng_56891419}
```

flag is `picoCTF{545h_r1ng1ng_56891419}`

---

### PW Crack 2

Tags:  #General-skills #password_cracking #python
Author: LT 'syreal' Jones

#### Description

Can you crack the password to get the flag? Download the password checker [here](https://artifacts.picoctf.net/c/15/level2.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/15/level2.flag.txt.enc) in the same directory too.

##### Solution:

```shell
python3 level2.py
Please enter correct password for flag: jjj
That password is incorrect
```

open source code

```python
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
###############################################################################
flag_enc = open('level2.flag.txt.enc', 'rb').read()
def level_2_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == chr(0x33) + chr(0x39) + chr(0x63) + chr(0x65) ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")
level_2_pw_check()
```

```python
>>> chr(0x33) + chr(0x39) + chr(0x63) + chr(0x65)
'39ce'
>>>
```

```shell
 python3 level2.py
Please enter correct password for flag: 39ce
Welcome back... your flag, user:
picoCTF{tr45h_51ng1ng_502ec42e}
```

flag is `picoCTF{tr45h_51ng1ng_502ec42e}`

---

### PW Crack 3

Tags: #General-skills #password_cracking #hashing #python

#### Description

Can you crack the password to get the flag? Download the password checker [here](https://artifacts.picoctf.net/c/16/level3.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/16/level3.flag.txt.enc) and the [hash](https://artifacts.picoctf.net/c/16/level3.hash.bin) in the same directory too. There are 7 potential passwords with 1 being correct. You can find these by examining the password checker script.

##### Solution:

```python
import hashlib
### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
###############################################################################
flag_enc = open('level3.flag.txt.enc', 'rb').read()
correct_pw_hash = open('level3.hash.bin', 'rb').read()

def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()

def level_3_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    user_pw_hash = hash_pw(user_pw)
    # print(user_pw_hash)
    print(correct_pw_hash)
    if( user_pw_hash == correct_pw_hash ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")



level_3_pw_check()


# The strings below are 7 possibilities for the correct password.
#   (Only 1 is correct)
pos_pw_list = ["6997", "3ac8", "f0ac", "4b17", "ec27", "4e66", "865e"]
```

note: last line pos_pw_list is hint

```shell
python3 level3.py
Please enter correct password for flag: 865e
Welcome back... your flag, user:
picoCTF{m45h_fl1ng1ng_2b072a90}
```

flag is `picoCTF{m45h_fl1ng1ng_2b072a90}`

---

### PW Crack 4

Tags: #General-skills #hashing #password_cracking #python
Author: LT 'syreal' Jones

#### Description

Can you crack the password to get the flag? Download the password checker [here](https://artifacts.picoctf.net/c/19/level4.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/19/level4.flag.txt.enc) and the [hash](https://artifacts.picoctf.net/c/19/level4.hash.bin) in the same directory too. There are 100 potential passwords with only 1 being correct. You can find these by examining the password checker script.

##### Solution:

```python
import hashlib

### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
###############################################################################

flag_enc = open('level4.flag.txt.enc', 'rb').read()
correct_pw_hash = open('level4.hash.bin', 'rb').read()

def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()

def level_4_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    user_pw_hash = hash_pw(user_pw)
    if( user_pw_hash == correct_pw_hash ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")

level_4_pw_check()

# The strings below are 100 possibilities for the correct password.
#   (Only 1 is correct)
pos_pw_list = ["6288", "6152", "4c7a", "b722", "9a6e", "6717", "4389", "1a28", "37ac", "de4f", "eb28", "351b", "3d58", "948b", "231b", "973a", "a087", "384a", "6d3c", "9065", "725c", "fd60", "4d4f", "6a60", "7213", "93e6", "8c54", "537d", "a1da", "c718", "9de8", "ebe3", "f1c5", "a0bf", "ccab", "4938", "8f97", "3327", "8029", "41f2", "a04f", "c7f9", "b453", "90a5", "25dc", "26b0", "cb42", "de89", "2451", "1dd3", "7f2c", "8919", "f3a9", "b88f", "eaa8", "776a", "6236", "98f5", "492b", "507d", "18e8", "cfb5", "76fd", "6017", "30de", "bbae", "354e", "4013", "3153", "e9cc", "cba9", "25ea", "c06c", "a166", "faf1", "2264", "2179", "cf30", "4b47", "3446", "b213", "88a3", "6253", "db88", "c38c", "a48c", "3e4f", "7208", "9dcb", "fc77", "e2cf", "8552", "f6f8", "7079", "42ef", "391e", "8a6d", "2154", "d964", "49ec"]
```

modified

```python
import hashlib

### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
###############################################################################

flag_enc = open('level4.flag.txt.enc', 'rb').read()
correct_pw_hash = open('level4.hash.bin', 'rb').read()

def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()

def level_4_pw_check():
    for x in pos_pw_list: # for loop to iterate through the pos_pw_list
        user_pw = x
        user_pw_hash = hash_pw(user_pw)
        print(user_pw) # printing user_pw
        if( user_pw_hash == correct_pw_hash ):
            print("Welcome back... your flag, user:")
            decryption = str_xor(flag_enc.decode(), user_pw)
            print(decryption)
            return
        print("That password is incorrect")

# level_4_pw_check()
# The strings below are 100 possibilities for the correct password.
#   (Only 1 is correct)
pos_pw_list = ["6288", "6152", "4c7a", "b722", "9a6e", "6717", "4389", "1a28", "37ac", "de4f", "eb28", "351b", "3d58", "948b", "231b", "973a", "a087", "384a", "6d3c", "9065", "725c", "fd60", "4d4f", "6a60", "7213", "93e6", "8c54", "537d", "a1da", "c718", "9de8", "ebe3", "f1c5", "a0bf", "ccab", "4938", "8f97", "3327", "8029", "41f2", "a04f", "c7f9", "b453", "90a5", "25dc", "26b0", "cb42", "de89", "2451", "1dd3", "7f2c", "8919", "f3a9", "b88f", "eaa8", "776a", "6236", "98f5", "492b", "507d", "18e8", "cfb5", "76fd", "6017", "30de", "bbae", "354e", "4013", "3153", "e9cc", "cba9", "25ea", "c06c", "a166", "faf1", "2264", "2179", "cf30", "4b47", "3446", "b213", "88a3", "6253", "db88", "c38c", "a48c", "3e4f", "7208", "9dcb", "fc77", "e2cf", "8552", "f6f8", "7079", "42ef", "391e", "8a6d", "2154", "d964", "49ec"]

level_4_pw_check()
```

973a
Welcome back... your flag, user:
`picoCTF{fl45h_5pr1ng1ng_ae0fb77c}`

Note another method using range

```python
for x in range(len(pos_pw_list)):
user_pw = pos_pw_list[x]
```

---

### PW Crack 5

Tags: #General-skills #hashing #password_cracking #python
Author: LT 'syreal' Jones

#### Description

Can you crack the password to get the flag? Download the password checker [here](https://artifacts.picoctf.net/c/31/level5.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/31/level5.flag.txt.enc) and the [hash](https://artifacts.picoctf.net/c/31/level5.hash.bin) in the same directory too. Here's a [dictionary](https://artifacts.picoctf.net/c/31/dictionary.txt) with all possible passwords based on the password conventions we've seen so far.

##### Solution

```python
import hashlib

### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
###############################################################################

flag_enc = open('level5.flag.txt.enc', 'rb').read()
correct_pw_hash = open('level5.hash.bin', 'rb').read()

def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()

def level_5_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    user_pw_hash = hash_pw(user_pw)

    if( user_pw_hash == correct_pw_hash ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")

level_5_pw_check()
```

edited python

```python
import hashlib
### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################

def str_xor(secret, key):
    # extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c, new_key_c) in zip(secret, new_key)])
###############################################################################

flag_enc = open('level5.flag.txt.enc', 'rb').read()
correct_pw_hash = open('level5.hash.bin', 'rb').read()

def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()

def level_5_pw_check():
    # user_pw = input("Please enter correct password for flag: ")
    dictionary = open("dictionary.txt", "r")
    # with open("dictionary.txt", "r") as dictionary:
    for user_pw in dictionary:
        user_pw = user_pw.strip()
        if hash_pw(user_pw) == correct_pw_hash:
            print(user_pw)
            print("Welcome back... your flag, user:")
            decryption = str_xor(flag_enc.decode(), user_pw)
            print(decryption)
            return
        print("incorrect")
level_5_pw_check()
```

9581
Welcome back... your flag, user:
`picoCTF{h45h_sl1ng1ng_36e992a6}`

---

### runme.py

Tags: #General-skills #python

#### Description

Run the `runme.py` script to get the flag. Download the script with your browser or with `wget` in the webshell. [Download runme.py Python script](https://artifacts.picoctf.net/c/34/runme.py)

##### Solution:

simply run the script
python3 runme.py
`picoCTF{run_s4n1ty_run}`

---

### Serpentine

Tags: #General-skills #python

#### Description

Find the flag in the Python script! [Download Python script](https://artifacts.picoctf.net/c/35/serpentine.py)

```python
import random
import sys

def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])


flag_enc = chr(0x15) + chr(0x07) + chr(0x08) + chr(0x06) + chr(0x27) + chr(0x21) + chr(0x23) + chr(0x15) + chr(0x5c) + chr(0x01) + chr(0x57) + chr(0x2a) + chr(0x17) + chr(0x5e) + chr(0x5f) + chr(0x0d) + chr(0x3b) + chr(0x19) + chr(0x56) + chr(0x5b) + chr(0x5e) + chr(0x36) + chr(0x53) + chr(0x07) + chr(0x51) + chr(0x18) + chr(0x58) + chr(0x05) + chr(0x57) + chr(0x11) + chr(0x3a) + chr(0x0f) + chr(0x0e) + chr(0x59) + chr(0x06) + chr(0x4d) + chr(0x55) + chr(0x0c) + chr(0x0f) + chr(0x14)


def print_flag():
  flag = str_xor(flag_enc, 'enkidu')
  print(flag)


def print_encouragement():
  encouragements = ['You can do it!', 'Keep it up!',
                    'Look how far you\'ve come!']
  choice = random.choice(range(0, len(encouragements)))
  print('\n-----------------------------------------------------')
  print(encouragements[choice])
  print('-----------------------------------------------------\n\n')

def main():

  print(
'''
    Y
  .-^-.
 /     \      .- ~ ~ -.
()     ()    /   _ _   `.                     _ _ _
 \_   _/    /  /     \   \                . ~  _ _  ~ .
   | |     /  /       \   \             .' .~       ~-. `.
   | |    /  /         )   )           /  /             `.`.
   \ \_ _/  /         /   /           /  /                `'
    \_ _ _.'         /   /           (  (
                    /   /             \  \\
                   /   /               \  \\
                  /   /                 )  )
                 (   (                 /  /
                  `.  `.             .'  /
                    `.   ~ - - - - ~   .'
                       ~ . _ _ _ _ . ~
'''
  )
  print('Welcome to the serpentine encourager!\n\n')

  while True:
    print('a) Print encouragement')
    print('b) Print flag')
    print('c) Quit\n')
    choice = input('What would you like to do? (a/b/c) ')

    if choice == 'a':
      print_encouragement()

    elif choice == 'b':
      #print('\nOops! I must have misplaced the print_flag function! Check my source code!\n\n')
      print('\nOops! I must have misplaced the print_flag function! Check my source code!\n\n', print_flag())
    elif choice == 'c':
      sys.exit(0)

    else:
      print('\nI did not understand "' + choice + '", input only "a", "b" or "c"\n\n')

if __name__ == "__main__":
  main()

```

fixed the code part

```python
print('\nOops! I must have misplaced the print_flag function! Check my source code!\n\n')


print('\nOops! I must have misplaced the print_flag function! Check my source code!\n\n', print_flag()
```

What would you like to do? (a/b/c) b
`picoCTF{7h3_r04d_l355_7r4v3l3d_ae0b80bd}`

---

### First Find

Tags: #General-skills #Linux

#### Description

Unzip this archive and find the file named 'uber-secret.txt'

- [Download zip file](https://artifacts.picoctf.net/c/502/files.zip)

##### Solution:

unzip and find uber-secret.txt
`picoCTF{f1nd_15_f457_ab443fd1}`

---

### Big Zip

Tags: #General-skills #Linux

#### Description

Unzip this archive and find the flag.

- [Download zip file](https://artifacts.picoctf.net/c/504/big-zip-files.zip)

##### Solution:

```shell
 grep -lir pico
folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt
cat folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt
information on the record will last a billion years. Genes and brains and books encode picoCTF{gr3p_15_m4g1c_ef8790dc}
```

flag is `picoCTF{gr3p_15_m4g1c_ef8790dc}`

---

### chrono

Tags: #General-skills #Linux

#### Description

How to automate tasks to run at intervals on linux servers?
Additional details will be available after launching your challenge instance.

##### Solution

Note: What is Crontab?
[**Crontab**](https://www.geeksforgeeks.org/crontab-in-linux-with-examples/)
refers to the command-line utility that allows users to create, edit, and manage their own cron schedules. When a user wants to schedule a task using cron, they use the **crontab** command to define the schedule in their user-specific crontab file. Each user can have their own crontab, and the cron daemon reads these files to know when to execute scheduled tasks.

```shell
Server: saturn.picoctf.net
Port: 57328
Username: picoplayer
Password: kZx-HVJKu8
```

```
ssh picoplayer@saturn.picoctf.net -p 57328
password -> kZx-HVJKu8
picoplayer@challenge:/$ cat /etc/crontab
# picoCTF{Sch3DUL7NG_T45K3_L1NUX_5b7059d0}
```

flag is `picoCTF{Sch3DUL7NG_T45K3_L1NUX_5b7059d0}`

---

### money-ware

Tags:

#### Description

Flag format: picoCTF{Malwarename} The first letter of the malware name should be capitalized and the rest lowercase. Your friend just got hacked and has been asked to pay some bitcoins to `1Mz7153HMuxXTuR2R1t78mGSdzaAtNbBWX`. He doesn’t seem to understand what is going on and asks you for advice. Can you identify what malware he’s being a victim of?

##### Solution:

search `1Mz7153HMuxXTuR2R1t78mGSdzaAtNbBWX` on google search engine
you will get information about **Petya** Ransomware Fast Spreading Attack
flag is `picoCTF{Petya}`

---

### Permissions

Tags: #General-skills #vim #Linux #GTFObins

#### Description

Can you read files in the root file?
Additional details will be available after launching your challenge instance.
`ssh -p 62634 picoplayer@saturn.picoctf.net` Password: `j4ks-9nxB-` Can you login and read the root file?

##### Solution:

first login to system
then type `sudo -l` it will give the information about permission

```shell
picoplayer@challenge:~$ sudo -l
[sudo] password for picoplayer:
Matching Defaults entries for picoplayer on challenge:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User picoplayer may run the following commands on challenge:
    (ALL) /usr/bin/vi
```

once we get the information that `vi` will help to root access
no go to [GTFO bins](https://gtfobins.github.io/) and search about vi and click on sudo

```shell
sudo vi -c ':!/bin/sh' /dev/null
```

now run the command
you will get `#` symbol which indicate root access
to verify type `whoami` it will show `root`
now you are root user

```shell
picoplayer@challenge:~$ sudo -l
[sudo] password for picoplayer:
Matching Defaults entries for picoplayer on challenge:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User picoplayer may run the following commands on challenge:
    (ALL) /usr/bin/vi
picoplayer@challenge:~$ sudo vi -c ':!/bin/sh' /dev/null
#
# bash
root@challenge:/home/picoplayer# ls
root@challenge:/home/picoplayer# whoami
root
root@challenge:/home/picoplayer# cd /
root@challenge:/# ls
bin  boot  challenge  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@challenge:/# cd challenge/
root@challenge:/challenge# ls
metadata.json
root@challenge:/challenge# cat metadata.json
{"flag": "picoCTF{uS1ng_v1m_3dit0r_021d10ab}", "username": "picoplayer", "password": "j4ks-9nxB-"}root@challenge:/challenge#
root@challenge:/challenge#
```

flag is `picoCTF{uS1ng_v1m_3dit0r_021d10ab}`

---

### repetitions

Tags: #General-skills #base64
Author: Theoneste Byagutangaza

#### Description

Can you make sense of this file? Download the file [here](https://artifacts.picoctf.net/c/473/enc_flag).

##### solution :

```python
import base64

def decode_until_word(encoded_str, target_word):
    while True:
        decoded_str = base64.b64decode(encoded_str).decode('utf-8')
        if target_word in decoded_str:
            return decoded_str
        encoded_str = decoded_str

# File path containing the encoded string split across multiple lines
file_path = 'enc_flag'

# Read the contents of the file and concatenate them into a single string
with open(file_path, 'r') as file:
    encoded_str = ''.join(file.readlines())

# Decode until the word "pico" is found
decoded_str = decode_until_word(encoded_str, "pico")

print("Decoded string:", decoded_str)
```

or another method is use **CyberChef** to decode the base64
add base64 multiple times
flag is `picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_dfe803c6}`

---

### useless

Tags: #General-skills #man
Author: Loic Shema

#### Description

There's an interesting script in the user's home directory
Additional details will be available after launching your challenge instance.
some basic calculations, explore the script and find a flag.

```
Hostname: saturn.picoctf.net
Port:     52001
Username: picoplayer
Password: password
```

##### Solution:

```shell
picoplayer@challenge:~$ ./useless
Read the code first
```

```shell
picoplayer@challenge:~$ cat useless
#!/bin/bash
# Basic mathematical operations via command-line arguments

if [ $# != 3 ]
then
  echo "Read the code first"
else
	if [[ "$1" == "add" ]]
	then
	  sum=$(( $2 + $3 ))
	  echo "The Sum is: $sum"

	elif [[ "$1" == "sub" ]]
	then
	  sub=$(( $2 - $3 ))
	  echo "The Substract is: $sub"

	elif [[ "$1" == "div" ]]
	then
	  div=$(( $2 / $3 ))
	  echo "The quotient is: $div"

	elif [[ "$1" == "mul" ]]
	then
	  mul=$(( $2 * $3 ))
	  echo "The product is: $mul"

	else
	  echo "Read the manual"

	fi
fi
```

```shell
picoplayer@challenge:~$ ./useless  add 4 5
The Sum is: 9
picoplayer@challenge:~$ ./useless sub 4 5
The Substract is: -1
picoplayer@challenge:~$ man useless

useless
     useless, — This is a simple calculator script

SYNOPSIS
     useless, [add sub mul div] number1 number2

DESCRIPTION
     Use the useless, macro to make simple calulations like addition,subtraction, multiplication and division.

Examples
     ./useless add 1 2
       This will add 1 and 2 and return 3

     ./useless mul 2 3
       This will return 6 as a product of 2 and 3

     ./useless div 6 3
       This will return 2 as a quotient of 6 and 3

     ./useless sub 6 5
       This will return 1 as a remainder of substraction of 5 from 6

Authors
     This script was designed and developed by Cylab Africa

     picoCTF{us3l3ss_ch4ll3ng3_3xpl0it3d_4151}

```

flag is `picoCTF{us3l3ss_ch4ll3ng3_3xpl0it3d_4151}`

---

### ASCII Numbers

Tags: #General-skills
Author: LT 'syreal' Jones

#### Description

Convert the following string of ASCII numbers into a readable string: `0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x34 0x35 0x63 0x31 0x31 0x5f 0x6e 0x30 0x5f 0x71 0x75 0x33 0x35 0x37 0x31 0x30 0x6e 0x35 0x5f 0x31 0x6c 0x6c 0x5f 0x74 0x33 0x31 0x31 0x5f 0x79 0x33 0x5f 0x6e 0x30 0x5f 0x6c 0x31 0x33 0x35 0x5f 0x34 0x34 0x35 0x64 0x34 0x31 0x38 0x30 0x7d`

##### Solution:

use cyberchef and select from hex
your flag is `picoCTF{45c11_n0_qu35710n5_1ll_t311_y3_n0_l135_445d4180}`

---

### binhexa

Tags: #General-skills #browser_web_shell
Author: Nana Ama Atombo-Sackey

#### Description

How well can you perfom basic binary operations?
Additional details will be available after launching your challenge instance.
Start searching for the flag here `nc titan.picoctf.net 59196`

##### Solution:

```shell
└──╼ $ nc titan.picoctf.net 59196

Welcome to the Binary Challenge!"
Your task is to perform the unique operations in the given order and find the final result in hexadecimal that yields the flag.

Binary Number 1: 01110111
Binary Number 2: 01000011


Question 1/6:
Operation 1: '>>'
Perform a right shift of Binary Number 2 by 1 bits .
Enter the binary result: 00100001
Correct!

Question 2/6:
Operation 2: '<<'
Perform a left shift of Binary Number 1 by 1 bits.
Enter the binary result: 11101110
Correct!

Question 3/6:
Operation 3: '|'
Perform the operation on Binary Number 1&2.
Enter the binary result: 01110111
Correct!

Question 4/6:
Operation 4: '*'
Perform the operation on Binary Number 1&2.
Enter the binary result: 01111100100101
Correct!

Question 5/6:
Operation 5: '+'
Perform the operation on Binary Number 1&2.
Enter the binary result: 010111010
Correct!

Question 6/6:
Operation 6: '&'
Perform the operation on Binary Number 1&2.
Enter the binary result: 01000011
Correct!

Enter the results of the last operation in hexadecimal: 43

Correct answer!
The flag is: picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_d6f8047e}

```

flag is `picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_d6f8047e}`

---

### Binary Search

Tags: #General-skills #browser_web_shell #shell #ls
Author: Jeffery John

#### Description

Want to play a game? As you use more of the shell, you might be interested in how they work! Binary search is a classic algorithm used to quickly find an item in a sorted list. Can you find the flag? You'll have 1000 possibilities and only 10 guesses. Cyber security often has a huge amount of data to look through - from logs, vulnerability reports, and forensics. Practicing the fundamentals manually might help you in the future when you have to write your own tools! You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_atlas/5/challenge.zip)
  Additional details will be available after launching your challenge instance.
  `ssh -p 51428 ctf-player@atlas.picoctf.net` Using the password `1ad5be0d`. Accept the fingerprint with `yes`, and `ls` once connected to begin. Remember, in a shell, passwords are hidden!

##### Solution

read the zip file code then try and experiment to get flag

```shell
 ssh -p 51428 ctf-player@atlas.picoctf.net
ctf-player@atlas.picoctf.net's password:
Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 500
Lower! Try again.
Enter your guess: 300
Lower! Try again.
Enter your guess: 200
Higher! Try again.
Enter your guess: 250
Lower! Try again.
Enter your guess: 230
Higher! Try again.
Enter your guess: 240
Lower! Try again.
Enter your guess: 235
Higher! Try again.
Enter your guess: 239
Congratulations! You guessed the correct number: 239
Here's your flag: picoCTF{g00d_gu355_3af33d18}
Connection to atlas.picoctf.net closed.

```

---

### Based

Tags: #General-skills
Author: Alex Fulton/Daniel Tunitis

#### Description

To get truly 1337, you must understand different data encodings, such as hexadecimal or binary. Can you get the flag from this program to prove you are on the way to becoming 1337? Connect with `nc jupiter.challenges.picoctf.org 29956`.

##### Solution:

```shell
┌─[✔][alpha@speed:🐧]─[~/Downloads]:
└──╼ $ nc jupiter.challenges.picoctf.org 29956
Let us see how data is stored
test
Please give the 01110100 01100101 01110011 01110100 as a word.
...
you have 45 seconds.....

Input:
test
Please give me the  163 154 165 144 147 145 as a word.
Input:
sludge
Please give me the 6e75727365 as a word.
Input:
nurse
You've beaten the challenge
Flag: picoCTF{learning_about_converting_values_b375bb16}

```

---

### plumbing

Tags: #General-skills
Author: Alex Fulton/Danny Tunitis

#### Description

Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag? Connect to `jupiter.challenges.picoctf.org 4427`.

##### Solution:

when you will run `nc jupiter.challenges.picoctf.org 4427` into terminal lot of text will print in terminal so better to store data into file to capture ctf
`nc jupiter.challenges.picoctf.org 4427 > plumbing.txt 2>&1`
flag is `picoCTF{digital_plumb3r_5ea1fbd7}`

---

### endianness

Tags: #General-skills #browser_web_shell

Author: Nana Ama Atombo-Sackey

#### Description

Know of little and big endian? [Source](https://artifacts.picoctf.net/c_titan/80/flag.c)
Additional details will be available after launching your challenge instance
`nc titan.picoctf.net 58031`

##### Solution:

when you run the offline code

```shell
Welcome to the Endian CTF!
You need to find both the little endian and big endian representations of a word.
If you get both correct, you will receive the flag.
Word: fhpsd
Enter the Little Endian representation: 6473706866
Correct Little Endian representation!
Enter the Big Endian representation: 6668707364
Correct Big Endian representation!
Flag not found. Please run this on the server
```

`Word: fhpsd`
The ASCII representation of each character in hexadecimal is:

- 'f' -> 66
- 'h' -> 68
- 'p' -> 70
- 's' -> 73
- 'd' -> 64
  so **big endian** representation is _6668707364_
  Now, we reverse the order of these hexadecimal representations:

- 'd' -> 64
- 's' -> 73
- 'p' -> 70
- 'h' -> 68
- 'f' -> 66
  so **little endian** representation is _6473706866_
  Now run server

```shell
nc titan.picoctf.net 58031
Welcome to the Endian CTF!
You need to find both the little endian and big endian representations of a word.
If you get both correct, you will receive the flag.
Word: kbqhu
Enter the Little Endian representation: 756871626B
Correct Little Endian representation!
Enter the Big Endian representation: 6B62716875
Correct Big Endian representation!
Congratulations! You found both endian representations correctly!
Your Flag is: picoCTF{3ndi4n_sw4p_su33ess_02999450}
```

---

### mus1c

Tags: #General-skills
Author: Danny

#### Description

I wrote you a [song](https://jupiter.challenges.picoctf.org/static/0e21e3ca94779f56b122296424e879f8/lyrics.txt). Put it in the picoCTF{} flag format.

##### Solution:

Rockstar is a computer programming language designed for creating programs that are also hair metal power ballads.
Pasting the -lyrics into the [online interpreter](https://codewithrockstar.com/online), we get the following output

```shell
114
114
114
111
99
107
110
114
110
48
49
49
51
114
Program completed in 594 ms

```

convert hex to text
`114 114 114 111 99 107 110 114 110 48 49 49 51 114` -> `rrrocknrn0113r`
flag is `picoCTF{rrrocknrn0113r}`

---

### flag_shop

Tags: #General-skills
Author: Danny

#### Description

There's a flag shop selling stuff, can you buy a flag? [Source](https://jupiter.challenges.picoctf.org/static/253c4651d852ac6342752ff222cf2a83/store.c). Connect with `nc jupiter.challenges.picoctf.org 9745`.

##### Solution:

Note: read code and run code
we have Balance: 1100 and

1. Definitely not the flag Flag
2. 1337 Flag
   option 1: These knockoff Flags cost 900 each, enter desired quantity
   option 2: 1337 flags cost 100000 dollars,
   to solve this we have to overflow integer value and option 1 have loop hole

```md
2147483647 => 2^128
2^128 \* 900 => 1.9327353e+12 = 1932735282300

3000000*900 = 2700000000
2^128 = 2147483647
2222222*900 = 1999999800
2299999*900 = 2069999100
3000000*900 = -1594967296
```

```python
import numpy
>>> numpy.int32(2222222*900)
1999999800
>>> numpy.int32(3000000*900)
-1594967296
>>> numpy.int32(2222229*900)
2000006100
>>> numpy.int32(2222299*900)
2000069100
>>> numpy.int32(2999999*900)
-1594968196
>>> numpy.int32(2899999*900)
-1684968196
>>> numpy.int32(2399999*900)
-2134968196
>>> numpy.int32(2299999*900)
2069999100
>>> numpy.int32(2147483647*900)
-900
>>> numpy.int32(2147483648*900)
0
>>> numpy.int32(2147483646*900)
-1800
>>> numpy.int32(2147483647*100)
-100
>>> numpy.int32(2147483647*10)
-10
>>> numpy.int32(2147483647*1)
2147483647
>>> numpy.int32(2147483647*2)
-2
>>> numpy.int32(2147483647*900)
-900
```

`nc jupiter.challenges.picoctf.org 9745`

```shell
┌─[✔][alpha@speed:🍇]─[~]:
└──╼ $ nc jupiter.challenges.picoctf.org 9745
Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
1
These knockoff Flags cost 900 each, enter desired quantity
3000000

The final cost is: -1594967296

Your current balance after transaction: 1594968396

Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
1



 Balance: 1594968396


Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
2
1337 flags cost 100000 dollars, and we only have 1 in stock
Enter 1 to buy one1
YOUR FLAG IS: picoCTF{m0n3y_bag5_65d67a74}
Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection


```

---

### Special

Tags: #General-skills #bash #ssh
Author: LT 'syreal' Jones

#### Description

Don't power users get tired of making spelling mistakes in the shell? Not anymore! Enter Special, the Spell Checked Interface for Affecting Linux. Now, every word is properly spelled and capitalized... automatically and behind-the-scenes! Be the first to test Special in beta, and feel free to tell us all about how Special streamlines every development process that you face. When your co-workers see your amazing shell interface, just tell them: That's Special (TM) Start your instance to see connection details.

Additional details will be available after launching your challenge instance.
Start your instance to see connection details. `ssh -p 53530 ctf-player@saturn.picoctf.net` The password is `8a707622`

##### Solution:

```shell
Special$ ${parameter=ls}
${parameter=ls}
blargh
Special$ ${parameter=cd blargh}
${parameter=cd blargh}
Special$ ${parameter=ls}
${parameter=ls}
blargh
Special$ ${parameter=ls blargh}
${parameter=ls blargh}
flag.txt
Special$ ${parameter=cat blargh/flag.txt}
${parameter=cat blargh/flag.txt}
picoCTF{5p311ch3ck_15_7h3_w0r57_a60bdf40}Special$
```

picoCTF{5p311ch3ck_15_7h3_w0r57_a60bdf40}

Note: [github link](https://github.com/noamgariani11/PicoCTF-2023-Writeup/blob/main/General%20Skills/Special/Special.md)
and [parameter](https://mywiki.wooledge.org/BashGuide/Parameters)

```shell
Special$ ${parameter:-ls}
${parameter:-ls}
blargh
Special$ ${parameter:-ls blargh}
${parameter:-ls blargh}
flag.txt
Special$ ${parameter:-cat blargh/flag.txt}
${parameter:-cat blargh/flag.txt}
picoCTF{5p311ch3ck_15_7h3_w0r57_a60bdf40}Special$
```

---

### dont-you-love-banners

Tags: #General-skills #shell #browser_web_shell
Author: Loic Shema / syreal

#### Description

Can you abuse the banner?
Additional details will be available after launching your challenge instance.
The server has been leaking some crucial information on `tethys.picoctf.net 61629`. Use the leaked information to get to the server. To connect to the running application use `nc tethys.picoctf.net 60282`. From the above information abuse the machine and find the flag in the /root directory.

##### Solution:

Note:
A **symlink** is a _symbolic Linux/ UNIX_ link that points to another file or folder on your computer, or a connected file system. This is similar to a Windows shortcut.
more info about [symlink](https://www.freecodecamp.org/news/symlink-tutorial-in-linux-how-to-create-and-remove-a-symbolic-link/)

```shell
 nc tethys.picoctf.net 61629
SSH-2.0-OpenSSH_7.6p1 My_Passw@rd_@1234


Protocol mismatch.

 nc tethys.picoctf.net 60282`
*************************************
**************WELCOME****************
*************************************

what is the password?
My_Passw@rd_@1234
What is the top cyber security conference in the world?
DEFCON
the first hacker ever was known for phreaking(making free phone calls), who was it?
JOHN DRAPER
player@challenge:~$ ls
banner  text
player@challenge:~$ ln -s /root/flag.txt banner
ln -s /root/flag.txt banner
ln: failed to create symbolic link 'banner': File exists
player@challenge:~$ rm -r banner
rm -r banner
player@challenge:~$ ln -s /root/flag.txt banner
ln -s /root/flag.txt banner
┌─[✘][alpha@speed:🍉]─[~]:
└──╼ $ nc tethys.picoctf.net 60965
picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_b3ee718e}

```

---

### 1_wanna_b3_a_r0ck5tar

Tags: #General-skills
Author: Alex Bushkin
The Rockstar language has changed since this problem was released! Use this Wayback Machine URL to use an older version of Rockstar, [here](https://web.archive.org/web/20190522020843/https://codewithrockstar.com/online).

#### Description

I wrote you another [song](https://jupiter.challenges.picoctf.org/static/62f0cc3605aaf108a4f743b5b7f0dac4/lyrics.txt). Put the flag in the picoCTF{} flag format

##### Solution:

first read the document on Rockstar

```
guitar is a six-string
Shout guitar
```

output will be 136
Note: shout is used to print variable

```python
'''# Rocknroll is right
Rocknroll = True
# Silence is wrong
Silence = False
# A guitar is a six-string
guitar = 136 #a=1 six=3 string=6
# Tommy's been down
Tommy = 4
# Music is a billboard-burning razzmatazz!
Music = 1970
# If the music is a guitar
if(Music == guitar):
  # Say "Keep on rocking!"
  print("Keep on rocking!")
  # Listen to the rhythm
  rhythm=input()
  # If the rhythm without Music is nothing
  if(rhythm - Music == 0):
    # Tommy is rockin guitar
    Tommy = 66
    # Shout Tommy!
    print(Tommy)
    # Music is amazing sensation
    Music = 79
    # Jamming is awesome presence
    Jamming = 78
    # Scream Music!
    print(Music)
    # Scream Jamming!
    print(Jamming)
    # Tommy is playing rock
    Tommy = 74
    # Scream Tommy!
    print(Tommy)
    # They are dazzled audiences
    Tommy = 79
    # Shout it!
    print(Tommy)
    # Rock is electric heaven
    Rock = 86
    # Scream it!
    print(Rock)
    # Tommy is jukebox god
    Tommy = 73
    # Say it!
    print(Tommy)
    # Break it down
    # Shout "Bring on the rock!"
    print("Bring on the rock!")
    # Else Whisper "That ain't it, Chief"
  else:
    print("That ain't it, Chief")
    # Break it down
'''


Rocknroll = True
Silence = False
# guitar = 136
guitar = 19
Tommy = 4
# Music = 1970
Music = 19
if (Music == guitar):
    print("Keep on rocking!")
    rhythm = int(input("Enter the number "))
    if (rhythm - Music == 0):
        Tommy = 66
        print(Tommy)
        Music = 79
        Jamming = 78
        print(Music)
        print(Jamming)
        Tommy = 74
        print(Tommy)
        Tommy=79
        print(Tommy)
        Rock = 86
        print(Rock)
        Tommy = 73
        print(Tommy)
        print("Bring on the rock!")
    else:
        print("That ain't it, Chief")
        # Break it down
#Note: Music = 1970 and guitar = 19
# if (Music == guitar): we should write music = 19 and guitar = 19
#if (rhythm - Music == 0): we should enter the number to make it 0
```

Keep on rocking!
Enter the number 19
66
79
78
74
79
86
73
Bring on the rock!
if you convert [66 79 78 74 79 86 73] = _BONJOVI_

```python
 l=[66,79,78,74,79,86,73]
>>> ''.join(chr(i) for i in l)
'BONJOVI'
```

flag is `picoCTF{BONJOVI}`

---

### Specialer

Tags: #General-skills #bash #ssh
Author: LT 'syreal' Jones, et al.

#### Description

Reception of Special has been cool to say the least. That's why we made an exclusive version of Special, called Secure Comprehensive Interface for Affecting Linux Empirically Rad, or just 'Specialer'. With Specialer, we really tried to remove the distractions from using a shell. Yes, we took out spell checker because of everybody's complaining. But we think you will be excited about our new, reduced feature set for keeping you focused on what needs it the most. Please start an instance to test your very own copy of Specialer.

Additional details will be available after launching your challenge instance.
`ssh -p 55706 ctf-player@saturn.picoctf.net`. The password is `3f39b042`

##### Solution:

```shell
Specialer$ echo *
abra ala sim
Specialer$ cd ala
Specialer$ echo *
kazam.txt mode.txt
Specialer$ echo $(<kazam.txt)
return 0 picoCTF{y0u_d0n7_4ppr3c1473_wh47_w3r3_d01ng_h3r3_811ae7e9}

```

---

### SansAlpha

Tags: #General-skills #shell #browser_web_shell #shell_escape
Author: syreal

#### Description

The Multiverse is within your grasp! Unfortunately, the server that contains the secrets of the multiverse is in a universe where keyboards only have numbers and (most) symbols.

Additional details will be available after launching your challenge instance
`ssh -p 63057 ctf-player@mimas.picoctf.net` Use password: `1ad5be0d`

---
