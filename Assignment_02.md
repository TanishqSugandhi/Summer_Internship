# GCC Compilation Process and Executable Analysis

## Introduction

The GNU Compiler Collection (GCC) is a powerful compiler toolchain used for compiling C, C++, and other programming languages in Linux.

This assignment demonstrates:
- GCC toolchain
- Compilation stages
- File generation
- Debugging
- Executable analysis
- Memory sections

---

# 1. GCC Compiler and Toolchain

## What is GCC?

GCC (GNU Compiler Collection) is an open-source compiler used to convert source code into executable machine code.

---

# GCC Toolchain Components

| Component | Function |
|---|---|
| Preprocessor | Processes directives |
| Compiler | Converts C code to assembly |
| Assembler | Converts assembly to object code |
| Linker | Generates executable file |

---

# Compilation Flow

```text
Source Code (.c)
        ↓
Preprocessor
        ↓
Expanded Code (.i)
        ↓
Compiler
        ↓
Assembly Code (.s)
        ↓
Assembler
        ↓
Object File (.o)
        ↓
Linker
        ↓
Executable File
```

---

# 2. Writing a C Program

## File: `hello.c`

```c
#include <stdio.h>

int global_var = 100;

int main() {

    int local_var = 10;

    printf("Hello GCC Toolchain\n");

    return 0;
}
```

---

# 3. Compilation Process

## Step 1: Preprocessing

### Generate `.i` File

```bash
gcc -E hello.c -o hello.i
```

---

## Purpose

The preprocessor:
- Expands macros
- Includes header files
- Removes comments

---

# Step 2: Compilation

## Generate `.s` File

```bash
gcc -S hello.c -o hello.s
```

---

## Purpose

The compiler converts C code into assembly language.

---

# Step 3: Assembling

## Generate `.o` File

```bash
gcc -c hello.c -o hello.o
```

---

## Purpose

The assembler converts assembly code into machine-level object code.

---

# Step 4: Linking

## Generate Executable File

```bash
gcc hello.o -o hello
```

---

## Execute Program

```bash
./hello
```

---

# 4. Debugging Programs Using GDB

## Compile with Debugging Symbols

```bash
gcc -g hello.c -o hello
```

---

## Start GDB

```bash
gdb ./hello
```

---

## Common GDB Commands

```bash
break main
run
next
print local_var
quit
```

---

# 5. Demonstration of Generated Files

| File Type | Description |
|---|---|
| `.i` | Preprocessed file |
| `.s` | Assembly code |
| `.o` | Object file |
| Executable | Final runnable program |

---

# View Generated Files

## List Files

```bash
ls
```

---

# 6. Executable Analysis Tools

Linux provides tools to analyze executable files and symbols.

---

# size Command

## Display Program Size

```bash
size hello
```

---

## Example Output

```text
text    data     bss     dec     hex
1200    200      16      1416    588
```

---

# nm Command

## Display Symbols

```bash
nm hello
```

---

## Purpose

Displays:
- Functions
- Variables
- Symbols

---

# objdump Command

## Disassemble Executable

```bash
objdump -d hello
```

---

## Purpose

Displays assembly instructions inside executable files.

---

# readelf Command

## View ELF File Information

```bash
readelf -h hello
```

---

## Purpose

Displays:
- ELF headers
- Section information
- Program metadata

---

# 7. Memory Sections in C Programs

A compiled C program is divided into multiple memory sections.

---

# Text Section

## Description

Stores executable machine instructions.

---

# Data Section

## Description

Stores initialized global and static variables.

---

# BSS Section

## Description

Stores uninitialized global and static variables.

---

# Heap Section

## Description

Dynamic memory allocation area.

---

## Example

```c
int *ptr = malloc(sizeof(int));
```

---

# Stack Section

## Description

Stores:
- Local variables
- Function calls
- Return addresses

---

# Memory Layout Diagram

```text
---------------------
|     Stack         |
---------------------
|                    |
|       Heap         |
|                    |
---------------------
|       BSS          |
---------------------
|      Data          |
---------------------
|      Text          |
---------------------
```

---

# Applications of GCC Toolchain

- Software Development
- Embedded Systems
- Operating Systems
- Linux Kernel Development
- System Programming

---

# Advantages of GCC

- Open-source
- Multi-language support
- Powerful optimization
- Cross-platform compatibility

---

# Conclusion

The GCC toolchain plays an essential role in compiling, debugging, linking, and analyzing programs in Linux environments. Understanding compilation stages and memory sections is fundamental for software and embedded systems development.
