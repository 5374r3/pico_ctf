### Ready Gladiator 1

#Medium #Reverse_Engineering  #picoCTF2023 #CoreWars

Author: LT 'syreal' Jones

#### Description

Can you make a CoreWars warrior that wins?Your opponent is the Imp. The source is available [here](https://artifacts.picoctf.net/c/411/imp.red). If you wanted to pit the Imp against himself, you could download the Imp and connect to the CoreWars server like this:`nc saturn.picoctf.net 53869 < imp.red`To get the flag, you must beat the Imp at least once out of the many rounds.

##### Solution:
given code is 
```css
;redcode
;name Imp Ex
;assert 1
mov 0, 1
end
```

To get the flag, you must beat the Imp at least once out of the many rounds.( from question)
use this website [codewars](https://vyznev.net/corewar/guide.html)

modified code
```css
;redcode
;name Imp Ex
;assert 1
ADD #4, 3        ; execution begins here
MOV 2, @2
JMP -2
DAT #0, #0
end
```


```css
┌─[✔]──[alpha@speed:🍇]──[~/Videos]:
└──╼ $ nc saturn.picoctf.net 50461 < imp1_modified.red 
;redcode
;name Imp Ex
;assert 1
ADD #4, 3        ; execution begins here
MOV 2, @2
JMP -2
DAT #0, #0
end
Submit your warrior: (enter 'end' when done)

Warrior1:
;redcode
;name Imp Ex
;assert 1
ADD #4, 3        ; execution begins here
MOV 2, @2
JMP -2
DAT #0, #0
end

Rounds: 100
Warrior 1 wins: 20
Warrior 2 wins: 0
Ties: 80
You did it!
picoCTF{1mp_1n_7h3_cr055h41r5_dba6f40d}

```