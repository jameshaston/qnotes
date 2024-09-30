---
title: c-lang-program-structure-and-scope
tags: [structure, header, scope, c, clang] 
id: 8sif
date: 2024-09-29
time: 20:41
---

# c lang program structure and scope

This note is based on the [Program Structure](https://www.gnu.org/software/gnu-c-manual/gnu-c-manual.html#Program-Structure) chapter of the gnu c language 
reference manual. 

# Program Structure

A C program may exist entirely within a single source file, but more commonly,
any non-trivial program will consist of several custom **header files** and
**source files**, and will also include and link with files from existing libraries.

By convention, header files like (.h extension) contain variable and function 
declarations, and source files (.c extension) contain the corresponding definitions.

Source files may also store declarations if they are not for objects which need to
be seen by other files. 

For example, if you write a function that computes square roots, and you wanted 
this function to be accessible to files other than where you define the function, 
you would put the function declaration into a **header file** with the `.h` 
extension. 

```c
/* sqrt.h */

double 
computeSqrt (double x);
```

This header file could be included by other source files which need to use your 
function but do not need to know how it was implemented. The implementation
of the function would go into a corresponding source file `.c` extension. 

```c
/* sqrt.c */
#include "sqrt.h"

double
computeSqrt (double x) {
    double result;
    
    /* code */

    return result;
}
```

# Scope

Scope refers to what parts of the program can "see" a declared object. A declared
object can be visible only within a particular function, or within a particular
file, or may be visible to an entire set of files by way of header files and 
`extern` declarations.

Unless explicitly stated otherwise, declarations made at the top-level of a file
(not within a function) are visible to the entire file, including within functions,
but are not visible outside of the file. 

Declarations made within functions are visible only within those functions.

A declaration is not visible to declarations that came before it, for example:

```c
/* works */
int x = t;
int y = x + 10;

/* does not works */
int x = y + 10;
int y = 5;
```


# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)








