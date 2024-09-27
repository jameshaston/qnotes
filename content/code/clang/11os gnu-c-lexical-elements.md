---
title: gnu c lexical elements
tags: [c, clang, lexical] 
id: 11os
date: 2024-09-22
time: 21:25
---

# GNU C Reference Manual Notes

These notes are based on the [GNU C Reference Manual](https://www.gnu.org/software/gnu-c-manual/gnu-c-manual.html#Identifiers). 

# Lexical Elements 

The main lexical elements of `c` are called tokens. There are five tokens:

1. keywords
2. identifiers
3. constants
4. operators
5. separators

## Identifiers

**Identifiers** are sequences of characters used for naming variables, functions, new
data types, and preprocessor macros. They can include chars, floats, and `_`. 

The first character of an identifier **cannot be a digit**. Identifiers are also 
case-sensitive. 

When using GNU extensions, you can include `$` in identifiers.

## Keywords

**Keywords** are special identifiers reserved for `c` and builtin to the language. 

#### ANSI C89 Keywords

```
auto break case char const continue default do double else enum extern
float for goto if int long register return short signed sizeof static
struct switch typedef union unsigned void volatile while
```

#### ISO C99 Keywords

```
inline _Bool _Complex _Imaginary
```

#### GNU Extension Keywords

```
__FUNCTION__ __PRETTY_FUNCTION__ __alignof __alignof__ __asm
__asm__ __attribute __attribute__ __builtin_offsetof __builtin_va_arg
__complex __complex__ __const __extension__ __func__ __imag __imag__ 
__inline __inline__ __label__ __null __real __real__ 
__restrict __restrict__ __signed __signed__ __thread __typeof
__volatile __volatile__
```

> The `restrict` keyword is recognized as a keyword with GNU Extensions.

## Constants

A **constant** is a literal numeric or character value such as `5` or `m`. All 
constants have a specific data type. 

Constants can be type cast explicitly or inferred by the compiler based
on its value. 

#### Integer Constants

An **integer constant** is a sequence of digits, with an *optional* prefix
to denote a number base.

**Hexadecimal** (base 16) values are preceded by `0x` or `0X`. Hex values may 
use the digits `0-9` and the letters `a-f`. Examples:

- `0x2f`, `0x88`, `0xAB43`, `0x1`, `0xAbCd`

Base 8 - **octal constants** begin with `0`, but do not have `x` in the
prefix. Octal values only use the digits `0-7`. Examples:

- `057`, `012`, `03`, `0241`

All other cases are considered **decimal constants** with the digits
`0-9`, such as `438`, `2481`, and `8`.

> There are various types of integer **data types**.

Integers can be short, long, signed, and unsigned. You can force an integer
constant to be of long or unsigned by appending a sequence of one or more
letters to the end of the constant. `U` and `u` for unsigned, and `l` and `L`
for long.

For example, `45U` is an unsigned `int` constant. You can also combine
letters in any order, such as `45UL` for an unsigned long int constant.

Both ISO C99 and GNU C extensions add the integer types `long long int`. For
example, `45ULL` is an unsigned long long int constant. 

#### Character Constants

A **character constant** is usually a single character enclosed within single
quotation marks like `h`. `char` are type `int` by default. 

Some characters, such as `'`, cannot be represented using only one character
and must be **escaped** with "escape sequences". Examples:

- `\\`  backslash character
- `\?`  question mark
- `\'`  single quote
- `\"`  double quote
- `\a`  audible alert 
- `\b`  backspace
- `\e`  escape
- `\f`  form feed
- `\n`  newline
- `\r`  carriage return
- `\t`  horizontal tab
- `\v`  vertical tab
- `\o`  octal and also `\oo` and `\ooo`
- `\xh` hex and also `\xhh` and `xhhh` etc

> To use any of these escape sequences, enclose the sequence in single quotes,
and treat it as if it were any other character. For example, the letter m is 
`m` and the newline character is `\n`.

#### Real Number Constants (Floats)

A real number constant - a **float** - is a value that represents a fractional
number. Floats are represented in `c` using the `double` and `F` or `f` keywords,
such as `double a = 4.7f`. 

Floats can also be followed by `e` or `E` and an integer exponent. The exponent
can be positive or negative. 

```c
double x, y;

x = 5e2f;
y = 8e-3;
```

#### String Constants

A **string constant** is a sequence of zero or more characters, digits, and
escape sequences enclosed within double quotation marks `"a string"`. A string
constant is of type `array of characters`.

All string constants contain a *null termination character* `\0` as their 
last character. Strings are stored as arrays of characters with no inherent 
size attribute. 

The null termination character lets string-processing functions know where the
string ends. 

```
/* single string constant */
"tutti frutti ice cream"

/* concatenated string constant */
"tutti" "frutti" "ice" "cream"

/* escaping double quotes in string constant */
"\"tutti frutti ice cream\""
```

## Operators

An operator is a special **token** that performs an operation, such as addition
or subtraction on either one, two, or three operands. 

Full coverage of operators is in a later chapter called [Expressions and Operators](https://www.gnu.org/software/gnu-c-manual/gnu-c-manual.html#Expressions-and-Operators).

## Separators

A separator separates tokens. White space is a separator, but it is not a token. 
The other separators are all single-character tokens:

- `( ) [ ] { } ; , . :`

## White Space

White space is the collective term used for several characters:

- space, tab, newline, vertical tab, and form-feed.

White space is ignored, except in literal character constants and literal string 
constants. It is optional except when it is used to separate tokens.

# Zk Reference Notes

- [c-lang-node](3xe5-c-lang-node.md)
- [lexical analysis](../rust/d9rt%20lexical-analysis.md)

