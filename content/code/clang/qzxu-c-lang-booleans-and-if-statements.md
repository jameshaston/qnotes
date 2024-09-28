---
title: c-lang-booleans-and-if-statements
tags: [c, clang, bool, if, statements] 
id: qzxu
date: 2024-09-27
time: 21:15
---

# c lang booleans and if statements

The `c` standard library does not contain booleans types by default. If you want
to use booleans in your program, you have a few options:

1. import the `<stdbool.h> file`
2. use enums
3. use macros

In older `c` programs, you may encounter `0` and `1` to reference `false` and `true`, 
respectively. 

- `0` = false
- `1` = true

Booleans are useful for evaluating conditions. Here is a basic example of creating
a `bool`:

```c
#include <stdbool.h>
#include <stdio.h>

int main(void) {
  // get age from user
  int age;
  printf("How old are you?\n");
  scanf("%d", &age);

  // bool condition to evaluate
  bool ageCheck = (age >= 18);
  bool invalidAge = (age < 0);

  // execute code based on condition
  if (invalidAge) {
    printf("Invalid entry.\n");
  } else if (ageCheck) {
    printf("You are an adult\n");
  } else {
    printf("You are a little tiny baby\n");
  }

  return 0;
```

The gnu c reference manual contains documentation about `statements` in `c`. See
[Chapter 4 - Statements](https://www.gnu.org/software/gnu-c-manual/gnu-c-manual.html#Statements) for more information.

Also, see [Chapter 3 - Expressions and Operators](https://www.gnu.org/software/gnu-c-manual/gnu-c-manual.html#Expressions-and-Operators) for useful operators and expressions
for working with booleans and statements.






# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)























