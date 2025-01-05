### Custom encryption

Author: NGIRIMANA Schadrack
#Medium #cryptography #picoCTF2024 #browser_web_shell #ASCII_encoding
#### Description

Can you get sense of this code file and write the function that will decode the given encrypted file content. Find the encrypted file here [flag_info](https://artifacts.picoctf.net/c_titan/94/enc_flag) and [code file](https://artifacts.picoctf.net/c_titan/94/custom_encryption.py) might be good to analyze and get the flag.

##### Solution:
given code is 

```python
from random import randint
import sys


def generator(g, x, p):
    return pow(g, x) % p


def encrypt(plaintext, key):
    cipher = []
    for char in plaintext:
        cipher.append(((ord(char) * key*311)))
    return cipher


def is_prime(p):
    v = 0
    for i in range(2, p + 1):
        if p % i == 0:
            v = v + 1
    if v > 1:
        return False
    else:
        return True


def dynamic_xor_encrypt(plaintext, text_key):
    cipher_text = ""
    key_length = len(text_key)
    for i, char in enumerate(plaintext[::-1]):
        key_char = text_key[i % key_length]
        encrypted_char = chr(ord(char) ^ ord(key_char))
        cipher_text += encrypted_char
    return cipher_text


def test(plain_text, text_key):
    p = 97
    g = 31
    if not is_prime(p) and not is_prime(g):
        print("Enter prime numbers")
        return
    a = randint(p-10, p)
    b = randint(g-10, g)
    print(f"a = {a}")
    print(f"b = {b}")
    u = generator(g, a, p)
    v = generator(g, b, p)
    key = generator(v, a, p)
    b_key = generator(u, b, p)
    shared_key = None
    if key == b_key:
        shared_key = key
    else:
        print("Invalid key")
        return
    semi_cipher = dynamic_xor_encrypt(plain_text, text_key)
    cipher = encrypt(semi_cipher, shared_key)
    print(f'cipher is: {cipher}')


if __name__ == "__main__":
    message = sys.argv[1]
    test(message, "trudeau")

```

this code used to decrypt the flag
```python
def generator(g, x, p):
    return pow(g, x) % p


def dynamic_xor_decrypt(semi_cipher, text_key):
    decrypted_text = ""
    key_length = len(text_key)
    for i, char in enumerate(semi_cipher):
        key_char = text_key[i % key_length]
        decrypted_char = chr(ord(char) ^ ord(key_char))
        decrypted_text += decrypted_char
    return decrypted_text[::-1]  # Reverse back to original order


def decrypt(cipher, shared_key, text_key):
    # Step 1: Reverse the final encryption step
    semi_cipher = []
    for code in cipher:
        if code == 0:
            semi_cipher.append(
                chr(0)
            )  # Handle zero separately to prevent division by zero
        else:
            char_code = code // (shared_key * 311)
            semi_cipher.append(chr(char_code))

    # Step 2: Reverse the XOR encryption
    decrypted_text = dynamic_xor_decrypt(semi_cipher, text_key)
    return decrypted_text


# Constants based on provided values
p = 97
g = 31
a = 95 
b = 21
text_key = "trudeau"

cipher = [
    237915,
    1850450,
    1850450,
    158610,
    2458455,
    2273410,
    1744710,
    1744710,
    1797580,
    1110270,
    0,
    2194105,
    555135,
    132175,
    1797580,
    0,
    581570,
    2273410,
    26435,
    1638970,
    634440,
    713745,
    158610,
    158610,
    449395,
    158610,
    687310,
    1348185,
    845920,
    1295315,
    687310,
    185045,
    317220,
    449395,
]

# Generate the shared key
u = generator(g, a, p)
v = generator(g, b, p)
shared_key = generator(v, a, p)

# Decrypt the provided cipher
decrypted_text = decrypt(cipher, shared_key, text_key)
print(f"Decrypted text: {decrypted_text}")

```

```css
┌─[✔]──[alpha@speed:]──[~/Downloads]:
└──╼ $ python3 test2.py 
Decrypted text: picoCTF{custom_d2cr0pt6d_66778b34}

```