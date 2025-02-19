### FactCheck

#Medium #Reverse_Engineering #picoCTF2024 #browserwebshell 

Author: Junias Bonou
#### Description

This binary is putting together some important piece of information... Can you uncover that information? Examine this [file](https://artifacts.picoctf.net/c_titan/187/bin). Do you understand its inner workings?

##### Solution:
use ghidra to disassemble the code

here is main file code

```cpp
/* WARNING: Removing unreachable block (ram,0x0010170c) */

undefined8 main(void)

{
  char cVar1;
  char *pcVar2;
  long in_FS_OFFSET;
  allocator local_249;
  string local_248 [32];
  string local_228 [32];
  string local_208 [32];
  string local_1e8 [32];
  string local_1c8 [32];
  string local_1a8 [32];
  string local_188 [32];
  string local_168 [32];
  string local_148 [32];
  string local_128 [32];
  string local_108 [32];
  string local_e8 [32];
  string local_c8 [32];
  string local_a8 [32];
  string local_88 [32];
  string local_68 [32];
  string local_48 [40];
  long local_20;
  
  local_20 = *(long *)(in_FS_OFFSET + 0x28);
  std::allocator<char>::allocator();
                    /* try { // try from 001012cf to 001012d3 has its CatchHandler @ 00101975 */
  std::string::string(local_248,"picoCTF{wELF_d0N3_mate_",&local_249);
  std::allocator<char>::~allocator((allocator<char> *)&local_249);
  std::allocator<char>::allocator();
                    /* try { // try from 0010130a to 0010130e has its CatchHandler @ 00101996 */
  std::string::string(local_228,"0",&local_249);
  std::allocator<char>::~allocator((allocator<char> *)&local_249);
  std::allocator<char>::allocator();
                    /* try { // try from 00101345 to 00101349 has its CatchHandler @ 001019b1 */
  std::string::string(local_208,"5",&local_249);
  std::allocator<char>::~allocator((allocator<char> *)&local_249);
  std::allocator<char>::allocator();
                    /* try { // try from 00101380 to 00101384 has its CatchHandler @ 001019cc */
  std::string::string(local_1e8,"d",&local_249);
  std::allocator<char>::~allocator((allocator<char> *)&local_249);
  std::allocator<char>::allocator();
                    /* try { // try from 001013bb to 001013bf has its CatchHandler @ 001019e7 */
  std::string::string(local_1c8,"3",&local_249);
  std::allocator<char>::~allocator((allocator<char> *)&local_249);
  std::allocator<char>::allocator();
                    /* try { // try from 001013f6 to 001013fa has its CatchHandler @ 00101a02 */
  std::string::string(local_1a8,"2",&local_249);
  std::allocator<char>::~allocator((allocator<char> *)&local_249);
  std::allocator<char>::allocator();
                    /* try { // try from 00101431 to 00101435 has its CatchHandler @ 00101a1d */
  std::string::string(local_188,"a",&local_249);
  std::allocator<char>::~allocator((allocator<char> *)&local_249);
  std::allocator<char>::allocator();
                    /* try { // try from 0010146c to 00101470 has its CatchHandler @ 00101a38 */
  std::string::string(local_168,"a",&local_249);
  std::allocator<char>::~allocator((allocator<char> *)&local_249);
  std::allocator<char>::allocator();
                    /* try { // try from 001014a7 to 001014ab has its CatchHandler @ 00101a53 */
  std::string::string(local_148,"e",&local_249);
  std::allocator<char>::~allocator((allocator<char> *)&local_249);
  std::allocator<char>::allocator();
                    /* try { // try from 001014e2 to 001014e6 has its CatchHandler @ 00101a6e */
  std::string::string(local_128,"e",&local_249);
  std::allocator<char>::~allocator((allocator<char> *)&local_249);
  std::allocator<char>::allocator();
                    /* try { // try from 0010151d to 00101521 has its CatchHandler @ 00101a89 */
  std::string::string(local_108,"d",&local_249);
  std::allocator<char>::~allocator((allocator<char> *)&local_249);
  std::allocator<char>::allocator();
                    /* try { // try from 00101558 to 0010155c has its CatchHandler @ 00101aa4 */
  std::string::string(local_e8,"b",&local_249);
  std::allocator<char>::~allocator((allocator<char> *)&local_249);
  std::allocator<char>::allocator();
                    /* try { // try from 00101593 to 00101597 has its CatchHandler @ 00101abf */
  std::string::string(local_c8,"e",&local_249);
  std::allocator<char>::~allocator((allocator<char> *)&local_249);
  std::allocator<char>::allocator();
                    /* try { // try from 001015ce to 001015d2 has its CatchHandler @ 00101ada */
  std::string::string(local_a8,"6",&local_249);
  std::allocator<char>::~allocator((allocator<char> *)&local_249);
  std::allocator<char>::allocator();
                    /* try { // try from 00101606 to 0010160a has its CatchHandler @ 00101af5 */
  std::string::string(local_88,"c",&local_249);
  std::allocator<char>::~allocator((allocator<char> *)&local_249);
  std::allocator<char>::allocator();
                    /* try { // try from 0010163e to 00101642 has its CatchHandler @ 00101b0d */
  std::string::string(local_68,"9",&local_249);
  std::allocator<char>::~allocator((allocator<char> *)&local_249);
  std::allocator<char>::allocator();
                    /* try { // try from 00101676 to 0010167a has its CatchHandler @ 00101b25 */
  std::string::string(local_48,"8",&local_249);
  std::allocator<char>::~allocator((allocator<char> *)&local_249);
                    /* try { // try from 00101699 to 0010185f has its CatchHandler @ 00101b3d */
  pcVar2 = (char *)std::string::operator[]((ulong)local_208);
  if (*pcVar2 < 'B') {
    std::string::operator+=(local_248,local_c8);
  }
  pcVar2 = (char *)std::string::operator[]((ulong)local_a8);
  if (*pcVar2 != 'A') {
    std::string::operator+=(local_248,local_68);
  }
  pcVar2 = (char *)std::string::operator[]((ulong)local_1c8);
  cVar1 = *pcVar2;
  pcVar2 = (char *)std::string::operator[]((ulong)local_148);
  if ((int)cVar1 - (int)*pcVar2 == 3) {
    std::string::operator+=(local_248,local_1c8);
  }
  std::string::operator+=(local_248,local_1e8);
  std::string::operator+=(local_248,local_188);
  pcVar2 = (char *)std::string::operator[]((ulong)local_168);
  if (*pcVar2 == 'G') {
    std::string::operator+=(local_248,local_168);
  }
  std::string::operator+=(local_248,local_1a8);
  std::string::operator+=(local_248,local_88);
  std::string::operator+=(local_248,local_228);
  std::string::operator+=(local_248,local_128);
  std::string::operator+=(local_248,'}');
  std::string::~string(local_48);
  std::string::~string(local_68);
  std::string::~string(local_88);
  std::string::~string(local_a8);
  std::string::~string(local_c8);
  std::string::~string(local_e8);
  std::string::~string(local_108);
  std::string::~string(local_128);
  std::string::~string(local_148);
  std::string::~string(local_168);
  std::string::~string(local_188);
  std::string::~string(local_1a8);
  std::string::~string(local_1c8);
  std::string::~string(local_1e8);
  std::string::~string(local_208);
  std::string::~string(local_228);
  std::string::~string(local_248);
  if (local_20 == *(long *)(in_FS_OFFSET + 0x28)) {
    return 0;
  }
                    /* WARNING: Subroutine does not return */
  __stack_chk_fail();
}
```

flag is `picoCTF{wELF_d0N3_mate_` which is not completed 
so lets break the code into steps

## step 1
```css
std::string::string(local_248,"picoCTF{wELF_d0N3_mate_",&local_249);
std::string::string(local_228,"0",&local_249);
std::string::string(local_208,"5",&local_249);
std::string::string(local_1e8,"d",&local_249);
std::string::string(local_1c8,"3",&local_249);
std::string::string(local_1a8,"2",&local_249);
std::string::string(local_188,"a",&local_249);
std::string::string(local_168,"a",&local_249);
std::string::string(local_148,"e",&local_249);
std::string::string(local_128,"e",&local_249);
std::string::string(local_108,"d",&local_249);
std::string::string(local_e8,"b",&local_249);
std::string::string(local_c8,"e",&local_249);
std::string::string(local_a8,"6",&local_249);
std::string::string(local_88,"c",&local_249);
std::string::string(local_68,"9",&local_249);
std::string::string(local_48,"8",&local_249);
```

convert the 0 , 5 , d .... 8 to ASCII code

here python code
```python
characters = ['0', '5', 'd', '3', '2', 'a', 'a', 'e', 'e', 'd', 'b', 'e', '6', 'c', '9', '8']
ascii_values = [ord(c) for c in characters]
print(ascii_values)
# output [48, 53, 100, 51, 50, 97, 97, 101, 101, 100, 98, 101, 54, 99, 57, 56]
```

Hexadecimal to ASCII Values 
- **Hex**: ['0', '5', 'd', '3', '2', 'a', 'a', 'e', 'e', 'd', 'b', 'e', '6', 'c', '9', '8'] 
- **ASCII**: [48, 53, 100, 51, 50, 97, 97, 101, 101, 100, 98, 101, 54, 99, 57, 56]

## step 2
these are condition in code
```css
``cpp
pcVar2 = (char *)std::string::operator[]((ulong)local_208);
if (*pcVar2 < 'B') {
    std::string::operator+=(local_248, local_c8);
}
pcVar2 = (char *)std::string::operator[]((ulong)local_a8);
if (*pcVar2 != 'A') {
    std::string::operator+=(local_248, local_68);
}
pcVar2 = (char *)std::string::operator[]((ulong)local_1c8);
cVar1 = *pcVar2;
pcVar2 = (char *)std::string::operator[]((ulong)local_148);
if ((int)cVar1 - (int)*pcVar2 == 3) {
    std::string::operator+=(local_248, local_1c8);
}
std::string::operator+=(local_248, local_1e8);
std::string::operator+=(local_248, local_188);
pcVar2 = (char *)std::string::operator[]((ulong)local_168);
if (*pcVar2 == 'G') {
    std::string::operator+=(local_248, local_168);
}
std::string::operator+=(local_248, local_1a8);
std::string::operator+=(local_248, local_88);
std::string::operator+=(local_248, local_228);
std::string::operator+=(local_248, local_128);
std::string::operator+=(local_248, '}');

```

flag is

```css
local_248 = "picoCTF{wELF_d0N3_mate_"
```

Condition Checks

First Check:

```cpp
pcVar2 = (char *)std::string::operator[]((ulong)local_208); // "5"
if (*pcVar2 < 'B') {
    std::string::operator+=(local_248, local_c8); // "e"
}
```

    "5" < 'B' is true, so we append local_c8 ("e") to local_248.
    ascii value 54 < 66 => true

```css
Append local_c8 ("e"):
"picoCTF{wELF_d0N3_mate_e"
```

Second Check:

```cpp
pcVar2 = (char *)std::string::operator[]((ulong)local_a8); // "6"
if (*pcVar2 != 'A') {
    std::string::operator+=(local_248, local_68); // "9"
}
```

    "6" != 'A' is true, so we append local_68 ("9") to local_248.
    ascii value 55 != 65 => true

```css
Append local_68 ("9"):
"picoCTF{wELF_d0N3_mate_e9"
```

Third Check:

```cpp
pcVar2 = (char *)std::string::operator[]((ulong)local_1c8); // "3"
cVar1 = *pcVar2; // cVar1 = "3"
pcVar2 = (char *)std::string::operator[]((ulong)local_148); // "e"
if ((int)cVar1 - (int)*pcVar2 == 3) {
    std::string::operator+=(local_248, local_1c8); // "3"
}
```

    The difference check is ('3' - 'e'), which is 51 - 101 = -50. This condition is false, so nothing is appended.
    ascii value -50 == 101 => false
	flag will be same no change because condition failed

```css
"picoCTF{wELF_d0N3_mate_e9"
```
Appending Strings:

```cpp
std::string::operator+=(local_248, local_1e8); // "d"
std::string::operator+=(local_248, local_188); // "a"
```

    Append local_1e8 ("d") to local_248.
    Append local_188 ("a") to local_248.
	directly add the alphabet to the flag 

```css
Append local_1e8 ("d"):
"picoCTF{wELF_d0N3_mate_e9d"

Append local_188 ("a"):
"picoCTF{wELF_d0N3_mate_e9da"
```

Fourth Check:

```cpp
pcVar2 = (char *)std::string::operator[]((ulong)local_168); // "a"
if (*pcVar2 == 'G') {
    std::string::operator+=(local_248, local_168); // "a"
}
```

    Since "a" != 'G', this condition is false, so nothing is appended.
    ascii value 101 == 71 => false
	condition failed so flag remain same
	
```css
"picoCTF{wELF_d0N3_mate_e9da"
```

Final Appendings:

```cpp
 std::string::operator+=(local_248, local_1a8); // "2"
    std::string::operator+=(local_248, local_88); // "c"
    std::string::operator+=(local_248, local_228); // "0"
    std::string::operator+=(local_248, local_128); // "e"
    std::string::operator+=(local_248, '}'); // '}'
```


```css
Append local_1a8 ("2"):
"picoCTF{wELF_d0N3_mate_e9da2"

Append local_88 ("c"):
"picoCTF{wELF_d0N3_mate_e9da2c"

Append local_228 ("0"):
"picoCTF{wELF_d0N3_mate_e9da2c0"

Append local_128 ("e"):
"picoCTF{wELF_d0N3_mate_e9da2c0e"

Append }:
"picoCTF{wELF_d0N3_mate_e9da2c05}"

Final Flag

The constructed flag is:

picoCTF{wELF_d0N3_mate_e9da2c0e}

