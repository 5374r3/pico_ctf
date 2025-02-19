### Collaborative Development

Author: Jeffery John
#easy #General-skills #picoCTF2024 #browser_web_shell #git 
#### Description

My team has been working very hard on new features for our flag printing program! I wonder how they'll work together? You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/176/challenge.zip)
##### Solution:
extract zip file and into terminal type git branch
you have a python file with text `print("Printing the flag...")`
```css
git branch
* (HEAD detached at eb19d0e)
  feature/part-1
  feature/part-2
  feature/part-3
  main
```
switch to branch feature/part-1
```css
git checkout feature/part-1  
Previous HEAD position was eb19d0e init flag printer
Switched to branch 'feature/part-1'
```
now python file text is 
```python
print("Printing the flag...")

print("picoCTF{t3@mw0rk_", end='')
```
switch to branch feature/part-2
```css
 git checkout feature/part-2
Switched to branch 'feature/part-2'
```
now python file text is 
```python
print("Printing the flag...")

print("m@k3s_th3_dr3@m_", end='')
```
switch to branch feature/part-2
```css
git checkout feature/part-3
Switched to branch 'feature/part-3'
```
python file text is 
```python
print("Printing the flag...")

print("w0rk_2c91ca76}")
```

now combine python file `print("picoCTF{t3@mw0rk_", end='')` `print("m@k3s_th3_dr3@m_", end='')` `print("w0rk_2c91ca76}")`
flag is `picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_2c91ca76}`