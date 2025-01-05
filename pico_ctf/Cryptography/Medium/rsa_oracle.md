### rsa_oracle

Author: Geoffrey Njogu
#Medium #cryptography #picoCTF2024 #browser_web_shell 
#### Description

Can you abuse the oracle? An attacker was able to intercept communications between a bank and a fintech company. They managed to get the [message](https://artifacts.picoctf.net/c_titan/149/secret.enc) (ciphertext) and the [password](https://artifacts.picoctf.net/c_titan/149/password.enc) that was used to encrypt the message. After some intensive reconassainance they found out that the bank has an oracle that was used to encrypt the password and can be found here `nc titan.picoctf.net 64064`. Decrypt the password and use it to decrypt the message. The oracle can decrypt anything except the password.

##### Solution
download both file
use pwn tool

first method

```python
from pwn import *

def conn():
    r = remote("titan.picoctf.net", 64064)
    r.recvuntil(b"E --> encrypt D --> decrypt.")
    return r


with open("password.enc") as file:
    c_password = int(file.read())
# c_password = 2336150584734702647514724021470643922433811330098144930425575029773908475892259185520495303353109615046654428965662643241365308392679139063000973730368839
r = conn()

def encrypt(plain):
    r.sendline(b"E")
    r.recvuntil(b"enter text to encrypt (encoded length must be less than keysize): ")
    r.sendline(plain)
    print(r.recvuntil(b"ciphertext (m ^ e mod n) "))

    return r.recvline().strip().decode()

def decrypt(cipher):
    r.sendline(b"D")
    r.recvuntil(b"Enter text to decrypt: ")
    r.sendline(cipher)
    print(r.recvuntil(b"decrypted ciphertext as hex (c ^ d mod n): "))

    return r.recvline().strip().decode()

c_two = encrypt(b"\x02")
c_two = int(c_two)

print(c_two*c_password)

# encryption of plain t: C = t^e mod n
# decrypting the ciphertext C: C^d mod n = t^e^d mod n = t mod n

# if C_2 is the ciphertext of \x02, and C_password is the ciphertext of the password t
# then (C_2 * C_password)^d mod n = (2^e*t^e)^d mod n = (2^e^d)(t^e^d) mod n = 2t mod n

attack = decrypt(str(c_two*c_password).encode()).encode()
attack = int(attack, 16)
attack = attack // 2

print(attack.to_bytes((attack.bit_length() + 7) // 8, "big"))

# password is 60f50
# use openssl to decrypt the secret.enc file:
# openssl enc -aes-256-cbc -d -in secret.enc
```

```css
┌──(myenv)─(kali㉿kali)-[~/Downloads]
└─$ python3 ras.py     
[+] Opening connection to titan.picoctf.net on port 64064: Done
b'\x02\n\nencoded cleartext as Hex m: 2\n\nciphertext (m ^ e mod n) '
18076387826468720523893266140976116385194180518258294838965139649378891829626064600438838013115795971437584584488138284886940475192715375039672686708094717607510546087912481320314436676403766192383573518367387308778753288368751320518634321128602031667790118465944509598016636546237455684942611011139037897690
b'decrypted ciphertext as hex (c ^ d mod n): '
b'3319c'
[*] Closed connection to titan.picoctf.net port 64064
```

2nd method

```python
from pwn import *

context.log_level='critical'
p = remote("titan.picoctf.net", 64064)

p.recvuntil(b"decrypt.")

with open("password.enc") as file:
    c = int(file.read())

p.sendline(b"E")
p.recvuntil(b"keysize): ")
p.sendline(b"\x02")
p.recvuntil(b"mod n) ")

c_a = int(p.recvline())

p.sendline(b"D")
p.recvuntil(b"decrypt: ")
p.sendline(str(c_a*c).encode())
p.recvuntil(b"mod n): ")

password = int(p.recvline(), 16) // 2
password = password.to_bytes(len(str(password))-7, "big").decode("utf-8")

print("Password:", password)
```

```css
┌──(myenv)─(kali㉿kali)-[~/Downloads]
└─$ python3 rsa1.py                               
Password: 3319c
```

after getting password decode them

```css
┌──(myenv)─(kali㉿kali)-[~/Downloads]
└─$ openssl enc -aes-256-cbc -d -in secret.enc
enter AES-256-CBC decryption password:
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
picoCTF{su((3ss_(r@ck1ng_r3@_3319c817}  
```
