---
id: 5cuu
title: rust book variables and mutability
date: 2024-08-08
time: 21:41
keywords: [rust, variables, mutability] 
---

# Rust Book Variables And Mutability 

See [The Rust Book Section 3.1](https://doc.rust-lang.org/book/ch03-01-variables-and-mutability.html) for references to these notes.

Variables are immutable by default in rust. When a variable is immutable, once a
value is bound to a name, you cannot change its value.

> Example - Cannot assign twice to immutable variable:

```rust
// This code will produce a compiler error. 
fn main() {
    let x = 5;
    println!("The value of x is: {x}");
    x = 6;
    println!("The value of x is: {x}");
}
```

*Results:*

```
error[E0384]: cannot assign twice to immutable variable `x`
 --> temp.rs:5:5
  |
3 |     let x = 5;
  |         -
  |         |
  |         first assignment to `x`
  |         help: consider making this binding mutable: `mut x`
4 |     println!("The value of x is: {x}");
5 |     x = 6;
  |     ^^^^^ cannot assign twice to immutable variable

error: aborting due to 1 previous error

For more information about this error, try `rustc --explain E0384`.
```

```bash
# run this with :MdEval to see the explanation.
rustc --explain E0384
```

# `mut` and Shadowing

The failed code can be fixed in two ways: 

- `mut` to make the variable mutable.
- Shadowing by assigning a new value to the same variable name. 

You can declare a new variable with the same name as a previous variable. Rustaceans
say that the first variable is *shadowed* by the second, which means that the 
compiler sees the second variable when you use the same name.

Shadowing effectively creates a new variable when we use the `let` keyword again,
and we can change the type of the value but reuse the same name.

Let's complete an example for both methods to see the difference.

> `mut` keyword to make a variable mutable:

```rust
// Fixing the compiler error with `mut` keyword.
fn main() {
    let mut x = 5; // add `mut` to make variable mutable
    println!("The value of x is: {x}");
    x = 6;
    println!("The value of x is: {x}");
}
```

*Results:*

```
The value of x is: 5
The value of x is: 6
```

> Shadow the variable using `let`:

```rust
// Fixing the compiler error with `let` keyword.
fn main() {
    let x = 5;  
    println!("The value of x is: {x}");
    let x = 6; // Shadow the variable with `let`
    println!("The value of x is: {x}");
}
```

*Results:*
```
The value of x is: 5
The value of x is: 6
```

This program first binds `x` to `5`. Then it creates a new variable `x` by 
repeating `let x =`, taking the original value and assigning `6` so the value 
of `x` is then `6`. 

By using `let`, we can perform transformations on a value but have the variable
be immutable after those transformations have been completed. 

> Another shadowing example:

```rust
fn main () {
    let spaces = "      ";
    let spaces = spaces.len();
    println!("The length of spaces is: {spaces}");
}
```

*Results:* `The length of spaces is: 6`

Using `mut` for the example above would create a compiler error.


```rust
fn main () {
    let mut spaces = "      ";
    spaces = spaces.len();
    println!("The length of spaces is: {spaces}");
}
```

*Results:*
```
error[E0308]: mismatched types
 --> temp.rs:3:14
  |
2 |     let mut spaces = "      ";
  |                      -------- expected due to this value
3 |     spaces = spaces.len();
  |              ^^^^^^^^^^^^ expected `&str`, found `usize`

error: aborting due to 1 previous error

For more information about this error, try `rustc --explain E0308`.
```

# `zk` References

- [primitive types in rust](sqna%20primitive-types-in-rust.md).


