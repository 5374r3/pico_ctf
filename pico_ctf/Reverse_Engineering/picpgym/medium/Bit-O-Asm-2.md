### Bit-O-Asm-2

#Medium #Reverse_Engineering #picoGym #Exclusive #x86_64

Author: LT 'syreal' Jones

#### Description

Can you figure out what is in the `eax` register? Put your answer in the picoCTF flag format: `picoCTF{n}` where `n` is the contents of the `eax` register in the decimal number base. If the answer was `0x11` your flag would be `picoCTF{17}`.Download the assembly dump [here](https://artifacts.picoctf.net/c/510/disassembler-dump0_b.txt).

##### Solution:
#### The Assembly Code:

```css
<+0>:     endbr64 
<+4>:     push   rbp
<+5>:     mov    rbp,rsp
<+8>:     mov    DWORD PTR [rbp-0x14],edi
<+11>:    mov    QWORD PTR [rbp-0x20],rsi
<+15>:    mov    DWORD PTR [rbp-0x4],0x9fe1a
<+22>:    mov    eax,DWORD PTR [rbp-0x4]
<+25>:    pop    rbp
<+26>:    ret

```

#### [Bit-O-Asm-2](#Assembly-Breakdown) Assembly Breakdown:

`<+0>: endbr64`

- This line signifies the ending of a 64-bit branch, added by Intel to protect against attacks

`<+4>: push rbp`

- In this line, we push the base pointer register to the internal stack

`<+5>: mov rbp,rsp`

- Here, we move the stack pointer register (rsp) into the base pointer register (rbp)

`<+8>: mov DWORD PTR [rbp-0x14],edi`

- DWORD PTR signifies our target operand is 32 bits, and we store the value of the edi register into the base pointer (subtracted by decimal 20 (=> using python3 => print(int(0x14))) )
- A DWORD, or double word, is a 32-bit integer that is typically made up of four bytes:

`<+11>: mov QWORD PTR [rbp-0x20],rsi`

- QWORD PTR signifies our target operand is 64 bits, and we store the value within rsi into the base pointer, this time subtracted by decimal 32 (=> using python3 => print(int(0x20)))
- QWORD or quad word is a 64-bit integer hat is typically made up of eight bytes:

`<+15>: mov DWORD PTR [rbp-0x4],0x9fe1a`

- Again, we store our 32 bit value 654874 (decimal 654874 => using python3 => print(int(0x9fe1a)) ) in the base pointer subtracted by 4

`<+22>: mov eax,DWORD PTR [rbp-0x4]`

- Here is the crux of the program, as we have to figure out what the value stored in eax is 
- We can see from the line previous that the value being inserted into eax is the value 0x9fe1a, which in decimal is 654874.

`<+25>: pop rbp`

- This pops the value stored in the base pointer

`<+26>: ret`

- This simply returns and finishes the program

conclusion

For the purposed of this CTF, we ignore most of the beginning lines until we reach line <+15> when 0x9fe1a is passed into the base pointer register. At line <+22>, we move this value from the base pointer at this address into eax, and we have found our value stored in eax. At this point, we convert 0x9fe1a into decimal, and find that it represents the number 654874. Now, we can put it in the PicoCTF syntax as `PicoCTF{654874}`, and we have successfully solved the challenge!