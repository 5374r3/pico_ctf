### Magikarp Ground Mission

Author: syreal
#easy #General-skills #picoCTF2021
#### Description

Do you know how to move between directories and read files in the shell? Start the container, `ssh` to it, and then `ls` once connected to begin. Login via `ssh` as `ctf-player` with the password, `6dee9772`

---
`ssh ctf-player@venus.picoctf.net -p 60899`

| Challenge Endpoints |                                             |
| ------------------- | ------------------------------------------- |
| SSH                 | `ssh ctf-player@venus.picoctf.net -p 60899` |
|                     |                                             |
##### Solution:
login through ssh and enter the given password

```css
ctf-player@pico-chall$ ls
1of3.flag.txt  instructions-to-2of3.txt
ctf-player@pico-chall$ cat 1of3.flag.txt
picoCTF{xxsh_
ctf-player@pico-chall$ cat instructions-to-2of3.txt
Next, go to the root of all things, more succinctly `/`
ctf-player@pico-chall$ cd /
ctf-player@pico-chall$ ls
2of3.flag.txt  boot  etc   instructions-to-3of3.txt  lib64  mnt  proc  run   srv  tmp  var
bin            dev   home  lib                       media  opt  root  sbin  sys  usr
ctf-player@pico-chall$ cat  2of3.flag.txt
0ut_0f_\/\/4t3r_
ctf-player@pico-chall$ cat instructions-to-3of3.txt
Lastly, ctf-player, go home... more succinctly `~`
ctf-player@pico-chall$ cd home
ctf-player@pico-chall$ ls
ctf-player
ctf-player@pico-chall$ cd ctf-player
ctf-player@pico-chall$ ls
3of3.flag.txt  drop-in
ctf-player@pico-chall$ cat 3of3.flag.txt
540e4e79}
ctf-player@pico-chall$ 

```

```css
cat 1of3.flag.txt
picoCTF{xxsh_
cat  2of3.flag.txt
0ut_0f_\/\/4t3r_
cat 3of3.flag.txt
540e4e79}

# final flag is picoCTF{xxsh_0ut_0f_\/\/4t3r_540e4e79}

```