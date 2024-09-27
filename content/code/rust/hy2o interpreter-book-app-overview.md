---
title: interpreter book app overview
tags: [interpreter, lexer, parser, ast, evaluator] 
id: hy2o
date: 2024-08-07
time: 20:52
---

# Interpreter Book App Overview 

These notes are based on the book ***Writing an Interpreter***. 

## Overview of What You Will Build

We will build an interpreter from scratch for the Monkey Language. The interpreter
will tokenize and parse Monkey source code in a REPL, building up an internal
representation of the code called abstract syntax tree, and then evaluate this 
tree. 

It will have a few major features:

- the lexer.
- the parser.
- the abstract syntax tree.
- the internal object system.
- the evaluator.

We will build these parts in exactly this order, from scratch.

## Related Notes

- [lexical analysis](d9rt%20lexical-analysis.md).
- [rust-node](l7rn-rust-node.md)

