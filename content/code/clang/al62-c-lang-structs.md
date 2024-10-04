---
title: c-lang-structs
tags: [structs, data, c, clang] 
id: al62
date: 2024-09-30
time: 20:35
---

# c lang structs

C `struct` is a type consisting of a sequence of *members* whose storage is allocated
in an *ordered* sequence. Details of [struct](https://devdocs.io/c/language/struct) implementation. 

Basically, a [structure](https://github.com/VernonGrant/gnu-c-language-manual/blob/main/markdown/Structures.md) is a user-defined data type that holds various *fields* of data.
Each field has a name and a data type specified in the `struct` definition.

Structs are useful for creating custom data types outside of the existing 
[gnu c primitive data types](89t5%20gnu-c-primitive-data-types.md).

# Basic Struct

```c
#include <stdio.h> 

/* struct keyword name */
struct student {
    /* properties / fields */
    char* name;
    char* email;
    int age;
};

int main(void) {
    /* declare instance of student struct */
    struct student james;
    /* declare properties of a student */
    james.name = "James H.";
    james.age = 36;
    james.email = "email@dot.com";

    printf("Here are the details of the student: %s\n", james.name);
    printf("Age: %d\n", james.age);
    printf("Email: %s\n", james.email);

    /* declare instance of student with properties */
    struct student julia = {"julia", "julia@dot.com", 31};
    printf("Here are the details of the student: %s\n", julia.name);
    printf("Age: %d\n", julia.age);
    printf("Email: %s\n", julia.email);

    return 0;
}
```

*Results:*
```
Here are the details of the student: James H.
Age: 36
Email: email@dot.com
Here are the details of the student: julia
Age: 31
Email: julia@dot.com
```

# Using `struct` Values

Suppose we defined `struct Point(int x, int y)`.

> Access Members

```
aPoint.x
aPoint.y
```

> Assign to Members

```
aPoint.x = 1;
aPoint.y = 8;
```

> Take the Address Of

```
Point *bPointPointer = &aPoint;
```

> Copy over all members of a struct

```
Point cPoint = aPoint;
*bPointPointer = someOtherPoint;
```

# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)
- [c-basics-of-pointers-and-addresses](68q5-c-basics-of-pointers-and-addresses.md)
- [c-lang-functions-with-pointers](v1w5-c-lang-functions-with-pointers.md)
- [c-lang-using-pointers-with-arrays](femq-c-lang-using-pointers-with-arrays.md)


