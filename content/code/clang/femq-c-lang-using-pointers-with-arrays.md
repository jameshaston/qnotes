---
title: c-lang-using-pointers-with-arrays
tags: [pointers, arrays, c, clang] 
id: femq
date: 2024-09-30
time: 00:07
---

# c lang using pointers with arrays

Pointers can be used with arrays to manipulate array values. Let's see a couple 
simple examples to demonstrate this concept.

# Using Pointers with Arrays

```c
#include <stdio.h>

int main(void) {

    int a[5];
    int *p;

    printf("a[2] = %d\n", a[2]);

    /* use *p to change the array 'a' */
    p = &a[2]; /* pointer to address of index 2 of array a */
    *p = 4;    /* use pointer to change the value of a[2] */

    printf("a[2] = %d\n", a[2]);

    /* move the memory address using a pointer */
    printf("Using a pointer to move to the next index of a change its value\n");
    printf("a[1] = %d\n", a[1]);
    p = &a[0];
    *(p + 1) = 15;
    printf("a[1] = %d\n", a[1]);

    return 0;
}
```

*Results:*
```
a[2] = -480575487
a[2] = 4
Using a pointer to move to the next index of a change its value
a[1] = -1925608776
a[1] = 15
```

# Use a Pointer to Iterate over Memory Address

In the following example, we will use a pointer to sum the elements of an array
using a `for` statement. 

```c
#include <stdio.h>

int main(void) {
    int a[3] = {5, 0, 4};
    int *p;
    int sum = 0;

    for (p = &a[0]; p < &a[3]; p++) {
        printf("p address is: %d\n", p);
        printf("p value is: %d\n", *p);
        sum += *p; /* get the value of the current address */
    }
    printf("sum = %d\n", sum);
}
```

*Results:*
```
p address is: 1802510696
p value is: 5
p address is: 1802510700
p value is: 0
p address is: 1802510704
p value is: 4
sum = 9
```

# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)
- [c-basics-of-pointers-and-addresses](68q5-c-basics-of-pointers-and-addresses.md)
- [c-lang-functions-with-pointers](v1w5-c-lang-functions-with-pointers.md)





