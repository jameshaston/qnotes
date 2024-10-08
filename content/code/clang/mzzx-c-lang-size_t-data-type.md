---
title: c-lang-size_t-data-type
tags: [size_t, data, type, c, clang] 
id: mzzx
date: 2024-10-07
time: 19:58
---

# c lang size_t data type

[size_t](https://devdocs.io/c/types/size_t) is the unsigned integer type of the result of `sizeof`, `_Alignof`, and `offsetof`
depending on the data model. It is advised to use `size_t` when using functions
that do type casting, such as `strlen(str)` or `malloc(sizeof(int) * 16)`. Both of those
functions return `size_t`.

Note that `size_t` can:

- store the max size of a theoretically possible object of any type (including array)
- is commonly used for array indexing and loop counting.

See also [c-lang-sizeof-operator](hhcz-c-lang-sizeof-operator.md).

# Example

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char *argv[])
{
    char str[] = "Here is an example";

    for (size_t i = 0; i < strlen(str); i++)
    {
        printf("%c", str[i]);
    }
    printf("\n");
}
```

*Results:* `Here is an example`

# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)

