---
id: wx47
title: formatted print in rust
date: 2024-08-08
time: 20:02
keywords: [formatted:print, print, rust, macros, traits] 
---

# Formatted Print In Rust 

In rust, printing is handled by a series of macros defined in `std::fmt`, some
of which include the following:

- `format!` write formatted text to `String`.
- `print!` same as above but the text is printed to `io::stdout`.
- `println!` same as `print!` but a newline is appended.
- `eprint!` same as `print!` but text is printed to `io::stderr`.
- `eprintln!` same as `eprint!` but a newline is appended.

> See `std::fmt` [rust documentation](https://doc.rust-lang.org/std/fmt/). 

# Formatted Traits

`std::fmt` contains many [traits](https://doc.rust-lang.org/std/fmt/#formatting-traits) which govern the display of text.
The base form of two important traits are listed below:

- `fmt::Debug` uses the `{:?}` marker for debugging purposes.
- `fmt::Display` uses the `{}` marker for pretty printing text.

Implementing the `fmt::Display` trait automatically implements the `ToString` trait
which allows us to convert the type to `String`.


