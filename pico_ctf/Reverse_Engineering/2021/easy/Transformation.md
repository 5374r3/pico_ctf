### Transformation

Author: madStacks
#easy #Reverse_Engineering #picoCTF2021 
#### Description

I wonder what this really is... [enc](https://mercury.picoctf.net/static/1d8a5a2779c4dc24999f0358d7a1a786/enc) `''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])`

##### Solution:
enc value is
```css
灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸彥㜰㍢㐸㙽
```

using CyberChef you can decode this just add magic and tick mark on intensive mode
you will get your flag `picoCTF{16_bits_inst34d_of_8_e703b486}`


you can use python script to decode as well
test.py file
```css
enc = "灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸彥㜰㍢㐸㙽"

# Decoding process
flag = []
for c in enc:
    value = ord(c)  # Get the Unicode value of the encoded character
    first_char = chr(value >> 8)  # Extract the first character (high 8 bits)
    second_char = chr(value & 0xFF)  # Extract the second character (low 8 bits)
    flag.append(first_char)
    flag.append(second_char)

# Join the list of characters into a single string
decoded_flag = ''.join(flag)

print("Decoded flag:", decoded_flag)

```

```css
python3 test.py               
Decoded flag: picoCTF{16_bits_inst34d_of_8_e703b486}
```

