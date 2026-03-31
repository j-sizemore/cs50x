# C

## Classification

- procedural (i.e. functions)
- structural (i.e. code blocks)
- weakly typed (i.e. supports implicit type conversion)

## Dev tools

- compiler: gcc
- linker: ld (binutils)
- editor: vim

## C compilation procedure

- source code is passed to *preprocessor* (cpp)
    - preprocessor instructions start with `#`
- then, is compiled and optimized by the compiler (gcc) into assembly
- assembler translates this into executable binaries
- linker (ld) finally links the executable to all necessary binaries

use the gcc flag `-save-temps` to see all intermediate files in the compilation process

## hello.c

### Source

```C
#include <stdio.h>
/* This is a comment */

int main() {
    printf("Hello, world!\n");
    return 0;
}
```

### Description

- preprocessor directive `#include` requests `stdio.h` header file, which provides `printf`
- `int main()` function definition is mandatory
- `\n` is an escape sequence that prints a new line
- `return 0` signals successful execution to the compiler
- statements (not preprocessor directives) require semicolons at the end

### Compilation and execution

```sh
$ gcc hello.c -o hello
$ ./hello
```

- the `-o` flag writes the build output to an output file indicated by the following argument

## Common escape sequences

- `\n`: new line
- `\r`: return to start of line
- `\"`: double quote
- `\'`: single quote
- `\\`: backslash

## hello\_improved.c

### Source

```C
// get_string and printf with %s

#include "cs50.h"
#include <stdio.h>

int main(void) {
    string answer = get_string("What's your name? ");
    printf("Hello, %s\n", answer);
    return 0;
}
```

### Description
- preprocessor directive `#include` requests `cs50.h` custom  header file, which provides `get_string`
- `get_string` passes user input to the variable `answer`
- `%s` is *format code* that passes a string (`answer`) to `printf`

### CS50x custom library

- the CS50x custom library is defined in `/include/cs50.h`
- the library contains helper functions for accepting user input:
    - `get_char`
    - `get_double`
    - `get_float`
    - `get_int`
    - `get_long`
    - `get_string`
- each function takes a string prompt as a parameter and accepts user input with the indicated type

### Compilation and execution

```sh
$ gcc hello_improved.c ../include/cs50.c -I ../include -o hello_improved
$ ./hello_improved
```

- since we're using a custom library, we need to compile both `hello_improved.c` and `cs50.c`
- the `-I` flag tellc gcc where to find the header file, `cs50.h`





















