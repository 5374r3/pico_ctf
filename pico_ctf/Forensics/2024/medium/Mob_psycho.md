### Mob psycho

Author: NGIRIMANA Schadrack
#Medium #forensics #picoCTF2024 #browser_web_shell #apk
#### Description

Can you handle APKs? Download the android apk [here](https://artifacts.picoctf.net/c_titan/53/mobpsycho.apk).

##### Solution:
first unzip apk file
```css
┌──(kali㉿kali)-[~/Downloads]
└─$ unzip mobpsycho.apk -d apk_file/
....


Note: apk_file is folder location
```

now search for  `.txt` file
```css
┌──(kali㉿kali)-[~/Downloads]
└─$ find apk_file -type f -name "*.txt"
apk_file/res/color/flag.txt

┌──(kali㉿kali)-[~/Downloads]
└─$ cat apk_file/res/color/flag.txt
7069636f4354467b6178386d433052553676655f4e5838356c346178386d436c5f61336562356163327d

┌──(kali㉿kali)-[~/Downloads]
└─$ echo "7069636f4354467b6178386d433052553676655f4e5838356c346178386d436c5f61336562356163327d" | xxd -r -p

picoCTF{ax8mC0RU6ve_NX85l4ax8mCl_a3eb5ac2}                                                                                                                                                                   
```

