# Reversing and Cracking first simple Program - bin 0x05

```css
#include <string.h>
#include <stdio.h>

int main(int argc, char *argv[]) {
        if(argc==2) {
		printf("Checking License: %s\n", argv[1]);
		if(strcmp(argv[1], "AAAA-Z10N-42-OK")==0) {
			printf("Access Granted!\n");
		} else {
			printf("WRONG!\n");
		}
	} else {
		printf("Usage: <key>\n");
	}
	return 0;
}
```

```css
┌─[✔]──[alpha@speed:🚀]──[~/Public/share_file/liveoverflow/liveoverflow_youtube/0x05_simple_crackme_intro_assembler]± ● master:
└──╼ $ gdb ./license_1  -q
Reading symbols from ./license_1...
(No debugging symbols found in ./license_1)
(gdb) disassemble main
Dump of assembler code for function main:
   0x00000000004005bd <+0>:     push   %rbp
   0x00000000004005be <+1>:     mov    %rsp,%rbp
   0x00000000004005c1 <+4>:     sub    $0x10,%rsp
   0x00000000004005c5 <+8>:     mov    %edi,-0x4(%rbp)
   0x00000000004005c8 <+11>:    mov    %rsi,-0x10(%rbp)
   0x00000000004005cc <+15>:    cmpl   $0x2,-0x4(%rbp)
   0x00000000004005d0 <+19>:    jne    0x400623 <main+102>
   0x00000000004005d2 <+21>:    mov    -0x10(%rbp),%rax
   0x00000000004005d6 <+25>:    add    $0x8,%rax
   0x00000000004005da <+29>:    mov    (%rax),%rax
   0x00000000004005dd <+32>:    mov    %rax,%rsi
   0x00000000004005e0 <+35>:    mov    $0x4006c4,%edi
   0x00000000004005e5 <+40>:    mov    $0x0,%eax
   0x00000000004005ea <+45>:    call   0x400490 <printf@plt>
   0x00000000004005ef <+50>:    mov    -0x10(%rbp),%rax
   0x00000000004005f3 <+54>:    add    $0x8,%rax
   0x00000000004005f7 <+58>:    mov    (%rax),%rax
   0x00000000004005fa <+61>:    mov    $0x4006da,%esi
   0x00000000004005ff <+66>:    mov    %rax,%rdi
   0x0000000000400602 <+69>:    call   0x4004b0 <strcmp@plt>
   0x0000000000400607 <+74>:    test   %eax,%eax
   0x0000000000400609 <+76>:    jne    0x400617 <main+90>
   0x000000000040060b <+78>:    mov    $0x4006ea,%edi
   0x0000000000400610 <+83>:    call   0x400480 <puts@plt>
   0x0000000000400615 <+88>:    jmp    0x40062d <main+112>
   0x0000000000400617 <+90>:    mov    $0x4006fa,%edi
   0x000000000040061c <+95>:    call   0x400480 <puts@plt>
   0x0000000000400621 <+100>:   jmp    0x40062d <main+112>
   0x0000000000400623 <+102>:   mov    $0x400701,%edi
   0x0000000000400628 <+107>:   call   0x400480 <puts@plt>
   0x000000000040062d <+112>:   mov    $0x0,%eax
   0x0000000000400632 <+117>:   leave  
   0x0000000000400633 <+118>:   ret    
End of assembler dump.
(gdb) set dis
disable-randomization  disassembler-options   disconnected-dprintf   displaced-stepping     
disassemble-next-line  disassembly-flavor     disconnected-tracing   
(gdb) set disassembly-flavor [ press tab ]
att    intel  
(gdb) set disassembly-flavor intel
(gdb) 
```

intel view

```css
(gdb) disassemble main
Dump of assembler code for function main:

   0x00000000004005bd <+0>:     push   rbp
   0x00000000004005be <+1>:     mov    rbp,rsp*/
   0x00000000004005c1 <+4>:     sub    rsp,0x10
   0x00000000004005c5 <+8>:     mov    DWORD PTR [rbp-0x4],edi
   0x00000000004005c8 <+11>:    mov    QWORD PTR [rbp-0x10],rsi
   0x00000000004005cc <+15>:    cmp    DWORD PTR [rbp-0x4],0x2
   0x00000000004005d0 <+19>:    jne    0x400623 <main+102>
   0x00000000004005d2 <+21>:    mov    rax,QWORD PTR [rbp-0x10]
   0x00000000004005d6 <+25>:    add    rax,0x8
   0x00000000004005da <+29>:    mov    rax,QWORD PTR [rax]
   0x00000000004005dd <+32>:    mov    rsi,rax
   0x00000000004005e0 <+35>:    mov    edi,0x4006c4
   0x00000000004005e5 <+40>:    mov    eax,0x0
   0x00000000004005ea <+45>:    call   0x400490 <printf@plt>
   0x00000000004005ef <+50>:    mov    rax,QWORD PTR [rbp-0x10]
   0x00000000004005f3 <+54>:    add    rax,0x8
   0x00000000004005f7 <+58>:    mov    rax,QWORD PTR [rax]
   0x00000000004005fa <+61>:    mov    esi,0x4006da
   0x00000000004005ff <+66>:    mov    rdi,rax
   0x0000000000400602 <+69>:    call   0x4004b0 <strcmp@plt>
   0x0000000000400607 <+74>:    test   eax,eax
   0x0000000000400609 <+76>:    jne    0x400617 <main+90>
   0x000000000040060b <+78>:    mov    edi,0x4006ea
   0x0000000000400610 <+83>:    call   0x400480 <puts@plt>
   0x0000000000400615 <+88>:    jmp    0x40062d <main+112>
   0x0000000000400617 <+90>:    mov    edi,0x4006fa
   0x000000000040061c <+95>:    call   0x400480 <puts@plt>
   0x0000000000400621 <+100>:   jmp    0x40062d <main+112>
   0x0000000000400623 <+102>:   mov    edi,0x400701
   0x0000000000400628 <+107>:   call   0x400480 <puts@plt>
   0x000000000040062d <+112>:   mov    eax,0x0
   0x0000000000400632 <+117>:   leave  
   0x0000000000400633 <+118>:   ret    
End of assembler dump.
(gdb) 
```

```css
(gdb) b main
Breakpoint 1 at 0x4005c1
(gdb) r
Starting program: /home/saket/Public/share_file/liveoverflow/liveoverflow_youtube/0x05_simple_crackme_intro_assembler/license_1 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".

Breakpoint 1, 0x00000000004005c1 in main ()
(gdb) layout asm
```

type `ctrl + x + a`

```css
┌───────────────────────────────────────────────────────────────────────────────────────────────────────────────┐
│B+> 0x4005c1 <main+4>       sub    $0x10,%rsp                                                                  │
│    0x4005c5 <main+8>       mov    %edi,-0x4(%rbp)                                                             │
│    0x4005c8 <main+11>      mov    %rsi,-0x10(%rbp)                                                            │
│    0x4005cc <main+15>      cmpl   $0x2,-0x4(%rbp)                                                             │
│    0x4005d0 <main+19>      jne    0x400623 <main+102>                                                         │
│    0x4005d2 <main+21>      mov    -0x10(%rbp),%rax                                                            │
│    0x4005d6 <main+25>      add    $0x8,%rax                                                                   │
│    0x4005da <main+29>      mov    (%rax),%rax                                                                 │
│    0x4005dd <main+32>      mov    %rax,%rsi                                                                   │
│    0x4005e0 <main+35>      mov    $0x4006c4,%edi                                                              │
│    0x4005e5 <main+40>      mov    $0x0,%eax                                                                   │
│    0x4005ea <main+45>      call   0x400490 <printf@plt>                                                       │
│    0x4005ef <main+50>      mov    -0x10(%rbp),%rax                                                            │
│    0x4005f3 <main+54>      add    $0x8,%rax                                                                   │
│    0x4005f7 <main+58>      mov    (%rax),%rax                                                                 │
│    0x4005fa <main+61>      mov    $0x4006da,%esi                                                              │
│    0x4005ff <main+66>      mov    %rax,%rdi                                                                   │
│    0x400602 <main+69>      call   0x4004b0 <strcmp@plt>                                                       │
│    0x400607 <main+74>      test   %eax,%eax                                                                   │
│    0x400609 <main+76>      jne    0x400617 <main+90>                                                          │
│    0x40060b <main+78>      mov    $0x4006ea,%edi                                                              │
│    0x400610 <main+83>      call   0x400480 <puts@plt>                                                         │
│    0x400615 <main+88>      jmp    0x40062d <main+112>                                                         │
│    0x400617 <main+90>      mov    $0x4006fa,%edi                                                              │
│    0x40061c <main+95>      call   0x400480 <puts@plt>                                                         │
│    0x400621 <main+100>     jmp    0x40062d <main+112>                                                         │
│    0x400623 <main+102>     mov    $0x400701,%edi                                                              │
│    0x400628 <main+107>     call   0x400480 <puts@plt>                                                         │
│    0x40062d <main+112>     mov    $0x0,%eax                                                                   │
│    0x400632 <main+117>     leave                                                                              │
│    0x400633 <main+118>     ret                                                                                │
│    0x400634                cs nopw 0x0(%rax,%rax,1)                                                           │
└───────────────────────────────────────────────────────────────────────────────────────────────────────────────┘
multi-thre Thread 0x7ffff7d7e7 In: main                                                       L??   PC: 0x4005c1 
(gdb) 
```

```css
(gdb) info register
rax            0x4005bd            4195773
rbx            0x0                 0
rcx            0x400640            4195904
rdx            0x7fffffffdd68      140737488346472
rsi            0x7fffffffdd58      140737488346456
rdi            0x1                 1
rbp            0x7fffffffdc40      0x7fffffffdc40
rsp            0x7fffffffdc40      0x7fffffffdc40
r8             0x7ffff7f9cf10      140737353731856
r9             0x7ffff7fc9040      140737353912384
r10            0x7ffff7fc3908      140737353890056
r11            0x7ffff7fde660      140737353999968
r12            0x7fffffffdd58      140737488346456
r13            0x4005bd            4195773
r14            0x0                 0
r15            0x7ffff7ffd040      140737354125376
rip            0x4005c1            0x4005c1 <main+4>
eflags         0x246               [ PF ZF IF ]
cs             0x33                51
ss             0x2b                43
ds             0x0                 0
es             0x0                 0
fs             0x0                 0
gs             0x0                 0
(gdb) quit

```


```css
(gdb) disassemble main
Dump of assembler code for function main:
   0x00000000004005bd <+0>:     push   %rbp
   0x00000000004005be <+1>:     mov    %rsp,%rbp
   0x00000000004005c1 <+4>:     sub    $0x10,%rsp
   0x00000000004005c5 <+8>:     mov    %edi,-0x4(%rbp)
   0x00000000004005c8 <+11>:    mov    %rsi,-0x10(%rbp)
   0x00000000004005cc <+15>:    cmpl   $0x2,-0x4(%rbp)
   0x00000000004005d0 <+19>:    jne    0x400623 <main+102>
   0x00000000004005d2 <+21>:    mov    -0x10(%rbp),%rax
   0x00000000004005d6 <+25>:    add    $0x8,%rax
   0x00000000004005da <+29>:    mov    (%rax),%rax
   0x00000000004005dd <+32>:    mov    %rax,%rsi
   0x00000000004005e0 <+35>:    mov    $0x4006c4,%edi
   0x00000000004005e5 <+40>:    mov    $0x0,%eax
   0x00000000004005ea <+45>:    call   0x400490 <printf@plt>
   0x00000000004005ef <+50>:    mov    -0x10(%rbp),%rax
   0x00000000004005f3 <+54>:    add    $0x8,%rax
   0x00000000004005f7 <+58>:    mov    (%rax),%rax
   0x00000000004005fa <+61>:    mov    $0x4006da,%esi
   0x00000000004005ff <+66>:    mov    %rax,%rdi
   0x0000000000400602 <+69>:    call   0x4004b0 <strcmp@plt>
   0x0000000000400607 <+74>:    test   %eax,%eax
   0x0000000000400609 <+76>:    jne    0x400617 <main+90>
   0x000000000040060b <+78>:    mov    $0x4006ea,%edi
   0x0000000000400610 <+83>:    call   0x400480 <puts@plt>
   0x0000000000400615 <+88>:    jmp    0x40062d <main+112>
   0x0000000000400617 <+90>:    mov    $0x4006fa,%edi
   0x000000000040061c <+95>:    call   0x400480 <puts@plt>
   0x0000000000400621 <+100>:   jmp    0x40062d <main+112>
   0x0000000000400623 <+102>:   mov    $0x400701,%edi
   0x0000000000400628 <+107>:   call   0x400480 <puts@plt>
   0x000000000040062d <+112>:   mov    $0x0,%eax
   0x0000000000400632 <+117>:   leave  
   0x0000000000400633 <+118>:   ret    
End of assembler dump.
(gdb) set disassembly-flavor intel
(gdb) disassemble main
Dump of assembler code for function main:
   0x00000000004005bd <+0>:     push   rbp
   0x00000000004005be <+1>:     mov    rbp,rsp
   0x00000000004005c1 <+4>:     sub    rsp,0x10
   0x00000000004005c5 <+8>:     mov    DWORD PTR [rbp-0x4],edi
   0x00000000004005c8 <+11>:    mov    QWORD PTR [rbp-0x10],rsi
   0x00000000004005cc <+15>:    cmp    DWORD PTR [rbp-0x4],0x2
   0x00000000004005d0 <+19>:    jne    0x400623 <main+102>
   0x00000000004005d2 <+21>:    mov    rax,QWORD PTR [rbp-0x10]
   0x00000000004005d6 <+25>:    add    rax,0x8
   0x00000000004005da <+29>:    mov    rax,QWORD PTR [rax]
   0x00000000004005dd <+32>:    mov    rsi,rax
   0x00000000004005e0 <+35>:    mov    edi,0x4006c4
   0x00000000004005e5 <+40>:    mov    eax,0x0
   0x00000000004005ea <+45>:    call   0x400490 <printf@plt>
   0x00000000004005ef <+50>:    mov    rax,QWORD PTR [rbp-0x10]
   0x00000000004005f3 <+54>:    add    rax,0x8
   0x00000000004005f7 <+58>:    mov    rax,QWORD PTR [rax]
   0x00000000004005fa <+61>:    mov    esi,0x4006da
   0x00000000004005ff <+66>:    mov    rdi,rax
   0x0000000000400602 <+69>:    call   0x4004b0 <strcmp@plt>
   0x0000000000400607 <+74>:    test   eax,eax
   0x0000000000400609 <+76>:    jne    0x400617 <main+90>
   0x000000000040060b <+78>:    mov    edi,0x4006ea
   0x0000000000400610 <+83>:    call   0x400480 <puts@plt>
   0x0000000000400615 <+88>:    jmp    0x40062d <main+112>
   0x0000000000400617 <+90>:    mov    edi,0x4006fa
   0x000000000040061c <+95>:    call   0x400480 <puts@plt>
   0x0000000000400621 <+100>:   jmp    0x40062d <main+112>
   0x0000000000400623 <+102>:   mov    edi,0x400701
   0x0000000000400628 <+107>:   call   0x400480 <puts@plt>
   0x000000000040062d <+112>:   mov    eax,0x0
   0x0000000000400632 <+117>:   leave  
   0x0000000000400633 <+118>:   ret    
End of assembler dump.
(gdb) info registers 
The program has no registers now.
(gdb) r
Starting program: /home/saket/Public/share_file/liveoverflow/liveoverflow_youtube/0x05_simple_crackme_intro_assembler/license_1 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".

Breakpoint 1, 0x00000000004005c1 in main ()
(gdb) info registers 
rax            0x4005bd            4195773
rbx            0x0                 0
rcx            0x400640            4195904
rdx            0x7fffffffdb78      140737488345976
rsi            0x7fffffffdb68      140737488345960
rdi            0x1                 1
rbp            0x7fffffffda50      0x7fffffffda50
rsp            0x7fffffffda50      0x7fffffffda50
r8             0x7ffff7f9cf10      140737353731856
r9             0x7ffff7fc9040      140737353912384
r10            0x7ffff7fc3908      140737353890056
r11            0x7ffff7fde660      140737353999968
r12            0x7fffffffdb68      140737488345960
r13            0x4005bd            4195773
r14            0x0                 0
r15            0x7ffff7ffd040      140737354125376
rip            0x4005c1            0x4005c1 <main+4>
eflags         0x246               [ PF ZF IF ]
cs             0x33                51
ss             0x2b                43
ds             0x0                 0
es             0x0                 0
fs             0x0                 0
gs             0x0                 0
(gdb) si
0x00000000004005c5 in main ()
(gdb) info registers 
rax            0x4005bd            4195773
rbx            0x0                 0
rcx            0x400640            4195904
rdx            0x7fffffffdb78      140737488345976
rsi            0x7fffffffdb68      140737488345960
rdi            0x1                 1
rbp            0x7fffffffda50      0x7fffffffda50
rsp            0x7fffffffda40      0x7fffffffda40
r8             0x7ffff7f9cf10      140737353731856
r9             0x7ffff7fc9040      140737353912384
r10            0x7ffff7fc3908      140737353890056
r11            0x7ffff7fde660      140737353999968
r12            0x7fffffffdb68      140737488345960
r13            0x4005bd            4195773
r14            0x0                 0
r15            0x7ffff7ffd040      140737354125376
rip            0x4005c5            0x4005c5 <main+8>
eflags         0x202               [ IF ]
cs             0x33                51
ss             0x2b                43
ds             0x0                 0
es             0x0                 0
fs             0x0                 0
gs             0x0                 0
(gdb) 
```

```css
(gdb) ni
0x00000000004005c8 in main ()
(gdb) 
0x00000000004005cc in main ()
(gdb) 
0x00000000004005d0 in main ()
(gdb) 
0x0000000000400623 in main ()
(gdb) 
0x0000000000400628 in main ()
(gdb) 
Usage: <key>
0x000000000040062d in main ()
(gdb) 
0x0000000000400632 in main ()
(gdb) 
0x0000000000400633 in main ()
(gdb) 
0x00007ffff7daad90 in __libc_start_call_main (main=main@entry=0x4005bd <main>, argc=argc@entry=1, argv=argv@entry=0x7fffffffdb68) at ../sysdeps/nptl/libc_start_call_main.h:58
58      ../sysdeps/nptl/libc_start_call_main.h: No such file or directory.
(gdb) 
```

```css
(gdb) r AAA-Key
The program being debugged has been started already.
Start it from the beginning? (y or n) y
Starting program: /home/saket/Public/share_file/liveoverflow/liveoverflow_youtube/0x05_simple_crackme_intro_assembler/license_1 AAA-Key
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".

Breakpoint 1, 0x00000000004005c1 in main ()
(gdb) ni
0x00000000004005c5 in main ()
(gdb) 
0x00000000004005c8 in main ()
(gdb) 
0x00000000004005cc in main ()
(gdb) 
0x00000000004005d0 in main ()
(gdb) 
0x00000000004005d2 in main ()
(gdb) 
0x00000000004005d6 in main ()
(gdb) 
0x00000000004005da in main ()
(gdb) 
0x00000000004005dd in main ()
(gdb) 
0x00000000004005e0 in main ()
(gdb) 
0x00000000004005e5 in main ()
(gdb) 
0x00000000004005ea in main ()
(gdb) 
Checking License: AAA-Key
0x00000000004005ef in main ()
(gdb) 
0x00000000004005f3 in main ()
(gdb) 
0x00000000004005f7 in main ()
(gdb) 
0x00000000004005fa in main ()
(gdb) 
0x00000000004005ff in main ()
(gdb) 
0x0000000000400602 in main ()
(gdb) 
0x0000000000400607 in main ()
(gdb) 
0x0000000000400609 in main ()
(gdb) 
0x0000000000400617 in main ()
(gdb) 
0x000000000040061c in main ()
(gdb) 
WRONG!
0x0000000000400621 in main ()
(gdb) 
```

```css
 0x00000000004005cc <+15>:    cmp    DWORD PTR [rbp-0x4],0x2
 0x00000000004005d0 <+19>:    jne    0x400623 <main+102>
```

```css
0x00000000004005ea <+45>:    call   0x400490 <printf@plt>
0x0000000000400602 <+69>:    call   0x4004b0 <strcmp@plt>
0x0000000000400607 <+74>:    test   eax,eax
0x0000000000400609 <+76>:    jne    0x400617 <main+90>
```

```css
0x0000000000400609 <+76>:    jne    0x400617 <main+90>
```

```css
0x0000000000400610 <+83>:    call   0x400480 <puts@plt>
0x0000000000400615 <+88>:    jmp    0x40062d <main+112>
```

```css
0x40061c <main+95>      call   0x400480 <puts@plt>                                                         
0x400621 <main+100>     jmp    0x40062d <main+112>       
```

```css
0x0000000000400621 <+100>:   jmp    0x40062d <main+112>
0x0000000000400628 <+107>:   call   0x400480 <puts@plt>
```

```css
0x0000000000400628 <+107>:   call   0x400480 <puts@plt>

0x0000000000400628 in main ()
(gdb) 
Usage: <key>
```

```css
0x00000000004005ea <+45>:    call   0x400490 <printf@plt>


0x00000000004005ea in main ()
(gdb) 
Checking License: AAA-Key

```

```css
0x000000000040061c <+95>:    call   0x400480 <puts@plt>

0x000000000040061c in main ()
(gdb) 
WRONG!
```

```css
(gdb) b main
Breakpoint 1 at 0x4005c1
(gdb) b *main+74
Breakpoint 2 at 0x400607
(gdb) r aa
Starting program: /home/saket/Public/share_file/liveoverflow/liveoverflow_youtube/0x05_simple_crackme_intro_assembler/license_1 aa
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".

Breakpoint 1, 0x00000000004005c1 in main ()
(gdb) c
Continuing.
Checking License: aa

Breakpoint 2, 0x0000000000400607 in main ()
(gdb) info registers 
rax            0x20                32
rbx            0x0                 0
rcx            0xffffffff          4294967295
rdx            0x41                65
rsi            0x4006da            4196058
rdi            0x7fffffffdf8a      140737488347018
rbp            0x7fffffffda30      0x7fffffffda30
rsp            0x7fffffffda20      0x7fffffffda20
r8             0x0                 0
r9             0x7fffffff          2147483647
r10            0x7ffff7d8a360      140737351557984
r11            0x7ffff7f19940      140737353193792
r12            0x7fffffffdb48      140737488345928
r13            0x4005bd            4195773
r14            0x0                 0
r15            0x7ffff7ffd040      140737354125376
rip            0x400607            0x400607 <main+74>
eflags         0x202               [ IF ]
cs             0x33                51
ss             0x2b                43
ds             0x0                 0
es             0x0                 0
fs             0x0                 0
gs             0x0                 0

```

```css
(gdb) set $eax=0
(gdb) info registers 
rax            0x0                 0
rbx            0x0                 0
rcx            0xffffffff          4294967295
rdx            0x41                65
rsi            0x4006da            4196058
rdi            0x7fffffffdf8a      140737488347018
rbp            0x7fffffffda30      0x7fffffffda30
rsp            0x7fffffffda20      0x7fffffffda20
r8             0x0                 0
r9             0x7fffffff          2147483647
r10            0x7ffff7d8a360      140737351557984
r11            0x7ffff7f19940      140737353193792
r12            0x7fffffffdb48      140737488345928
r13            0x4005bd            4195773
r14            0x0                 0
r15            0x7ffff7ffd040      140737354125376
rip            0x400607            0x400607 <main+74>
eflags         0x202               [ IF ]
cs             0x33                51
ss             0x2b                43
ds             0x0                 0
es             0x0                 0
fs             0x0                 0
gs             0x0                 0
(gdb) ni
0x0000000000400609 in main ()
(gdb) 
0x000000000040060b in main ()
(gdb) 
0x0000000000400610 in main ()
(gdb) 
Access Granted!
0x0000000000400615 in main ()
(gdb) 
0x000000000040062d in main ()
(gdb) 
```

when it check with real key

```css
(gdb) r AAAA-Z10N-42-OK
The program being debugged has been started already.
Start it from the beginning? (y or n) y
Starting program: /home/saket/Public/share_file/liveoverflow/liveoverflow_youtube/0x05_simple_crackme_intro_assembler/license_1 AAAA-Z10N-42-OK
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".

Breakpoint 1, 0x00000000004005c1 in main ()
(gdb) b *main+74
Note: breakpoint 2 also set at pc 0x400607.
Breakpoint 3 at 0x400607
(gdb) c
Continuing.
Checking License: AAAA-Z10N-42-OK

Breakpoint 2, 0x0000000000400607 in main ()
(gdb) info registers
rax            0x0                 0
rbx            0x0                 0
rcx            0x0                 0
rdx            0xf                 15
rsi            0x4006da            4196058
rdi            0x7fffffffdf7d      140737488347005
rbp            0x7fffffffda20      0x7fffffffda20
rsp            0x7fffffffda10      0x7fffffffda10
r8             0x0                 0
r9             0x7fffffff          2147483647
r10            0x7ffff7d8a360      140737351557984
r11            0x7ffff7f19940      140737353193792
r12            0x7fffffffdb38      140737488345912
r13            0x4005bd            4195773
r14            0x0                 0
r15            0x7ffff7ffd040      140737354125376
rip            0x400607            0x400607 <main+74>
eflags         0x246               [ PF ZF IF ]
cs             0x33                51
ss             0x2b                43
ds             0x0                 0
es             0x0                 0
fs             0x0                 0
gs             0x0                 0
(gdb) 
```