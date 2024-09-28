---
title: c-lang-logical-operators-and-switches
tags: [logical, operators, switches, c, clang] 
id: buo7
date: 2024-09-27
time: 23:22
---

# c lang logical operators and switches

Logical operators apply standard boolean algebra operations to their operands.

In `c`, there are three logical operators: 

| Operator | Name | Example | Result |
| --------------- | --------------- | --------------- | --------------- |
| `!` | NOT | `!a` | negation of a |
| `&&` | AND | `a && b` | both a and b |
| `pipe pipe` | OR | `a OR b` | a or b or both |

Refer to the `c` documentation for logical operators [here](https://devdocs.io/c/language/operator_logical). Also, see 
[gnu c lexical elements](11os%20gnu-c-lexical-elements.md) in reference to operators and other `c` literals.

# Example Using Logical Operators

```c
#include <stdio.h>

int main(void) {
    // OR 
    int age = 159;
    printf("You are %d years old.\n", age);

    if ((age < 0) || (age > 130)) {
        printf("Age is invalid...\n");
    } 
    // AND
    age = 9;
    printf("You are %d years old.\n", age);

    if ((age > 0) && (age < 18)) {
        printf("Age is invalid...\n");
    } else {
        printf("You are a kid...\n");
    } 
    // NOT
    age = 56;
    printf("You are %d years old.\n", age);

    if (!(age >= 55)) {
        printf("You don't qualify for AARP yet...\n");
    } else {
        printf("You qualify for AARP!!!\n");
    }
    return 0;
}
```

*Results:*
```
You are 159 years old.
Age is invalid...
You are 9 years old.
Age is invalid...
You are 56 years old.
You qualify for AARP!!!
```

# Switch Statements

Refer to the `c` language manual for details on the [switch statement](https://devdocs.io/c/language/switch). `switch` statements are
useful for matching and can be used as a replacement for the `if` statement. See this note
for more information on basic `if` statements: [c-lang-booleans-and-if-statements](qzxu-c-lang-booleans-and-if-statements.md).


> WARNING: Run this code in the editor only!

```c
#include <stdio.h>

int main(void) {
    // basic switch statement example
    int weekday = 0;
    printf("Enter a number for the day of the week. (1 - 7)...\n");
    scanf("%d", &weekday);

    // switch statement 
    //      faster than if else if etc...
    //      similar to rust enums matching
    switch(weekday) {
        case 1:
            weekday = 1;
            printf("Monday is: %d\n", weekday);
            break;

        case 2:
            weekday = 2;
            printf("Tuesday is: %d\n", weekday);
            break;

        // etc...
        // the default case is for every other case outside of the options
        default: 
            printf("invalid day of the week. use 1 - 7 for the days of the week\n");
    }

    return 0; 
}
```

*Results:*
```
Enter a number for the day of the week. (1 - 7)...
invalid day of the week. use 1 - 7 for the days of the week
```

# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)


