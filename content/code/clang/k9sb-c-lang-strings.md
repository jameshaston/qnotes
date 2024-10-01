---
title: c-lang-strings
tags: [strings, char, c, clang] 
id: k9sb
date: 2024-09-30
time: 19:16
---

# c lang strings

A [string](https://github.com/VernonGrant/gnu-c-language-manual/blob/main/markdown/Strings.md) in C is a sequence of elements of type `char`, terminated with the 
null character `\0`. To write a string in a C program, use a *string constant* 
such as "Take me to your leader!". The data type of a string constant is 
`char *`. See [string constants](https://github.com/VernonGrant/gnu-c-language-manual/blob/main/markdown/String-Constants.md).

To declare a place to store a *non-constant string*, declare an array of type
`char`.

> Keep in mind that it must include one extra `char` for the terminating null.

For example, you can declare a non-constant string like so with `char`:

```c
char text[] = {'h', 'e', 'l', 'l', 'o', 0 };
/* or */
char text[] = "Hello"; /* copies the elements of string constant, inluding \0 */
```

# Character Arrays for Strings

To print a character [array](vgpy%20array-basics-in-c-lang.md) string, use `%s` to get the entire string. Use `c[i]` to
get the `ith` element.

```c
#include <stdio.h>

int main(void) {
    char c[] = "hello!";
    printf("%s\n", c);
    
    printf("%c\n", c[0]);
    printf("%c\n", c[5]);

    return 0;
}

```

*Results:*
```
hello!
h
!
```

# Pointers with Strings

You can use a pointer to declare a string. The pointer will point to the beginning 
of the string. C puts the null terminating `\0` at the end of the string, so it 
knows where the string ends. See [c-lang-using-pointers-with-arrays](femq-c-lang-using-pointers-with-arrays.md), [c-basics-of-pointers-and-addresses](68q5-c-basics-of-pointers-and-addresses.md),
and [c-lang-using-pointers-with-arrays](femq-c-lang-using-pointers-with-arrays.md) for pointer notes.


```c
#include <stdio.h>

int main(void) {
    char *c = "sup yo!";
    /* dereference to get a char */
    printf("%c\n", *c);
    /* dereference to get the next char */
    printf("%c\n", *(c + 1));
    /* dereference to get the next char */
    printf("%c\n", *(c + 2));

    /* print the entire string with %s and no dereference */
    printf("%s\n", c);

    return 0;
}
```

*Results:*
```
s
u
p
sup yo!
```

# `<string.h>` 

A useful library of string functions is included in C called the `<string.h>` 
header file. See this [reference](https://cplusplus.com/reference/cstring/) for more information.

```c
#include <stdio.h>
#include <string.h>

int main(void) {
    char *s = "a string...";
    printf("the length of the string is: %d\n", strlen(s));
    
    return 0;
}
```

*Results:* `the length of the string is: 11`

# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)


