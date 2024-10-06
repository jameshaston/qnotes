---
title: c-lang-enums
tags: [enums, c, clang] 
id: ynam
date: 2024-10-05
time: 17:03
---

# c lang enums

An [enumerated type](https://devdocs.io/c/language/enum), `enum`, is a distinct type whose value is a value of its underlying
type, which inlcudes the values of explicitly named constants. 

The gnu c manual describes [enums](https://www.gnu.org/software/c-intro-and-ref/manual/html_node/Enumeration-Types.html) as a limited set of integer values, each with a name.
`enums` are effectively equivalent to a primitive integer type. See [gnu c primitive data types](89t5%20gnu-c-primitive-data-types.md).

# Enum Example

The syntax of an `enum` is similar to [c-lang-structs](al62-c-lang-structs.md).

```c
#include <stdio.h>

enum Day {
    Monday = 1, 
    Tuesday,
    Wednesday,
    Thursday,
    Friday,
    Saturday,
    Sunday,
};

typedef enum button {
    OFF,
    ON, 
} Button;

int main(void) {

    enum Day today = Saturday;
    printf("today is Saturday -> %d\n", today);

    /*Button power = ON;*/
    Button power = OFF;
    switch(power) {
        case 0: 
            printf("power state is OFF -> %d\n", power);
            break;

        case 1:
            printf("power state is ON -> %d\n", power);
            break;
    }

    return 0;
}
```

*Results:*
```
today is Saturday -> 6
power state is OFF -> 0
```

# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)
