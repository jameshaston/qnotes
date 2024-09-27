---
title: rust literals and operators
tags: [rust, literals, operators, expressions, statements] 
id: jsl0
date: 2024-08-08
time: 20:32
---

# Rust Literals And Operators 

Rust is primarily an expression language. This means that most forms of value-
producing or effect-causing evaluation are directed by the uniform syntax
category of expressions. 

Each kind of expression can typically nest within each other kind of expression,
and rules for evaluation of expression involve specifying both the value
produced by the expression and the order in which its sub-expressions are themselves
evaluated. 

In contrast, statements serve mostly to contain and explicitly sequence expression
evaluation. 

> See [The Rust Reference]() for documentation on expressions, statements, and more.

# Literal Expressions

A `literal expression` is an expression consisting of a single token, rather
than a sequence of tokens, that immediately and directly denotes the value
it evaluates to, rather than referring to it by name or by some other
evaluation rule. 

A literal is a form of `constant expression`, so is evaluated (primarily) at 
compile time. Each of the lexical literal forms can make up a literal
expression, as can the keywords `true` and `false`.

> See [Literal Expressions in the Rust Reference](https://doc.rust-lang.org/reference/expressions/literal-expr.html).

Some examples are `char`, `int`, `float`, `byte`, `str`, and `c-str`.

Integers can be expressed using hexadecimal, octal, or binary notation
using `0x`, `0o`, and `0b`, respectively. 

Rust also supports `e-notation`, e.g. `1e6`, `7.5e-4` and the associated
type is `f64`. See [e-notation wiki](https://en.wikipedia.org/wiki/Scientific_notation#E_notation) for a reference on scientific notation.

# Operator Expressions

Operators are defined for built in types. Many of the operators can be overloaded
using traits in `std::ops` or `std::cmp`. A few examples of operator expressions
are:

- `BorrowExpression`
- `DereferenceExpression`
- `ComparisonExpression`
- `TypeCastExpression`
- `AssignmentExpression`

> See [Operator Expression in the Rust Reference](https://doc.rust-lang.org/reference/expressions/operator-expr.html). 


# Zk Reference Notes

- [rust-node](l7rn-rust-node.md)
- [lexical analysis](d9rt%20lexical-analysis.md).
- [primitive types in rust](sqna%20primitive-types-in-rust.md).

