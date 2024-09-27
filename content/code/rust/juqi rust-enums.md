---
title: rust enums
tags: [enums, structs]
id: juqi
date: 2024-07-23
time: 17:29
---

# Rust Enums

An `enum` is a rust data structure which allows you to define a type by enumerating 
its possible variants. Any variant that is valid as a `struct` is also valid 
in an enum. The [Rust Book](https://doc.rust-lang.org/book/ch06-00-enums.html) explains enums and error handling with pattern 
matching in Chapter 6. Additionally, there are great examples of implementing enums
in [Rust by Example](https://doc.rust-lang.org/rust-by-example/custom_types/enum.html). 

# Defining an Enum 

We will define an `enum` for a lexer (tokenizer) as an example. [^1]

```rust
pub struct Token {
    pub kind: TokenKind,
    pub span: Span,
}

pub struct Span {
    pub start: usize,
    pub end: usize,
}

pub enum TokenKind {
    ILLEGAL,
    EOF,

    IDENTIFIER { name: String },
    INT(i64),
    // snip
}
```
The example above utilizes both structs and enums to create a custom data type
for a lexer. [^2] 

> References

- [rust-node](l7rn-rust-node.md)
[1^] [[d9rt lexical-analysis]]
[2^] [token.rs](https://github.com/jameshaston/monkey-rust-gengilawen/blob/main/lexer/token.rs)  

