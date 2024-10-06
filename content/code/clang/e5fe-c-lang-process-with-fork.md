---
title: c-lang-process-with-fork
tags: [fork, processes, unistd, c, clang] 
id: e5fe
date: 2024-10-05
time: 18:03
---

# c lang process with fork

The fork function is the primitave for creating a process. It is declared in the 
header file `unistd.h`. See [creating a process](https://www.gnu.org/software/libc/manual/html_node/Creating-a-Process.html) in the libc manual.

# `fork` Function

`Function: pid_t fork (void)` - the `fork` function creates a new process. 

If successful, there are both *parent* and *child* processes and both see fork return
with different values: 0 in the child process and the child process ID in the parent
process. 

If process creation failed, `fork` returns -1 in the parent process. The following are
the `errno` error conditions:

- EAGAIN: Not enough system resources to create another process.
- ENOMEM: The process requires more space than the system can supply. 

# `vfork` and `_Fork`

`_Fork` is similar to `fork` but does not invoke any callbacks registered with `pthread_atfork` and 
does not reset any internal state or locks.

`vfork` function is similar to `fork` but is more efficient on *some* systems. 

# Example

This trivial example will output `hello world` two times using `fork`. 

```c
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(void) {
    fork();
    printf("hello world\n");
    return 0;
}
```

*Results:*
```
hello world
hello world
```

You can get the `id` of the process by storing `fork` in a variable.

```c
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(void) {
    int id = fork();

    if (id == 0) {
        printf("hello world from child process with id: %d\n", id);
    } else {
        printf("hello world from parent/main process with id: %d\n", id);
    }

    return 0;
}
```

*Results:*
```
hello world from parent/main process with id: 77460
hello world from child process with id: 0
```

# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)

