---
title: clang-pointer-operators
tags: [clang, pointers, operators, address, memory] 
id: d0vo
date: 2024-11-22
time: 19:50
---

# clang pointer operators

| Operator  | Name  | Meaning  |
| --------------- | --------------- | --------------- |
| * | indirection operator  | Declare a pointer  |
| * | dereference | dereference a pointer |
| -> | point-to | access fields of a structure referenced by a pointer |
| == or != | equality, inequality | comparison |
| >= > < <= | equality | comparison |
| (data type) | cast | change the type of pointer  |

# pointer arithmetic

Several arithmetic operations are performed on pointers to data. 

- adding an integer to a pointer 
- subtracting an integer from a pointer 
- subtracting two pointers from each other 
- comparing pointers 

Note that these operations are not always permitted on pointers to functions.

## adding an integer to a pointer 

This is a very common operation. When we add an integer to a pointer, the amount
added is the product of the integer times the number of bytes of the underlying 
data type. 

| data type    | size in bytes     |
|--------------- | --------------- |
| byte    | 1   |
| char   | 1   |
| short   | 2   |
| int    | 4   |
| long | 8   |
| float | 4   |
| double | 8   |

### Example - adding an integer to a pointer 

```c 
#include <stdio.h>

int main(void) {
        short vector[] = {2, 9, 1};
        short* ptr = vector;
        
        printf("value = %3d, address: %o\n", *ptr, ptr);
        ptr += 1;
        printf("value = %3d, address: %o\n", *ptr, ptr);
        ptr += 1;
        printf("value = %3d, address: %o\n", *ptr, ptr);

        return 0;
}
```

*Results:*
```
value =   2, address: 15537762244
value =   9, address: 15537762246
value =   1, address: 15537762250
```

## Example - subtracting an integer to a pointer 

```c 
#include <stdio.h>

int main(void) {
        short vector[] = {2, 9, 1};
        short* ptr = vector + 2;
        
        printf("value = %3d, address: %o\n", *ptr, ptr);
        ptr--;
        printf("value = %3d, address: %o\n", *ptr, ptr);
        ptr--;
        printf("value = %3d, address: %o\n", *ptr, ptr);

        return 0;
}
```

*Results:*
```
value =   1, address: 15517562250
value =   9, address: 15517562246
value =   2, address: 15517562244
```

## subtracting two pointers 

When one pointer is subtracted from another, we get the difference between their addresses.
The difference between the pointers is the number of "units" by which they differ. We use
"unit" as the operand. 

```c 
#include <stdio.h>

int main(void) {
        int array[] = {3, -1, 8, 12};
        int* p0 = array;
        int* p1 = array+1;
        int* p2 = array+2;
        int* p3 = array+3;

        printf("p3-p0:  %d\n", p3-p0);
        printf("p3-p1:  %d\n", p3-p1);
        printf("p3-p2:  %d\n", p3-p2);
        printf("p3-p3:  %d\n", p3-p3);

        return 0;
}
```

*Results:*
```
p3-p0:  3
p3-p1:  2
p3-p2:  1
p3-p3:  0
```

The type `ptrdiff_t` is a portable way to express the difference between two pointers.
Since pointer sizes can differ, this type simplifies the task of working with their
differences. 

In the following example, we use pointers to determine the difference between the
value stored in the array's first and second elements. 

```c 
#include <stdio.h>

int main(void) {
        int array[] = {3, -1, 8, 12};
        int* p0 = array;
        int* p1 = array+1;
        int* p2 = array+2;
        int* p3 = array+3;

        printf("*p0-*p1:  %d\n", *p0-*p1);

        return 0;
}

```

*Results:* `*p0-*p1:  4`

## comparing pointers 

```c 
#include <stdio.h>

int main(void) {
        int array[] = {3, -1, 8, 12};
        int* p0 = array;
        int* p1 = array+1;
        int* p2 = array+2;
        int* p3 = array+3;

        printf("p3 > p1:  %d\n", p3 > p1);
        printf("p0 > p2:  %d\n", p0 > p2);

        return 0;
}

```

*Results:*
```
p3 > p1:  1
p0 > p2:  0
```

# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)
- [c-lang-node-struct-with-pointers](sk9x-c-lang-node-struct-with-pointers.md)
- [c-lang-void-pointers](8nce-c-lang-void-pointers.md)
- [c-lang-functions-with-pointers](v1w5-c-lang-functions-with-pointers.md)
- [c-lang-using-pointers-with-arrays](femq-c-lang-using-pointers-with-arrays.md)

