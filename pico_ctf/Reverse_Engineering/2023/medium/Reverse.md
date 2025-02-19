### Reverse

#Medium #Reverse_Engineering  #picoCTF2023

Author: Mubarak Mikail

#### Description

Try reversing this file? Can ya?I forgot the password to this [file](https://artifacts.picoctf.net/c/273/ret). Please find it for me?

##### Solution:

```css
┌─[✔]──[alpha@speed:🍑]──[~/Videos]:
└──╼ $ file ret 
ret: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=64856d07d138e412faf30b9722d92f507e3b5c9c, for GNU/Linux 3.2.0, not stripped
```

use ghidra to decode the code and select main function

```c
undefined8 main(void)

{
  int iVar1;
  long in_FS_OFFSET;
  char local_68 [48];
  char local_38 [40];
  long local_10;
  
  local_10 = *(long *)(in_FS_OFFSET + 0x28);
  builtin_strncpy(local_38,"picoCTF{3lf_r3v3r5ing_succe55ful_d7b14d4",0x28);
  printf("Enter the password to unlock this file: ");
  __isoc99_scanf(&DAT_00102031,local_68);
  printf("You entered: %s\n",local_68);
  iVar1 = strcmp(local_68,local_38);
  if (iVar1 == 0) {
    puts("Password correct, please see flag: picoCTF{3lf_r3v3r5ing_succe55ful_d7b14d43}");
    puts(local_38);
  }
  else {
    puts("Access denied");
  }
  if (local_10 != *(long *)(in_FS_OFFSET + 0x28)) {
                    /* WARNING: Subroutine does not return */
    __stack_chk_fail();
  }
  return 0;
}

```

flag is `picoCTF{3lf_r3v3r5ing_succe55ful_d7b14d43}`

2nd method using strings command to get flag

```css
┌─[✔]──[alpha@speed:🍓]──[~/Videos]:
└──╼ $ strings ret 
/lib64/ld-linux-x86-64.so.2
/P~;\
libc.so.6
__isoc99_scanf
puts
__stack_chk_fail
printf
__cxa_finalize
strcmp
__libc_start_main
GLIBC_2.7
GLIBC_2.4
GLIBC_2.2.5
_ITM_deregisterTMCloneTable
__gmon_start__
_ITM_registerTMCloneTable
u+UH
picoCTF{H
3lf_r3v3H
r5ing_suH
cce55fulH
_d7b14d4H
[]A\A]A^A_
Enter the password to unlock this file: 
You entered: %s
Password correct, please see flag: picoCTF{3lf_r3v3r5ing_succe55ful_d7b14d43}
Access denied
:*3$"
GCC: (Ubuntu 9.4.0-1ubuntu1~20.04.1) 9.4.0
crtstuff.c
deregister_tm_clones
```