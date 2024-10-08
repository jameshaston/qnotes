---
title: c-lang-generic-data-types
tags: [generic, types, structs, unions, enums, c, clang] 
id: deim
date: 2024-10-07
time: 21:12
---

# c lang generic data types

[Generic programming](https://en.wikipedia.org/wiki/Generic_programming) is a style of programming in which algorithms are written in terms of
data types *to be specified later* that are then *instantiated* when needed for specific
types provided as parameters to functions.

> Note: There is no specific implementation for generic types in C.

See this [blog post](https://iafisher.com/blog/2020/06/type-safe-generics-in-c) on how to create type-safe generic data structures in C. Also, see
this [github repo](https://github.com/Carzuiliam/generic-data-structures) for an example of how to build a workaround for generic data types in
C. 

> Generics often use [c-lang-void-pointers](8nce-c-lang-void-pointers.md)

# Create a Generic Stack

This example will explain how to create a generic stack that can hold many different
data types using generic programming. 

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Data types for struct Stack
typedef enum {
    STACK_INT,
    STACK_CHAR,
    STACK_UINT64
} StackDataType;

// Generic stack data structure
typedef struct Stack
{
    StackDataType type;
    size_t size;
    void* data;
    void* top;
} Stack;

// Function to create a Stack
Stack stackCreate(size_t size, StackDataType type)
{
    size_t stack_size = 0;
    if (type == STACK_CHAR) stack_size = size * sizeof(char);
    if (type == STACK_INT) stack_size = size * sizeof(int);
    if (type == STACK_UINT64) stack_size = size * sizeof(unsigned long long);


    Stack stack = {
        .type = type,
        .size = size,
        .data = malloc(stack_size),
        .top = NULL
    };
    return stack;
}

void stackDelete(Stack* stack) {
    free(stack->data);
    stack->data = NULL;
}

int
main(int argc, char *argv[])
{
    Stack int_stack = stackCreate(10, STACK_INT);
    ((int*)int_stack.data)[0] = 29; // type cast int_stack.data to an int pointer
    int_stack.top = ((int*)int_stack.data) + 0; // move top

    ((int*)int_stack.data)[1] = 8;
    int_stack.top = ((int*)int_stack.data) + 1;

    printf("size of int_stack is: %lu bytes\n", sizeof(int_stack));
    printf("size of int_stack.size is: %lu bytes\n", sizeof(int_stack.size));

    stackDelete(&int_stack);

    return 0;
}
```

*Results:*
```
size of int_stack is: 32 bytes
size of int_stack.size is: 8 bytes
```

# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)
- [c-lang-enums](ynam-c-lang-enums.md)
- [c-lang-structs](al62-c-lang-structs.md)
- [c-lang-node-struct-with-pointers](sk9x-c-lang-node-struct-with-pointers.md)
- [c-lang-unions](ua9d-c-lang-unions.md)

