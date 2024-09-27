---
title: c-lang-first-program
tags: [c, clang]
id: sg38
date: 2024-09-26
time: 17:36
---

# c lang first program

Notes based on the [Intro to C - OliveStem Course](https://youtu.be/TLaQhNlx08Q?si=X5PG50dnNTR62w60).

## A Very Basic C Program

This is the basic structure of a `c` program. 

```c
// including the standard input/output library
#include <stdio.h> 
// entry point of the program is main()
int main(void) {
    // code to execute
    printf("hello, world! \n");
    // exit code return specified by the function signature
    return 0;
}
```

> *Results:* `hello, world! `

## Elements of the Program

The `main()` function is the entry point of the `c` program. The `main` function 
must be used as the entry point of a `c` program. 

`int` specifies the return value of the `main` function. The `return` statement
must be of the same type in the signature of `main`. In this case, that is
type `int`. For more information about primitive types in `c`, see these notes:

- [gnu c lexical elements](11os%20gnu-c-lexical-elements.md)
- [gnu c primitive data types](89t5%20gnu-c-primitive-data-types.md)

The `main` function has arguments, which in this case is `void`. This tells the
compiler that the function has no arguments. 

The `#include` statement adds functions to the namespace of the program. In
this case, we include the `stdio.h` library to use the `printf` function.

## Compiling and Linking

After writing `*.c`, the program needs to be compiled. The compilation process
will create an executable (a binary file). This binary executable is run in
the terminal using the `./executable file name` convention. 

node: [c-lang-node](3xe5-c-lang-node.md)
