---
title: while loop basics in c lang
tags: [c, while:loops] 
id: qm3k
date: 2024-09-24
time: 21:37
---

# While Loop Basics In C Lang 

The `while` statement is a loop with an exit test at the beginning of the loop.
The general format of the `while` statement is:

```
while (test)
    statement
```

The `while` statement first evaluates *test*. If *test* is true, *statement* is 
executed, and then the *test* is evaluated again. *statement* continues to execute 
repeatedly as long as *test* is true.  

A break statement can be used to exit a while loop.

See the [GNU Reference Manual - 4.5 The `while` statement](https://www.gnu.org/software/gnu-c-manual/gnu-c-manual.html#The-while-Statement). 

```c

#include <stdio.h>

int main() {

  // test/condition for while loop
  int countdown = 5;

  while (countdown > 0) {
    printf("countdown = %d\n", countdown);
    countdown = countdown - 1;
  }

  printf("after the while loop, condition = %d\n", countdown);

  return 0;
}

```

*Results:*
```
countdown = 5
countdown = 4
countdown = 3
countdown = 2
countdown = 1
after the while loop, condition = 0
```

# Zk Reference Notes 

- [c-lang-node](3xe5-c-lang-node.md)
- [for loop basics in c](1yg2%20for-loop-basics-in-c.md)
- [gnu c primitive data types](89t5%20gnu-c-primitive-data-types.md)
- [array basics in c lang](vgpy%20array-basics-in-c-lang.md)

