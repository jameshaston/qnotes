---
title: c-lang-node-struct-with-pointers
tags: [node, structs, pointers, c, clang] 
id: sk9x
date: 2024-09-30
time: 21:11
---

# c lang node struct with pointers

The fundamental concept of many linear data structures is linking one node to 
another node using pointers. We will demonstrate this concept using a `struct`
and pointers to connect nodes in a linear fashion. These skills will be helpful
for creating other data structures like stacks, queues, etc.

See other notes on pointers for reference:

- [c-basics-of-pointers-and-addresses](68q5-c-basics-of-pointers-and-addresses.md)
- [c-lang-functions-with-pointers](v1w5-c-lang-functions-with-pointers.md)
- [c-lang-using-pointers-with-arrays](femq-c-lang-using-pointers-with-arrays.md)

# Node Data Type Using a Struct

Create a `node.h` header file that contains the `struct` implementation. Then use
the `struct` in the main program. The implementation would look something like
the following:

```c
/* node.h */
struct node {
    int location;
    struct node *next;
};
```

```c
/* main.c */
#include <stdio.h>
/*#include "node.h"*/

/* node.h */
struct node {
    int location;
    struct node *next;
};

int main(void) {
    struct node james;
    james.location = 0;

    struct node jane;
    jane.location = 1;

    /* james.next points to the address of the node 'jane' */
    james.next = &jane;

    printf("node james.location = %d\n", james.location);
    printf("node jane.location = %d\n", jane.location);
    printf("\n\n");
    printf("node james.next.location value = %d\n", james.next->location);
    printf("node jane.location value = %d\n", jane.location);
    printf("james.node.location successfully points to jane.location!\n");
    
    struct node julia;
    julia.location = 2;
    jane.next = &julia;

    printf("\n\n");
    printf("node jane.next.location value = %d\n", jane.next->location);
    printf("node julia.location value = %d\n", julia.location);
    printf("jane.node.location successfully points to julia.location!\n");

    struct node end;
    end.location = 3;
    julia.next = &end;

    printf("\n\n");
    printf("julia.next.location value = %d\n", julia.next->location);
    printf("end.location value = %d\n", end.location);

    return 0;
}
```

*Results:*
```
node james.location = 0
node jane.location = 1


node james.next.location value = 1
node jane.location value = 1
james.node.location successfully points to jane.location!


node jane.next.location value = 2
node julia.location value = 2
jane.node.location successfully points to julia.location!


julia.next.location value = 3
end.location value = 3
```


# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)


