---
title: c-lang-scanf
tags: [scanf, glibc, c, clang, input] 
id: 7low
date: 2024-09-27
time: 19:28
---

# c lang scanf

`scanf` is part of the C standard library and is documented [here](https://sourceware.org/glibc/manual/latest/html_mono/libc.html) on the gnu libc website.

The `scanf` function reads formatted input from the stream `stdin` under the control of
the template string `template`. 

The optional arguments are pointers to the places which receive the resulting values.
The `return` value is normally the number of successful assignments. If an end-of-file
condition is detected before any matches are performed, including matches against
whitespace and literal characters in the template, then `EOF` is returned. 

See this `scanf` [reference](https://cplusplus.com/reference/cstdio/scanf/) for more documentation.

# A Basic `scanf` Example

> **WARNING** 
> Do not run this program inside of nvim. This program accepts user input from `stdin`.

```c
#include <stdio.h>

int main(void) {
    // insantiate variables which are used as placeholders for user input
    int i = 0;
    int j = 0;

    // use scanf to receive user input from stdin and place the user 
    // input value into the address of the variable
    scanf("%d%d", &i, &j);

    // print the values provided by user input
    printf("The user input for i was: %d\n", i);
    printf("The user input for j was: %d\n", j);

    return 0;
}
```

Note that `scanf` must place the user input into the **memory address** of the 
referenced variable. By default, `scanf` uses **whitespace** to distinguish 
multiple values passed by user input. 

For example, for the variables `i` and `j`, any whitespace literal can be used
to tell the compiler that those values are distinct from each other. Refer
to [gnu c lexical elements](11os%20gnu-c-lexical-elements.md) for an overview of `character constants` used for
whitespace in `c`. 

This means that the whitespace character for newline `\n` is treated the 
same as the whitespace character for the carriage return `\r`. The same goes
for a tab `\t`, etc. 

# Specified Formats for `scanf`

You can explictly declare a specified format that `scanf` will use to distinguish
between the values of multiple variables. 

For example, `scanf(%d/%d, &i, &j)` tells `scanf` to use `/` as the character 
to use to distinguish the difference between `i` and `j`. 

Another example would use a comma as a formatter, such as `scanf(%d,%d, &i, &j)`.
In this example, values passed by `stdin` must be separated by a `,`. For example,
`user@host$ 11,4` would store `11` into `i` and `4` into `j`. 


# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)

