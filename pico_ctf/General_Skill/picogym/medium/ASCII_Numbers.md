### ASCII Numbers

#Medium #picoGym #Exclusive #General-skills 

Author: LT 'syreal' Jones

#### Description

Convert the following string of ASCII numbers into a readable string:`0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x34 0x35 0x63 0x31 0x31 0x5f 0x6e 0x30 0x5f 0x71 0x75 0x33 0x35 0x37 0x31 0x30 0x6e 0x35 0x5f 0x31 0x6c 0x6c 0x5f 0x74 0x33 0x31 0x31 0x5f 0x79 0x33 0x5f 0x6e 0x30 0x5f 0x6c 0x31 0x33 0x35 0x5f 0x34 0x34 0x35 0x64 0x34 0x31 0x38 0x30 0x7d`

##### Solution:
```python
hex_string = "0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x34 0x35 0x63 0x31 0x31 0x5f 0x6e 0x30 0x5f 0x71 0x75 0x33 0x35 0x37 0x31 0x30 0x6e 0x35 0x5f 0x31 0x6c 0x6c 0x5f 0x74 0x33 0x31 0x31 0x5f 0x79 0x33 0x5f 0x6e 0x30 0x5f 0x6c 0x31 0x33 0x35 0x5f 0x34 0x34 0x35 0x64 0x34 0x31 0x38 0x30 0x7d"

# Split the string into individual hex values, convert to characters, and join into a single string

decoded_text = "".join(chr(int(h, 16)) for h in hex_string.split())

# Print the result

print(decoded_text)
```

```css
┌─[✔]──[alpha@speed:🍇]──[~/Videos]:
└──╼ $ python3 test.py 
picoCTF{45c11_n0_qu35710n5_1ll_t311_y3_n0_l135_445d4180}
```