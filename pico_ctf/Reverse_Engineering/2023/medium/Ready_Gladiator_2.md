### Ready Gladiator 2

#Medium #Reverse_Engineering #picoCTF2023 #CoreWars

Author: LT 'syreal' Jones

#### Description

Can you make a CoreWars warrior that wins every single round?Your opponent is the Imp. The source is available [here](https://artifacts.picoctf.net/c/278/imp.red). If you wanted to pit the Imp against himself, you could download the Imp and connect to the CoreWars server like this:`nc saturn.picoctf.net 57160 < imp.red`To get the flag, you must beat the Imp all 100 rounds.

##### Solution:
given code
```css
;redcode
;name Imp Ex
;assert 1
mov 0, 1
end
```

modified code
```css
;redcode
;name Imp Ex
;assert 1
jmp 0,<-2
end
```


```css
┌─[✔]──[alpha@speed:🐧]──[~/Videos]:
└──╼ $ nc saturn.picoctf.net 64571 < imp.red
;redcode
;name Imp Ex
;assert 1
jmp 0,<-2
end
Submit your warrior: (enter 'end' when done)

Warrior1:
;redcode
;name Imp Ex
;assert 1
jmp 0,<-2
end

Rounds: 100
Warrior 1 wins: 100
Warrior 2 wins: 0
Ties: 0
You did it!
picoCTF{d3m0n_3xpung3r_106bc275}
```