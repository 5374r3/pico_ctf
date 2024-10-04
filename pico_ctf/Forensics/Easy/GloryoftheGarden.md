### Glory of the Garden

Author: jedavis/Danny
#easy #forensics #picoCTF2019 
#### Description

This [garden](https://jupiter.challenges.picoctf.org/static/4153422e18d40363e7ffc7e15a108683/garden.jpg) contains more than it seems.

##### solution:
use strings to get flag
```css
strings garden.jpg| grep pico
Here is a flag "picoCTF{more_than_m33ts_the_3y33dd2eEF5}"
```

use hex-editor to get flag
simply open image file and search flag

![[hexeditor_flag.jpg]]


