---
title: c-basics-of-pointers-and-addresses
tags: [c, clang, pointers, addresses] 
id: 68q5
date: 2024-09-27
time: 17:38
---

# c basics of pointers and addresses

When a variable is declared in a program, the language finds a location in the
computer's memory and stores the value of the variable at that specific location.

Refer to [gnu c primitive data types](89t5%20gnu-c-primitive-data-types.md) for a refresher on variables and types.

The `c` language allows you to access the memory address of an associated variable
using the `&` syntax to reference the location of the variable and the `%p` format
syntax to print its address. See the following example that instantiates a variable, 
prints its value, and prints its memory address.

```c
#include <stdio.h>

int main(void) {
    int i = 4;

    // how do you get the address of the variables location in memory?
    //      %p is the format for addresses
    //      &i is refers to the memory address of `i` variable
    printf("the address of 'i' is: %p\n", &i);

    return 0;
}
```

*Results:* `the address of 'i' is: 0x16f4e22a8`

In the program above, when `i` is initialized, `c` finds a location in memory,
gets the memory address, and stores the value of the variable in that memory 
address location.

This can be clarified by writing the program in the following manner:

```c
#include <stdio.h>

int main(void) {
    int i = 4;
    
    printf("The memory address of 'i' is:    %p\n", &i);
    printf("The value of 'i' is:             %d", i);

    return 0;
}
```

*Results:*
```
The memory address of 'i' is:    0x16b01e2a8
The value of 'i' is:             4
```

# Pointers - Reference the Location of a Memory Address

Pointers are variables that store a *memory address as a value* rather than
a string, number, or any other value. A pointer's type must be the same type
as the value in the memory address location. 

Here is an example of a pointer:

```c
#include <stdio.h> 

int main(void) {
    int i = 4;
    int *p = &i;

    printf("The value of 'p' is: %p\n", p);
    printf("The memory address of 'i' is: %p\n", &i);
    printf("The value of 'i' is: %d\n", i);
    printf("\n");
    printf("Dereference the value of p (address) to get p's value\n");
    printf("The dereferenced value of p is: %d\n", *p);
}
```

*Results:*
```
The value of 'p' is: 0x16f30a2ac
The memory address of 'i' is: 0x16f30a2ac
The value of 'i' is: 4

Dereference the value of p (address) to get p's value
The dereferenced value of p is: 4
```

Notice a couple of important concepts:

- `&i` and `p` have the same memory address.
- the pointer `p` has a value that is a memory address
- to get p's value, it must be **dereferenced** using `*p` 

For more detailed information about pointers in `c`, visit the chapter on pointers
in the gnu c reference manual [here](https://www.gnu.org/software/gnu-c-manual/gnu-c-manual.html#Pointers).

# Why Pointers

Why would you want to use pointers? Simply put, pointers help you understand how
your program interfaces with the computer at a deeper level. Understanding this
topic will help you understand programming concepts more than before, which will
help you create better programs. 

For instance, let's say you declare an array. How does the computer store the 
information contained in your array? The following table provides a basic idea 
of what happens when you insantiate an array. 

> Table 1 - An Array in Memory

We declare an array `[4, 8, 1]`, the program finds a contiguous location in 
memory, then stores the array in that contiguous location. The location is made
up of separate blocks of memory, each with their own reference (memory address).

| Values | 4 | 8 | 1 |
| --------------- | --------------- | --------------- | --------------- |
| Address | 1000 | 1004 | 1008 |
| Pointer| * | * | * |
| Location| 1000 | 1000 + 4 | 1000 + 8 |

# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)
- [c-lang-functions-with-pointers](v1w5-c-lang-functions-with-pointers.md)
- [c-lang-functions](0iuz-c-lang-functions.md)


