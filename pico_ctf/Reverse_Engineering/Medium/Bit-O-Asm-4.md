### Bit-O-Asm-4

#Medium #Reverse_Engineering #picoGym #Exclusive #x86_64

Author: LT 'syreal' Jones

#### Description

Can you figure out what is in the `eax` register? Put your answer in the picoCTF flag format: `picoCTF{n}` where `n` is the contents of the `eax` register in the decimal number base. If the answer was `0x11` your flag would be `picoCTF{17}`.Download the assembly dump [here](https://artifacts.picoctf.net/c/511/disassembler-dump0_d.txt).

##### Solution:
```css
<+0>:     endbr64 
<+4>:     push   rbp
<+5>:     mov    rbp,rsp
<+8>:     mov    DWORD PTR [rbp-0x14],edi
<+11>:    mov    QWORD PTR [rbp-0x20],rsi
<+15>:    mov    DWORD PTR [rbp-0x4],0x9fe1a
<+22>:    cmp    DWORD PTR [rbp-0x4],0x2710
<+29>:    jle    0x55555555514e <main+37>
<+31>:    sub    DWORD PTR [rbp-0x4],0x65
<+35>:    jmp    0x555555555152 <main+41>
<+37>:    add    DWORD PTR [rbp-0x4],0x65
<+41>:    mov    eax,DWORD PTR [rbp-0x4]
<+44>:    pop    rbp
<+45>:    ret

```

```css
1. Read from bottom to top to remove every line not related with eax

2. Read from top to bottom to “translate” the instructions

After step 1, you have the following instructions left;

<+15>: mov DWORD PTR [rbp-0x4],0x9fe1a  
<+22>: cmp DWORD PTR [rbp-0x4],0x2710  
<+29>: jle 0x55555555514e <main+37>  
<+31>: sub DWORD PTR [rbp-0x4],0x65  
<+35>: jmp 0x555555555152 <main+41>  
<+37>: add DWORD PTR [rbp-0x4],0x65  
<+41>: mov eax,DWORD PTR [rbp-0x4]

Mov instruction is putting the value on the right of the comma inside the left, you can write it in an other way ;

DWORD PTR [rbp-0x4] = 0x9fe1a

We treat the register position as if it were a variable in a programming language.

You need to analyze lines +22 and +29 together. First, we compare and then, depending of the result we are jumping to another line (instruction on +29 is to jump to line 37).

If we translate;

Is DWORD PTR [rbp-0x4] less than or equal to 0x2710 ?

note: JL - Jump If Less, 
note: JLE - Jump If Less or Equal

No ! We already know the value of DWORD PTR [rbp-0x4], which is 0x9fe1a.

We do nothing with lines +22 and +29.

On line +31, we use the sub instruction to subtract a value from the left of the comma. We can write ;

DWORD PTR [rbp-0x4] = 0x9fe1a — 0x65

Line +35, you have a jmp instruction, it’s a jump instruction to go the line +41. This is not a conditional jump as we saw earlier.

Line +41 is a mov instruction like the first one we translated;

eax = DWORD PTR [rbp-0x4] = 0x9fe1a — 0x65

or

eax = 0x9fe1a — 0x65

You have to “translate” the values from hexadecimal to decimal, do the calculations on put the result on the picoCTF{} format.

```

```python
>>> print(int(0x9fe1a - 0x65))
654773
```

flag is `picoCTF{654773}`