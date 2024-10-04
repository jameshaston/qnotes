---
title: c-lang-command-line-arguments
tags: [argc, argv, cli, arguments, c, clang] 
id: 0zws
date: 2024-10-03
time: 22:31
---

# c lang command line arguments

C programs can interact with the shell with command line arguments. See the glibc
manual about [program arguments](https://sourceware.org/glibc/manual/latest/html_mono/libc.html#Program-Arguments) here for information about `argc` and `argv`.

The system starts a C program by calling the `main` function. In ISO C, you can define
`main` to take no arguments or to take two arguments that represent the command line
arguments to the program, like so:

```
int main(int argc, char *argv[]) {}
```

The command line arguments are the whitespace-separated tokens passed by the shell 
command used to invoke the program. 

- `argc` is the number of command line arguments.
- `argv` is a vector of C strings where its elements are the individual cli args strings.

For example, for the command `cat foo bar`, `argc` is 3 and `argv` has three elements -
"cat", "foo", and "bar". 

On UNIX systems, you can define `main` using three arguments:

```
int main(int argc, char *argv[], char *envp[]) {}
```

The new argument `envp[]` gives the program's environment and is the same value of
`environ`. See [Environment Variables](https://sourceware.org/glibc/manual/latest/html_mono/libc.html#Environment-Variables) for more information.

Note that POSIX.1 does not allow the three-argument form, so for portability, its
best to use the two-argument syntax. 

# Example

Running the following example from neovim provides the output below. Create a C
program and run in terminal to see different output.

```c
#include <stdio.h>

int main(int argc, char *argv[]) {
    printf("argc: %d\n", argc);

    for (int i = 0; i < argc; i++) {
        printf("argv[%d] = %s\n", i, argv[i]);
    }

    return 0;
}
```

*Results:*
```
argc: 1
argv[0] = /tmp/mdeval//0zwsclangcommandlineargumentsmd_48_60.out
```

Finally, running the code with multiple args and printing with a for loop produces
the following:

```
../dev/clang/tutorial/commandline                      v15.0.0
➜ ./main 1 2 3 command4
argc: 5
argv[0] = ./main
argv[1] = 1
argv[2] = 2
argv[3] = 3
argv[4] = command4
```

# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)

