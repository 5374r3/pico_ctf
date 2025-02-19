### Safe Opener 2

#Medium #Reverse_Engineering #picoCTF2023

Author: Mubarak Mikail

#### Description

What can you do with this file?I forgot the key to my safe but this [file](https://artifacts.picoctf.net/c/286/SafeOpener.class) is supposed to help me with retrieving the lost key. Can you help me unlock my safe?

##### solution 
using online tool you can convert .class to java file
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Base64;
import java.util.Base64.Encoder;

public class SafeOpener {
   public static void main(String[] args) throws IOException {
      BufferedReader keyboard = new BufferedReader(new InputStreamReader(System.in));
      Encoder encoder = Base64.getEncoder();
      String encodedkey = "";
      String key = "";

      for(int i = 0; i < 3; ++i) {
         System.out.print("Enter password for the safe: ");
         key = keyboard.readLine();
         encodedkey = encoder.encodeToString(key.getBytes());
         System.out.println(encodedkey);
         boolean isOpen = openSafe(encodedkey);
         if (isOpen) {
            break;
         }

         System.out.println("You have  " + (2 - i) + " attempt(s) left");
      }

   }

   public static boolean openSafe(String password) {
      String encodedkey = "picoCTF{SAf3_0p3n3rr_y0u_solv3d_it_3dae8463}";
      if (password.equals(encodedkey)) {
         System.out.println("Sesame open");
         return true;
      } else {
         System.out.println("Password is incorrect\n");
         return false;
      }
   }
}
```

flag is `picoCTF{SAf3_0p3n3rr_y0u_solv3d_it_3dae8463}`

The `javap` tool is included in the JDK and provides information about the `.class` file. While it doesn't generate full source code, it can be useful for examining methods, fields, and bytecode.

```css
┌─[✔]──[alpha@speed:🚀]──[~/Videos]:
└──╼ $ javap -c SafeOpener.class 
Compiled from "SafeOpener.java"
public class SafeOpener {
  public SafeOpener();
    Code:
       0: aload_0
       1: invokespecial #1                  // Method java/lang/Object."<init>":()V
       4: return

  public static void main(java.lang.String[]) throws java.io.IOException;
    Code:
       0: new           #2                  // class java/io/BufferedReader
       3: dup
       4: new           #3                  // class java/io/InputStreamReader
       7: dup
       8: getstatic     #4                  // Field java/lang/System.in:Ljava/io/InputStream;
      11: invokespecial #5                  // Method java/io/InputStreamReader."<init>":(Ljava/io/InputStream;)V
      14: invokespecial #6                  // Method java/io/BufferedReader."<init>":(Ljava/io/Reader;)V
      17: astore_1
      18: invokestatic  #7                  // Method java/util/Base64.getEncoder:()Ljava/util/Base64$Encoder;
      21: astore_2
      22: ldc           #8                  // String
      24: astore_3
      25: ldc           #8                  // String
      27: astore        4
      29: iconst_0
      30: istore        5
      32: iload         5
      34: iconst_3
      35: if_icmpge     119
      38: getstatic     #9                  // Field java/lang/System.out:Ljava/io/PrintStream;
      41: ldc           #10                 // String Enter password for the safe:
      43: invokevirtual #11                 // Method java/io/PrintStream.print:(Ljava/lang/String;)V
      46: aload_1
      47: invokevirtual #12                 // Method java/io/BufferedReader.readLine:()Ljava/lang/String;
      50: astore        4
      52: aload_2
      53: aload         4
      55: invokevirtual #13                 // Method java/lang/String.getBytes:()[B
      58: invokevirtual #14                 // Method java/util/Base64$Encoder.encodeToString:([B)Ljava/lang/String;
      61: astore_3
      62: getstatic     #9                  // Field java/lang/System.out:Ljava/io/PrintStream;
      65: aload_3
      66: invokevirtual #15                 // Method java/io/PrintStream.println:(Ljava/lang/String;)V
      69: aload_3
      70: invokestatic  #16                 // Method openSafe:(Ljava/lang/String;)Z
      73: istore        6
      75: iload         6
      77: ifne          119
      80: getstatic     #9                  // Field java/lang/System.out:Ljava/io/PrintStream;
      83: new           #17                 // class java/lang/StringBuilder
      86: dup
      87: invokespecial #18                 // Method java/lang/StringBuilder."<init>":()V
      90: ldc           #19                 // String You have
      92: invokevirtual #20                 // Method java/lang/StringBuilder.append:(Ljava/lang/String;)Ljava/lang/StringBuilder;
      95: iconst_2
      96: iload         5
      98: isub
      99: invokevirtual #21                 // Method java/lang/StringBuilder.append:(I)Ljava/lang/StringBuilder;
     102: ldc           #22                 // String  attempt(s) left
     104: invokevirtual #20                 // Method java/lang/StringBuilder.append:(Ljava/lang/String;)Ljava/lang/StringBuilder;
     107: invokevirtual #23                 // Method java/lang/StringBuilder.toString:()Ljava/lang/String;
     110: invokevirtual #15                 // Method java/io/PrintStream.println:(Ljava/lang/String;)V
     113: iinc          5, 1
     116: goto          32
     119: return

  public static boolean openSafe(java.lang.String);
    Code:
       0: ldc           #24                 // String picoCTF{SAf3_0p3n3rr_y0u_solv3d_it_3dae8463}
       2: astore_1
       3: aload_0
       4: aload_1
       5: invokevirtual #25                 // Method java/lang/String.equals:(Ljava/lang/Object;)Z
       8: ifeq          21
      11: getstatic     #9                  // Field java/lang/System.out:Ljava/io/PrintStream;
      14: ldc           #26                 // String Sesame open
      16: invokevirtual #15                 // Method java/io/PrintStream.println:(Ljava/lang/String;)V
      19: iconst_1
      20: ireturn
      21: getstatic     #9                  // Field java/lang/System.out:Ljava/io/PrintStream;
      24: ldc           #27                 // String Password is incorrect\n
      26: invokevirtual #15                 // Method java/io/PrintStream.println:(Ljava/lang/String;)V
      29: iconst_0
      30: ireturn
}
```