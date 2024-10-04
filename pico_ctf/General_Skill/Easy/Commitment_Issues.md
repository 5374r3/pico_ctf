### Commitment Issues

Author: Jeffery John
#easy #General-skills #picoCTF2024 #browser_web_shell #git 
#### Description

I accidentally wrote the flag down. Good thing I deleted it! You download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/136/challenge.zip)
##### Solution:
extract zip file
open into vscode or in terminal type `git log`
```css
git log                                                     
commit 8dc51806c760dfdbb34b33a2008926d3d8e8ad49 (HEAD -> master)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:06:17 2024 +0000

    remove sensitive info

commit 87b85d7dfb839b077678611280fa023d76e017b8
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:06:17 2024 +0000

    create flag
```

now checkout to commit `87b85d7dfb839b077678611280fa023d76e017b8`
```css
┌──(kali㉿kali)-[~/Downloads/drop-in]± master
└─╼ $ git checkout 87b85d7dfb839b077678611280fa023d76e017b8       
Note: switching to '87b85d7dfb839b077678611280fa023d76e017b8'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 87b85d7 create flag  
┌──(kali㉿kali)-[~/Downloads/drop-in]± master~1
└─╼ $ cat message.txt     
picoCTF{s@n1t1z3_ea83ff2a}
```
you flag is `picoCTF{s@n1t1z3_ea83ff2a}`
