---
id: ujjw
title: rust book functions
date: 2024-08-09
time: 19:35
keywords: [rust, functions, parameters] 
---

# Rust Functions 

Functions are prevalent in rust. One of the most important functions in rust is
the `fn main() {}` function, which is the entry point for many rust programs.

Rust code uses `snake_case` as the conventional style for function and variable
names. Additionally, arguments in rust are type annotated. You can specify a
return type using the `->` syntax. 

See the [Rust Book Functions Chapter](https://doc.rust-lang.org/book/ch03-03-how-functions-work.html) for more details.  

## Basic Function Example

```rust
fn main() {
    println!("sup aliens!");

    another_function(); // call `another_function()`
}

fn another_function() {
    println!("This is another function that just prints text.");
}
```

*Results:*
```
sup aliens!
This is another function that just prints text.
```

> Rust doesn't care where you define functions. `another_function` could be defined before `main`.

# Parameters

We can define functions to have parameters, which are special variables that
are part of a function's *signature*. When a function has *parameters*, you can
provide it with concrete values referred to as *arguments*.  

```rust
// basic function with parameters
fn main() {
    another_function(5);
}

fn another_function(x: i32) {
    println!("x is: {}", x);
}
```

*Results:* `x is: 5`

> Signatures must declare the type of each parameter.

Here is an example of a function with multiple parameters:

```rust
// basic function with parameters
fn main() {
    another_function(5, 'z');
}

fn another_function(x: i32, character: char) {
    println!("x is: {} and character is: {}", x, character);
}
```

*Results:* `x is: 5 and character is: z`

# Statements and Expressions

Function bodies are made up of a series of statements and optionally ending in
an expression. 

- **Statements** are instructions that perform an action and do not return a value.
- **Expressions** evaluate to a resultant value. 

```rust
// statements and expressions
fn main() {
    // statement
    let y = 5;
    // expression
    let z = {
        y + 3
    };

    println!("y = {} and z = {}", y, z);
}
```

*Results:* `y = 5 and z = 8`

The expression is the above example is:

```rust
{
    y + 3
}
```

# Functions with Return Values

Functions can return values to the code that calls them. We don't name return
values, but we must declare their type after an arrow `->`. In rust, the return
value of the function is synonymous with the value of the final expression
in the block of the body of a function. 

You can return early from a function by using the `return` keyword and 
specifying a value. Most functions return the last expression implicitly. 

```rust
fn five() -> i32 {
    29
}

fn main() {
    let x = five();
    println!("x = {x}");
}
```

*Results:* `x = 29`

```rust
fn plus_one(x: i32) -> i32 {
    x + 1
}

fn main() {
    let num = 11;
    
    let num = plus_one(num);

    println!("num is {num}");
}
```

*Results:* `num is 12`

Note that functions that don't return a value actually return the unit type `()`.
These functions can omit the `-> ()` syntax from the function signature without
producing an error. We have seen this in `main()`:

```rust
fn main() -> () {
    println!("supppp");
}
```

*Results:* `supppp`









