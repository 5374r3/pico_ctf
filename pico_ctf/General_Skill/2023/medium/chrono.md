### chrono

#Medium #General-skills #picoCTF2023 #linux

Author: Mubarak Mikail

#### Description

How to automate tasks to run at intervals on linux servers?Use ssh to connect to this server:

```
Server: saturn.picoctf.net
Port: 51539
Username: picoplayer 
Password: ENAFb6zfzn
```

##### Solution:

```css
picoplayer@challenge:~$ whereis crontab
crontab: /usr/bin/crontab /etc/crontab
picoplayer@challenge:~$ cat /etc/crontab 
# picoCTF{Sch3DUL7NG_T45K3_L1NUX_1d781160}
picoplayer@challenge:~$ 

```