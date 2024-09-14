---
id: 1ye3
title: basic comments in rust
date: 2024-08-08
time: 19:52
keywords: [rust, comments] 
---

# Basic Comments In Rust 

Rust supports a variety of comments for code explaination and documentation.
Here are a few basic examples.

See [Rust Book - Publishing a Crate](https://doc.rust-lang.org/book/ch14-02-publishing-to-crates-io.html) for details on the various
types of comments and their purpose. 

```rust
// Line comments which go to the end of a line.

/* 
Block comments which go to the closing delimiter. 
You can skip lines.
Include many lines.
*/

/// Generate library docs for the following item. Parsed into HTML.

//! Generate library docs for the enclosing item. Parsed into HTML.
fn main() {
    println!("hello there");
}
```

*Results:*
```
error[E0753]: expected outer doc comment
  --> temp.rs:11:1
   |
11 |   //! Generate library docs for the enclosing item. Parsed into HTML.
   |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
12 | / fn main() {
13 | |     println!("hello there");
14 | | }
   | |_- the inner doc comment doesn't annotate this function
   |
help: to annotate the function, change the doc comment from inner to outer style
   |
11 | /// Generate library docs for the enclosing item. Parsed into HTML.
   |   ~

error: aborting due to 1 previous error

For more information about this error, try `rustc --explain E0753`.
```

