# Verify
Author: Jeffery John
#easy #forensics #picoCTF2024 #grep #browser_web_shell #cheksum
#### Description

People keep trying to trick my players with imitation flags. I want to make sure they get the real thing! I'm going to provide the SHA-256 hash and a decrypt script to help you know that my flags are legitimate. You can download the challenge files here:

- `[challenge.zip](https://artifacts.picoctf.net/c_rhea/11/challenge.zip)`

Additional details will be available after launching your challenge instance.

The same files are accessible via SSH here: `ssh -p 52668 ctf-player@rhea.picoctf.net` Using the password `1ad5be0d`. Accept the fingerprint with `yes`, and `ls` once connected to begin. Remember, in a shell, passwords are hidden!

- Checksum: 5848768e56185707f76c1d74f34f4e03fb0573ecc1ca7b11238007226654bcda
- To decrypt the file once you've verified the hash, run `./decrypt.sh files/<file>`.

##### Solution:
open zip file and extract you will get home folder navigate through folder you will get checksum.txt , decrypt.sh ,files folder (lot of files inside this folder)
here decrypt.sh code
```sh
     #!/bin/bash
        # Check if the user provided a file name as an argument
        if [ $# -eq 0 ]; then
            echo "Expected usage: decrypt.sh <filename>"
            exit 1
        fi
        # Store the provided filename in a variable
        file_name="$1"
        # Check if the provided argument is a file and not a folder
        if [ ! -f "/home/kali/Downloads/home/ctf-player/drop-in/$file_name" ]; then
            echo "Error: '$file_name' is not a valid file. Look inside the 'files' folder with 'ls -R'!"
            exit 1
        fi
        # If there's an error reading the file, print an error message
        if ! openssl enc -d -aes-256-cbc -pbkdf2 -iter 100000 -salt -in "/home/kali/Downloads/home/ctf-player/drop-in/$file_name" -k picoCTF; then
            echo "Error: Failed to decrypt '$file_name'. This flag is fake! Keep looking!"
        fi
```

change your path `/home/kali/Downloads/home/ctf-player/drop-in` according to your system
```css
cat checksum.txt 
5848768e56185707f76c1d74f34f4e03fb0573ecc1ca7b11238007226654bcda
```

```css
 sha256sum files/*                                                                        
8c939ff784b9bc798a4821bd5b34cf3b4baeec547b2cdd3ecd6d87f79fb5e094  files/0Djw1Yn9
c67ea887485e7901c8f46d448290f32f37eae06a6543224c6930296050867845  files/0hCC1ddM
5e8652b3e46bd17d7317ef058fce7e1356285c2b2cb4ef367c380bf550315452  files/6rbLdRBE
53c03f89814448d6f6d2958c9b839f76a1dc0aba75841a7aed005e39246d54fa  files/6SMm8dlr
c3c406acfb3a21e7839eb3d5979cfda112cf899fcd488658c78cd6c1d633b188  files/7BqS9rvi
1b9b67f14c7d8236a3be05123cbc9408111d2986daa362829a28163f4a1180fe  files/7gssXCp6
b6cadb603d9bb191bd7c2eddbbb52256db31ef343ec4b0201f2785412da1c94e  files/7HasXrdt
1a00253d723a431f5061c20647a171563abceba9006bdd8f33077e6c3e3e52c4  files/7YwKDwt5
c5df6691d1814d1f88098c66071e0246069654fe362e2d6c0a9563941df79f8a  files/7ywOJtA5
4298bd0081a73d417c2644862c02d9335e356666b2994879be7eff8834a6e1ec  files/8AI0vFUP
b68b6f7c850b1a531e8ff796af5a3b84320ba0bea987eae7599b35aa87762e3c  files/8BmF7YU3
5848768e56185707f76c1d74f34f4e03fb0573ecc1ca7b11238007226654bcda  files/8eee7195
7a6f19f2034655ac67c04a740d13cb6647fa9ee330fa99d90a24dacfa5dd4bca  files/8KBG6Ho5
0883fc76c9eee70bc7802b8923a99d4b9294acd4d5949db637d54ee8425fb98f  files/ZQjoMAN3
95925142aedd0b61226272941e5e9d05593944e0cea1065a1f79e69ba6bb8048  files/ztuBoBBF
# note list is long so i try to show less
```

use grep command  to filter checksum file 
```css
sha256sum files/* | grep 5848768e56185707f76c1d74f34f4e03fb0573ecc1ca7b11238007226654bcda
5848768e56185707f76c1d74f34f4e03fb0573ecc1ca7b11238007226654bcda  files/8eee7195
```

```css
./decrypt.sh files/8eee7195
picoCTF{trust_but_verify_8eee7195}
```

online 
```css
┌──(kali㉿kali)-[~/Downloads/home/ctf-player/drop-in]
└─╼ $ ssh -p 52668 ctf-player@rhea.picoctf.net
The authenticity of host '[rhea.picoctf.net]:52668 ([64:ff9b::388:bfe4]:52668)' can't be established.
ED25519 key fingerprint is SHA256:QKdv+RGJL0UYRDM66IiGQ5dsXOX7DQFqB7umTylh+IU.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[rhea.picoctf.net]:52668' (ED25519) to the list of known hosts.
ctf-player@rhea.picoctf.net's password: 
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 6.5.0-1016-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

ctf-player@pico-chall$ ls
checksum.txt  decrypt.sh  files
ctf-player@pico-chall$ cat checksum.txt
5848768e56185707f76c1d74f34f4e03fb0573ecc1ca7b11238007226654bcda
ctf-player@pico-chall$ sha256sum files/* | grep 5848768e56185707f76c1d74f34f4e03fb0573ecc1ca7b11238007226654bcda
5848768e56185707f76c1d74f34f4e03fb0573ecc1ca7b11238007226654bcda  files/8eee7195
ctf-player@pico-chall$ ls
checksum.txt  decrypt.sh  files
ctf-player@pico-chall$ ./decrypt.sh files/8eee7195 
picoCTF{trust_but_verify_8eee7195}

```