---
title: c-lang-sizeof-operator
tags: [sizeof, operator, c, clang] 
id: hhcz
date: 2024-10-03
time: 21:55
---

# c lang sizeof operator

The `sizeof` operator return the number of *bytes* of its operand. It is not a 
function. See the C manual reference for the [sizeof operator](https://devdocs.io/c/language/sizeof). 

# Syntax

| sizeof(type) | (1) |
| -------------- | --------------- |
| sizeof expression | (2) |

1. Returns the size, in bytes, of the [object representation](https://devdocs.io/c/language/object#Object_representation) of type.
2. Returns the size, in bytes, of the object representation of the type of *expression*. 

> Both versions return a value of type `size_t`. See [size_t](https://devdocs.io/c/types/size_t).

# Example

```c
#include <stdio.h>
 
int main(void)
{
    short x;
    // type argument:
    printf("sizeof(float)          = %zu\n", sizeof(float));
    printf("sizeof(void(*)(void))  = %zu\n", sizeof(void(*)(void)));
    printf("sizeof(char[10])       = %zu\n", sizeof(char[10]));
//  printf("sizeof(void(void))     = %zu\n", sizeof(void(void))); // Error: function type
//  printf("sizeof(char[])         = %zu\n", sizeof(char[])); // Error: incomplete type
 
    // expression argument:
    printf("sizeof 'a'             = %zu\n", sizeof 'a'); // type of 'a' is int
//  printf("sizeof main            = %zu\n", sizeof main); // Error: Function type
    printf("sizeof &main           = %zu\n", sizeof &main);
    printf("sizeof \"hello\"         = %zu\n", sizeof "hello"); // type is char[6]
    printf("sizeof x               = %zu\n", sizeof x); // type of x is short
    printf("sizeof (x+1)           = %zu\n", sizeof(x + 1)); // type of x+1 is int
}
```

Possible output:

```c
sizeof(float)          = 4
sizeof(void(*)(void))  = 8
sizeof(char[10])       = 10
sizeof 'a'             = 4
sizeof &main           = 8
sizeof "hello"         = 6
sizeof x               = 2
sizeof (x+1)           = 4
```

# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)
- [gnu c primitive data types](89t5%20gnu-c-primitive-data-types.md)

