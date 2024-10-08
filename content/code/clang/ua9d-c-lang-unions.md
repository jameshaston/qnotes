---
title: c-lang-unions
tags: [unions, structs, c, clang] 
id: ua9d
date: 2024-10-07
time: 19:13
---

# c lang unions

A [union](https://www.gnu.org/software/gnu-c-manual/gnu-c-manual.html#Unions) is a custom data type used for storing several variables in the *same* memory
space. You can access any of the variables at any time, but you should only read from
one of them at a time. Assigning a value to one member overwrites the values in the
other members. 

The practical value of a `union` is saving space in memory for data structures that
do not need each of its members to be declared at the same time. 

# Defining Unions 

Use the `union` keyword followed by the declarations of its members enclosed in braces.
The definition of unions looks like the definition of a [c-lang-structs](al62-c-lang-structs.md).

```c
union numbers {
    int i;
    float f;
}
```

# Declaring Union Variables at Definition

You can declare variables of a union type when you define the union type by putting
the variable names after the closing brace of the union but before the final semicolon.

```c
union numbers {
    int i;
    float f;
} number_int, number_float;
```

OR

```c
union numbers {
    int i;
    float f;
}; 
union numbers number_int, number_float;
```

# Initializing Union Members

You can initialize the first member of a union variable when you declare it:

```c
union numbers {
    int i;
    float f;
};
union numbers number_int = {5};
// or 
// union numbers number_float = {f: 3.14159};
// or 
// union numbers number_float = {.f = 3.14159};
```

# Accessing Union Members

You can access the members of a union variable using the member access operator. Put
the name of the variable on the left side of the operator, and the name of the member
on the right side. 

```c
union numbers {
    int i;
    float f;
};
union numbers number_int;
number_int.i = 5;
number_int.f = 3.88;
```

Notice in that example that giving a value to the `f` member overrides the value stored 
in the `i` member.

# Size of Unions

The size of the union is equal to the size of its *largest member*. The size of the
union data type is the same as `sizeof(float)` since `float` is larger the `int`.
See [c-lang-sizeof-operator](hhcz-c-lang-sizeof-operator.md) for more information.

Since all members of a union occupy the same memory space, the union data type size
doesn't need to be large enough to hold the sum of all their sizes. It just needs to
be large enough to hold the size of the largest member. 

# Declaring Unions in Structs

It is common to declare a `union` in a custom `struct`. 

```c
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

typedef struct CustomFloat 
{
    bool isExtended;
    union 
    {
        float value;
        double valueExtended;
    };
} CustomFloat;

int main(int argc, char *argv[]) 
{
    CustomFloat cf, cfe;
    cf.isExtended = false;
    cf.value = 12.5f;

    cfe.isExtended = true;
    cfe.valueExtended = 0.248;

    printf("cf value is: %f\n", cf.value);
    printf("cfe value is: %f\n", cfe.valueExtended);
    printf("the address of cf is: %p\n", &cf);
    printf("the address of cfe is: %p\n", &cfe);
    printf("the size of the struct is: %d\n", sizeof(CustomFloat));
    printf("the size of cf is: %d\n", sizeof(cf));
    printf("the size of cfe is: %d\n", sizeof(cfe));

    return 0;
}
```

*Results:*
```
cf value is: 12.500000
cfe value is: 0.248000
the address of cf is: 0x16f57a820
the address of cfe is: 0x16f57a810
the size of the struct is: 16
the size of cf is: 16
the size of cfe is: 16
```

# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)

