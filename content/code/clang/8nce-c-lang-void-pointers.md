---
title: c-lang-void-pointers
tags: [void, pointers, c, clang] 
id: 8nce
date: 2024-10-07
time: 21:42
---

# c lang void pointers

[Void pointers](https://www.gnu.org/software/c-intro-and-ref/manual/html_node/Void-Pointers.html) in C is a pointer whose target type is `void`. It represents a pointer to 
"we-dont-say-what." Void pointers are used frequently in C. For example, the functions 
for dynamic memory allocation use type `void *` to refer to blocks of memory, regardless
of what sort of data the program stores in those blocks. See [dynamic memory allocation](https://www.gnu.org/software/c-intro-and-ref/manual/html_node/Dynamic-Memory-Allocation.html).

Also, see the gnu c manual regarding the [void type](https://www.gnu.org/software/c-intro-and-ref/manual/html_node/The-Void-Type.html).

# Void Pointer Example

This is a basic implementation of a void pointer to demonstrate how it works. For a more
useful example, see [c-lang-generic-data-types](deim-c-lang-generic-data-types.md).

```c
// compiled in ~/dev/clang/tutorial/void-pointers/voidpointers.c
#include <stdio.h>

int
main(int argc, char *argv[])
{
    int a = 5;
    double b = 3;

    // INVALID. This will generate a warning
    // since `b` type is double. 
    int *p = &b;
    printf("%d\n", *p);
    return 0;
}
```

*Results:*  

```
➜ gcc -g -o voidpointers voidpointers.c
voidpointers.c: In function 'main':
voidpointers.c:9:12: error: initialization of 'int *' from incompatible pointer type 'double *' [-Wincompatible-pointer-types]
    9 |   int *p = &b;
      |            ^
```

To fix this issue, we can use a `void *` that can be used with *any* data type. Let's see
an example:

```c
// compiled in ~/dev/clang/tutorial/void-pointers/voidpointers.c
#include <stdio.h>

int
main(int argc, char *argv[])
{
    int a = 5;
    double b = 3;

    // declaring a void * to use on both variables a and b
    void *p;

    p = &a;
    printf("p=&a is: %d\n", *((int *)p));

    p = &b;
    printf("p=&b is: %f\n", *((double *)p));

    return 0;
}

```

*Results:*
```
p=&a is: 5
p=&b is: 3.000000
```

# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)

