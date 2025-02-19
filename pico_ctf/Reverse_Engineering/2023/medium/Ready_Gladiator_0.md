### Ready Gladiator 0

#Medium #Reverse_Engineering #picoCTF2023 #CoreWars

Author: LT 'syreal' Jones

#### Description

Can you make a CoreWars warrior that always loses, no ties?Your opponent is the Imp. The source is available [here](https://artifacts.picoctf.net/c/308/imp.red). If you wanted to pit the Imp against himself, you could download the Imp and connect to the CoreWars server like this:`nc saturn.picoctf.net 50640 < imp.red`

##### Solution:
actual code
```css
;redcode
;name Imp Ex
;assert 1
mov 0, 1
end
```

note : To kill a program, you'd have to copy a `DAT` over its code.
modified code
```css
;redcode
;name Imp Ex
;assert 1
dat 0, 1
end
```

```css
┌─[✔]──[alpha@speed:🐧]──[~/Videos]:
└──╼ $ nc saturn.picoctf.net 63028 < imp0_modified.red 
;redcode
;name Imp Ex
;assert 1
dat 0, 1
end
Submit your warrior: (enter 'end' when done)

Warrior1:
;redcode
;name Imp Ex
;assert 1
dat 0, 1
end

Rounds: 100
Warrior 1 wins: 0
Warrior 2 wins: 100
Ties: 0
You did it!
picoCTF{h3r0_t0_z3r0_4m1r1gh7_be33d1f6}
```