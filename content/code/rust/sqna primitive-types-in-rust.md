---
title: primitive types in rust
tags: [primitives, types, rust, std] 
id: sqna
date: 2024-08-08
time: 20:18
---

# Primitive Types In Rust 

Rust provides access to a wide variety of `primitives` through the standard library.

> [The Rust Standard Library Documentation](https://doc.rust-lang.org/std/).

`std` is available to all rust crates by default. The standard library can be
accessed in `use` statements through the path `std`, as in `use std::env`. 

In `std`, `primitives` are listed and defined. A few examples include the following.

## Scalar Types

- Signed integers `i8`, `i128`, `isize` (pointer size).
- Unsigned integers `u16`, `u32`, `usize` (pointer size).
- Floating points `f32`.
- Characters `char` which are unicode scalar values `a` (4 bytes each).
- Booleans `bool` which are `true` and `false`.
- Unit type `()` whose only possible value is an empty tuple.

Despite the value of a unit type being a tuple, it is not considered a 
compound type because it does not contain multiple values. 

## Compound Types 

- Arrays `[1, 2, 3]`.
- Tuples `(1, true)`.

Variables can always be type annotated. Numbers may additionally be 
annotated by a *suffic* or by *default*. 

> Integers default to `i32` and flots to `f64`.

Rust can infer types from context. 

# Zk Reference Notes

- [rust-node](l7rn-rust-node.md)
- [rust book data types](65ml%20rust-book-data-types.md)
- [rust literals and operators](jsl0%20rust-literals-and-operators.md)

