### ASCII FTW

#Medium #Reverse_Engineering #picoGym #Exclusive

Author: Abhishek Agarwal

#### Description

This program has constructed the flag using hex ascii values. Identify the flag text by disassembling the program.You can download the file from [here](https://artifacts.picoctf.net/c/506/asciiftw).

##### Solution:
using ghidra 

```css
        00101184 c6 45 d0 70     MOV        byte ptr [RBP + local_38],0x70
        00101188 c6 45 d1 69     MOV        byte ptr [RBP + local_37],0x69
        0010118c c6 45 d2 63     MOV        byte ptr [RBP + local_36],0x63
        00101190 c6 45 d3 6f     MOV        byte ptr [RBP + local_35],0x6f
        00101194 c6 45 d4 43     MOV        byte ptr [RBP + local_34],0x43
        00101198 c6 45 d5 54     MOV        byte ptr [RBP + local_33],0x54
        0010119c c6 45 d6 46     MOV        byte ptr [RBP + local_32],0x46
        001011a0 c6 45 d7 7b     MOV        byte ptr [RBP + local_31],0x7b
        001011a4 c6 45 d8 41     MOV        byte ptr [RBP + local_30],0x41
        001011a8 c6 45 d9 53     MOV        byte ptr [RBP + local_2f],0x53
        001011ac c6 45 da 43     MOV        byte ptr [RBP + local_2e],0x43
        001011b0 c6 45 db 49     MOV        byte ptr [RBP + local_2d],0x49
        001011b4 c6 45 dc 49     MOV        byte ptr [RBP + local_2c],0x49
        001011b8 c6 45 dd 5f     MOV        byte ptr [RBP + local_2b],0x5f
        001011bc c6 45 de 49     MOV        byte ptr [RBP + local_2a],0x49
        001011c0 c6 45 df 53     MOV        byte ptr [RBP + local_29],0x53
        001011c4 c6 45 e0 5f     MOV        byte ptr [RBP + local_28],0x5f
        001011c8 c6 45 e1 45     MOV        byte ptr [RBP + local_27],0x45
        001011cc c6 45 e2 41     MOV        byte ptr [RBP + local_26],0x41
        001011d0 c6 45 e3 53     MOV        byte ptr [RBP + local_25],0x53
        001011d4 c6 45 e4 59     MOV        byte ptr [RBP + local_24],0x59
        001011d8 c6 45 e5 5f     MOV        byte ptr [RBP + local_23],0x5f
        001011dc c6 45 e6 33     MOV        byte ptr [RBP + local_22],0x33
        001011e0 c6 45 e7 43     MOV        byte ptr [RBP + local_21],0x43
        001011e4 c6 45 e8 46     MOV        byte ptr [RBP + local_20],0x46
        001011e8 c6 45 e9 34     MOV        byte ptr [RBP + local_1f],0x34
        001011ec c6 45 ea 42     MOV        byte ptr [RBP + local_1e],0x42
        001011f0 c6 45 eb 46     MOV        byte ptr [RBP + local_1d],0x46
        001011f4 c6 45 ec 41     MOV        byte ptr [RBP + local_1c],0x41
        001011f8 c6 45 ed 44     MOV        byte ptr [RBP + local_1b],0x44
        001011fc c6 45 ee 7d     MOV        byte ptr [RBP + local_1a],0x7d

```

python script
```python
from ghidra.program.model.mem import MemoryAccessException

start_addr = currentProgram.getAddressFactory().getAddress("00101184")
end_addr = currentProgram.getAddressFactory().getAddress("001011fc")

byte_list = []


current_addr = start_addr
while current_addr <= end_addr:
	instruction = getInstructionAt(current_addr)
	if instruction is not None:
		
		operand = instruction.getOpObjects(1)[0] # get second operand
		byte_val = operand.getValue() & 0xFF # convert to unsigned byte
		byte_list.append(byte_val)
                
       
        current_addr = current_addr.next()

flag = list(map(chr, byte_list))
print("Flag:", "".join(flag))
```

use this script in ghidra and and run to get flag

```css
pico_ctf_ascii.py> Running...
('Flag:', 'picoCTF{ASCII_IS_EASY_3CF4BFAD}')
pico_ctf_ascii.py> Finished!

```

another method is manual

```python
hex_string = " 0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x41 0x53 0x43 0x49 0x49 0x5f 0x49 0x53 0x5f 0x45 0x41 0x53 0x59 0x5f 0x33 0x43 0x46 0x34 0x42 0x46 0x41 0x44 0x7d"

# Split the string into individual hex values, convert to characters, and join into a single string

decoded_text = "".join(chr(int(h, 16)) for h in hex_string.split())

# Print the result

print(decoded_text)
```

```css
┌─[✘]──[alpha@speed:🍓]──[~/Videos]:
└──╼ $ python3 test.py 
picoCTF{ASCII_IS_EASY_3CF4BFAD}
```

using ida 
```css
mov     [rbp+var_30], 70h ; 'p'
mov     [rbp+var_2F], 69h ; 'i'
mov     [rbp+var_2E], 63h ; 'c'
mov     [rbp+var_2D], 6Fh ; 'o'
mov     [rbp+var_2C], 43h ; 'C'
mov     [rbp+var_2B], 54h ; 'T'
mov     [rbp+var_2A], 46h ; 'F'
mov     [rbp+var_29], 7Bh ; '{'
mov     [rbp+var_28], 41h ; 'A'
mov     [rbp+var_27], 53h ; 'S'
mov     [rbp+var_26], 43h ; 'C'
mov     [rbp+var_25], 49h ; 'I'
mov     [rbp+var_24], 49h ; 'I'
mov     [rbp+var_23], 5Fh ; '_'
mov     [rbp+var_22], 49h ; 'I'
mov     [rbp+var_21], 53h ; 'S'
mov     [rbp+var_20], 5Fh ; '_'
mov     [rbp+var_1F], 45h ; 'E'
mov     [rbp+var_1E], 41h ; 'A'
mov     [rbp+var_1D], 53h ; 'S'
mov     [rbp+var_1C], 59h ; 'Y'
mov     [rbp+var_1B], 5Fh ; '_'
mov     [rbp+var_1A], 33h ; '3'
mov     [rbp+var_19], 43h ; 'C'
mov     [rbp+var_18], 46h ; 'F'
mov     [rbp+var_17], 34h ; '4'
mov     [rbp+var_16], 42h ; 'B'
mov     [rbp+var_15], 46h ; 'F'
mov     [rbp+var_14], 41h ; 'A'
mov     [rbp+var_13], 44h ; 'D'
mov     [rbp+var_12], 7Dh ; '}'
```


note : open vscode use regex to get flag 
first is `.*; '` second is `'\n`

```css
picoCTF{ASCII_IS_EASY_3CF4BFAD}
```

method 3

```css
┌─[✔]──[alpha@speed:🍇]──[~/Videos]:
└──╼ $ gdb ./asciiftw -q
Reading symbols from ./asciiftw...
(No debugging symbols found in ./asciiftw)
(gdb) disas main
Dump of assembler code for function main:
   0x0000000000001169 <+0>:     endbr64 
   0x000000000000116d <+4>:     push   %rbp
   0x000000000000116e <+5>:     mov    %rsp,%rbp
   0x0000000000001171 <+8>:     sub    $0x30,%rsp
   0x0000000000001175 <+12>:    mov    %fs:0x28,%rax
   0x000000000000117e <+21>:    mov    %rax,-0x8(%rbp)
   0x0000000000001182 <+25>:    xor    %eax,%eax
   0x0000000000001184 <+27>:    movb   $0x70,-0x30(%rbp)
   0x0000000000001188 <+31>:    movb   $0x69,-0x2f(%rbp)
   0x000000000000118c <+35>:    movb   $0x63,-0x2e(%rbp)
   0x0000000000001190 <+39>:    movb   $0x6f,-0x2d(%rbp)
   0x0000000000001194 <+43>:    movb   $0x43,-0x2c(%rbp)
   0x0000000000001198 <+47>:    movb   $0x54,-0x2b(%rbp)
   0x000000000000119c <+51>:    movb   $0x46,-0x2a(%rbp)
   0x00000000000011a0 <+55>:    movb   $0x7b,-0x29(%rbp)
   0x00000000000011a4 <+59>:    movb   $0x41,-0x28(%rbp)
   0x00000000000011a8 <+63>:    movb   $0x53,-0x27(%rbp)
   0x00000000000011ac <+67>:    movb   $0x43,-0x26(%rbp)
   0x00000000000011b0 <+71>:    movb   $0x49,-0x25(%rbp)
   0x00000000000011b4 <+75>:    movb   $0x49,-0x24(%rbp)
   0x00000000000011b8 <+79>:    movb   $0x5f,-0x23(%rbp)
   0x00000000000011bc <+83>:    movb   $0x49,-0x22(%rbp)
   0x00000000000011c0 <+87>:    movb   $0x53,-0x21(%rbp)
   0x00000000000011c4 <+91>:    movb   $0x5f,-0x20(%rbp)
   0x00000000000011c8 <+95>:    movb   $0x45,-0x1f(%rbp)
   0x00000000000011cc <+99>:    movb   $0x41,-0x1e(%rbp)
   0x00000000000011d0 <+103>:   movb   $0x53,-0x1d(%rbp)
   0x00000000000011d4 <+107>:   movb   $0x59,-0x1c(%rbp)
   0x00000000000011d8 <+111>:   movb   $0x5f,-0x1b(%rbp)
   0x00000000000011dc <+115>:   movb   $0x33,-0x1a(%rbp)
   0x00000000000011e0 <+119>:   movb   $0x43,-0x19(%rbp)
   0x00000000000011e4 <+123>:   movb   $0x46,-0x18(%rbp)
   0x00000000000011e8 <+127>:   movb   $0x34,-0x17(%rbp)
   0x00000000000011ec <+131>:   movb   $0x42,-0x16(%rbp)
   0x00000000000011f0 <+135>:   movb   $0x46,-0x15(%rbp)
   0x00000000000011f4 <+139>:   movb   $0x41,-0x14(%rbp)
   0x00000000000011f8 <+143>:   movb   $0x44,-0x13(%rbp)
   0x00000000000011fc <+147>:   movb   $0x7d,-0x12(%rbp)
   0x0000000000001200 <+151>:   movzbl -0x30(%rbp),%eax
   0x0000000000001204 <+155>:   movsbl %al,%eax
   0x0000000000001207 <+158>:   mov    %eax,%esi
   0x0000000000001209 <+160>:   lea    0xdf4(%rip),%rdi        # 0x2004
   0x0000000000001210 <+167>:   mov    $0x0,%eax
   0x0000000000001215 <+172>:   call   0x1070 <printf@plt>
   0x000000000000121a <+177>:   nop
   0x000000000000121b <+178>:   mov    -0x8(%rbp),%rax
   0x000000000000121f <+182>:   xor    %fs:0x28,%rax
   0x0000000000001228 <+191>:   je     0x122f <main+198>
   0x000000000000122a <+193>:   call   0x1060 <__stack_chk_fail@plt>
   0x000000000000122f <+198>:   leave  
   0x0000000000001230 <+199>:   ret    
End of assembler dump.
(gdb) 
(gdb) show dis
disable-randomization  disassembler-options   disconnected-dprintf   displaced-stepping
disassemble-next-line  disassembly-flavor     disconnected-tracing   
(gdb) show disassembly-flavor 
The disassembly flavor is "att".
(gdb) set disassembly-flavor intel
(gdb) disas main
Dump of assembler code for function main:
   0x0000000000001169 <+0>:     endbr64 
   0x000000000000116d <+4>:     push   rbp
   0x000000000000116e <+5>:     mov    rbp,rsp
   0x0000000000001171 <+8>:     sub    rsp,0x30
   0x0000000000001175 <+12>:    mov    rax,QWORD PTR fs:0x28
   0x000000000000117e <+21>:    mov    QWORD PTR [rbp-0x8],rax
   0x0000000000001182 <+25>:    xor    eax,eax
   0x0000000000001184 <+27>:    mov    BYTE PTR [rbp-0x30],0x70
   0x0000000000001188 <+31>:    mov    BYTE PTR [rbp-0x2f],0x69
   0x000000000000118c <+35>:    mov    BYTE PTR [rbp-0x2e],0x63
   0x0000000000001190 <+39>:    mov    BYTE PTR [rbp-0x2d],0x6f
   0x0000000000001194 <+43>:    mov    BYTE PTR [rbp-0x2c],0x43
   0x0000000000001198 <+47>:    mov    BYTE PTR [rbp-0x2b],0x54
   0x000000000000119c <+51>:    mov    BYTE PTR [rbp-0x2a],0x46
   0x00000000000011a0 <+55>:    mov    BYTE PTR [rbp-0x29],0x7b
   0x00000000000011a4 <+59>:    mov    BYTE PTR [rbp-0x28],0x41
   0x00000000000011a8 <+63>:    mov    BYTE PTR [rbp-0x27],0x53
   0x00000000000011ac <+67>:    mov    BYTE PTR [rbp-0x26],0x43
   0x00000000000011b0 <+71>:    mov    BYTE PTR [rbp-0x25],0x49
   0x00000000000011b4 <+75>:    mov    BYTE PTR [rbp-0x24],0x49
   0x00000000000011b8 <+79>:    mov    BYTE PTR [rbp-0x23],0x5f
   0x00000000000011bc <+83>:    mov    BYTE PTR [rbp-0x22],0x49
   0x00000000000011c0 <+87>:    mov    BYTE PTR [rbp-0x21],0x53
   0x00000000000011c4 <+91>:    mov    BYTE PTR [rbp-0x20],0x5f
   0x00000000000011c8 <+95>:    mov    BYTE PTR [rbp-0x1f],0x45
   0x00000000000011cc <+99>:    mov    BYTE PTR [rbp-0x1e],0x41
   0x00000000000011d0 <+103>:   mov    BYTE PTR [rbp-0x1d],0x53
   0x00000000000011d4 <+107>:   mov    BYTE PTR [rbp-0x1c],0x59
   0x00000000000011d8 <+111>:   mov    BYTE PTR [rbp-0x1b],0x5f
   0x00000000000011dc <+115>:   mov    BYTE PTR [rbp-0x1a],0x33
   0x00000000000011e0 <+119>:   mov    BYTE PTR [rbp-0x19],0x43
   0x00000000000011e4 <+123>:   mov    BYTE PTR [rbp-0x18],0x46
   0x00000000000011e8 <+127>:   mov    BYTE PTR [rbp-0x17],0x34
   0x00000000000011ec <+131>:   mov    BYTE PTR [rbp-0x16],0x42
   0x00000000000011f0 <+135>:   mov    BYTE PTR [rbp-0x15],0x46
   0x00000000000011f4 <+139>:   mov    BYTE PTR [rbp-0x14],0x41
   0x00000000000011f8 <+143>:   mov    BYTE PTR [rbp-0x13],0x44
   0x00000000000011fc <+147>:   mov    BYTE PTR [rbp-0x12],0x7d
   0x0000000000001200 <+151>:   movzx  eax,BYTE PTR [rbp-0x30]
   0x0000000000001204 <+155>:   movsx  eax,al
   0x0000000000001207 <+158>:   mov    esi,eax
   0x0000000000001209 <+160>:   lea    rdi,[rip+0xdf4]        # 0x2004
   0x0000000000001210 <+167>:   mov    eax,0x0
   0x0000000000001215 <+172>:   call   0x1070 <printf@plt>
   0x000000000000121a <+177>:   nop
   0x000000000000121b <+178>:   mov    rax,QWORD PTR [rbp-0x8]
   0x000000000000121f <+182>:   xor    rax,QWORD PTR fs:0x28
   0x0000000000001228 <+191>:   je     0x122f <main+198>
   0x000000000000122a <+193>:   call   0x1060 <__stack_chk_fail@plt>
   0x000000000000122f <+198>:   leave  
   0x0000000000001230 <+199>:   ret    
End of assembler dump.
```

Since hexadecimal numbers are stored in rbp, set a breakpoint at main+151 and extract the information from rbp-0x30.
```css
(gdb) b *main+151
Breakpoint 1 at 0x1200
(gdb) r
Starting program: /home/saket/Videos/asciiftw 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
Breakpoint 1, 0x0000555555555200 in main ()
(gdb)  x/100xb $rbp-0x30
0x7fffffffdd70: 0x70    0x69    0x63    0x6f    0x43    0x54    0x46    0x7b
0x7fffffffdd78: 0x41    0x53    0x43    0x49    0x49    0x5f    0x49    0x53
0x7fffffffdd80: 0x5f    0x45    0x41    0x53    0x59    0x5f    0x33    0x43
0x7fffffffdd88: 0x46    0x34    0x42    0x46    0x41    0x44    0x7d    0x00
0x7fffffffdd90: 0x00    0x10    0x00    0x00    0x00    0x00    0x00    0x00
0x7fffffffdd98: 0x00    0x90    0xca    0x83    0xe4    0xd9    0x7e    0x21
0x7fffffffdda0: 0x01    0x00    0x00    0x00    0x00    0x00    0x00    0x00
0x7fffffffdda8: 0x90    0xad    0xda    0xf7    0xff    0x7f    0x00    0x00
0x7fffffffddb0: 0x00    0x00    0x00    0x00    0x00    0x00    0x00    0x00
0x7fffffffddb8: 0x69    0x51    0x55    0x55    0x55    0x55    0x00    0x00
0x7fffffffddc0: 0xa0    0xde    0xff    0xff    0x01    0x00    0x00    0x00
0x7fffffffddc8: 0xb8    0xde    0xff    0xff    0xff    0x7f    0x00    0x00
0x7fffffffddd0: 0x00    0x00    0x00    0x00
(gdb) 
Breakpoint 1, 0x0000555555555200 in main ()
(gdb) x/100xb $rbp-0x30
0x7fffffffdd70: 0x70    0x69    0x63    0x6f    0x43    0x54    0x46    0x7b
0x7fffffffdd78: 0x41    0x53    0x43    0x49    0x49    0x5f    0x49    0x53
0x7fffffffdd80: 0x5f    0x45    0x41    0x53    0x59    0x5f    0x33    0x43
0x7fffffffdd88: 0x46    0x34    0x42    0x46    0x41    0x44    0x7d    0x00
0x7fffffffdd90: 0x00    0x10    0x00    0x00    0x00    0x00    0x00    0x00
0x7fffffffdd98: 0x00    0xb0    0xfe    0x96    0xc9    0xcf    0xef    0x1f
0x7fffffffdda0: 0x01    0x00    0x00    0x00    0x00    0x00    0x00    0x00
0x7fffffffdda8: 0x90    0xad    0xda    0xf7    0xff    0x7f    0x00    0x00
0x7fffffffddb0: 0x00    0x00    0x00    0x00    0x00    0x00    0x00    0x00
0x7fffffffddb8: 0x69    0x51    0x55    0x55    0x55    0x55    0x00    0x00
0x7fffffffddc0: 0xa0    0xde    0xff    0xff    0x01    0x00    0x00    0x00
0x7fffffffddc8: 0xb8    0xde    0xff    0xff    0xff    0x7f    0x00    0x00
0x7fffffffddd0: 0x00    0x00    0x00    0x00
(gdb) 
(gdb) x/s $rbp-0x30
0x7fffffffdd70: "picoCTF{ASCII_IS_EASY_3CF4BFAD}"
```