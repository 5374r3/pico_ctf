### weirdSnake

Author: Junias Bonou
#Medium #Reverse_Engineering #picoCTF2024 #python #browser_web_shell 
#### Description

I have a friend that enjoys coding and he hasn't stopped talking about a snake recently He left this [file](https://artifacts.picoctf.net/c_titan/124/snake) on my computer and dares me to uncover a secret phrase from it. Can you assist?

##### Solution:
ascii file

```css
  1           0 LOAD_CONST               0 (4)
              2 LOAD_CONST               1 (54)
              4 LOAD_CONST               2 (41)
              6 LOAD_CONST               3 (0)
              8 LOAD_CONST               4 (112)
             10 LOAD_CONST               5 (32)
             12 LOAD_CONST               6 (25)
             14 LOAD_CONST               7 (49)
             16 LOAD_CONST               8 (33)
             18 LOAD_CONST               9 (3)
             20 LOAD_CONST               3 (0)
             22 LOAD_CONST               3 (0)
             24 LOAD_CONST              10 (57)
             26 LOAD_CONST               5 (32)
             28 LOAD_CONST              11 (108)
             30 LOAD_CONST              12 (23)
             32 LOAD_CONST              13 (48)
             34 LOAD_CONST               0 (4)
             36 LOAD_CONST              14 (9)
             38 LOAD_CONST              15 (70)
             40 LOAD_CONST              16 (7)
             42 LOAD_CONST              17 (110)
             44 LOAD_CONST              18 (36)
             46 LOAD_CONST              19 (8)
             48 LOAD_CONST              11 (108)
             50 LOAD_CONST              16 (7)
             52 LOAD_CONST               7 (49)
             54 LOAD_CONST              20 (10)
             56 LOAD_CONST               0 (4)
             58 LOAD_CONST              21 (86)
             60 LOAD_CONST              22 (43)
             62 LOAD_CONST              23 (106)
             64 LOAD_CONST              24 (123)
             66 LOAD_CONST              25 (89)
             68 LOAD_CONST              26 (87)
             70 LOAD_CONST              27 (18)
             72 LOAD_CONST              28 (62)
             74 LOAD_CONST              29 (47)
             76 LOAD_CONST              20 (10)
             78 LOAD_CONST              30 (78)
             80 BUILD_LIST              40
             82 STORE_NAME               0 (input_list)

  2          84 LOAD_CONST              31 ('J')
             86 STORE_NAME               1 (key_str)

  3          88 LOAD_CONST              32 ('_')
             90 LOAD_NAME                1 (key_str)
             92 BINARY_ADD
             94 STORE_NAME               1 (key_str)

  4          96 LOAD_NAME                1 (key_str)
             98 LOAD_CONST              33 ('o')
            100 BINARY_ADD
            102 STORE_NAME               1 (key_str)

  5         104 LOAD_NAME                1 (key_str)
            106 LOAD_CONST              34 ('3')
            108 BINARY_ADD
            110 STORE_NAME               1 (key_str)

  6         112 LOAD_CONST              35 ('t')
            114 LOAD_NAME                1 (key_str)
            116 BINARY_ADD
            118 STORE_NAME               1 (key_str)

  9         120 LOAD_CONST              36 (<code object <listcomp> at 0x7f704e8a4d40, file "snake.py", line 9>)
            122 LOAD_CONST              37 ('<listcomp>')
            124 MAKE_FUNCTION            0
            126 LOAD_NAME                1 (key_str)
            128 GET_ITER
            130 CALL_FUNCTION            1
            132 STORE_NAME               2 (key_list)

 11     >>  134 LOAD_NAME                3 (len)
            136 LOAD_NAME                2 (key_list)
            138 CALL_FUNCTION            1
            140 LOAD_NAME                3 (len)
            142 LOAD_NAME                0 (input_list)
            144 CALL_FUNCTION            1
            146 COMPARE_OP               0 (<)
            148 POP_JUMP_IF_FALSE      162

 12         150 LOAD_NAME                2 (key_list)
            152 LOAD_METHOD              4 (extend)
            154 LOAD_NAME                2 (key_list)
            156 CALL_METHOD              1
            158 POP_TOP
            160 JUMP_ABSOLUTE          134

 15     >>  162 LOAD_CONST              38 (<code object <listcomp> at 0x7f704e8a4df0, file "snake.py", line 15>)
            164 LOAD_CONST              37 ('<listcomp>')
            166 MAKE_FUNCTION            0
            168 LOAD_NAME                5 (zip)
            170 LOAD_NAME                0 (input_list)
            172 LOAD_NAME                2 (key_list)
            174 CALL_FUNCTION            2
            176 GET_ITER
            178 CALL_FUNCTION            1
            180 STORE_NAME               6 (result)

 18         182 LOAD_CONST              39 ('')
            184 LOAD_METHOD              7 (join)
            186 LOAD_NAME                8 (map)
            188 LOAD_NAME                9 (chr)
            190 LOAD_NAME                6 (result)
            192 CALL_FUNCTION            2
            194 CALL_METHOD              1
            196 STORE_NAME              10 (result_text)
            198 LOAD_CONST              40 (None)
            200 RETURN_VALUE

Disassembly of <code object <listcomp> at 0x7f704e8a4d40, file "snake.py", line 9>:
  9           0 BUILD_LIST               0
              2 LOAD_FAST                0 (.0)
        >>    4 FOR_ITER                12 (to 18)
              6 STORE_FAST               1 (char)
              8 LOAD_GLOBAL              0 (ord)
             10 LOAD_FAST                1 (char)
             12 CALL_FUNCTION            1
             14 LIST_APPEND              2
             16 JUMP_ABSOLUTE            4
        >>   18 RETURN_VALUE

Disassembly of <code object <listcomp> at 0x7f704e8a4df0, file "snake.py", line 15>:
 15           0 BUILD_LIST               0
              2 LOAD_FAST                0 (.0)
        >>    4 FOR_ITER                16 (to 22)
              6 UNPACK_SEQUENCE          2
              8 STORE_FAST               1 (a)
             10 STORE_FAST               2 (b)
             12 LOAD_FAST                1 (a)
             14 LOAD_FAST                2 (b)
             16 BINARY_XOR
             18 LIST_APPEND              2
             20 JUMP_ABSOLUTE            4
        >>   22 RETURN_VALUE
  1           0 LOAD_CONST               0 (4)
              2 LOAD_CONST               1 (54)
              4 LOAD_CONST               2 (41)
              6 LOAD_CONST               3 (0)
              8 LOAD_CONST               4 (112)
             10 LOAD_CONST               5 (32)
             12 LOAD_CONST               6 (25)
             14 LOAD_CONST               7 (49)
             16 LOAD_CONST               8 (33)
             18 LOAD_CONST               9 (3)
             20 LOAD_CONST               3 (0)
             22 LOAD_CONST               3 (0)
             24 LOAD_CONST              10 (57)
             26 LOAD_CONST               5 (32)
             28 LOAD_CONST              11 (108)
             30 LOAD_CONST              12 (23)
             32 LOAD_CONST              13 (48)
             34 LOAD_CONST               0 (4)
             36 LOAD_CONST              14 (9)
             38 LOAD_CONST              15 (70)
             40 LOAD_CONST              16 (7)
             42 LOAD_CONST              17 (110)
             44 LOAD_CONST              18 (36)
             46 LOAD_CONST              19 (8)
             48 LOAD_CONST              11 (108)
             50 LOAD_CONST              16 (7)
             52 LOAD_CONST               7 (49)
             54 LOAD_CONST              20 (10)
             56 LOAD_CONST               0 (4)
             58 LOAD_CONST              21 (86)
             60 LOAD_CONST              22 (43)
             62 LOAD_CONST              23 (106)
             64 LOAD_CONST              24 (123)
             66 LOAD_CONST              25 (89)
             68 LOAD_CONST              26 (87)
             70 LOAD_CONST              27 (18)
             72 LOAD_CONST              28 (62)
             74 LOAD_CONST              29 (47)
             76 LOAD_CONST              20 (10)
             78 LOAD_CONST              30 (78)
             80 BUILD_LIST              40
             82 STORE_NAME               0 (input_list)

  2          84 LOAD_CONST              31 ('J')
             86 STORE_NAME               1 (key_str)

  3          88 LOAD_CONST              32 ('_')
             90 LOAD_NAME                1 (key_str)
             92 BINARY_ADD
             94 STORE_NAME               1 (key_str)

  4          96 LOAD_NAME                1 (key_str)
             98 LOAD_CONST              33 ('o')
            100 BINARY_ADD
            102 STORE_NAME               1 (key_str)

  5         104 LOAD_NAME                1 (key_str)
            106 LOAD_CONST              34 ('3')
            108 BINARY_ADD
            110 STORE_NAME               1 (key_str)

  6         112 LOAD_CONST              35 ('t')
            114 LOAD_NAME                1 (key_str)
            116 BINARY_ADD
            118 STORE_NAME               1 (key_str)

  9         120 LOAD_CONST              36 (<code object <listcomp> at 0x7f704e8a4d40, file "snake.py", line 9>)
            122 LOAD_CONST              37 ('<listcomp>')
            124 MAKE_FUNCTION            0
            126 LOAD_NAME                1 (key_str)
            128 GET_ITER
            130 CALL_FUNCTION            1
            132 STORE_NAME               2 (key_list)

 11     >>  134 LOAD_NAME                3 (len)
            136 LOAD_NAME                2 (key_list)
            138 CALL_FUNCTION            1
            140 LOAD_NAME                3 (len)
            142 LOAD_NAME                0 (input_list)
            144 CALL_FUNCTION            1
            146 COMPARE_OP               0 (<)
            148 POP_JUMP_IF_FALSE      162

 12         150 LOAD_NAME                2 (key_list)
            152 LOAD_METHOD              4 (extend)
            154 LOAD_NAME                2 (key_list)
            156 CALL_METHOD              1
            158 POP_TOP
            160 JUMP_ABSOLUTE          134

 15     >>  162 LOAD_CONST              38 (<code object <listcomp> at 0x7f704e8a4df0, file "snake.py", line 15>)
            164 LOAD_CONST              37 ('<listcomp>')
            166 MAKE_FUNCTION            0
            168 LOAD_NAME                5 (zip)
            170 LOAD_NAME                0 (input_list)
            172 LOAD_NAME                2 (key_list)
            174 CALL_FUNCTION            2
            176 GET_ITER
            178 CALL_FUNCTION            1
            180 STORE_NAME               6 (result)

 18         182 LOAD_CONST              39 ('')
            184 LOAD_METHOD              7 (join)
            186 LOAD_NAME                8 (map)
            188 LOAD_NAME                9 (chr)
            190 LOAD_NAME                6 (result)
            192 CALL_FUNCTION            2
            194 CALL_METHOD              1
            196 STORE_NAME              10 (result_text)
            198 LOAD_CONST              40 (None)
            200 RETURN_VALUE

Disassembly of <code object <listcomp> at 0x7f704e8a4d40, file "snake.py", line 9>:
  9           0 BUILD_LIST               0
              2 LOAD_FAST                0 (.0)
        >>    4 FOR_ITER                12 (to 18)
              6 STORE_FAST               1 (char)
              8 LOAD_GLOBAL              0 (ord)
             10 LOAD_FAST                1 (char)
             12 CALL_FUNCTION            1
             14 LIST_APPEND              2
             16 JUMP_ABSOLUTE            4
        >>   18 RETURN_VALUE

Disassembly of <code object <listcomp> at 0x7f704e8a4df0, file "snake.py", line 15>:
 15           0 BUILD_LIST               0
              2 LOAD_FAST                0 (.0)
        >>    4 FOR_ITER                16 (to 22)
              6 UNPACK_SEQUENCE          2
              8 STORE_FAST               1 (a)
             10 STORE_FAST               2 (b)
             12 LOAD_FAST                1 (a)
             14 LOAD_FAST                2 (b)
             16 BINARY_XOR
             18 LIST_APPEND              2
             20 JUMP_ABSOLUTE            4
        >>   22 RETURN_VALUE

```

now break this file into small section

step 1
```css
			  0 LOAD_CONST               0 (4) # Load constants (4, 54, 41, ...) onto the stack
              2 LOAD_CONST               1 (54)
              4 LOAD_CONST               2 (41)
              6 LOAD_CONST               3 (0)
              8 LOAD_CONST               4 (112)
             10 LOAD_CONST               5 (32)
             12 LOAD_CONST               6 (25)
             14 LOAD_CONST               7 (49)
             16 LOAD_CONST               8 (33)
             18 LOAD_CONST               9 (3)
             20 LOAD_CONST               3 (0)
             22 LOAD_CONST               3 (0)
             24 LOAD_CONST              10 (57)
             26 LOAD_CONST               5 (32)
             28 LOAD_CONST              11 (108)
             30 LOAD_CONST              12 (23)
             32 LOAD_CONST              13 (48)
             34 LOAD_CONST               0 (4)
             36 LOAD_CONST              14 (9)
             38 LOAD_CONST              15 (70)
             40 LOAD_CONST              16 (7)
             42 LOAD_CONST              17 (110)
             44 LOAD_CONST              18 (36)
             46 LOAD_CONST              19 (8)
             48 LOAD_CONST              11 (108)
             50 LOAD_CONST              16 (7)
             52 LOAD_CONST               7 (49)
             54 LOAD_CONST              20 (10)
             56 LOAD_CONST               0 (4)
             58 LOAD_CONST              21 (86)
             60 LOAD_CONST              22 (43)
             62 LOAD_CONST              23 (106)
             64 LOAD_CONST              24 (123)
             66 LOAD_CONST              25 (89)
             68 LOAD_CONST              26 (87)
             70 LOAD_CONST              27 (18)
             72 LOAD_CONST              28 (62)
             74 LOAD_CONST              29 (47)
             76 LOAD_CONST              20 (10)
             78 LOAD_CONST              30 (78)
             80 BUILD_LIST              40 # Build a list from 40 constants
             82 STORE_NAME               0 (input_list) # Store the list into the variable `input_list`
```

in python it is written as


```python
# Step 1: Create the input_list
input_list = [
    4, 54, 41, 0, 112, 32, 25, 49, 33, 3, 0, 0,
    57, 32, 108, 23, 48, 4, 9, 70, 7, 110, 36, 8,
    108, 7, 49, 10, 4, 86, 43, 106, 123, 89, 87, 18,
    62, 47, 10, 78
]

# Convert each integer to its corresponding ASCII character and print them
ascii_chars = ''.join([chr(i) for i in input_list])
print(ascii_chars)
```

```css
┌──(kali㉿kali)-[~/Downloads/pico_ctf_lab]
└─$ python3 snakeascii.py
6)p 1!9 l0      Fnl1
V+j{YW>/
N
```

step 2

```css
  2          84 LOAD_CONST              31 ('J')  # Start key_str with 'J'
             86 STORE_NAME               1 (key_str)

  3          88 LOAD_CONST              32 ('_')  # Prepend '_' to key_str
             90 LOAD_NAME                1 (key_str)  # key_str = 'J'
             92 BINARY_ADD                      # key_str = '_' + key_str
             94 STORE_NAME               1 (key_str)  # key_str = '_J'

  4          96 LOAD_NAME                1 (key_str)  
             98 LOAD_CONST              33 ('o')  # Prepend 'o' to key_str
            100 BINARY_ADD                      # key_str =  key_str  + 'o' 
            102 STORE_NAME               1 (key_str)  # key_str = '_Jo'

  5         104 LOAD_NAME                1 (key_str)  
            106 LOAD_CONST              34 ('3')  # Prepend '3' to key_str
            108 BINARY_ADD                      # key_str =  key_str + '3'
            110 STORE_NAME               1 (key_str)  # key_str = '_Jo3'

  6         112 LOAD_CONST              35 ('t')  # Prepend 't' to key_str
            114 LOAD_NAME                1 (key_str)
            116 BINARY_ADD                      # key_str = 't' + key_str
            118 STORE_NAME               1 (key_str)  # Final key_str = 't_Jo3'


```

```css
  9         120 LOAD_CONST              36 (<code object <listcomp> at 0x7f704e8a4d40, file "snake.py", line 9>)
            122 LOAD_CONST              37 ('<listcomp>')
            124 MAKE_FUNCTION            0
            126 LOAD_NAME                1 (key_str)  # key_str = 'to_J3'
            128 GET_ITER
            130 CALL_FUNCTION            1
            132 STORE_NAME               2 (key_list)

```

```python
# Step 1: Create the input_list
input_list = [
    4, 54, 41, 0, 112, 32, 25, 49, 33, 3, 0, 0,
    57, 32, 108, 23, 48, 4, 9, 70, 7, 110, 36, 8,
    108, 7, 49, 10, 4, 86, 43, 106, 123, 89, 87, 18,
    62, 47, 10, 78
]

# Convert each integer to its corresponding ASCII character and print them
ascii_chars = ''.join([chr(i) for i in input_list])
print(ascii_chars)

# Step 2: Construct the key_str
key_str = "J"           #     "J"
key_str = "_" + key_str #     "_J"
key_str = key_str + "o" #     "_Jo"
key_str = key_str + "3" #     "_Jo3"
key_str = "t" + key_str #     "t_Jo3"

print("Key string:", key_str)
```

output

```css
┌──(kali㉿kali)-[~/Downloads/pico_ctf_lab]
└─$ python3 snakeascii.py
6)p 1!9 l0      Fnl1
V+j{YW>/
N
Key string: t_Jo3
```

step 3 print order

```css
Disassembly of <code object <listcomp> at 0x7f704e8a4d40, file "snake.py", line 9>:
  9           0 BUILD_LIST               0
              2 LOAD_FAST                0 (.0)
        >>    4 FOR_ITER                12 (to 18)
              6 STORE_FAST               1 (char)
              8 LOAD_GLOBAL              0 (ord)  # Apply ord()
             10 LOAD_FAST                1 (char)  # to each char
             12 CALL_FUNCTION            1
             14 LIST_APPEND              2  # Append result to the list
             16 JUMP_ABSOLUTE            4
        >>   18 RETURN_VALUE

```

now to print order list

```python
# Step 1: Create the input_list
input_list = [
    4, 54, 41, 0, 112, 32, 25, 49, 33, 3, 0, 0,
    57, 32, 108, 23, 48, 4, 9, 70, 7, 110, 36, 8,
    108, 7, 49, 10, 4, 86, 43, 106, 123, 89, 87, 18,
    62, 47, 10, 78
]

# Convert each integer to its corresponding ASCII character and print them
ascii_chars = ''.join([chr(i) for i in input_list])
print(ascii_chars)

# Step 2: Construct the key_str
key_str = "J"           #     "J"
key_str = "_" + key_str #     "_J"
key_str = key_str + "o" #     "_Jo"
key_str = key_str + "3" #     "_Jo3"
key_str = "t" + key_str #     "t_Jo3"

# Step 3: Create the key_list based on the key_str
key_list = [ord(char) for char in key_str]

print("Key string:", key_str)
print("Order list:", key_list)
```

output

```css
┌──(kali㉿kali)-[~/Downloads/pico_ctf_lab]
└─$ python3 snakeascii.py
6)p 1!9 l0      Fnl1
V+j{YW>/
N
Key string: t_Jo3
Order list: [116, 95, 74, 111, 51]
```

step 4
This section compares the length of `key_list` with `input_list`. If `key_list` is shorter, it extends itself by repeating the same values until its length matches `input_list`.

```css
 11     >>  134 LOAD_NAME                3 (len)   # Get length of `key_list`
            136 LOAD_NAME                2 (key_list)
            138 CALL_FUNCTION            1

            140 LOAD_NAME                3 (len)   # Get length of `input_list`
            142 LOAD_NAME                0 (input_list)
            144 CALL_FUNCTION            1

            146 COMPARE_OP               0 (<)     # Compare len(key_list) < len(input_list)
            148 POP_JUMP_IF_FALSE      162         # If false, jump to line 162

 12         150 LOAD_NAME                2 (key_list)  
            152 LOAD_METHOD              4 (extend)  # Extend key_list by appending itself
            154 LOAD_NAME                2 (key_list)
            156 CALL_METHOD              1           # Repeat until key_list matches input_list length
            160 JUMP_ABSOLUTE          134           # Loop until length condition is met

```

```python
# Step 1: Create the input_list
input_list = [
    4, 54, 41, 0, 112, 32, 25, 49, 33, 3, 0, 0,
    57, 32, 108, 23, 48, 4, 9, 70, 7, 110, 36, 8,
    108, 7, 49, 10, 4, 86, 43, 106, 123, 89, 87, 18,
    62, 47, 10, 78
]

# Convert each integer to its corresponding ASCII character and print them
ascii_chars = ''.join([chr(i) for i in input_list])
print(ascii_chars)

# Step 2: Construct the key_str
key_str = "J"           #     "J"
key_str = "_" + key_str #     "_J"
key_str = key_str + "o" #     "_Jo"
key_str = key_str + "3" #     "_Jo3"
key_str = "t" + key_str #     "t_Jo3"

# Step 3: Create the key_list based on the key_str
key_list = [ord(char) for char in key_str]

print("Key string:", key_str)
print("Order list:", key_list)

# Step 4: Extend key_list if necessary (in this case, not required)
while len(key_list) < len(input_list):
    key_list.extend(key_list)
    print(key_list)
print(len(key_list))
```

output

```css
┌──(kali㉿kali)-[~/Downloads/pico_ctf_lab]
└─$ python3 snakeascii.py
6)p 1!9 l0      Fnl1
V+j{YW>/
N
Key string: t_Jo3
Order list: [116, 95, 74, 111, 51]
[116, 95, 74, 111, 51, 116, 95, 74, 111, 51]
[116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51]
[116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51]
40
```

step 5

XOR Operation with `zip()` (lines 162-180)

Now, the code performs an XOR operation between corresponding elements of `input_list` and `key_list`.

```css
 15         162 LOAD_CONST              38 (<code object <listcomp>>)  # Another list comprehension
            164 LOAD_CONST              37 ('<listcomp>')  
            166 MAKE_FUNCTION            0
            168 LOAD_NAME                5 (zip)    # Zip the input_list and key_list together
            170 LOAD_NAME                0 (input_list)  
            172 LOAD_NAME                2 (key_list)  
            174 CALL_FUNCTION            2
            176 GET_ITER
            178 CALL_FUNCTION            1          # Apply XOR (a ^ b for each pair from input_list, key_list)
            180 STORE_NAME               6 (result)  # Store result of XOR operation in `result`

```

```python
# Step 1: Create the input_list
input_list = [
    4, 54, 41, 0, 112, 32, 25, 49, 33, 3, 0, 0,
    57, 32, 108, 23, 48, 4, 9, 70, 7, 110, 36, 8,
    108, 7, 49, 10, 4, 86, 43, 106, 123, 89, 87, 18,
    62, 47, 10, 78
]

# Convert each integer to its corresponding ASCII character and print them
ascii_chars = ''.join([chr(i) for i in input_list])
print(ascii_chars)

# Step 2: Construct the key_str
key_str = "J"           #     "J"
key_str = "_" + key_str #     "_J"
key_str = key_str + "o" #     "_Jo"
key_str = key_str + "3" #     "_Jo3"
key_str = "t" + key_str #     "t_Jo3"

# Step 3: Create the key_list based on the key_str
key_list = [ord(char) for char in key_str]

print("Key string:", key_str)
print("Order list:", key_list)

# Step 4: Extend key_list if necessary (in this case, not required)
while len(key_list) < len(input_list):
    key_list.extend(key_list)
    print(key_list)
print(len(key_list))

# Step 5: Generate the result using zip and XOR operation
result = [a^b for a,b in zip(input_list, key_list)]
print(result)
```

output

```css
┌──(kali㉿kali)-[~/Downloads/pico_ctf_lab]
└─$ python3 snakeascii.py
6)p 1!9 l0      Fnl1
V+j{YW>/
N
Key string: t_Jo3
Order list: [116, 95, 74, 111, 51]
[116, 95, 74, 111, 51, 116, 95, 74, 111, 51]
[116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51]
[116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51]
40
[112, 105, 99, 111, 67, 84, 70, 123, 78, 48, 116, 95, 115, 79, 95, 99, 111, 78, 102, 117, 115, 49, 110, 103, 95, 115, 110, 64, 107, 101, 95, 53, 49, 54, 100, 102, 97, 101, 101, 125]   
```

step 6
Finally, the result from the XOR operation is transformed into a string by converting each number back to its corresponding ASCII character using chr()

```css
 18         182 LOAD_CONST              39 ('')    # Start with an empty string
            184 LOAD_METHOD              7 (join)  # Prepare to join the characters into a string
            186 LOAD_NAME                8 (map)   # Use map() with chr() to convert each number to a character
            188 LOAD_NAME                9 (chr)
            190 LOAD_NAME                6 (result)
            192 CALL_FUNCTION            2
            194 CALL_METHOD              1         # Join all characters
            196 STORE_NAME              10 (result_text)  # Store final result as `result_text`

```


```python
# Step 1: Create the input_list
input_list = [
    4, 54, 41, 0, 112, 32, 25, 49, 33, 3, 0, 0,
    57, 32, 108, 23, 48, 4, 9, 70, 7, 110, 36, 8,
    108, 7, 49, 10, 4, 86, 43, 106, 123, 89, 87, 18,
    62, 47, 10, 78
]

# Convert each integer to its corresponding ASCII character and print them
ascii_chars = ''.join([chr(i) for i in input_list])
print(ascii_chars)

# Step 2: Construct the key_str
key_str = "J"           #     "J"
key_str = "_" + key_str #     "_J"
key_str = key_str + "o" #     "_Jo"
key_str = key_str + "3" #     "_Jo3"
key_str = "t" + key_str #     "t_Jo3"

# Step 3: Create the key_list based on the key_str
key_list = [ord(char) for char in key_str]

print("Key string:", key_str)
print("Order list:", key_list)

# Step 4: Extend key_list if necessary (in this case, not required)
while len(key_list) < len(input_list):
    key_list.extend(key_list)
    print(key_list)
print(len(key_list))

# Step 5: Generate the result using zip and XOR operation
result = [a^b for a,b in zip(input_list, key_list)]
print(result)

# Step 6: Convert result to a string
result_text = ''.join(map(chr,result))
print(result_text)
```

output

```css
┌──(kali㉿kali)-[~/Downloads/pico_ctf_lab]
└─$ python3 snakeascii.py
6)p 1!9 l0      Fnl1
V+j{YW>/
N
Key string: t_Jo3
Order list: [116, 95, 74, 111, 51]
[116, 95, 74, 111, 51, 116, 95, 74, 111, 51]
[116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51]
[116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51, 116, 95, 74, 111, 51]
40
[112, 105, 99, 111, 67, 84, 70, 123, 78, 48, 116, 95, 115, 79, 95, 99, 111, 78, 102, 117, 115, 49, 110, 103, 95, 115, 110, 64, 107, 101, 95, 53, 49, 54, 100, 102, 97, 101, 101, 125]
picoCTF{N0t_sO_coNfus1ng_sn@ke_516dfaee}
```