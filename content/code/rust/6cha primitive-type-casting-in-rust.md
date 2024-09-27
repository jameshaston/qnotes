---
title: primitive type casting in rust
tags: [primitive, types, rust] 
id: 6cha
date: 2024-08-12
time: 20:30
---

# Primitive Type Casting In Rust 

Sometimes you have a primitive of one type, and you want to use it as a different
type. This happens frequently with numbers, where you want to perform an operation
on a `u8` variable and a `i32` variable, for example. 

This type of operation is not allowed in rust and will throw a compiler error 
unless you explicitly cast one of the primitive types to the other. This helps
prevent overflow errors. 

Casting with the `as <type>` keyword is how to accomplish this. Be careful with
casting to a smaller value as it may create overflow errors. 

```rust
fn main() {
    let x: i32 = 13;
    let y: u8 = 10;
    let z = x + (y as i32);
    println!("x + y = {z}");
}
```

*Results:* `x + y = 23`

If we did not cast `y`, we would get a compiler error. 


```rust
fn main() {
    let x: i32 = 13;
    let y: u8 = 10;
    let z = x + y;
    println!("x + y = {z}");
}
```

*Results:*
```
error[E0308]: mismatched types
 --> temp.rs:4:17
  |
4 |     let z = x + y;
  |                 ^ expected `i32`, found `u8`

error[E0277]: cannot add `u8` to `i32`
 --> temp.rs:4:15
  |
4 |     let z = x + y;
  |               ^ no implementation for `i32 + u8`
  |
  = help: the trait `Add<u8>` is not implemented for `i32`
  = help: the following other types implement trait `Add<Rhs>`:
            <&'a i32 as Add<i32>>
            <&i32 as Add<&i32>>
            <i32 as Add<&i32>>
            <i32 as Add>

error: aborting due to 2 previous errors

Some errors have detailed explanations: E0277, E0308.
For more information about an error, try `rustc --explain E0277`.
```

# Zk Reference Notes

- [rust-node](l7rn-rust-node.md)


