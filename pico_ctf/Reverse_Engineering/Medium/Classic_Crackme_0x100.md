### Classic Crackme 0x100

Author: Nandan Desai
#Medium #Reverse_Engineering #picoCTF2024 #browser_web_shell 
#### Description

A classic Crackme. Find the password, get the flag! Binary can be downloaded [here](https://artifacts.picoctf.net/c_titan/105/crackme100). Crack the Binary file locally and recover the password. Use the same password on the server to get the flag!

Additional details will be available after launching your challenge instance.
Access the server using `nc titan.picoctf.net 53036`

##### Solution:
using Ida disassemble generate pseudo code

```cpp
int __fastcall main(int argc, const char **argv, const char **envp)
{
  char input[64]; // [rsp+0h] [rbp-A0h] BYREF
  char output[60]; // [rsp+40h] [rbp-60h] BYREF
  int random2; // [rsp+7Ch] [rbp-24h]
  int random1; // [rsp+80h] [rbp-20h]
  char fix; // [rsp+87h] [rbp-19h]
  int secret3; // [rsp+88h] [rbp-18h]
  int secret2; // [rsp+8Ch] [rbp-14h]
  int secret1; // [rsp+90h] [rbp-10h]
  int len; // [rsp+94h] [rbp-Ch]
  int i_0; // [rsp+98h] [rbp-8h]
  int i; // [rsp+9Ch] [rbp-4h]

  strcpy(output, "qhcpgbpuwbaggepulhstxbwowawfgrkzjstccbnbshekpgllze");
  setvbuf(_bss_start, 0LL, 2, 0LL);
  printf("Enter the secret password: ");
  __isoc99_scanf("%50s", input);
  i = 0;
  len = strlen(output);
  secret1 = 85;
  secret2 = 51;
  secret3 = 15;
  fix = 97;
  while ( i <= 2 )
  {
    for ( i_0 = 0; i_0 < len; ++i_0 )
    {
      random1 = (secret1 & (i_0 % 255)) + (secret1 & ((i_0 % 255) >> 1));
      random2 = (random1 & secret2) + (secret2 & (random1 >> 2));
      input[i_0] = ((random2 & secret3) + input[i_0] - fix + (secret3 & (random2 >> 4))) % 26 + fix;
    }
    ++i;
  }
  if ( !memcmp(input, output, len) )
    printf("SUCCESS! Here is your flag: %s\n", "picoCTF{sample_flag}");
  else
    puts("FAILED!");
  return 0;
```

now how to get password
this python code help to crack the password

```python
def reverse_transform(output, secret1, secret2, secret3, fix, iterations):
    len_output = len(output)
    input_chars = list(output)

    for _ in range(iterations):
        for i_0 in range(len_output - 1, -1, -1):  # Iterate backwards
            random1 = (secret1 & (i_0 % 255)) + (secret1 & ((i_0 % 255) >> 1))
            random2 = (random1 & secret2) + (secret2 & (random1 >> 2))
            
            # Reverse the transformation
            input_chars[i_0] = chr(
                (ord(input_chars[i_0]) - fix - (random2 & secret3) - (secret3 & (random2 >> 4))) % 26 + fix
            )

    return "".join(input_chars)

# Given output string
output = "qhcpgbpuwbaggepulhstxbwowawfgrkzjstccbnbshekpgllze"

# Known parameters
secret1 = 85
secret2 = 51
secret3 = 15
fix = 97

# Perform the reverse transformation
original_input = reverse_transform(output, secret1, secret2, secret3, fix, 3)
print("Recovered password:", original_input)
```

```css
┌──(kali㉿kali)-[~/Downloads/pico_ctf_lab]
└─$ python3 crack_passwd.py
Recovered password: qezjdvjltvuxavgiibmkrsncqrntxfykgmntwsepmyvyguzwtv
```

similarly in using cpp we can crack password

```cpp
#include <iostream>
#include <cstring>

int main() {
    char output[] = "qhcpgbpuwbaggepulhstxbwowawfgrkzjstccbnbshekpgllze";
    int len = strlen(output);

    // Secret values used in transformations
    int secret1 = 85;
    int secret2 = 51;
    int secret3 = 15;
    char fix = 97;  // ASCII for 'a'

    // Create a buffer for the original input
    char input[64];
    strncpy(input, output, len);

    // Reverse the transformation logic 3 times
    for (int i = 0; i < 3; ++i) {  // Repeat the reversal 3 times
        for (int i_0 = len - 1; i_0 >= 0; --i_0) {  // Iterate backwards
            int random1 = (secret1 & (i_0 % 255)) + (secret1 & ((i_0 % 255) >> 1));
            int random2 = (random1 & secret2) + (secret2 & (random1 >> 2));

            // Reverse the transformation applied to input[i_0]
            input[i_0] = ((input[i_0] - fix - (random2 & secret3) - (secret3 & (random2 >> 4))) + 26) % 26 + fix;
        }
    }

    // Print the recovered original input
    std::cout << "Recovered input (password): " << input << std::endl;

    return 0;
}

```

```css
┌──(kali㉿kali)-[~/Downloads/pico_ctf_lab]
└─$ g++ crac_pass.cpp && ./a.out
Recovered input (password): qezjdvjltvuxavgiibmkrsncqrntxfykgmntwsepmyvyguzwtv
```

```css
┌──(kali㉿kali)-[~/Downloads/pico_ctf_lab]
└─$ ./crackme100
Enter the secret password: qezjdvjltvuxavgiibmkrsncqrntxfykgmntwsepmyvyguzwtv
SUCCESS! Here is your flag: picoCTF{sample_flag}
```

now go to online to get the actual flag

```css
┌──(kali㉿kali)-[~/Downloads/pico_ctf_lab]
└─$ nc titan.picoctf.net 53036
Enter the secret password: qezjdvjltvuxavgiibmkrsncqrntxfykgmntwsepmyvyguzwtv
SUCCESS! Here is your flag: picoCTF{s0lv3_angry_symb0ls_4699696e}
```