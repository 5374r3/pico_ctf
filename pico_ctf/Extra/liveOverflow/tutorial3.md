
# writing c program

```c
#include<stdio.h>
int main(int argc, char *argv[]) {

        printf("Knock , knock, Neo\n");
}

```

```css
┌─[✔]──[alpha@speed:🐧]──[~/Public/share_file/liveoverflow]:
└──╼ $ gcc matrix.c -o matrix                                                                                                                                                             

┌─[✔]──[alpha@speed:🐧]──[~/Public/share_file/liveoverflow]:
└──╼ $ ./matrix
Knock, knock ,Neo

┌─[✔]──[alpha@speed:🍓]──[~/Public/share_file/liveoverflow]:
└──╼ $ 

```

```css
┌─[✔]──[alpha@speed:🍓]──[~/Public/share_file/liveoverflow]:
└──╼ $ gcc matrix.c -o matrix -std=c90 -Wall                                                                                                                                              
matrix.c: In function ‘main’:                                                                                                                                                             
matrix.c:4:1: warning: control reaches end of non-void function [-Wreturn-type]                                                                                                           
    4 | }                                                                                                                                                                                 
      | ^                                                                                                                                                                                 

┌─[✔]──[alpha@speed:🚀]──[~/Public/share_file/liveoverflow]:
└──╼ $ 

```

**Note `-std=c90` (Old Standard That Requires Explicit `return` in `main()`)**
- In C90, reaching the end of `main()` **without `return 0;`** is **undefined behavior**, so GCC will warn:
- In **C99 and later**, if `main()` reaches the end **without a return statement**, it's treated as if `return 0;` was implicitly added.
- This is why **GCC does not always warn about missing `return 0;` in `main()`** unless you enforce stricter compliance.

```css
#include <stdio.h>
int main(int argc , char *argv[]) {
    printf("Knock, knock ,Neo\n");
    return 0;
}

```

```css
┌─[✔]──[alpha@speed:🚀]──[~/Public/share_file/liveoverflow]:
└──╼ $ gcc matrix.c -o matrix -std=c90 -Wall

```

```css
#include <stdio.h>
int main(int argc , char *argv[]) {
    if(argc==2){
    printf("Knock, knock ,%s\n",argv[1]);
    } else {
        fprintf(stderr,"Usage: %s <name>\n", argv[0]);
        return 1;
    }
    return 0;
}


```

**Note**: `return 1` will tell program exit with error

```css
┌─[✔]──[alpha@speed:🐧]──[~/Public/share_file/liveoverflow]:
└──╼ $ gcc matrix.c -o matrix -std=c90 -Wall

┌─[✔]──[alpha@speed:🐧]──[~/Public/share_file/liveoverflow]:
└──╼ $ ./matrix 
Usage: ./matrix <name>

┌─[✘]──[alpha@speed:🍑]──[~/Public/share_file/liveoverflow]:
└──╼ $ echo $?
1

┌─[✔]──[alpha@speed:🐧]──[~/Public/share_file/liveoverflow]:
└──╼ $ ./matrix  hello
Knock, knock ,hello

┌─[✔]──[alpha@speed:🐧]──[~/Public/share_file/liveoverflow]:
└──╼ $ echo $?
0

```

```css
┌─[✔]──[alpha@speed:🐧]──[~/Public/share_file/liveoverflow]:
└──╼ $ 

┌─[✔]──[alpha@speed:🐧]──[~/Public/share_file/liveoverflow]:
└──╼ $ ./matrix  $USER
Knock, knock ,saket

┌─[✔]──[alpha@speed:🍓]──[~/Public/share_file/liveoverflow]:
└──╼ $ ./matrix  \$USER
Knock, knock ,$USER
```