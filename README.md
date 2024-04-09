

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


---


---
### information
Tags: #forensics
#### Description
Files can always be changed in a secret way. Can you find the flag? [cat.jpg](https://mercury.picoctf.net/static/149ab4b27d16922142a1e8381677d76f/cat.jpg)
##### Solution: 
 use *exiftool* tool
exiftool filename and you will get details of cat file and you will notice 
License    : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
it is base64 to decrypt use
`echo cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9 | base64 -d`
`picoCTF{the_m3tadata_1s_modified}`
you can use CyberChef online tools to decrypt this use magic if you don't know it is base64 or something else

---


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


---

----
### keygenme-py
Tags:  #reverse-engineering 
#### Description

[keygenme-trial.py](https://mercury.picoctf.net/static/5a4198cd84f87c8a597cbd903d92fbf4/keygenme-trial.py)
##### Solution
```python
import hashlib
key_part_static1_trial = "picoCTF{1n_7h3_|<3y_of_"
key_part_dynamic1_trial = "xxxxxxxx"
key_part_static2_trial = "}"
key_full_template_trial = key_part_static1_trial + key_part_dynamic1_trial + key_part_static2_trial
username_trial = b"ANDERSON"
potential_dynamic_key = ""
positions = [4,5,3,6,2,7,1,8]
for p in positions:
potential_dynamic_key += hashlib.sha256(username_trial).hexdigest()[p]

key = key_part_static1_trial + potential_dynamic_key + key_part_static2_trial
print(key)
# print(len(key))
```

---
### Matryoshka doll
Tags: #forensics 
#### Description
Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one? Image: [this](https://mercury.picoctf.net/static/1b70cffdd2f05427fff97d13c496963f/dolls.jpg)
##### Solution:
use *binwalk* tools to extract image info
use `binwalk filename` to get hidden data inside image and to extract image file use `binwalk -e filename`
each time you will get image and check using `binwalk filename`
in this challenge you have to repeat 4 time  same command to get flag
`picoCTF{bf6acf878dcbd752f4721e41b1b1b66b}`

---
### crackme-py
Tags: #reverse-engineering 
#### Description
[crackme.py](https://mercury.picoctf.net/static/8fc4e878bd6708031d67cb846f03c140/crackme.py)
##### Solution:
```python
# Hiding this really important number in an obscure piece of code is brilliant!
# AND it's encrypted!
# We want our biggest client to know his information is safe with us.
bezos_cc_secret = "A:4@r%uL`M-^M0c0AbcM-MFE02fh3e4a5N"
# Reference alphabet
alphabet = "!\"#$%&'()*+,-./0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ"+ \
"[\\]^_`abcdefghijklmnopqrstuvwxyz{|}~"
def decode_secret(secret):
"""ROT47 decode
NOTE: encode and decode are the same operation in the ROT cipher family.
"""
# Encryption key
rotate_const = 47
# Storage for decoded secret
decoded = ""
# decode loop
for c in secret:
index = alphabet.find(c)
original_index = (index + rotate_const) % len(alphabet)
decoded = decoded + alphabet[original_index]
print(decoded)
# this call function was missing in original file
decode_secret(bezos_cc_secret)
def choose_greatest():
"""Echo the largest of the two numbers given by the user to the program
Warning: this function was written quickly and needs proper error handling
"""
user_value_1 = input("What's your first number? ")
user_value_2 = input("What's your second number? ")
greatest_value = user_value_1 # need a value to return if 1 & 2 are equal
if user_value_1 > user_value_2:
greatest_value = user_value_1
elif user_value_1 < user_value_2:
greatest_value = user_value_2
print( "The number with largest positive magnitude is "
+ str(greatest_value) )
choose_greatest()
```
Run `python crackme.py` into terminal
`picoCTF{1|\/|_4_p34|\|ut_a79b6c2d}`

method 2 use cyberChef and use *ROT47* decode  ``A:4@r%uL`M-^M0c0AbcM-MFE02fh3e4a5N`` you will get
`picoCTF{1|\/|_4_p34|\|ut_a79b6c2d}`

---


---
### tunn3l v1s10n
Tags: #forensics 
#### Description
We found this [file](https://mercury.picoctf.net/static/21c07c9dd20cd9f2459a0ae75d99af6e/tunn3l_v1s10n). Recover the flag.
##### Solution:
download file use *exiftool* to get details of file

File Type : BMP
File Type Extension : bmp
so rename add .bmp as extension make it `tunn3lv1s10n.bmp`
use hex editor online [hexed.it](https://hexed.it/) and observe hex value
and download another bmp extension file which is not corrupt
and use hex editor and observe hex value

this is `tunn3lv1s10n.bmp` hex value of first two line which is corrupt

`424d 8e26 2c00 0000 0000 bad0 0000 bad0
`0000 6e04 0000 3201 0000 0100 1800 0000`

this is  another bmp file `flower.bmp` which is not corrupt download for understand hex value

`42 4d 8a7b 0c00 0000 0000 8a00 0000 7c00
`0000 8002 0000 aa01 0000 0100 1800 0000`

in corrupt file `bad0` change with `8a00` and export file to check file is corrupt or not
it is corrupt file again now change with `7c00` and check it is work or not
it is working a stretch file found
now using exiftool you will get resolution also
`tunn3lv1s10n.bmp` is `height = 306 and width = 1134`
these value are in decimal change to hex
use python to get hex value
`hex(306) = '0x132'` which means `3201` height in hex
`hex(1134) = '0x46e'` which means `6e04` width in hex
now 306 is small change to 900
`hex(900) = '0x384'` which means `8403` height in hex
change `3201` with `8403` export file
you will get you flag on top of image
`picoCTF{qu1t3_a_v13w_2020}`

this is correct hex file 
`424d 8e26 2c00 0000 0000 7c00 0000 7c00  
`0000 6e04 0000 8403 0000 0100 1800 0000`

---
### Easy Peasy
Tags: #cryptography 
#### Description

A one-time pad is unbreakable, but can you manage to recover the flag? (Wrap with picoCTF{}) 
`nc mercury.picoctf.net 11188` [otp.py](https://mercury.picoctf.net/static/3cdfde8de474ba94b23aba4a2dfc7eeb/otp.py)
##### Solution:
step 1 
run `nc mercury.picoctf.net 11188` into terminal

```bash
┌──(kali㉿kali)-[~]
└─$ nc mercury.picoctf.net 11188 
******************Welcome to our OTP implementation!******************
This is the encrypted flag!
551e6c4c5e55644b56566d1b5100153d4004026a4b52066b4a5556383d4b0007

What data would you like to encrypt? ^C

```

`551e6c4c5e55644b56566d1b5100153d4004026a4b52066b4a5556383d4b0007` is 64 length which is hexadecimal 
*Note :* hexadecimal digits can indeed be represented by two characters (e.g., 0A, FF, 3B), hexadecimal numbers themselves are not limited to two digits. They can be of any length depending on the magnitude of the number they represent. For instance, the hexadecimal number "2F8" represents the decimal number 760 in base 10

step 2
read python code which is given
important point to note down is `KEY_LEN = 50000`
it uses a XOR pad of length 50000 to encrypt the input

step 3
49968+32 = 50000
run `python -c "print('A'*49968);print('A'*32)" |nc mercury.picoctf.net 11188`  into terminal
you will get `23661d3979721d3927711d392523361d3923741d3924771d3920201b1d392477` 64 length

*Note:* To convert a hexadecimal string to a `bytes` object, pass the string as a first argument into `bytes.fromhex(hex_string)`
```python
hex_string = 'ff'
print(bytes.fromhex(hex_string))
#b'\xff'
```

`pwntools is used to get flag`

```python
from pwn import *
enc_flag = bytes.fromhex("551e6c4c5e55644b56566d1b5100153d4004026a4b52066b4a5556383d4b0007")
enc_text = bytes.fromhex("23661d3979721d3927711d392523361d3923741d3924771d3920201b1d392477")
dec_text = b'A'*32
key = xor(enc_text, dec_text)
print(xor(enc_flag,key).decode())
```

you will get `7904ff830f1c5bba8f763707247ba3e1`
so final flag is `picoCTF{7904ff830f1c5bba8f763707247ba3e1}`

---
### ARMssembly 0
Tags: #reverse-engineering 
#### Description
What integer does this program print with arguments `4112417903` and `1169092511`? File: [chall.S](https://mercury.picoctf.net/static/55a414fdd81f39784d662e8023c5aeb8/chall.S) 
Flag format: picoCTF{XXXXXXXX} -> (hex, lowercase, no 0x, and 32 bits. ex. 5614267 would be picoCTF{0055aabb})

##### Solution:

hex(4112417903)
'0xf51e846f'
`picoCTF{f51e846f}`

---
### Cookies
Tags:  #web-exploitation 
#### Description
Who doesn't love cookies? Try to figure out the best one. [http://mercury.picoctf.net:64944/](http://mercury.picoctf.net:64944/)

##### Solution
go to the given URL search something into that search page section and you will see cookies value it is initially set to be -1 so change it to 0 and 1 you will get get different name
use burp-suite send to intruder
payload must be number 0 to 100 
and in grep match add `picoCTF{` click on attack you will get your flag

`picoCTF{3v3ry1_l0v3s_c00k135_cc9110ba}`

---
### vault-door-training
Author: Mark E. Haase
#### Description

Your mission is to enter Dr. Evil's laboratory and retrieve the blueprints for his Doomsday Project. The laboratory is protected by a series of locked vault doors. Each door is controlled by a computer and requires a password to open. Unfortunately, our undercover agents have not been able to obtain the secret passwords for the vault doors, but one of our junior agents obtained the source code for each vault's computer! You will need to read the source code for each level to figure out what the password is for that vault door. As a warmup, we have created a replica vault in our training facility. The source code for the training vault is here: [VaultDoorTraining.java](https://jupiter.challenges.picoctf.org/static/03c960ddcc761e6f7d1722d8e6212db3/VaultDoorTraining.java)

##### Solution
```java
class VaultDoorTraining {
    public static void main(String args[]) {
        VaultDoorTraining vaultDoor = new VaultDoorTraining();
        Scanner scanner = new Scanner(System.in); 
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
	}
   }

    // The password is below. Is it safe to put the password in the source code?
    // What if somebody stole our source code? Then they would know what our
    // password is. Hmm... I will think of some ways to improve the security
    // on the other doors.
    //
    // -Minion #9567
    public boolean checkPassword(String password) {
        return password.equals("w4rm1ng_Up_w1tH_jAv4_3808d338b46");
    }
}

```

in the above code 

```java
String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
```
and 
password `w4rm1ng_Up_w1tH_jAv4_3808d338b46`
now run the code 
```bash
javac VaultDoorTraining.java && java VaultDoorTraining
Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true
Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true
Enter vault password: picoCTF{w4rm1ng_Up_w1tH_jAv4_3808d338b46}
Access granted.
```

flag is `picoCTF{w4rm1ng_Up_w1tH_jAv4_3808d338b46}`

---
### Insp3ct0r
Tags:  #web-exploitation 
#### Description

Kishor Balan tipped us off that the following code may need inspection: `https://jupiter.challenges.picoctf.org/problem/9670/` ([link](https://jupiter.challenges.picoctf.org/problem/9670/)) or http://jupiter.challenges.picoctf.org:9670

##### Solution:
inspect the web URL first flag on html 2nd in css 3rd in javscript

```html
<!-- Html is neat. Anyways have 1/3 of the flag: picoCTF{tru3_d3 -->
/* You need CSS to make pretty pages. Here's part 2/3 of the flag: t3ct1ve_0r_ju5t */
/* Javascript sure is neat. Anyways part 3/3 of the flag: _lucky?2e7b23e3} */
```

`picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?2e7b23e3}`

---

---
### Glory of the Garden
Tag: #forensics 
#### Description
This [garden](https://jupiter.challenges.picoctf.org/static/4153422e18d40363e7ffc7e15a108683/garden.jpg) contains more than it seems.

##### Solution:
download file
use `binwalk -e bs.jpg` and you will get file info 
```shell
0             0x0             JPEG image data, JFIF standard 1.01
382           0x17E           Copyright string: "Copyright (c) 1998 Hewlett-Packard Company"
```

now use strings  `strings bs.jpg` you will get flag `picoCTF{more_than_m33ts_the_3y33dd2eEF5}`

---


`