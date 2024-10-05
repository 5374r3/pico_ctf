### The Numbers

Author: Danny
#easy #cryptography #picoCTF2019 
#### Description

The [numbers](https://jupiter.challenges.picoctf.org/static/f209a32253affb6f547a585649ba4fda/the_numbers.png)... what do they mean?

##### Solution:

![TheNumber/the\_numbers.png](TheNumber/the_numbers.png)

```css
| Number | Letter | Number | Letter | Number | Letter | Number | Letter |
|--------|--------|--------|--------|--------|--------|--------|--------|
| 1      | a      | 2      | b      | 3      | c      | 4      | d      |
| 5      | e      | 6      | f      | 7      | g      | 8      | h      |
| 9      | i      | 10     | j      | 11     | k      | 12     | l      |
| 13     | m      | 14     | n      | 15     | o      | 16     | p      |
| 17     | q      | 18     | r      | 19     | s      | 20     | t      |
| 21     | u      | 22     | v      | 23     | w      | 24     | x      |
| 25     | y      | 26     | z      |        |        |        |        |

```

python code to convert number to albhabet
```python
numbers = [16, 9, 3, 15, 3, 20, 6, 20, 8, 5, 14, 21, 13, 2, 5, 18, 19, 13, 1, 19, 15, 14]

alphabet_series = ''.join(chr((num - 1) + ord('a')) for num in numbers)

print(alphabet_series)

#output 
picoctfthenumbersmason
```

```css
16, 9, 3, 15, 3, 20, 6 => picoctf
20, 8, 5, 14, 21, 13, 2, 5, 18, 19, 13, 1, 19, 15, 14 =>  thenumbersmason


16, 9, 3, 15, 3, 20, 6 { 20, 8, 5, 14, 21, 13, 2, 5, 18, 19, 13, 1, 19, 15, 14 }
# flag look like as picoCTF{thenumbersmason}
```