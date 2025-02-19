```css

┌─[✔]──[alpha@speed:🍓]──[~/Public/share_file/liveoverflow/liveoverflow_youtube/0x05_simple_crackme_intro_assembler]± ● master:
└──╼ $ strings license_1
/lib64/ld-linux-x86-64.so.2
libc.so.6
puts
printf
strcmp
__libc_start_main
__gmon_start__
GLIBC_2.2.5
UH-P
UH-P
[]A\A]A^A_
Checking License: %s
AAAA-Z10N-42-OK
Access Granted!
WRONG!
Usage: <key>
;*3$"
GCC: (Ubuntu 4.8.4-2ubuntu1~14.04) 4.8.4
GCC: (Ubuntu 4.8.2-19ubuntu1) 4.8.2
.symtab
.strtab
.shstrtab
.interp
.note.ABI-tag
.note.gnu.build-id
.gnu.hash
.dynsym
.dynstr
.gnu.version
.gnu.version_r
.rela.dyn
.rela.plt
.init
.text
.fini
.rodata
.eh_frame_hdr
.eh_frame
.init_array
.fini_array
.jcr
.dynamic
.got
.got.plt
.data
.bss
.comment
crtstuff.c
__JCR_LIST__
deregister_tm_clones
register_tm_clones
__do_global_dtors_aux
completed.6973
__do_global_dtors_aux_fini_array_entry
frame_dummy
__frame_dummy_init_array_entry
crack.c
__FRAME_END__
__JCR_END__
__init_array_end
_DYNAMIC
__init_array_start
_GLOBAL_OFFSET_TABLE_
__libc_csu_fini
_ITM_deregisterTMCloneTable
data_start
puts@@GLIBC_2.2.5
_edata
_fini
printf@@GLIBC_2.2.5
__libc_start_main@@GLIBC_2.2.5
__data_start
strcmp@@GLIBC_2.2.5
__gmon_start__
__dso_handle
_IO_stdin_used
__libc_csu_init
_end
_start
__bss_start
main
_Jv_RegisterClasses
__TMC_END__
_ITM_registerTMCloneTable
_init

```


```css
┌─[✔]──[alpha@speed:🐧]──[~/Public/share_file/liveoverflow/liveoverflow_youtube/0x05_simple_crackme_intro_assembler]± ● master:
└──╼ $ objdump -d license_1
 
license_1:     file format elf64-x86-64


Disassembly of section .init:

0000000000400450 <_init>:
  400450:	48 83 ec 08          	sub    $0x8,%rsp
  400454:	48 8b 05 9d 0b 20 00 	mov    0x200b9d(%rip),%rax        # 600ff8 <__gmon_start__>
  40045b:	48 85 c0             	test   %rax,%rax
  40045e:	74 05                	je     400465 <_init+0x15>
  400460:	e8 5b 00 00 00       	call   4004c0 <__gmon_start__@plt>
  400465:	48 83 c4 08          	add    $0x8,%rsp
  400469:	c3                   	ret    

Disassembly of section .plt:

0000000000400470 <.plt>:
  400470:	ff 35 92 0b 20 00    	push   0x200b92(%rip)        # 601008 <_GLOBAL_OFFSET_TABLE_+0x8>
  400476:	ff 25 94 0b 20 00    	jmp    *0x200b94(%rip)        # 601010 <_GLOBAL_OFFSET_TABLE_+0x10>
  40047c:	0f 1f 40 00          	nopl   0x0(%rax)

0000000000400480 <puts@plt>:
  400480:	ff 25 92 0b 20 00    	jmp    *0x200b92(%rip)        # 601018 <puts@GLIBC_2.2.5>
  400486:	68 00 00 00 00       	push   $0x0
  40048b:	e9 e0 ff ff ff       	jmp    400470 <.plt>

0000000000400490 <printf@plt>:
  400490:	ff 25 8a 0b 20 00    	jmp    *0x200b8a(%rip)        # 601020 <printf@GLIBC_2.2.5>
  400496:	68 01 00 00 00       	push   $0x1
  40049b:	e9 d0 ff ff ff       	jmp    400470 <.plt>

00000000004004a0 <__libc_start_main@plt>:
  4004a0:	ff 25 82 0b 20 00    	jmp    *0x200b82(%rip)        # 601028 <__libc_start_main@GLIBC_2.2.5>
  4004a6:	68 02 00 00 00       	push   $0x2
  4004ab:	e9 c0 ff ff ff       	jmp    400470 <.plt>

00000000004004b0 <strcmp@plt>:
  4004b0:	ff 25 7a 0b 20 00    	jmp    *0x200b7a(%rip)        # 601030 <strcmp@GLIBC_2.2.5>
  4004b6:	68 03 00 00 00       	push   $0x3
  4004bb:	e9 b0 ff ff ff       	jmp    400470 <.plt>

00000000004004c0 <__gmon_start__@plt>:
  4004c0:	ff 25 72 0b 20 00    	jmp    *0x200b72(%rip)        # 601038 <__gmon_start__>
  4004c6:	68 04 00 00 00       	push   $0x4
  4004cb:	e9 a0 ff ff ff       	jmp    400470 <.plt>

Disassembly of section .text:

00000000004004d0 <_start>:
  4004d0:	31 ed                	xor    %ebp,%ebp
  4004d2:	49 89 d1             	mov    %rdx,%r9
  4004d5:	5e                   	pop    %rsi
  4004d6:	48 89 e2             	mov    %rsp,%rdx
  4004d9:	48 83 e4 f0          	and    $0xfffffffffffffff0,%rsp
  4004dd:	50                   	push   %rax
  4004de:	54                   	push   %rsp
  4004df:	49 c7 c0 b0 06 40 00 	mov    $0x4006b0,%r8
  4004e6:	48 c7 c1 40 06 40 00 	mov    $0x400640,%rcx
  4004ed:	48 c7 c7 bd 05 40 00 	mov    $0x4005bd,%rdi
  4004f4:	e8 a7 ff ff ff       	call   4004a0 <__libc_start_main@plt>
  4004f9:	f4                   	hlt    
  4004fa:	66 0f 1f 44 00 00    	nopw   0x0(%rax,%rax,1)

0000000000400500 <deregister_tm_clones>:
  400500:	b8 57 10 60 00       	mov    $0x601057,%eax
  400505:	55                   	push   %rbp
  400506:	48 2d 50 10 60 00    	sub    $0x601050,%rax
  40050c:	48 83 f8 0e          	cmp    $0xe,%rax
  400510:	48 89 e5             	mov    %rsp,%rbp
  400513:	77 02                	ja     400517 <deregister_tm_clones+0x17>
  400515:	5d                   	pop    %rbp
  400516:	c3                   	ret    
  400517:	b8 00 00 00 00       	mov    $0x0,%eax
  40051c:	48 85 c0             	test   %rax,%rax
  40051f:	74 f4                	je     400515 <deregister_tm_clones+0x15>
  400521:	5d                   	pop    %rbp
  400522:	bf 50 10 60 00       	mov    $0x601050,%edi
  400527:	ff e0                	jmp    *%rax
  400529:	0f 1f 80 00 00 00 00 	nopl   0x0(%rax)

0000000000400530 <register_tm_clones>:
  400530:	b8 50 10 60 00       	mov    $0x601050,%eax
  400535:	55                   	push   %rbp
  400536:	48 2d 50 10 60 00    	sub    $0x601050,%rax
  40053c:	48 c1 f8 03          	sar    $0x3,%rax
  400540:	48 89 e5             	mov    %rsp,%rbp
  400543:	48 89 c2             	mov    %rax,%rdx
  400546:	48 c1 ea 3f          	shr    $0x3f,%rdx
  40054a:	48 01 d0             	add    %rdx,%rax
  40054d:	48 d1 f8             	sar    %rax
  400550:	75 02                	jne    400554 <register_tm_clones+0x24>
  400552:	5d                   	pop    %rbp
  400553:	c3                   	ret    
  400554:	ba 00 00 00 00       	mov    $0x0,%edx
  400559:	48 85 d2             	test   %rdx,%rdx
  40055c:	74 f4                	je     400552 <register_tm_clones+0x22>
  40055e:	5d                   	pop    %rbp
  40055f:	48 89 c6             	mov    %rax,%rsi
  400562:	bf 50 10 60 00       	mov    $0x601050,%edi
  400567:	ff e2                	jmp    *%rdx
  400569:	0f 1f 80 00 00 00 00 	nopl   0x0(%rax)

0000000000400570 <__do_global_dtors_aux>:
  400570:	80 3d d9 0a 20 00 00 	cmpb   $0x0,0x200ad9(%rip)        # 601050 <__TMC_END__>
  400577:	75 11                	jne    40058a <__do_global_dtors_aux+0x1a>
  400579:	55                   	push   %rbp
  40057a:	48 89 e5             	mov    %rsp,%rbp
  40057d:	e8 7e ff ff ff       	call   400500 <deregister_tm_clones>
  400582:	5d                   	pop    %rbp
  400583:	c6 05 c6 0a 20 00 01 	movb   $0x1,0x200ac6(%rip)        # 601050 <__TMC_END__>
  40058a:	f3 c3                	repz ret 
  40058c:	0f 1f 40 00          	nopl   0x0(%rax)

0000000000400590 <frame_dummy>:
  400590:	48 83 3d 88 08 20 00 	cmpq   $0x0,0x200888(%rip)        # 600e20 <__JCR_END__>
  400597:	00 
  400598:	74 1e                	je     4005b8 <frame_dummy+0x28>
  40059a:	b8 00 00 00 00       	mov    $0x0,%eax
  40059f:	48 85 c0             	test   %rax,%rax
  4005a2:	74 14                	je     4005b8 <frame_dummy+0x28>
  4005a4:	55                   	push   %rbp
  4005a5:	bf 20 0e 60 00       	mov    $0x600e20,%edi
  4005aa:	48 89 e5             	mov    %rsp,%rbp
  4005ad:	ff d0                	call   *%rax
  4005af:	5d                   	pop    %rbp
  4005b0:	e9 7b ff ff ff       	jmp    400530 <register_tm_clones>
  4005b5:	0f 1f 00             	nopl   (%rax)
  4005b8:	e9 73 ff ff ff       	jmp    400530 <register_tm_clones>

00000000004005bd <main>:
  4005bd:	55                   	push   %rbp
  4005be:	48 89 e5             	mov    %rsp,%rbp
  4005c1:	48 83 ec 10          	sub    $0x10,%rsp
  4005c5:	89 7d fc             	mov    %edi,-0x4(%rbp)
  4005c8:	48 89 75 f0          	mov    %rsi,-0x10(%rbp)
  4005cc:	83 7d fc 02          	cmpl   $0x2,-0x4(%rbp)
  4005d0:	75 51                	jne    400623 <main+0x66>
  4005d2:	48 8b 45 f0          	mov    -0x10(%rbp),%rax
  4005d6:	48 83 c0 08          	add    $0x8,%rax
  4005da:	48 8b 00             	mov    (%rax),%rax
  4005dd:	48 89 c6             	mov    %rax,%rsi
  4005e0:	bf c4 06 40 00       	mov    $0x4006c4,%edi
  4005e5:	b8 00 00 00 00       	mov    $0x0,%eax
  4005ea:	e8 a1 fe ff ff       	call   400490 <printf@plt>
  4005ef:	48 8b 45 f0          	mov    -0x10(%rbp),%rax
  4005f3:	48 83 c0 08          	add    $0x8,%rax
  4005f7:	48 8b 00             	mov    (%rax),%rax
  4005fa:	be da 06 40 00       	mov    $0x4006da,%esi
  4005ff:	48 89 c7             	mov    %rax,%rdi
  400602:	e8 a9 fe ff ff       	call   4004b0 <strcmp@plt>
  400607:	85 c0                	test   %eax,%eax
  400609:	75 0c                	jne    400617 <main+0x5a>
  40060b:	bf ea 06 40 00       	mov    $0x4006ea,%edi
  400610:	e8 6b fe ff ff       	call   400480 <puts@plt>
  400615:	eb 16                	jmp    40062d <main+0x70>
  400617:	bf fa 06 40 00       	mov    $0x4006fa,%edi
  40061c:	e8 5f fe ff ff       	call   400480 <puts@plt>
  400621:	eb 0a                	jmp    40062d <main+0x70>
  400623:	bf 01 07 40 00       	mov    $0x400701,%edi
  400628:	e8 53 fe ff ff       	call   400480 <puts@plt>
  40062d:	b8 00 00 00 00       	mov    $0x0,%eax
  400632:	c9                   	leave  
  400633:	c3                   	ret    
  400634:	66 2e 0f 1f 84 00 00 	cs nopw 0x0(%rax,%rax,1)
  40063b:	00 00 00 
  40063e:	66 90                	xchg   %ax,%ax

0000000000400640 <__libc_csu_init>:
  400640:	41 57                	push   %r15
  400642:	41 89 ff             	mov    %edi,%r15d
  400645:	41 56                	push   %r14
  400647:	49 89 f6             	mov    %rsi,%r14
  40064a:	41 55                	push   %r13
  40064c:	49 89 d5             	mov    %rdx,%r13
  40064f:	41 54                	push   %r12
  400651:	4c 8d 25 b8 07 20 00 	lea    0x2007b8(%rip),%r12        # 600e10 <__frame_dummy_init_array_entry>
  400658:	55                   	push   %rbp
  400659:	48 8d 2d b8 07 20 00 	lea    0x2007b8(%rip),%rbp        # 600e18 <__do_global_dtors_aux_fini_array_entry>
  400660:	53                   	push   %rbx
  400661:	4c 29 e5             	sub    %r12,%rbp
  400664:	31 db                	xor    %ebx,%ebx
  400666:	48 c1 fd 03          	sar    $0x3,%rbp
  40066a:	48 83 ec 08          	sub    $0x8,%rsp
  40066e:	e8 dd fd ff ff       	call   400450 <_init>
  400673:	48 85 ed             	test   %rbp,%rbp
  400676:	74 1e                	je     400696 <__libc_csu_init+0x56>
  400678:	0f 1f 84 00 00 00 00 	nopl   0x0(%rax,%rax,1)
  40067f:	00 
  400680:	4c 89 ea             	mov    %r13,%rdx
  400683:	4c 89 f6             	mov    %r14,%rsi
  400686:	44 89 ff             	mov    %r15d,%edi
  400689:	41 ff 14 dc          	call   *(%r12,%rbx,8)
  40068d:	48 83 c3 01          	add    $0x1,%rbx
  400691:	48 39 eb             	cmp    %rbp,%rbx
  400694:	75 ea                	jne    400680 <__libc_csu_init+0x40>
  400696:	48 83 c4 08          	add    $0x8,%rsp
  40069a:	5b                   	pop    %rbx
  40069b:	5d                   	pop    %rbp
  40069c:	41 5c                	pop    %r12
  40069e:	41 5d                	pop    %r13
  4006a0:	41 5e                	pop    %r14
  4006a2:	41 5f                	pop    %r15
  4006a4:	c3                   	ret    
  4006a5:	66 66 2e 0f 1f 84 00 	data16 cs nopw 0x0(%rax,%rax,1)
  4006ac:	00 00 00 00 

00000000004006b0 <__libc_csu_fini>:
  4006b0:	f3 c3                	repz ret 

Disassembly of section .fini:

00000000004006b4 <_fini>:
  4006b4:	48 83 ec 08          	sub    $0x8,%rsp
  4006b8:	48 83 c4 08          	add    $0x8,%rsp
  4006bc:	c3                   	ret    

┌─[✔]──[alpha@speed:🐧]──[~/Public/share_file/liveoverflow/liveoverflow_youtube/0x05_simple_crackme_intro_assembler]± ● master:
└──╼ $ 

```

`objdump -x license_1 | less` run this command
the important things which we are interested is 

file format 

```css
license_1:     file format elf64-x86-64
license_1
architecture: i386:x86-64, flags 0x00000112:
EXEC_P, HAS_SYMS, D_PAGED
start address 0x00000000004004d0

```

header section

```css
Program Header:
    PHDR off    0x0000000000000040 vaddr 0x0000000000400040 paddr 0x0000000000400040 align 2**3
         filesz 0x00000000000001f8 memsz 0x00000000000001f8 flags r-x
  INTERP off    0x0000000000000238 vaddr 0x0000000000400238 paddr 0x0000000000400238 align 2**0
         filesz 0x000000000000001c memsz 0x000000000000001c flags r--
    LOAD off    0x0000000000000000 vaddr 0x0000000000400000 paddr 0x0000000000400000 align 2**21
         filesz 0x000000000000083c memsz 0x000000000000083c flags r-x
    LOAD off    0x0000000000000e10 vaddr 0x0000000000600e10 paddr 0x0000000000600e10 align 2**21
         filesz 0x0000000000000240 memsz 0x0000000000000248 flags rw-
 DYNAMIC off    0x0000000000000e28 vaddr 0x0000000000600e28 paddr 0x0000000000600e28 align 2**3
         filesz 0x00000000000001d0 memsz 0x00000000000001d0 flags rw-
    NOTE off    0x0000000000000254 vaddr 0x0000000000400254 paddr 0x0000000000400254 align 2**2
         filesz 0x0000000000000044 memsz 0x0000000000000044 flags r--
EH_FRAME off    0x0000000000000710 vaddr 0x0000000000400710 paddr 0x0000000000400710 align 2**2
         filesz 0x0000000000000034 memsz 0x0000000000000034 flags r--
   STACK off    0x0000000000000000 vaddr 0x0000000000000000 paddr 0x0000000000000000 align 2**4
         filesz 0x0000000000000000 memsz 0x0000000000000000 flags rw-
   RELRO off    0x0000000000000e10 vaddr 0x0000000000600e10 paddr 0x0000000000600e10 align 2**0
         filesz 0x00000000000001f0 memsz 0x00000000000001f0 flags r--

```


```css
 STACK off    0x0000000000000000 vaddr 0x0000000000000000 paddr 0x0000000000000000 align 2**4
         filesz 0x0000000000000000 memsz 0x0000000000000000 flags rw- => rw means read write not executable
```

sections

```css
Sections:
Idx Name          Size      VMA               LMA               File off  Algn
  0 .interp       0000001c  0000000000400238  0000000000400238  00000238  2**0
                  CONTENTS, ALLOC, LOAD, READONLY, DATA
  1 .note.ABI-tag 00000020  0000000000400254  0000000000400254  00000254  2**2
                  CONTENTS, ALLOC, LOAD, READONLY, DATA
  2 .note.gnu.build-id 00000024  0000000000400274  0000000000400274  00000274  2**2
                  CONTENTS, ALLOC, LOAD, READONLY, DATA
  3 .gnu.hash     0000001c  0000000000400298  0000000000400298  00000298  2**3
                  CONTENTS, ALLOC, LOAD, READONLY, DATA
  4 .dynsym       00000090  00000000004002b8  00000000004002b8  000002b8  2**3
                  CONTENTS, ALLOC, LOAD, READONLY, DATA
  5 .dynstr       0000004b  0000000000400348  0000000000400348  00000348  2**0
                  CONTENTS, ALLOC, LOAD, READONLY, DATA
  6 .gnu.version  0000000c  0000000000400394  0000000000400394  00000394  2**1
                  CONTENTS, ALLOC, LOAD, READONLY, DATA
  7 .gnu.version_r 00000020  00000000004003a0  00000000004003a0  000003a0  2**3
                  CONTENTS, ALLOC, LOAD, READONLY, DATA
  8 .rela.dyn     00000018  00000000004003c0  00000000004003c0  000003c0  2**3
                  CONTENTS, ALLOC, LOAD, READONLY, DATA
  9 .rela.plt     00000078  00000000004003d8  00000000004003d8  000003d8  2**3
                  CONTENTS, ALLOC, LOAD, READONLY, DATA
 10 .init         0000001a  0000000000400450  0000000000400450  00000450  2**2
                  CONTENTS, ALLOC, LOAD, READONLY, CODE
 11 .plt          00000060  0000000000400470  0000000000400470  00000470  2**4
                  CONTENTS, ALLOC, LOAD, READONLY, CODE
 12 .text         000001e2  00000000004004d0  00000000004004d0  000004d0  2**4
                  CONTENTS, ALLOC, LOAD, READONLY, CODE
 13 .fini         00000009  00000000004006b4  00000000004006b4  000006b4  2**2
                  CONTENTS, ALLOC, LOAD, READONLY, CODE
 14 .rodata       0000004e  00000000004006c0  00000000004006c0  000006c0  2**2
                  CONTENTS, ALLOC, LOAD, READONLY, DATA
 15 .eh_frame_hdr 00000034  0000000000400710  0000000000400710  00000710  2**2
                  CONTENTS, ALLOC, LOAD, READONLY, DATA
 16 .eh_frame     000000f4  0000000000400748  0000000000400748  00000748  2**3
                  CONTENTS, ALLOC, LOAD, READONLY, DATA
 17 .init_array   00000008  0000000000600e10  0000000000600e10  00000e10  2**3
                  CONTENTS, ALLOC, LOAD, DATA
 18 .fini_array   00000008  0000000000600e18  0000000000600e18  00000e18  2**3
                  CONTENTS, ALLOC, LOAD, DATA
 19 .jcr          00000008  0000000000600e20  0000000000600e20  00000e20  2**3
                  CONTENTS, ALLOC, LOAD, DATA
 20 .dynamic      000001d0  0000000000600e28  0000000000600e28  00000e28  2**3
                  CONTENTS, ALLOC, LOAD, DATA
 21 .got          00000008  0000000000600ff8  0000000000600ff8  00000ff8  2**3
                  CONTENTS, ALLOC, LOAD, DATA
 22 .got.plt      00000040  0000000000601000  0000000000601000  00001000  2**3
                  CONTENTS, ALLOC, LOAD, DATA
 23 .data         00000010  0000000000601040  0000000000601040  00001040  2**3
                  CONTENTS, ALLOC, LOAD, DATA
 24 .bss          00000008  0000000000601050  0000000000601050  00001050  2**0
                  ALLOC
 25 .comment      0000004d  0000000000000000  0000000000000000  00001050  2**0
:

```

this section hold code section
```css
12 .text         000001e2  00000000004004d0  00000000004004d0  000004d0  2**4
                  CONTENTS, ALLOC, LOAD, READONLY, CODE
```

```css
(gdb) disassemble main
Dump of assembler code for function main:
   0x00000000004005bd <+0>:	push   %rbp
   0x00000000004005be <+1>:	mov    %rsp,%rbp
   0x00000000004005c1 <+4>:	sub    $0x10,%rsp
   0x00000000004005c5 <+8>:	mov    %edi,-0x4(%rbp)
   0x00000000004005c8 <+11>:	mov    %rsi,-0x10(%rbp)
   0x00000000004005cc <+15>:	cmpl   $0x2,-0x4(%rbp)
   0x00000000004005d0 <+19>:	jne    0x400623 <main+102>
   0x00000000004005d2 <+21>:	mov    -0x10(%rbp),%rax
   0x00000000004005d6 <+25>:	add    $0x8,%rax
   0x00000000004005da <+29>:	mov    (%rax),%rax
   0x00000000004005dd <+32>:	mov    %rax,%rsi
   0x00000000004005e0 <+35>:	mov    $0x4006c4,%edi
   0x00000000004005e5 <+40>:	mov    $0x0,%eax
   0x00000000004005ea <+45>:	call   0x400490 <printf@plt>
   0x00000000004005ef <+50>:	mov    -0x10(%rbp),%rax
   0x00000000004005f3 <+54>:	add    $0x8,%rax
   0x00000000004005f7 <+58>:	mov    (%rax),%rax
   0x00000000004005fa <+61>:	mov    $0x4006da,%esi
   0x00000000004005ff <+66>:	mov    %rax,%rdi
   0x0000000000400602 <+69>:	call   0x4004b0 <strcmp@plt>
   0x0000000000400607 <+74>:	test   %eax,%eax
   0x0000000000400609 <+76>:	jne    0x400617 <main+90>
   0x000000000040060b <+78>:	mov    $0x4006ea,%edi
   0x0000000000400610 <+83>:	call   0x400480 <puts@plt>
   0x0000000000400615 <+88>:	jmp    0x40062d <main+112>
   0x0000000000400617 <+90>:	mov    $0x4006fa,%edi
   0x000000000040061c <+95>:	call   0x400480 <puts@plt>
   0x0000000000400621 <+100>:	jmp    0x40062d <main+112>
   0x0000000000400623 <+102>:	mov    $0x400701,%edi
   0x0000000000400628 <+107>:	call   0x400480 <puts@plt>
   0x000000000040062d <+112>:	mov    $0x0,%eax
   0x0000000000400632 <+117>:	leave  
   0x0000000000400633 <+118>:	ret    
End of assembler dump.
(gdb) 

```

rodata string found here
```css
14 .rodata       0000004e  00000000004006c0  00000000004006c0  000006c0  2**2
                  CONTENTS, ALLOC, LOAD, READONLY, DATA
```

```css
(gdb) b *main+69
Breakpoint 1 at 0x400602
(gdb) r AAAA
Starting program: /home/saket/Public/share_file/liveoverflow/liveoverflow_youtube/0x05_simple_crackme_intro_assembler/license_1 AAAA
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
Checking License: AAAA

Breakpoint 1, 0x0000000000400602 in main ()
(gdb) info registers
rax            0x7fffffffe1bf      140737488347583
rbx            0x0                 0
rcx            0x1                 1
rdx            0x0                 0
rsi            0x4006da            4196058
rdi            0x7fffffffe1bf      140737488347583
rbp            0x7fffffffdce0      0x7fffffffdce0
rsp            0x7fffffffdcd0      0x7fffffffdcd0
r8             0x0                 0
r9             0x7fffffff          2147483647
r10            0x0                 0
r11            0x246               582
r12            0x7fffffffddf8      140737488346616
r13            0x4005bd            4195773
r14            0x0                 0
r15            0x7ffff7ffd040      140737354125376
rip            0x400602            0x400602 <main+69>
eflags         0x216               [ PF AF IF ]
cs             0x33                51
ss             0x2b                43
ds             0x0                 0
es             0x0                 0
fs             0x0                 0
gs             0x0                 0
(gdb) x/s 0x4006da
0x4006da:	"AAAA-Z10N-42-OK"
(gdb) 

```

strace

```css
┌─[✔]──[alpha@speed:🐧]──[~/Public/share_file/liveoverflow/liveoverflow_youtube/0x05_simple_crackme_intro_assembler]± ● master:
└──╼ $ strace ./license_1 
execve("./license_1", ["./license_1"], 0x7fff2f353ce0 /* 55 vars */) = 0
brk(NULL)                               = 0xf87000
arch_prctl(0x3001 /* ARCH_??? */, 0x7ffdf173b430) = -1 EINVAL (Invalid argument)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7ff8bb995000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
newfstatat(3, "", {st_mode=S_IFREG|0644, st_size=67959, ...}, AT_EMPTY_PATH) = 0
mmap(NULL, 67959, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7ff8bb984000
close(3)                                = 0
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\237\2\0\0\0\0\0"..., 832) = 832
pread64(3, "\6\0\0\0\4\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0"..., 784, 64) = 784
pread64(3, "\4\0\0\0 \0\0\0\5\0\0\0GNU\0\2\0\0\300\4\0\0\0\3\0\0\0\0\0\0\0"..., 48, 848) = 48
pread64(3, "\4\0\0\0\24\0\0\0\3\0\0\0GNU\0I\17\357\204\3$\f\221\2039x\324\224\323\236S"..., 68, 896) = 68
newfstatat(3, "", {st_mode=S_IFREG|0755, st_size=2220400, ...}, AT_EMPTY_PATH) = 0
pread64(3, "\6\0\0\0\4\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0"..., 784, 64) = 784
mmap(NULL, 2264656, PROT_READ, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7ff8bb75b000
mprotect(0x7ff8bb783000, 2023424, PROT_NONE) = 0
mmap(0x7ff8bb783000, 1658880, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x28000) = 0x7ff8bb783000
mmap(0x7ff8bb918000, 360448, PROT_READ, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1bd000) = 0x7ff8bb918000
mmap(0x7ff8bb971000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x215000) = 0x7ff8bb971000
mmap(0x7ff8bb977000, 52816, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7ff8bb977000
close(3)                                = 0
mmap(NULL, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7ff8bb758000
arch_prctl(ARCH_SET_FS, 0x7ff8bb758740) = 0
set_tid_address(0x7ff8bb758a10)         = 26436
set_robust_list(0x7ff8bb758a20, 24)     = 0
rseq(0x7ff8bb7590e0, 0x20, 0, 0x53053053) = 0
mprotect(0x7ff8bb971000, 16384, PROT_READ) = 0
mprotect(0x600000, 4096, PROT_READ)     = 0
mprotect(0x7ff8bb9cf000, 8192, PROT_READ) = 0
prlimit64(0, RLIMIT_STACK, NULL, {rlim_cur=8192*1024, rlim_max=RLIM64_INFINITY}) = 0
munmap(0x7ff8bb984000, 67959)           = 0
newfstatat(1, "", {st_mode=S_IFCHR|0620, st_rdev=makedev(0x88, 0x1), ...}, AT_EMPTY_PATH) = 0
getrandom("\x28\x9e\xf8\xb1\x06\x72\xfc\x48", 8, GRND_NONBLOCK) = 8
brk(NULL)                               = 0xf87000
brk(0xfa8000)                           = 0xfa8000
write(1, "Usage: <key>\n", 13Usage: <key>
)          = 13
exit_group(0)                           = ?
+++ exited with 0 +++


```

tell linux for execution 
```css
execve("./license_1", ["./license_1"], 0x7fff2f353ce0 /* 55 vars */) = 0
```

```css
┌─[✔]──[alpha@speed:🍓]──[~/Public/share_file/liveoverflow/liveoverflow_youtube/0x05_simple_crackme_intro_assembler]± ● master:
└──╼ $ strace ./license_1  AAAAKKK
execve("./license_1", ["./license_1", "AAAAKKK"], 0x7ffd3f360b78 /* 55 vars */) = 0
brk(NULL)                               = 0xc4c000
arch_prctl(0x3001 /* ARCH_??? */, 0x7fff517a8690) = -1 EINVAL (Invalid argument)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4470ee9000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
newfstatat(3, "", {st_mode=S_IFREG|0644, st_size=67959, ...}, AT_EMPTY_PATH) = 0
mmap(NULL, 67959, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f4470ed8000
close(3)                                = 0
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\237\2\0\0\0\0\0"..., 832) = 832
pread64(3, "\6\0\0\0\4\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0"..., 784, 64) = 784
pread64(3, "\4\0\0\0 \0\0\0\5\0\0\0GNU\0\2\0\0\300\4\0\0\0\3\0\0\0\0\0\0\0"..., 48, 848) = 48
pread64(3, "\4\0\0\0\24\0\0\0\3\0\0\0GNU\0I\17\357\204\3$\f\221\2039x\324\224\323\236S"..., 68, 896) = 68
newfstatat(3, "", {st_mode=S_IFREG|0755, st_size=2220400, ...}, AT_EMPTY_PATH) = 0
pread64(3, "\6\0\0\0\4\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0"..., 784, 64) = 784
mmap(NULL, 2264656, PROT_READ, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f4470caf000
mprotect(0x7f4470cd7000, 2023424, PROT_NONE) = 0
mmap(0x7f4470cd7000, 1658880, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x28000) = 0x7f4470cd7000
mmap(0x7f4470e6c000, 360448, PROT_READ, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1bd000) = 0x7f4470e6c000
mmap(0x7f4470ec5000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x215000) = 0x7f4470ec5000
mmap(0x7f4470ecb000, 52816, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f4470ecb000
close(3)                                = 0
mmap(NULL, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4470cac000
arch_prctl(ARCH_SET_FS, 0x7f4470cac740) = 0
set_tid_address(0x7f4470caca10)         = 26506
set_robust_list(0x7f4470caca20, 24)     = 0
rseq(0x7f4470cad0e0, 0x20, 0, 0x53053053) = 0
mprotect(0x7f4470ec5000, 16384, PROT_READ) = 0
mprotect(0x600000, 4096, PROT_READ)     = 0
mprotect(0x7f4470f23000, 8192, PROT_READ) = 0
prlimit64(0, RLIMIT_STACK, NULL, {rlim_cur=8192*1024, rlim_max=RLIM64_INFINITY}) = 0
munmap(0x7f4470ed8000, 67959)           = 0
newfstatat(1, "", {st_mode=S_IFCHR|0620, st_rdev=makedev(0x88, 0x1), ...}, AT_EMPTY_PATH) = 0
getrandom("\xcc\xe5\x60\xe1\x1a\xe6\xc5\xba", 8, GRND_NONBLOCK) = 8
brk(NULL)                               = 0xc4c000
brk(0xc6d000)                           = 0xc6d000
write(1, "Checking License: AAAAKKK\n", 26Checking License: AAAAKKK
) = 26
write(1, "WRONG!\n", 7WRONG!
)                 = 7
exit_group(0)                           = ?
+++ exited with 0 +++

```

```css
write(1, "Checking License: AAAAKKK\n", 26Checking License: AAAAKKK
) = 26
write(1, "WRONG!\n", 7WRONG!
)                 = 7
```

```css
┌──(kali㉿kali)-[~/Downloads/pico_ctf_lab/liveoverflow_youtube/0x05_simple_crackme_intro_assembler]± ● master
└─$ ltrace ./license_1
__libc_start_main(["./license_1"] <unfinished ...>
puts("Usage: <key>"Usage: <key>
)                                                                                                = 13
+++ exited (status 0) +++

```

```css
┌──(kali㉿kali)-[~/Downloads/pico_ctf_lab/liveoverflow_youtube/0x05_simple_crackme_intro_assembler]± ● master
└─$ ltrace ./license_1 AAAAA
__libc_start_main(["./license_1", "AAAAA"] <unfinished ...>
printf("Checking License: %s\n", "AAAAA"Checking License: AAAAA
)                                                                           = 24
strcmp("AAAAA", "AAAA-Z10N-42-OK")                                                                                  = 20
puts("WRONG!"WRONG!
)                                                                                                      = 7
+++ exited (status 0) +++

```

radare2

```css
┌──(kali㉿kali)-[~/Downloads/pico_ctf_lab/liveoverflow_youtube/0x05_simple_crackme_intro_assembler]± ● master
└─$ r2 ./license_1
WARN: Relocs has not been applied. Please use `-e bin.relocs.apply=true` or `-e bin.cache=true` next time
[0x004004d0]> aaa
INFO: Analyze all flags starting with sym. and entry0 (aa)
INFO: Analyze imports (af@@@i)
INFO: Analyze entrypoint (af@ entry0)
INFO: Analyze symbols (af@@@s)
INFO: Analyze all functions arguments/locals (afva@@@F)
INFO: Analyze function calls (aac)
INFO: Analyze len bytes of instructions for references (aar)
INFO: Finding and parsing C++ vtables (avrr)
INFO: Analyzing methods (af @@ method.*)
INFO: Recovering local variables (afva@@@F)
INFO: Type matching analysis for all functions (aaft)
INFO: Propagate noreturn information (aanr)
INFO: Use -AA or aaaa to perform additional experimental analysis
[0x004004d0]> 

```

```css
[0x004004d0]> afl
0x00400480    1      6 sym.imp.puts
0x00400490    1      6 sym.imp.printf
0x004004a0    1      6 sym.imp.__libc_start_main
0x004004b0    1      6 sym.imp.strcmp
0x004004d0    1     41 entry0
0x00400500    4     41 sym.deregister_tm_clones
0x00400530    4     57 sym.register_tm_clones
0x00400570    3     28 entry.fini0
0x00400590    4     42 entry.init0
0x004006b0    1      2 sym.__libc_csu_fini
0x004006b4    1      9 sym._fini
0x00400640    4    101 sym.__libc_csu_init
0x004005bd    6    119 main
0x00400450    3     26 sym._init
0x004004c0    1      6 loc.imp.__gmon_start__
[0x004004d0]> 

```

```css
[0x004004d0]> ?
Usage: [.][times][cmd][~grep][@[@iter]addr!size][|>pipe] ; ...
Append '?' to any char command to get detailed help
Prefix with number to repeat command N times (f.ex: 3x)
| %var=value              alias for 'env' command
| "[?]["..|.."]           quote to not evaluate special chars
| '[...]                  run a command without evaluating any special chars (see ?')
| *[?] off[=[0x]value]    pointer read/write data/values (see ?v, wx, wv)
| (macro arg0 arg1)       manage scripting macros
| .[?] [-|(m)|f|!sh|cmd]  Define macro or load r2, cparse or rlang file
| ,[?] [/jhr]             create and query or filter a table with data from file
| :cmd                    run an io command (same as =!)
| -[?]                    open editor and run the r2 commands in the saved document
| _[?]                    Print last output
| =[?] [cmd]              submit or listen to remote commands
| <[str]                  feed stdin with given escaped string
| /[?]                    search for bytes, regexps, patterns, ..
| ![?] [cmd]              run given command as in system(3)
| #[?] !lang [..]         Hashbang to run an rlang script
| {[?] ...}               run a command using the json syntax for r2pipe2
| a[?]                    analysis commands
| b[?]                    display or change the block size
| c[?] [arg]              compare block with given data
| C[?]                    code metadata (comments, format, hints, ..)
| d[?]                    debugger commands
| e[?] [a[=b]]            list/get/set config evaluable vars
| f[?] [name][sz][at]     add flag at current address
| g[?] [arg]              generate shellcodes with r_egg
| i[?] [file]             get info about opened file from r_bin
| k[?] [query]            evaluate an sdb query
| l[?] [filepattern]      list files and directories
| L[?] [-] [plugin]       list, unload load r2 plugins
| m[?]                    mount filesystems and inspect its contents
| o[?] [file] ([addr])    open file at optional address
| p[?] [len]              print current block with format and length
| P[?]                    project management utilities
| q[?] [ret]              quit program with a return value
| r[?] [len]              resize file
| s[?] [addr]             seek to given address
| t[?]                    types, noreturn, signatures, C parser and more
| T[?] [-] [num|msg]      text log utility (used to chat, sync, log, ...)
| u[?]                    uname/undo seek/write
| v                       panels mode
| V                       visual mode (Vv: func/var, VV: graph mode, ...)
| w[?] [str]              multiple write operations
| x[?] [len]              alias for 'px' (print hexadecimal)
| y[?] [len] [[[@]addr    yank/paste bytes from/to memory
| z[?]                    zignatures management
| ?[??][expr]             help or evaluate math expression
| ?$?                     show available '$' variables and aliases
| ?@?                     misc help for '@' (seek), '~' (grep) (see ~?""?)
| ?>?                     output redirection
| ?|?                     help for '|' (pipe)
[0x004004d0]> 

```

```css
| ?|?                     help for '|' (pipe)
[0x004004d0]> a?
Usage: a  [abdefFghoprxstc] [...]
| a                alias for aai - analysis information
| a:[cmd]          run a command implemented by an analysis plugin (like : for io)
| a*               same as afl*;ah*;ax*
| aa[?]            analyze all (fcns + bbs) (aa0 to avoid sub renaming)
| a8 [hexpairs]    analyze bytes
| ab[?]            analyze basic block
| ac[?]            manage classes
| aC[?]            analyze function call
| ad[?]            analyze data trampoline (wip) (see 'aod' to describe mnemonics)
| ad [from] [to]   analyze data pointers to (from-to)
| ae[?] [expr]     analyze opcode eval expression (see ao)
| af[?]            analyze functions
| aF               same as above, but using anal.depth=1
| ag[?] [options]  draw graphs in various formats
| ah[?]            analysis hints (force opcode size, ...)
| ai [addr]        address information (show perms, stack, heap, ...)
| aj               same as a* but in json (aflj)
| aL[jq]           list all asm/anal plugins (See `e asm.arch=?` and `La[jq]`)
| an[?] [name]     show/rename/create whatever var/flag/function used in current instruction
| ao[?] [len]      analyze Opcodes (or emulate it)
| aO[?] [len]      analyze N instructions in M bytes
| ap               find prelude for current offset
| ar[?]            like 'dr' but for the esil vm. (registers)
| as[?] [num]      analyze syscall using dbg.reg
| av[?] [.]        show vtables
| avg[?] [.]       manage global variables
| ax[?]            manage refs/xrefs (see also afx?)
[0x004004d0]> 

```

```css
[0x004004d0]> af?
Usage: af
| af ([name]) ([addr])                     analyze functions (start at addr or $$)
| af+ addr name [type] [diff]              hand craft a function (requires afb+)
| af- [addr]                               clean all function analysis data (or function at addr)
| afa                                      analyze function arguments in a call (afal honors dbg.funcarg)
| afB 16                                   set current function as thumb (change asm.bits)
| afb[?] [addr]                            List basic blocks of given function
| afb+ fcnA bbA sz [j] [f] ([t]( [d]))     add bb to function @ fcnaddr
| afbF([0|1])                              Toggle the basic-block 'folded' attribute
| afc[?] type @[addr]                      set calling convention for function
| afC[?] ([addr])@[addr]                   calculate the Cycles (afC) or Cyclomatic Complexity (afCc)
| afd[addr]                                show function + delta for given offset
| afF[1|0|]                                fold/unfold/toggle
| afi [addr|fcn.name]                      show function(s) information (verbose afl)
| afj [tableaddr] [elem_sz] [count] [seg]  analyze function jumptable (adding seg to each elem)
| afl[?] [ls*] [fcn name]                  list functions (addr, size, bbs, name) (see afll)
| afm name                                 merge two functions
| afM name                                 print functions map
| afn[?] name [addr]                       rename name for function at address (change flag too)
| afna                                     suggest automatic name for current offset
| afo[?j] [fcn.name]                       show address for the function name or current offset
| afr ([name]) ([addr])                    analyze functions recursively
| afs[?] ([fcnsign])                       get/set function signature at current address (afs! uses cfg.editor)
| afS[stack_size]                          set stack frame size for function at current address
| aft[?]                                   type matching, type propagation
| afu addr                                 resize and analyze function from current address until addr
| afv[?]                                   manipulate args, registers and variables in function
| afx[m]                                   list function references
[0x004004d0]> 

```

```css
[0x004004d0]> s sym.main 
[0x004005bd]> pdf
            ; ICOD XREF from entry0 @ 0x4004ed(r)
┌ 119: int main (uint32_t argc, char **argv);
│ `- args(rdi, rsi) vars(2:sp[0xc..0x18])
│           0x004005bd      55             push rbp
│           0x004005be      4889e5         mov rbp, rsp
│           0x004005c1      4883ec10       sub rsp, 0x10
│           0x004005c5      897dfc         mov dword [var_4h], edi     ; argc
│           0x004005c8      488975f0       mov qword [s1], rsi         ; argv
│           0x004005cc      837dfc02       cmp dword [var_4h], 2
│       ┌─< 0x004005d0      7551           jne 0x400623
│       │   0x004005d2      488b45f0       mov rax, qword [s1]
│       │   0x004005d6      4883c008       add rax, 8
│       │   0x004005da      488b00         mov rax, qword [rax]
│       │   0x004005dd      4889c6         mov rsi, rax
│       │   0x004005e0      bfc4064000     mov edi, str.Checking_License:__s_n ; 0x4006c4 ; "Checking License: %s\n" ; const char *format
│       │   0x004005e5      b800000000     mov eax, 0
│       │   0x004005ea      e8a1feffff     call sym.imp.printf         ; int printf(const char *format)
│       │   0x004005ef      488b45f0       mov rax, qword [s1]
│       │   0x004005f3      4883c008       add rax, 8
│       │   0x004005f7      488b00         mov rax, qword [rax]
│       │   0x004005fa      beda064000     mov esi, str.AAAA_Z10N_42_OK ; 0x4006da ; "AAAA-Z10N-42-OK" ; const char *s2
│       │   0x004005ff      4889c7         mov rdi, rax                ; const char *s1
│       │   0x00400602      e8a9feffff     call sym.imp.strcmp         ; int strcmp(const char *s1, const char *s2)
│       │   0x00400607      85c0           test eax, eax
│      ┌──< 0x00400609      750c           jne 0x400617
│      ││   0x0040060b      bfea064000     mov edi, str.Access_Granted_ ; 0x4006ea ; "Access Granted!" ; const char *s
│      ││   0x00400610      e86bfeffff     call sym.imp.puts           ; int puts(const char *s)
│     ┌───< 0x00400615      eb16           jmp 0x40062d
│     │││   ; CODE XREF from main @ 0x400609(x)
│     │└──> 0x00400617      bffa064000     mov edi, str.WRONG_         ; 0x4006fa ; "WRONG!" ; const char *s
│     │ │   0x0040061c      e85ffeffff     call sym.imp.puts           ; int puts(const char *s)
│     │┌──< 0x00400621      eb0a           jmp 0x40062d
│     │││   ; CODE XREF from main @ 0x4005d0(x)
│     ││└─> 0x00400623      bf01074000     mov edi, str.Usage:__key_   ; 0x400701 ; "Usage: <key>" ; const char *s
│     ││    0x00400628      e853feffff     call sym.imp.puts           ; int puts(const char *s)
│     ││    ; CODE XREFS from main @ 0x400615(x), 0x400621(x)
│     └└──> 0x0040062d      b800000000     mov eax, 0
│           0x00400632      c9             leave
└           0x00400633      c3             ret
[0x004005bd]> 

```

type capital `VV` to enter visual mode

when you press `?` it will display help menu  capital `R` is important key

now debugging using radare2
```css
┌──(kali㉿kali)-[~/Downloads/pico_ctf_lab/liveoverflow_youtube/0x05_simple_crackme_intro_assembler]± ● master
└─$ r2 -d ./license_1 
WARN: Relocs has not been applied. Please use `-e bin.relocs.apply=true` or `-e bin.cache=true` next time
[0x7f4829a1fb00]> s sym.
sym._init                   sym.imp.puts                sym.imp.printf              sym.imp.__libc_start_main   sym.imp.strcmp              
sym._start                  sym.deregister_tm_clones    sym.register_tm_clones      sym.__do_global_dtors_aux   sym.frame_dummy             
sym.main                    sym.__libc_csu_init         sym.__libc_csu_fini         sym._fini                   
[0x7f4829a1fb00]> s sym.main 
[0x004005bd]> 

```

```css
[0x004005bd]> aaa
INFO: Analyze all flags starting with sym. and entry0 (aa)
INFO: Analyze imports (af@@@i)
INFO: Analyze entrypoint (af@ entry0)
INFO: Analyze symbols (af@@@s)
INFO: Analyze all functions arguments/locals (afva@@@F)
INFO: Analyze function calls (aac)
INFO: Analyze len bytes of instructions for references (aar)
INFO: Finding and parsing C++ vtables (avrr)
INFO: Analyzing methods (af @@ method.*)
INFO: Recovering local variables (afva@@@F)
INFO: Skipping type matching analysis in debugger mode (aaft)
INFO: Propagate noreturn information (aanr)
INFO: Use -AA or aaaa to perform additional experimental analysis
[0x004005bd]> pdf
            ; ICOD XREF from entry0 @ 0x4004ed(r)
┌ 119: int main (int argc, char **argv);
│ `- args(rdi, rsi) vars(2:sp[0xc..0x18])
│           0x004005bd      55             push rbp
│           0x004005be      4889e5         mov rbp, rsp
│           0x004005c1      4883ec10       sub rsp, 0x10
│           0x004005c5      897dfc         mov dword [var_4h], edi     ; argc
│           0x004005c8      488975f0       mov qword [var_10h], rsi    ; argv
│           0x004005cc      837dfc02       cmp dword [var_4h], 2
│       ┌─< 0x004005d0      7551           jne 0x400623
│       │   0x004005d2      488b45f0       mov rax, qword [var_10h]
│       │   0x004005d6      4883c008       add rax, 8
│       │   0x004005da      488b00         mov rax, qword [rax]
│       │   0x004005dd      4889c6         mov rsi, rax
│       │   0x004005e0      bfc4064000     mov edi, str.Checking_License:__s_n ; 0x4006c4 ; "Checking License: %s\n"
│       │   0x004005e5      b800000000     mov eax, 0
│       │   0x004005ea      e8a1feffff     call sym.imp.printf         ; int printf(const char *format)
│       │   0x004005ef      488b45f0       mov rax, qword [var_10h]
│       │   0x004005f3      4883c008       add rax, 8
│       │   0x004005f7      488b00         mov rax, qword [rax]
│       │   0x004005fa      beda064000     mov esi, str.AAAA_Z10N_42_OK ; 0x4006da ; "AAAA-Z10N-42-OK"
│       │   0x004005ff      4889c7         mov rdi, rax
│       │   0x00400602      e8a9feffff     call sym.imp.strcmp         ; int strcmp(const char *s1, const char *s2)
│       │   0x00400607      85c0           test eax, eax
│      ┌──< 0x00400609      750c           jne 0x400617
│      ││   0x0040060b      bfea064000     mov edi, str.Access_Granted_ ; 0x4006ea ; "Access Granted!"
│      ││   0x00400610      e86bfeffff     call sym.imp.puts           ; int puts(const char *s)
│     ┌───< 0x00400615      eb16           jmp 0x40062d
│     │││   ; CODE XREF from main @ 0x400609(x)
│     │└──> 0x00400617      bffa064000     mov edi, str.WRONG_         ; 0x4006fa ; "WRONG!"
│     │ │   0x0040061c      e85ffeffff     call sym.imp.puts           ; int puts(const char *s)
│     │┌──< 0x00400621      eb0a           jmp 0x40062d
│     │││   ; CODE XREF from main @ 0x4005d0(x)
│     ││└─> 0x00400623      bf01074000     mov edi, str.Usage:__key_   ; 0x400701 ; "Usage: <key>"
│     ││    0x00400628      e853feffff     call sym.imp.puts           ; int puts(const char *s)
│     ││    ; CODE XREFS from main @ 0x400615(x), 0x400621(x)
│     └└──> 0x0040062d      b800000000     mov eax, 0
│           0x00400632      c9             leave
└           0x00400633      c3             ret
[0x004005bd]> db 0x004005bd => this is breakpoint
[0x004005bd]> 
```

now press capital `VV`
now to run the program type `:dc` (colon dc)

```css
> dc
INFO: hit breakpoint at: 0x4005bd
> 

```

now press enter and press `s` you will see `rip` in `Graph`
`shift +s` which means capital `S` => step into  
press `q` for quit

now summary how to debug

```css
r2 -d ./license_1 
s main or s sym.main => both will do same thing
aaa
pdf
db <breakpoint>
VV
:dc then press enter
s or Shift + s
q

```