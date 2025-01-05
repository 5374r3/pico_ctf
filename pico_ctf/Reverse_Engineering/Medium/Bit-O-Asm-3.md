### Bit-O-Asm-3

#Medium #Reverse_Engineering #picoGym Exclusive #x86_64

Author: LT 'syreal' Jones

#### Description

Can you figure out what is in the `eax` register? Put your answer in the picoCTF flag format: `picoCTF{n}` where `n` is the contents of the `eax` register in the decimal number base. If the answer was `0x11` your flag would be `picoCTF{17}`.Download the assembly dump [here](https://artifacts.picoctf.net/c/530/disassembler-dump0_c.txt).

##### Solution:
```css
<+0>:     endbr64 
<+4>:     push   rbp
<+5>:     mov    rbp,rsp
<+8>:     mov    DWORD PTR [rbp-0x14],edi
<+11>:    mov    QWORD PTR [rbp-0x20],rsi
<+15>:    mov    DWORD PTR [rbp-0xc],0x9fe1a
<+22>:    mov    DWORD PTR [rbp-0x8],0x4
<+29>:    mov    eax,DWORD PTR [rbp-0xc]
<+32>:    imul   eax,DWORD PTR [rbp-0x8]
<+36>:    add    eax,0x1f5
<+41>:    mov    DWORD PTR [rbp-0x4],eax
<+44>:    mov    eax,DWORD PTR [rbp-0x4]
<+47>:    pop    rbp
<+48>:    ret
```

```css
This instructions are assembly code (x86), they are in interactions with the registers on your CPU. Most of the time you obtain assembly code when you try to debug with GDB or when you try to reverse a software/malware.

How do you read assembly ?

Apart from the first line, you have three elements (not real names, but simplify);

<line number> <instruction> <elements>

<instruction> we will see mov, imul and add  
<elements> the instruction manipulates some elements

Here my methodology to solve this problem;

1. Read it from the bottom to the top of the instructions to remove every line not in connection with eax

2. Read from the top to the bottom to “translate” the instructions

After step 1, you finished with the following instructions;

<+15>: mov DWORD PTR [rbp-0xc],0x9fe1a  
<+22>: mov DWORD PTR [rbp-0x8],0x4  
<+29>: mov eax,DWORD PTR [rbp-0xc]  
<+32>: imul eax,DWORD PTR [rbp-0x8]  
<+36>: add eax,0x1f5  
<+41>: mov DWORD PTR [rbp-0x4],eax  
<+44>: mov eax,DWORD PTR [rbp-0x4]

Mov instruction is used to put the value on the right to the left. The first two instructions can be translated as the following;

DWORD PTR [rbp-0xc] = 0x9fe1a  
DWORD PTR [rbp-0x8] = 0x4

You can consider DWORD PTR [rbp-0xc] and DWORD PTR [rbp-0x8] and eax as variables.

On the third line we put the value of DWORD PTR [rbp-0xc] into eax. In other word ;

eax = DWORD PTR [rbp-0xc] = 0x9fe1a  
eax = 0x9fe1a

On line +32, we used the imul instruction for multiplication, the result is conserved in the element on the left (called destination)

We already know the value of DWORD PTR [rbp-0x8] so if we simplify as a mathematic formula;

eax = 0x9fe1a * DWORD PTR [rbp-0x8]  
which gives us  
eax = 0x9fe1a * 0x4

On line +36, we used the add instruction for addition. As imul, the result is conserved in the element on the left.

eax = (0x9fe1a * 0x4) + 0x1f5

The tricky part

<+41>: mov DWORD PTR [rbp-0x4],eax  
DWORD PTR [rbp-0x4] = eax = (0x9fe1a * 0x4) + 0x1f5
<+44>: mov eax,DWORD PTR [rbp-0x4]
eax = DWORD PTR [rbp-0x4] = (0x9fe1a * 0x4) + 0x1f5
Those two lines are here just to confuse you !

As we saw earlier, mov instruction is used to put the value from one position to another.  
On line 41 => we put the value of eax in DWORD PTR [rbp-0x4]  
On line 44 => we put the of DWORD PTR [rbp-0x4] in eax…..so the value of eax is still the same at the end of the operation

eax = (0x9fe1a * 0x4) + 0x1f5

Now, you have to translate hexadecimal codes in decimal then put the result inside the picoCTF flag format ; picoCTF{<your_answer_here>}
```

```python
┌─[✔]──[alpha@speed:🍓]──[~]:
└──╼ $ python3
Python 3.10.12 (main, Nov  6 2024, 20:22:13) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> print(int((0x9fe1a * 0x4) + 0x1f5))
2619997
>>> 
```

flag is `picoCTF{2619997}`