---
title: c-lang-character-types
tags: [char, ascii, c, clang] 
id: dqvm
date: 2024-09-29
time: 19:42
---

# c lang character types

The `char` type in C is of type `int` and depends on [ASCII codes](https://www.cs.cmu.edu/~pattis/15-1XX/common/handouts/ascii.html). A `char` is declared
with `char <name> = '<a single character or integer value>'`. You must define a 
character with single quotes `'` and not double quotes. Double quotes in C 
represent strings. 

Refer to [gnu c primitive data types](89t5%20gnu-c-primitive-data-types.md) note for information about the `char` type.

Use `%c` to display the character. The format `%d` will return the ascii code of
the character.

# ASCII

A `char` is stored in memory as a number and is converted to to show its character
using the ASCII encoding. See [ascii-code.com](https://www.ascii-code.com/) for a reference on ASCII codes.

For example, the ascii code for `A` is `65`. 

# Example of Declaring a `char` Type

```c
#include <stdio.h>

int main(void) {
    char grade = 'A';
    printf("Your grade is: %c\n", grade);
    printf("The ascii code for your grade is: %d\n", grade);

    grade = 'C';
    printf("Your grade is: %c\n", grade);
    printf("The ascii code for your grade is: %d\n", grade);
    
    return 0;
}
```

*Results:*
```
Your grade is: A
The ascii code for your grade is: 65
Your grade is: C
The ascii code for your grade is: 67
```

# Math Operations on ASCII Characters

You can use `+` and `-` to perform certain character conversions, such as converting
a lowercase character to an uppercase character. Performing this conversion is 
easy and can be accomplished by adding 32 to get the lowercase value and subtracting
32 to get the uppercase value. 

```c
#include <stdio.h>

int main(void) {
    char gradeUpper = 'a' - 32;
    printf("Your grade in uppercase is: %c\n", gradeUpper);
    printf("The ascii code for your grade is: %d\n", gradeUpper);
    printf("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~\n\n");

    char gradeLower = 'A' + 32;
    printf("Your grade is: %c\n", gradeLower);
    printf("The ascii code for your grade is: %d\n", gradeLower);
    printf("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~\n\n");
    
    char c = 78;
    printf("The ascii value you entered was: %d\n", c);
    printf("Your character is: %c\n", c);
    printf("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~\n\n");

    return 0;
}
```

*Results:*
```
Your grade in uppercase is: A
The ascii code for your grade is: 65
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Your grade is: a
The ascii code for your grade is: 97
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The ascii value you entered was: 78
Your character is: N
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

```

# Character Types

- `signed char` type for signed character representation
- `unsigned char` type for unsigned character representation and [object representation](https://devdocs.io/c/language/object) 
- `char` type for character representation and distinct from above

> Note that the standard library also defines `typedef` names. See [typedef](https://devdocs.io/c/language/typedef).  

For wide characters (since C11) we have `wchar_t`, `char16_t`, and `char32_t`. For UTF-8 
characters (since C23) we have `char8_t`.

# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)


















