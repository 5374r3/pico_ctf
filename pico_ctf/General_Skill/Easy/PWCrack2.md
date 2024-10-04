### PW Crack 2

Author: LT 'syreal' Jones
#easy #General-skills #picomini2022 #password_cracking 
#### Description

Can you crack the password to get the flag? Download the password checker [here](https://artifacts.picoctf.net/c/15/level2.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/15/level2.flag.txt.enc) in the same directory too.

##### Solution
download python file and encrypted file
here is the python file
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

simply run the code
```css
┌──(kali㉿kali)-[~/Downloads]
└─╼ $ python3 level2.py 
Please enter correct password for flag: 
```

now how to find the correct password ?
```css
user_pw == chr(0x33) + chr(0x39) + chr(0x63) + chr(0x65) )
# using python you will get password
>>> print(chr(0x33) + chr(0x39) + chr(0x63) + chr(0x65))
39ce
chr(0x33) = 3
chr(0x39) = 9
chr(0x63) = c
chr(0x65) = e
```

```css
┌──(kali㉿kali)-[~/Downloads]
└─╼ $ python3 level2.py 
Please enter correct password for flag: 39ce
Welcome back... your flag, user:
picoCTF{tr45h_51ng1ng_502ec42e}
```
