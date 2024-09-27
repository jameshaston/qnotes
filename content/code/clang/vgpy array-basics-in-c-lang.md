---
title: array basics in c lang
tags: [c, arrays, data:structures] 
id: vgpy
date: 2024-09-24
time: 20:56
---

# Array Basics In C Lang 

In `c`, arrays are a builtin data structure. Here is an example of a basic
array in c and printing values in the array.

For a detailed reference, see the [GNU C Reference Manual - 2.5 Arrays](https://www.gnu.org/software/gnu-c-manual/gnu-c-manual.html#Arrays).

### Basic Array Declaration and Assignment

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

  printf("array at index 4 is: %d\n", array[4]);
  printf("array at index 2 is: %d\n", array[2]);

  return 0;
}
```

*Results:*
```
array at index 4 is: -17
array at index 2 is: 4
```
In memory, the array would look something like this:

| 0 | 1 | 2 | 3 | 4 |
| --------------- | --------------- | --------------- | --------------- | --------------- |
| 23 | 0 | 4 | 65 | -17 |

# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)
- [gnu c primitive data types](89t5%20gnu-c-primitive-data-types.md)
- [for loop basics in c](1yg2%20for-loop-basics-in-c.md)

