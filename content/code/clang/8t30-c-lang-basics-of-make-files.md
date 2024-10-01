---
title: c-lang-basics-of-make-files
tags: [makefiles, make, c, clang] 
id: 8t30
date: 2024-09-30
time: 20:17
---

# c lang basics of make files

In [c-lang-multiple-files](s8cb-c-lang-multiple-files.md), we compiled with gcc many C files to create a binary
file. With the Make program, we can define a build and execute a single command
to build our program rather than doing `gcc add.c add.h divide.c divide.h etc`.

# A Basic Make File

See the [GNU make manual](https://devdocs.io/gnu_make/) for information on the make program that builds 
`c` programs and has other useful tools. 

```bash
touch makefile
```

```make
program: add.c add.h program.c 
        gcc add.c add.h program.c
```

The `makefile` declares the name of the program called `program`, checks for the
existence of the listed files, then executes the `gcc` command.

# Zk Reference Notes

- node: [c-lang-node](3xe5-c-lang-node.md)

