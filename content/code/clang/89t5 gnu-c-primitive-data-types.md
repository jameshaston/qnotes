---
title: gnu c primitive data types
tags: [primitives, types, c, clang] 
id: 89t5
date: 2024-09-23
time: 17:54
---

# Gnu C Primitive Data Types 

> These notes are based on the [GNU C Reference Manual](https://www.gnu.org/software/gnu-c-manual/gnu-c-manual.html#Primitive-Types).

There are three primitive data types in the `c` language: 

- Integer types
- Real number types 
- Complex number types

## Integer Types

The integer data types range in size from at least 8 bits to at least 32 bits. The
C99 standard extends this range to include integer sizes of at least 64 bits. The
sizes and ranges for these types are minimums that depend on the computer platform.

Integer types are used for whole numbers and `char` data type. These are the sizes
and ranges of the integer primitive data types:

| Type          | Size         | Range         |
|-------------|------------|---------------|
| `Signed char`  | 8-bit      | -128 to 127   |
| `Unsigned char`  | 8-bit      | 0 to 255     |
| `char`          | varies on system | -128 to 127 or 0 to 255 |
| `short int`     | 16-bit     | -32,768 to 32,767 |
| `unsigned short int` | 16-bit     | 0 to 65,535   |
| `int`           | 32-bit     | -2.1B to 2.1B |
| `unsigned int`   | 32-bit     | 0 to 4.2B    |
| `long int`       | 32-bit or 64-bit | at least -2.1B to 2.1B |
| `unsigned long int` | 32-bit or 64-bit | 0 to at least 4.2B  |
| `long long int`   | 64-bit     | -huge to huge |
| `unsigned long long int` | 64-bit     | 0 to huge    |

Here are some examples:

- `int foo;`
- `unsigned int bar = 58;`
- `char chr = 'a';`

## Real Number Types










# Zk Reference Notes

- [c-lang-node](3xe5-c-lang-node.md)
- [gnu c lexical elements](11os%20gnu-c-lexical-elements.md)

