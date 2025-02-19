### timer

#Medium #Reverse_Engineering #picoCT2023 #android

Author: Loic Shema

#### Description

You will find the flag after analysing this apkDownload [here](https://artifacts.picoctf.net/c/449/timer.apk).

##### Solution:

```css
┌─[✘]──[alpha@speed:🍇]──[~/Public/share_file]:
└──╼ $ java -jar ./apktool_2.10.0.jar d timer.apk -o timer_file
I: Using Apktool 2.10.0 on timer.apk with 8 thread(s).
I: Baksmaling classes.dex...
I: Baksmaling classes3.dex...
I: Baksmaling classes2.dex...
I: Loading resource table...
I: Decoding file-resources...
I: Loading resource table from file: /home/saket/.local/share/apktool/framework/1.apk
I: Decoding values */* XMLs...
I: Decoding AndroidManifest.xml with resources...
I: Regular manifest package...
I: Copying assets and libs...
I: Copying unknown files...
I: Copying original files...

```

```css
[✔]──[alpha@speed:🍇]──[~/Public/share_file/timer_file]:
└──╼ $ grep -rn "picoCTF" .*                                                                                                                
./smali_classes3/com/example/timer/BuildConfig.smali:15:.field public static final VERSION_NAME:Ljava/lang/String; = "picoCTF{t1m3r_r3v3rs3d
./apktool.yml:16:  versionName: picoCTF{t1m3r_r3v3rs3d_succ355fully_17496}                                                                  
../flag.txt:1:picoCTF{you_won}                                                                                                              
../timer_apk_file/smali_classes3/com/example/timer/BuildConfig.smali:15:.field public static final VERSION_NAME:Ljava/lang/String; = "picoCT
../timer_apk_file/apktool.yml:16:  versionName: picoCTF{t1m3r_r3v3rs3d_succ355fully_17496} 
```