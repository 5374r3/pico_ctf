
| 64-bit register | Lower 32 bits | Lower 16 bits | Lower 8 bits |
| --------------- | ------------- | ------------- | ------------ |
| rax             | eax           | ax            | al           |
| rbx             | ebx           | bx            | bl           |
| rcx             | ecx           | cx            | cl           |
| rdx             | edx           | dx            | dl           |
| rsi             | esi           | si            | sil          |
| rdi             | edi           | di            | dil          |
| rbp             | ebp           | bp            | bpl          |
| rsp             | esp           | sp            | spl          |
| r8              | r8d           | r8w           | r8b          |
| r9              | r9d           | r9w           | r9b          |
| r10             | r10d          | r10w          | r10b         |
| r11             | r11d          | r11w          | r11b         |
| r12             | r12d          | r12w          | r12b         |
| r13             | r13d          | r13w          | r13b         |
| r14             | r14d          | r14w          | r14b         |
| r15             | r15d          | r15w          | r15b         |


```css
┌─[✔]──[alpha@speed:🚀]──[~/Videos]:
└──╼ $ gdb ./debugger0_b -q
Reading symbols from ./debugger0_b...
(No debugging symbols found in ./debugger0_b)
(gdb) disassemble main
Dump of assembler code for function main:
   0x0000000000401106 <+0>:     endbr64 
   0x000000000040110a <+4>:     push   %rbp
   0x000000000040110b <+5>:     mov    %rsp,%rbp
   0x000000000040110e <+8>:     mov    %edi,-0x14(%rbp)
   0x0000000000401111 <+11>:    mov    %rsi,-0x20(%rbp)
   0x0000000000401115 <+15>:    movl   $0x1e0da,-0x4(%rbp)
   0x000000000040111c <+22>:    movl   $0x25f,-0xc(%rbp)
   0x0000000000401123 <+29>:    movl   $0x0,-0x8(%rbp)
   0x000000000040112a <+36>:    jmp    0x401136 <main+48>
   0x000000000040112c <+38>:    mov    -0x8(%rbp),%eax
   0x000000000040112f <+41>:    add    %eax,-0x4(%rbp)
   0x0000000000401132 <+44>:    addl   $0x1,-0x8(%rbp)
   0x0000000000401136 <+48>:    mov    -0x8(%rbp),%eax
   0x0000000000401139 <+51>:    cmp    -0xc(%rbp),%eax
   0x000000000040113c <+54>:    jl     0x40112c <main+38>
   0x000000000040113e <+56>:    mov    -0x4(%rbp),%eax
   0x0000000000401141 <+59>:    pop    %rbp
   0x0000000000401142 <+60>:    ret    
End of assembler dump.
```
# Assembly Instruction Full Forms and Details

## Full Forms

1. **`endbr64`**: End Branch 64-bit  
    (Part of Intel CET for indirect branch tracking security.)
    
2. **`ret`**: Return  
    (Ends a function and returns control to the caller.)
    
3. **`rbp`**: Register Base Pointer  
    (Holds the base address of the current stack frame.)
    
4. **`rsp`**: Register Stack Pointer  
    (Points to the top of the stack.)
    
5. **`mov`**: Move  
    (Copies data from source to destination; width depends on operands.)
    
6. **`movl`**: Move Long  
    (Explicitly copies 32-bit data.)
    
7. **`add`**: Addition  
    (Adds values; width depends on operands.)
    
8. **`addl`**: Addition Long  
    (Explicitly adds 32-bit values.)
    
9. **`cmp`**: Compare  
    (Compares two values and sets processor flags.)
    
10. **`jmp`**: Jump  
    (Unconditionally jumps to a specific address.)
    
11. **`jl`**: Jump If Less  
    (Conditionally jumps to an address if the comparison result is "less than.")

12. **`eax`**: Extended Accumulator Register  
(Holds the results of operations and is used for arithmetic, logic, and data transfer instructions.)
    


---

## Details of Working and Use

### 1. **`endbr64`**

- **Working**: This instruction is part of Intel's Control-flow Enforcement Technology (CET). It ensures that an indirect branch (e.g., via `jmp` or `call`) targets only a valid location.
- **Use**: Enhances security by preventing attacks such as Return-Oriented Programming (ROP) and Jump-Oriented Programming (JOP).

---

### 2. **`ret`**

- **Working**: Pops the return address from the stack and transfers control to that address.
- **Use**: Ends a function's execution and restores control to the caller. Essential for maintaining the flow of a program.

---

### 3. **`rbp`**

- **Working**: Holds the base address of the current stack frame, making it easier to access local variables and function arguments.
- **Use**: A key register for stack-based memory management.

---

### 4. **`rsp`**

- **Working**: Points to the top of the stack, where the most recently pushed data is located.
- **Use**: Used for stack operations like `push` and `pop`. Keeps track of stack growth and shrinkage.

---

### 5. **`mov`**

- **Working**: Copies data from a source location (register, memory, or immediate value) to a destination (register or memory).
- **Use**: Core instruction for transferring data within the CPU or between memory and registers.

---

### 6. **`movl`**

- **Working**: Copies a 32-bit value from the source to the destination.
- **Use**: A variant of `mov` specifically for 32-bit operations, ensuring compatibility with smaller data sizes.

---

### 7. **`add`**

- **Working**: Adds the source operand to the destination operand and stores the result in the destination.
- **Use**: Performs arithmetic addition. Operand width (e.g., 64-bit) depends on the operands used.

---

### 8. **`addl`**

- **Working**: Adds a 32-bit source operand to a 32-bit destination operand.
- **Use**: Ensures 32-bit arithmetic operations, useful in specific scenarios or for compatibility.

---

### 9. **`cmp`**

- **Working**: Compares two values by subtracting the source from the destination without storing the result. Sets flags in the processor's status register.
- **Use**: Used in conditional branching to determine the result of a comparison (e.g., less than, equal, greater than).

---

### 10. **`jmp`**

- **Working**: Unconditionally transfers control to the specified address.
- **Use**: Alters the flow of execution by jumping to a new instruction location.

---

### 11. **`jl`**

- **Working**: Transfers control to the specified address if the comparison flags indicate "less than".
- **Use**: Used in conditional branching to handle cases where one value is less than another.

---

### 12. **`eax`**
- **Working**: A 32-bit register used primarily for arithmetic and logic operations. It often holds the results of such operations and can also be used as an accumulator for data transfer.
- **Use**: Critical for performing and storing intermediate results in arithmetic operations and system calls.

---

```css
(gdb) info registers
rax            0x4af4b             307019
rbx            0x0                 0
rcx            0x401150            4198736
rdx            0x7fffffffdfc8      140737488347080
rsi            0x7fffffffdfb8      140737488347064
rdi            0x1                 1
rbp            0x1                 0x1
rsp            0x7fffffffdea8      0x7fffffffdea8
r8             0x7ffff7f9cf10      140737353731856
r9             0x7ffff7fc9040      140737353912384
r10            0x7ffff7fc3908      140737353890056
r11            0x7ffff7fde660      140737353999968
r12            0x7fffffffdfb8      140737488347064
r13            0x401106            4198662
r14            0x0                 0
r15            0x7ffff7ffd040      140737354125376
rip            0x401142            0x401142 <main+60>
eflags         0x246               [ PF ZF IF ]
cs             0x33                51
ss             0x2b                43
ds             0x0                 0
es             0x0                 0
fs             0x0                 0
gs             0x0                 0

```

## General Purpose Registers

### 1. **`rax`**: Register Accumulator (64-bit)

- **Working**: Used for arithmetic, logic operations, and system calls. Often serves as a return register for function results in x86-64.

### 2. **`rbx`**: Register Base (64-bit)

- **Working**: Often used as a general-purpose register but preserved across function calls (callee-saved).

### 3. **`rcx`**: Register Counter (64-bit)

- **Working**: Commonly used as a loop counter or for string operations (e.g., `rep` instructions).

### 4. **`rdx`**: Register Data (64-bit)

- **Working**: Typically holds additional data for operations, such as the remainder in division or arguments in system calls.

### 5. **`rsi`**: Register Source Index (64-bit)

- **Working**: Points to the source in string or memory operations. Also used to pass arguments in function calls.

### 6. **`rdi`**: Register Destination Index (64-bit)

- **Working**: Points to the destination in string or memory operations. Also used to pass arguments in function calls.

### 7. **`rbp`**: Register Base Pointer (64-bit)

- **Working**: Marks the base of the current stack frame for consistent access to function parameters and local variables.

### 8. **`rsp`**: Register Stack Pointer (64-bit)

- **Working**: Points to the top of the stack, tracking stack growth/shrinkage during execution.

### 9. **`r8` – `r15`**: Extended General-Purpose Registers (64-bit)

- **Working**: Additional registers introduced in x86-64 architecture for general-purpose use and passing arguments.

---

## Instruction Pointer and Flags

### 10. **`rip`**: Register Instruction Pointer (64-bit)

- **Working**: Holds the address of the next instruction to be executed. Updated automatically during program flow.

### 11. **`eflags`**: Extended Flags Register

- **Working**: Contains status flags that reflect the result of instructions (e.g., zero flag, carry flag). Used for conditional branching and other operations.

---

## Segment Registers

### 12. **`cs`**: Code Segment

- **Working**: Holds the selector for the segment containing the program code.

### 13. **`ss`**: Stack Segment

- **Working**: Holds the selector for the segment containing the stack.

### 14. **`ds`**: Data Segment

- **Working**: Selector for the segment containing data (default segment for most data operations).

### 15. **`es`**: Extra Segment

- **Working**: Used as an additional segment register for string and memory operations.

### 16. **`fs`**: FS Segment

- **Working**: Often used for thread-local storage.

### 17. **`gs`**: GS Segment

- **Working**: Also used for thread-local storage or additional memory segmentation.

---

## Explanation in Context of `gdb`

1. **General-purpose registers** like `rax`, `rbx`, `rcx`, etc., show the current state of computations and memory addresses.
2. **`rip`** indicates the instruction currently being executed (`main+60` at `0x401142`).
3. **Flags (`eflags`)** provide insights into the outcome of operations (e.g., `ZF` indicates the last result was zero).
4. **Segment registers (`cs`, `ss`)** are rarely modified in modern systems but retain backward compatibility.



----


# **Examining memory with GDB**

GDB provides you the power of examining the memory address using command **x** it is short for examine.

Command takes two arguments one is how to display memory and other is memory location.

Format for displaying memories are:

- o Display in octal.
- x Display in hexadecimal.-
- u Display in unsigned, standard base-10 decimal.
- t Display in binary.

```css
command: x/<format> address 
or  
x/<format> $<register> _$<register>_ this is equivalent to examining value at memory address register is pointing.
```


Default size the gdb will show is 4 bytes which is equivalent to 4 bytes. You can change the size.

- **b** A single byte
- **h** A halfword, which is two bytes in size
- **w** A word, which is four bytes in size
- **g** A giant, which is eight bytes in size

Command : `x/4xb <memory address>` examine 4 bytes with byte length of single and display it in hexadecimal format.

---


```css
┌─[✔]──[alpha@speed:🐧]──[~/Videos]:
└──╼ $ gdb --help
This is the GNU debugger.  Usage:

    gdb [options] [executable-file [core-file or process-id]]
    gdb [options] --args executable-file [inferior-arguments ...]

Selection of debuggee and its files:

  --args             Arguments after executable-file are passed to inferior.
  --core=COREFILE    Analyze the core dump COREFILE.
  --exec=EXECFILE    Use EXECFILE as the executable.
  --pid=PID          Attach to running process PID.
  --directory=DIR    Search for source files in DIR.
  --se=FILE          Use FILE as symbol file and executable file.
  --symbols=SYMFILE  Read symbols from SYMFILE.
  --readnow          Fully read symbol files on first access.
  --readnever        Do not read symbol files.
  --write            Set writing into executable and core files.

Initial commands and command files:

  --command=FILE, -x Execute GDB commands from FILE.
  --init-command=FILE, -ix
                     Like -x but execute commands before loading inferior.
  --eval-command=COMMAND, -ex
                     Execute a single GDB command.
                     May be used multiple times and in conjunction
                     with --command.
  --init-eval-command=COMMAND, -iex
                     Like -ex but before loading inferior.
  --nh               Do not read ~/.gdbinit.
  --nx               Do not read any .gdbinit files in any directory.

Output and user interface control:

  --fullname         Output information used by emacs-GDB interface.
  --interpreter=INTERP
                     Select a specific interpreter / user interface.
  --tty=TTY          Use TTY for input/output by the program being debugged.
  -w                 Use the GUI interface.
  --nw               Do not use the GUI interface.
  --tui              Use a terminal user interface.
  --dbx              DBX compatibility mode.
  -q, --quiet, --silent
                     Do not print version number on startup.

Operating modes:

  --batch            Exit after processing options.
  --batch-silent     Like --batch, but suppress all gdb stdout output.
  --return-child-result
                     GDB exit code will be the child's exit code.
  --configuration    Print details about GDB configuration and then exit.
  --help             Print this message and then exit.
  --version          Print version information and then exit.

Remote debugging options:

  -b BAUDRATE        Set serial port baud rate used for remote debugging.
  -l TIMEOUT         Set timeout in seconds for remote debugging.

Other options:

  --cd=DIR           Change current directory to DIR.
  --data-directory=DIR, -D
                     Set GDB's data-directory to DIR.

At startup, GDB reads the following early init files and executes their
commands:
   None found.

At startup, GDB reads the following init files and executes their commands:
   * system-wide init files: /etc/gdb/gdbinit

For more information, type "help" from within GDB, or consult the
GDB manual (available as on-line info or a printed manual).

Report bugs to <https://www.gnu.org/software/gdb/bugs/>.

You can ask GDB-related questions on the GDB users mailing list
(gdb@sourceware.org) or on GDB's IRC channel (#gdb on Freenode).

```

```css
┌─[✔]──[alpha@speed:🍓]──[~/Videos]:
└──╼ $ gdb ./debugger0_a
GNU gdb (Ubuntu 12.1-0ubuntu1~22.04.2) 12.1
Copyright (C) 2022 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Type "show copying" and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<https://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
    <http://www.gnu.org/software/gdb/documentation/>.

For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from ./debugger0_a...
(No debugging symbols found in ./debugger0_a)
(gdb) 
```

```css
-q, --quiet, --silent
                     Do not print version number on startup.
```

```css
┌─[✔]──[alpha@speed:🚀]──[~/Videos]:
└──╼ $ gdb ./debugger0_a -q
Reading symbols from ./debugger0_a...
(No debugging symbols found in ./debugger0_a)
(gdb) 
```


---

The `tui enable` and `layout asm` commands in `gdb` are related to different aspects of the TUI (Text User Interface) mode, and they serve distinct purposes:

### 1. `tui enable`:

- **Purpose**: The `tui enable` command enables TUI mode in `gdb`, which provides a more interactive and graphical interface in the terminal for debugging.
    
- **Functionality**: When you enter TUI mode, `gdb` splits the terminal screen into several panes. You can use these panes to display source code, assembly code, registers, and the stack.
    
- **What it does**: It activates the TUI interface, allowing you to use different layouts like the disassembly view or source code view.
    
    After enabling TUI mode using `tui enable`, you can switch between different layouts with commands like:
    
    - `layout asm`: Displays assembly code.
    - `layout src`: Displays source code.
    - `layout regs`: Displays registers.

### 2. `layout asm`:

- **Purpose**: The `layout asm` command is used specifically in TUI mode to switch the active pane to display the disassembly (assembly code) of the program being debugged.
    
- **Functionality**: It shows the assembly code of the current function or code being executed. This layout is particularly useful for low-level debugging, as you can see the machine instructions corresponding to your program.
    
    - **Usage**: You first need to enable TUI mode with `tui enable`, then use `layout asm` to display the assembly code in one of the panes.

### Key Differences:

- `tui enable` activates the TUI interface in `gdb`, while `layout asm` is a specific layout used within the TUI interface to show assembly code.
- `tui enable` is the prerequisite for using any layout, including `layout asm`.

So, to summarize:

- **`tui enable`**: Enables the full TUI interface.
- **`layout asm`**: Switches to the assembly code layout within the TUI interface.


Once the program has started, to enable TUI mode you can either use `Ctrl+X+A` or enter in `tui enable` into GDB to enter TUI mode.
`Ctrl+X+A` command used to enter TUI mode and pressing `Ctrl+X+A` will exit from TUI mode

