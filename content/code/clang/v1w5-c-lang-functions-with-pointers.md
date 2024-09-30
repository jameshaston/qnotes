---
title: c-lang-functions-with-pointers
tags: [functions, pointers, reference, c, clang] 
id: v1w5
date: 2024-09-29
time: 23:23
---

# c lang functions with pointers

A function name refers to a fixed function. Sometimes it is useful to call a function
to be determined at run time by using a *function pointer value* that points to the
chosen function. See the C reference manual for more details on [function pointers](https://github.com/VernonGrant/gnu-c-language-manual/blob/main/markdown/Function-Pointers.md).

Pointer-to-function types can be used to declare variables and other data, including
array elements, structure fields, and union alternatives.

You can use pointers for function parameters and return values. Here is an example
of using a pointer to add one to a variable. Refer to [c-basics-of-pointers-and-addresses](68q5-c-basics-of-pointers-and-addresses.md) 
for a quick refresher on pointers in C.

# Pointers to Change the Value of a Variable

```c
#include <stdio.h>

/*function prototypes*/
void addOne(int *);

int main(void) {

    int a = 0;
    printf("a is: %d\n\n", a);

    /*get the address of a and change it to add one*/
    addOne(&a);
    printf("a is: %d\n", a);

    return 0;
}

void addOne(int* a) {
    *a = *a + 1; 
}
```

*Results:*
```
a is: 0

a is: 1
```

# Pointers as a Return Value

```c
#include <stdio.h>
/*function prototypes*/
int* addOne(int *);

int main(void) {
    int i = 0;
    /* a is a pointer to the address of i */
    int* a = &i;

    printf("i is: %d\n", i);
    printf("a is: %d\n", *a);
    printf("~~~~~~~~~~~~~~~~~\n\n");

    a = addOne(a);
    printf("a is: %d\n", *a);
    printf("i is: %d\n", i);

    return 0;
}

int* addOne(int* a) {
    *a = *a + 1; 
    return a;
}
```

*Results:*
```
i is: 0
a is: 0
~~~~~~~~~~~~~~~~~

a is: 1
i is: 1
```

# Declaring Function Pointers

The declaration of a function [pointer variable](https://github.com/VernonGrant/gnu-c-language-manual/blob/main/markdown/Declaring-Function-Pointers.md) (or structure field) looks almost
like a function declaration, except it has an additional `*` before the variable
name. Proper nesting requires a pair of parentheses around the two of them.

Consider these examples:

```c
/* Declare a function returning char *.  */
char *a (char *);
/* Declare a pointer to a function returning char.  */
char (*a) (char *);
/* Declare a pointer to a function returning char *.  */
char *(*a) (char *);
```

# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)
- [c-lang-functions](0iuz-c-lang-functions.md)


