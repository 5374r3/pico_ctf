### Specialer

#Medium #General-skills #picoCTF2023 #bash #ssh

Author: LT 'syreal' Jones, et al.

#### Description

Reception of Special has been cool to say the least. That's why we made an exclusive version of Special, called Secure Comprehensive Interface for Affecting Linux Empirically Rad, or just 'Specialer'. With Specialer, we really tried to remove the distractions from using a shell. Yes, we took out spell checker because of everybody's complaining. But we think you will be excited about our new, reduced feature set for keeping you focused on what needs it the most. Please start an instance to test your very own copy of Specialer.`ssh -p 63974 ctf-player@saturn.picoctf.net`. The password is `af86add3`

##### Solution:
```css
┌─[✔]──[alpha@speed:🐧]──[~]:
└──╼ $ ssh -p 63974 ctf-player@saturn.picoctf.net
The authenticity of host '[saturn.picoctf.net]:63974 ([13.59.203.175]:63974)' can't be established.
ED25519 key fingerprint is SHA256:lMXKIC17ONzyUJx7ZYBY5VSwoxCz20uq5/Nm+IhXKew.
This host key is known by the following other names/addresses:
    ~/.ssh/known_hosts:8: [hashed name]
    ~/.ssh/known_hosts:10: [hashed name]
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:63974' (ED25519) to the list of known hosts.
ctf-player@saturn.picoctf.net's password: 
Specialer$ 
```

```css
Specialer$ ls
-bash: ls: command not found
Specialer$ pwd
/home/ctf-player
Specialer$ 
Specialer$ cd <tab> # press tab
.hushlogin  .profile    abra/       ala/        sim/  
Specialer$ cat <tab> # press tab
.hushlogin  .profile    abra/       ala/        sim/  
```

key point here is `<tab>` when you press tab it will display directory in cd and cat command, press tab two times you will get bunch of command list

```css
Specialer$  #press_tab #press_tab  
!          ]]         break      command    coproc     done       esac       false      function   if         local      pushd      return     source     times      ulimit     wait       
./         alias      builtin    compgen    declare    echo       eval       fc         getopts    in         logout     pwd        select     suspend    trap       umask      while      
:          bash       caller     complete   dirs       elif       exec       fg         hash       jobs       mapfile    read       set        test       true       unalias    {          
[          bg         case       compopt    disown     else       exit       fi         help       kill       popd       readarray  shift      then       type       unset      }          
[[         bind       cd         continue   do         enable     export     for        history    let        printf     readonly   shopt      time       typeset    until      
Specialer$ 

```

> Commands like **for**, **while**, **do**, **then**, **done**, **if**, **elif**, **echo** can be constructed as a program and it can be used to print the working directory contents. 

```bash
for file in *  
do  
if [ -d "$file" ]; then  
echo "$file is a directory."  
elif [ -f "$file" ]; then  
echo "$file is a file."  
fi  
done
```

```css
Specialer$ for file in *
> do
>   if [ -d "$file" ]; then
>     echo "$file is a directory."
>   elif [ -f "$file" ]; then
>     echo "$file is a file."
>   fi
> done
abra is a directory.
ala is a directory.
sim is a directory.
Specialer$ 
```

```css
Specialer$ cd abra
Specialer$ pwd
/home/ctf-player/abra
Specialer$ for file in *  
> do  
> if [ -d "$file" ]; then  
> echo "$file is a directory."  
> elif [ -f "$file" ]; then  
> echo "$file is a file."  
> fi  
> done
cadabra.txt is a file.
cadaniel.txt is a file.
done is a file.
echo is a file.
fi is a file.
Specialer$ 
```

```css
Specialer$ cat cadabra.txt 
-bash: cat: command not found
Specialer$ 
```

```css
Specialer$ echo $(<cadaniel.txt)
Yes, I did it! I really did it! I'm a true wizard!
Specialer$ 
Specialer$ echo $(<cadabra.txt)
Nothing up my sleeve!
Specialer$ echo $(< #press_tab)
.hushlogin  .profile    abra/       ala/        sim/        
Specialer$ cd ala    
Specialer$ echo $(<)
kazam.txt  mode.txt   
Specialer$ echo $(<kazam.txt)
return 0 picoCTF{y0u_d0n7_4ppr3c1473_wh47_w3r3_d01ng_h3r3_a8567b6f}
Specialer$
```