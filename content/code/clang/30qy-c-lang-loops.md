---
title: c-lang-loops
tags: [loops, c, clang] 
id: 30qy
date: 2024-09-28
time: 08:33
---

# c lang loops

Statements in `c` can control the flow of execution in a program. They can also
be written to not perform any action at all. Refer to the gnu reference manual
[Chapter 4 - Statements](https://www.gnu.org/software/gnu-c-manual/gnu-c-manual.html#Statements) for more details about `c` statements.

# The `while` Statement 

The `while` statement is a loop statement with an **exit** test/condition at the
beginning of the loop. It will execute the statement repeatedly as long as 
the test case is true.

```c
#include <stdio.h>

int main(void) {
    int x = 0;
    while (x <= 5) {
        printf("x = %d\n", x);
        // increment x so the test condition eventually terminates.
        x = x + 1; 
    }
    return 0;
}
```

*Results:*
```
x = 0
x = 1
x = 2
x = 3
x = 4
x = 5
```

# The `do` Statement

The `do` statement differs from the `while` statement because the test condition is
executed **after** the main logic of the code. Therefore, the `do` statement is 
gauranteed to run its main logic at least one time. See the gnu c reference manual
[here](https://www.gnu.org/software/gnu-c-manual/gnu-c-manual.html#The-while-Statement) for more information about the `do` statement.

Additionally, see [c-lang-booleans-and-if-statements](qzxu-c-lang-booleans-and-if-statements.md) for a refresher on conditional 
statements.

```c
#include <stdio.h>

int main(void) {

    /*int y = 5;*/
    int y = 1;

    printf("while 'y' is less than 4...execute the 'do' loop\n");
    // code to execute
    do {
        printf("The do statement runs at least one time...\n");
        printf("y = %d\n", y);
        y = y + 1;
    } while (y < 4);

    return 0;

}
```

*Results:*
```
while 'y' is less than 4...execute the 'do' loop
The do statement runs at least one time...
y = 1
The do statement runs at least one time...
y = 2
The do statement runs at least one time...
y = 3
```

# The `for` Statement

```c
#include <stdio.h>

int main(void) {

    for (int num = 5; num <= 10; num++) {
        printf("num = %d\n", num);
    }
}
```

*Results:*
```
num = 5
num = 6
num = 7
num = 8
num = 9
num = 10
```

# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)

