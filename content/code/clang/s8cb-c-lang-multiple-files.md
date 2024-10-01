---
title: c-lang-multiple-files
tags: [files, c, clang] 
id: s8cb
date: 2024-09-30
time: 19:48
---

# c lang multiple files

How can we construct a C project using multiple files? C let's us accomplish this
using scope and structure. See [c-lang-program-structure-and-scope](8sif-c-lang-program-structure-and-scope.md) for more information.

A basic example of creating multiple files to structure a C program would be the 
following:

1. `add.c` contains the implementation of a user created `add` function
2. `add.h` contains the declaration of the `add` function in `add.c`
3. `main.c` includes `#include "add.h"` to use the `add` function from `add.c`

> add.c

```c
/* add.c implementation file */
#include "add.h"
int add(int a, int b) {
    return a+b;
}
```

> add.h 

```c
/* add.h declaration header file */
int add(int, int);
```

> main.c

```c
/* main.c program */
#include <stdio.h>
#include "add.h"

int main(void) {
    int sum = add(2, 8);
}
```

The most important part of this process is to **compile all the files together**
like:

```bash
gcc add.c add.h main.c -o main
```

# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)



