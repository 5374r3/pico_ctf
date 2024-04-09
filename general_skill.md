# Challenges
### Obedient Cat
Tags: #General-skills
#### Description
This file has a flag in plain sight (aka "in-the-clear"). [Download flag](https://mercury.picoctf.net/static/a5683698ac318b47bd060cb786859f23/flag)
##### Solution: 
Download flag from description and submit

---
### Python Wrangling
Tags: #General-skills #python
#### Description
Python scripts are invoked kind of like programs in the Terminal... 
Can you run [this Python script](https://mercury.picoctf.net/static/2ac2139344d2e734d5d638ac928f1a8d/ende.py) using [this password](https://mercury.picoctf.net/static/2ac2139344d2e734d5d638ac928f1a8d/pw.txt) to get [the flag](https://mercury.picoctf.net/static/2ac2139344d2e734d5d638ac928f1a8d/flag.txt.en)?
##### Solution: 
 download python script file, password file and flag file
`python scriptfile.py -d flagfile.txt.en`
enter password you will get flag `picoCTF{4p0110_1n_7h3_h0us3_68f88f93}`

---
### Wave a flag
Tags: #General-skills 
#### Description
Can you invoke help flags for a tool or binary?
[This program](https://mercury.picoctf.net/static/fc1d77192c544314efece5dd309092e3/warm) has extraordinarily helpful information...
##### Solution: 
Download file and make it executable using chmod  +x filename
now execute ./filename
run ./filename -h to get flag
`picoCTF{b1scu1ts_4nd_gr4vy_6635aa47}`

---
### Nice netcat...
Tags: #General-skills 
#### Description
There is a nice program that you can talk to by using this command in a shell: 
`$ nc mercury.picoctf.net 49039`, but it doesn't speak English...
##### Solution: 
 run `nc mercury.picoctf.net 49039` into terminal you will get ASCII decimal value
convert decimal to char you will get flag or convert ASCII to text
`picoCTF{g00d_k1tty!_n1c3_k1tty!_3d84edc8}`

---
### Static ain't always noise
Tags: #General-skills 
#### Description
Can you look at the data in this binary: [static](https://mercury.picoctf.net/static/e9dd71b5d11023873b8abe99cdb45551/static)? This [BASH script](https://mercury.picoctf.net/static/e9dd71b5d11023873b8abe99cdb45551/ltdis.sh) might help!
##### Solution: 
run `sh ltdis.sh static` a file will generate *static.ltdis.strings.txt*
find flag `picoCTF{d15a5m_t34s3r_ae0b3ef2}`

---
### Tab, Tab, Attack
Tags:  #General-skills 
#### Description
Using tabcomplete in the Terminal will add years to your life, esp. when dealing with long rambling directory structures and filenames: [Addadshashanammu.zip](https://mercury.picoctf.net/static/a350754a299cb58988d6d47aed5be3ba/Addadshashanammu.zip)
##### Solution:
simply unzip and go to location using tab command and you will get `fang-of-haynekhtnamet` file name
run in terminal `./fang-of-haynekhtnamet`
`*ZAP!* picoCTF{l3v3l_up!_t4k3_4_r35t!_a00cae70}`

---
### Magikarp Ground Mission
Tags: #General-skills 
#### Description
Do you know how to move between directories and read files in the shell? Start the container, `ssh` to it, and then `ls` once connected to begin. Login via `ssh` as `ctf-player` with the password, `6dee9772`
Additional details will be available after launching your challenge instance.
##### Solution:
```shell
ssh ctf-player@venus.picoctf.net -p 51697

ctf-player@pico-chall$ ls
1of3.flag.txt  instructions-to-2of3.txt
ctf-player@pico-chall$ cat 1of3.flag.txt 
picoCTF{xxsh_
ctf-player@pico-chall$ pwd
/home/ctf-player/drop-in
ctf-player@pico-chall$ cd ..
ctf-player@pico-chall$ ls
3of3.flag.txt  drop-in
ctf-player@pico-chall$ cat 3of3.flag.txt 
540e4e79}
ctf-player@pico-chall$ pwd
/home/ctf-player
ctf-player@pico-chall$ cd ..
ctf-player@pico-chall$ ls
ctf-player
ctf-player@pico-chall$ cd ..
ctf-player@pico-chall$ ls
2of3.flag.txt  boot  etc   instructions-to-3of3.txt  lib64  mnt  proc  run   srv  tmp  var
bin            dev   home  lib                       media  opt  root  sbin  sys  usr
ctf-player@pico-chall$ cat 2of3.flag.txt 
0ut_0f_\/\/4t3r_
```

flagpart1: `picoCTF{xxsh_`
flagpart2: `0ut_0f_\/\/4t3r_`
flagpart3: `540e4e79}`

final flag: `picoCTF{xxsh_0ut_0f_\/\/4t3r_540e4e79}`

----
### Super SSH
Tags: #General-skills 
#### Description

Using a Secure Shell (SSH) is going to be pretty important.

Additional details will be available after launching your challenge instance.
##### Solution:
`ssh ctf-player@titan.picoctf.net -p 61424`

---
### Lets Warm Up
Tags:  #General-skills 
#### Description
If I told you a word started with 0x70 in hexadecimal, what would it start with in ASCII?
##### Solution: 
0x70 
bytearray.fromhex("70").decode() => 'p'
another way  =>  int("0x70", 16) = 112 => 'p'
`picoCTF{p}`

---
### Warmed Up
Tags: #General-skills 
#### Description
What is 0x3D (base 16) in decimal (base 10)?
##### Solution:
 int("0x3D",16) => 61
`picoCTF{61}`

---
### 2Warm
Tags:  #General-skills 
#### Description
Can you convert the number 42 (base 10) to binary (base 2)?
##### Solution:
bin(42) => '0b101010' => 101010
`picoCTF{101010}` 

---
### Commitment Issues
Tags:  #General-skills #git #browser_web_shell_solvable
#### Description
I accidentally wrote the flag down. Good thing I deleted it! You download the challenge files here:
- [challenge.zip](https://artifacts.picoctf.net/c_titan/136/challenge.zip)
##### Solution:
unzip file and open into terminal
`git reflog` is used for see list of commit
```shell
git reflog 
8dc5180 (HEAD -> master) HEAD@{0}: commit: remove sensitive info
87b85d7 HEAD@{1}: commit (initial): create flag
```
now  `git checkout 87b85d7`
cat message.txt                                                                                   
`picoCTF{s@n1t1z3_ea83ff2a}`

---
### Time Machine
Tags:  #General-skills #git #browser_web_shell_solvable 
#### Description
What was I last working on? I remember writing a note to help me remember... You can download the challenge files here:
- [challenge.zip](https://artifacts.picoctf.net/c_titan/161/challenge.zip)
##### Solution:
```shell
git reflog          
10228f3 (HEAD -> master) HEAD@{0}: commit (initial): picoCTF{t1m3m@ch1n3_8defe16a}
```
`picoCTF{t1m3m@ch1n3_8defe16a}`

---
### Blame Game
Tags: 
#### Description
Someone's commits seems to be preventing the program from working. Who is it? You can download the challenge files here:
- [challenge.zip](https://artifacts.picoctf.net/c_titan/158/challenge.zip)
##### Solution
use command `git log message.py `
```shell
commit 8c83358c32daee3f8b597d2b853c1d1966b23f0a
Author: picoCTF{@sk_th3_1nt3rn_2c6bf174} <ops@picoctf.com>
Date:   Tue Mar 12 00:07:11 2024 +0000

    optimize file size of prod code

commit caa945839a2fc0fb52584b559b4e89ac7c46bf54
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:11 2024 +0000

    create top secret project

```

flag: `picoCTF{@sk_th3_1nt3rn_2c6bf174}`

---
### Collaborative Development
Tags: 
#### Description
My team has been working very hard on new features for our flag printing program! I wonder how they'll work together? You can download the challenge files here:
- [challenge.zip](https://artifacts.picoctf.net/c_titan/176/challenge.zip)
##### Solution:
```shell
└─$ git reflog          
eb19d0e (HEAD -> main) HEAD@{0}: checkout: moving from feature/part-3 to main
8395824 (feature/part-3) HEAD@{1}: commit: add part 3
eb19d0e (HEAD -> main) HEAD@{2}: checkout: moving from main to feature/part-3
eb19d0e (HEAD -> main) HEAD@{3}: checkout: moving from feature/part-2 to main
7064732 (feature/part-2) HEAD@{4}: commit: add part 2
eb19d0e (HEAD -> main) HEAD@{5}: checkout: moving from main to feature/part-2
eb19d0e (HEAD -> main) HEAD@{6}: checkout: moving from feature/part-1 to main
0cd57e0 (feature/part-1) HEAD@{7}: commit: add part 1
eb19d0e (HEAD -> main) HEAD@{8}: checkout: moving from main to feature/part-1
eb19d0e (HEAD -> main) HEAD@{9}: commit (initial): init flag printer
```

interested file in  
`0cd57e0 (feature/part-1) HEAD@{7}: commit: add part 1`
`7064732 (feature/part-2) HEAD@{4}: commit: add part 2`
`8395824 (feature/part-3) HEAD@{1}: commit: add part 3`
use git checkout and commit number and using cat command
print("picoCTF{t3@mw0rk_", end='') 
print("m@k3s_th3_dr3@m_", end='')  
print("w0rk_2c91ca76}")
so final flag is `picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_2c91ca76}`

---


