---
title: lexical analysis
tags: [lexer, tokenizer, scanner, interpreter, syntax, ast]
id: d9rt
date: 2024-07-22
time: 22:30
---

# Lexing

> These are notes from the book *Writing An Interpreter* Chapter 1 by Thorsten Ball.  

See [Writing an Interpreter in Rust](https://www.dannyvankooten.com/blog/2022/rewriting-interpreter-rust/) for the rust implementation
of crafting an interpreter for the `monkey` language.

See this [rs-monkey-lang repo](https://github.com/wadackel/rs-monkey-lang) for source code. 

## Lexical Analysis 

A [lexer](https://en.wikipedia.org/wiki/Lexical_analysis), also referred to as a tokenizer or a scanner, transforms a programming language's
source code into tokens. This process is called lexical analysis or lexing. Tokens are small
easily categorizable data structures that are provided to a parser. The parser performs 
another transformation and turns tokens into an abstract syntax tree.

Here's an example of transforming source code into tokens using a lexer:

```rust
let x = 5 + 5;
```
Example token output:
```text
[
    LET,
    IDENTIFIER("x"),
    EQUAL_SIGN,
    INTEGER(5),
    PLUS_SIGN,
    INTEGER(5),
    SEMICOLON,
]
```
These tokens have the original source code representation attached. Note, in this example, 
whitespace characters do not show up as tokens. However, whitespace can be important in 
languages like Python. A production-ready lexer might also attach the line number,
column number, and filename to a token. Why? For example,  to later output more useful
error messages in the parsing stage, such as:

```
"error: expected simicolon token. line 42, column 23, program.monkey"
```

## Defining Our Token Data Structure

We need to create a data structure that will take `source code` as input and output the 
`tokens` that represent the input stream. In rust, the `enum` data structure is a good
starting place. See [rust enums](juqi%20rust-enums.md).

# Zk Reference Notes

- [rust-node](l7rn-rust-node.md)
- [gnu c lexical elements](../clang/11os%20gnu-c-lexical-elements.md)

