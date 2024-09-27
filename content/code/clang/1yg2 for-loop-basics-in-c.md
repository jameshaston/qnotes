---
title: for loop basics in c
tags: [c, clang, loops] 
id: 1yg2
date: 2024-09-24
time: 21:22
---

# For Loop Basics In C 

The `for` statement in `c` is a loop statement whose structure allows variable
initialization, expression testing, and variable modification. 

See the [GNU C Reference Manual - 4.7 The `for` Statement](https://www.gnu.org/software/gnu-c-manual/gnu-c-manual.html#The-for-Statement).

```c

#include <stdio.h>

int main() {

  // array assignment
  //    declaration:    int name[size];
  //    assignment:     name[index] = value;
  int array[5];
  array[0] = 23;
  array[1] = 0;
  array[2] = 4;
  array[3] = 65;
  array[4] = -17;

  // loop through array and print each value
  for (int ind = 0; ind < 5; ind = ind + 1) {
    printf("array[%d] = %d\n", ind, array[ind]);
  }

  return 0;
}

```

# Zk Reference Notes

- [c-lang-node](3xe5-c-lang-node.md)
- [array basics in c lang](vgpy%20array-basics-in-c-lang.md)
- [while loop basics in c lang](qm3k%20while-loop-basics-in-c-lang.md)
