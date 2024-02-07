# Challenges

### Obedient Cat
Tags: #General-skills
#### Description
This file has a flag in plain sight (aka "in-the-clear"). [Download flag](https://mercury.picoctf.net/static/a5683698ac318b47bd060cb786859f23/flag)
##### Solution: 
Download flag from description and submit

---
 ### Mod 26
Tags: #cryptography
#### Description
Cryptography can be easy, do you know what ROT13 is? 
`cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_uJdSftmh}`
##### Solution: 
go to website rot13.com or go to CyberChef and search rot13 
`cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_uJdSftmh}`
converted to 
`picoCTF{next_time_I'll_try_2_rounds_of_rot13_hWqFsgzu}`

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
### information
Tags: #forensics
#### Description
Files can always be changed in a secret way. Can you find the flag? [cat.jpg](https://mercury.picoctf.net/static/149ab4b27d16922142a1e8381677d76f/cat.jpg)
##### Solution: 
 use exiftool tool
exiftool filename and you will get details of cat file and you will notice 
License    : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
it is base64 to decrypt use
`echo cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9 | base64 -d`
`picoCTF{the_m3tadata_1s_modified}`
you can use CyberChef online tools to decrypt this use magic if you don't know it is base64 or something else

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
### Transformation
Tags: #reverse-engineering
#### Description
I wonder what this really is... [enc](https://mercury.picoctf.net/static/1d8a5a2779c4dc24999f0358d7a1a786/enc) 
`''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])`
##### Solution: 
use CyberChef and use magic and click on intensive mode
and put enc text to decode you will get flag `picoCTF{16_bits_inst34d_of_8_e703b486}`
it is [Encode_text('UTF-16BE (1201)')] so you can decode by python script as well

```python
text = '灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸彥㜰㍢㐸㙽'
print(text.encode('utf-16-be'))
```

---

### Stonks
Tags: #Binary-Exploitation
#### Description

I decided to try something noone else has before. I made a bot to automatically trade stonks for me using AI and machine learning. I wouldn't believe you if you told me it's unsecure! [vuln.c](https://mercury.picoctf.net/static/e4d297ce964e4f54225786fe7b153b4b/vuln.c) `nc mercury.picoctf.net 20195`
##### Solution:
type in termainal `nc mercury.picoctf.net 20195` 
type 1 and in api key
write %p 20 times and press enter you will get *0x6f636970* it is hex data used in memory
use CyberChef to decode hex file
in Recipe section add *swap endianness* and *hex* 
then you will get flag but not in proper way so delete some hex file from input eg: *0x6f636970*
you will get  flag`picoCTF{I_l05t_4ll_my_m0n3y_6045d60d}`

---
### GET aHEAD
Tags: #web-exploitation 
#### Description
Find the flag being held on this server to get ahead of the competition [http://mercury.picoctf.net:28916/](http://mercury.picoctf.net:28916/)
##### Solution:
simpley run command into interminal
`curl -I http://mercury.picoctf.net:28916/`
or in burpsuite use head request to get flag
`picoCTF{r3j3ct_th3_du4l1ty_70bc61c4}`

---
### Mind your Ps and Qs
Tags: #cryptography 
#### Description
In RSA, a small `e` value can be problematic, but what about `N`? Can you decrypt this? [values](https://mercury.picoctf.net/static/bf5e2c8811afb4669f4a6850e097e8aa/values)
##### Solution:
rsa key
```md
C = ciphertext
p and q = prime numbers (http://factordb.com) will help to find out
n = p * q
phi = (p-1) * (q-1)
e = some number that 1 < e < phi and gcd(e,phi) == 1 
d = e^(-1) mod phi
```

method 1
```python
from Crypto.Util.number import inverse, long_to_bytes
c = 421345306292040663864066688931456845278496274597031632020995583473619804626233684
n = 631371953793368771804570727896887140714495090919073481680274581226742748040342637
e = 65537
p = 1461849912200000206276283741896701133693
q = 431899300006243611356963607089521499045809
phi = (p-1)*(q-1)
d = inverse(e, phi)
m = pow(c,d,n)
print(long_to_bytes(m))
```
output
`b'picoCTF{sma11_N_n0_g0od_55304594}'`

method 2
[RsaCtfTool](https://github.com/RsaCtfTool/RsaCtfTool)

```shell
./RsaCtfTool.py --decrypt 421345306292040663864066688931456845278496274597031632020995583473619804626233684 -n 631371953793368771804570727896887140714495090919073481680274581226742748040342637 -e 65537
```
output
`utf-8 : picoCTF{sma11_N_n0_g0od_55304594}`

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

----
