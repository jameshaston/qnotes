---
title: c-lang-functions
tags: [functions, parameters, c, clang] 
id: 0iuz
date: 2024-09-29
time: 22:02
---

# c lang functions

All source files in C require the `main` function. Other functions are defined 
according to the specifications in the GNU C lanaguage manual [here](https://github.com/VernonGrant/gnu-c-language-manual/blob/main/markdown/Functions.md).

The basic structure of a C function looks like this:

```
returntype
functionname (parm_declarations…)
{
  body
}

or like this

returntype functionname (parm_declarations…) {
  body
}
```

The part before the open-brace is called the **function header**. Write `void` 
as the return type if the function does not return a value.

> For a full list of functions in glibc, refer to the [index](https://www.gnu.org/software/libc/manual/html_node/Function-Index.html). 

# Function Parameters

A function parameter vaiarable is a *local variable* used within the function to
store the value passed as an argument to the function. Usually we say "function" 
parameter or just "parameter" when referring to these variables. 

To use a function in the module, specificy a function prototype at the top of 
the source file. See [function declarations](https://github.com/VernonGrant/gnu-c-language-manual/blob/main/markdown/Function-Declarations.md) for more information. 

```c
#include <stdio.h>
#include <stdlib.h> /* for EXIT_SUCCESS */

/* function declarations */
int sumTwoInts(int, int);

int main(void) {
    int numOne = 2;
    int numTwo = -5;
    int sum = sumTwoInts(numOne, numTwo);
    
    printf("the sum of %d and %d is: %d\n", numOne, numTwo, sum);

    return EXIT_SUCCESS;
}

int sumTwoInts(int a, int b) {
    return a + b;
}
```

*Results:* `the sum of 2 and -5 is: -3`

# Static Functions

The keyword `static` makes a function available only to the current source file. 
Other source files will not be able to call static functions. Be sure to include
the `static` keyword in the prototype as well. 

```c
#include <stdio.h>

static int sumTwoInts(int, int);

int main(void) {
    ...
}

static int sumTwoInts(int a, int b) {
    ...
}
```

# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)

