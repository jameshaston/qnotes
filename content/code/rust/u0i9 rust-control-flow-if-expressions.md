---
title: rust control flow if expressions
tags: [rust, if, expressions, control, flow] 
id: u0i9
date: 2024-08-13
time: 20:42
---

# Rust Control Flow 

The ability to run some code depending on whether a condition is `true` and to
run code repeatedly while a condition is `true` are basic building blocks in
most programming languages. 

The common constructs that let you control the flow of execution of Rust code
are `if` expression and `loops`.

> [Rust Book Control Flow](https://doc.rust-lang.org/book/ch03-05-control-flow.html). 

# If Expressions 

An `if` expression allows you to branch your code depending on conditions. If
the condition is met, perform an action. If it is not true, then perform 
some other action. 

If expressions start with the keyword `if`, followed by a condition. `if`
statements are sometimes referred to as *arms*. `else` is an optional
expression. Curly braces, `{}`, are used for each expression.

The expression must evaluate to a `bool` and not any other data type. 

```rust
// simple if expression
fn main() {
    let number = 3;

    if number < 5 {
        println!("condition was true");
    } else {
        println!("condition was false");
    }
}
```

*Results:* `condition was true`

An example of an `if` expression with a condition that does not evaluate to a
`bool` value. 

```rust
// compiler error: if expression does not evaluate to a bool
fn main() {
    let number = 3;

    if number {
        println!("The condition of the if expression is not a bool");
    }
}
```

*Results:*
```
error[E0308]: mismatched types
 --> temp.rs:5:8
  |
5 |     if number {
  |        ^^^^^^ expected `bool`, found integer

error: aborting due to 1 previous error

For more information about this error, try `rustc --explain E0308`.
```

# Handling Multiple Conditions with `else` and `else if`

You can use multiple conditions by combining `if`, `if else`, and `else`. 

```rust
fn main() {
    let num = 5;

    if num % 4 == 0 {
        println!("num divisible by 4.");
    } else if num % 3 == 0 {
        println!("num divisible by 3.");
    } else if num % 2 == 0 {
        println!("num divisible by 2.");
    } else {
        println!("number is not divisible by 4, 3, or 2.");
    }
}
```

*Results:* `number is not divisible by 4, 3, or 2.`

# Using `if` in a `let` Statement

Since `if` is an expression, we can use it in a `let` statement to assign the
result to a variable. 

```rust
// using if in a let statement
fn main() {
    let condition = true;
    let num = if condition {
        5
    } else {
        8
    };

    println!("the value of num is: {num}");
}
```

*Results:* `the value of num is: 5`

```rust
// using if in a let statement
fn main() {
    let condition = false;
    let num = if condition {
        5
    } else {
        8
    };

    println!("the value of num is: {num}");
}
```

*Results:* `the value of num is: 8`

The `if`, `else`, and `if else` expressions must be of the same data type. You cannot
compare `5` with `hi there`.

# Zk Reference Notes

- [rust-node](l7rn-rust-node.md)
- [rust literals and operators](jsl0%20rust-literals-and-operators.md)





