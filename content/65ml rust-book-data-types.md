---
id: 65ml
title: rust book data types
date: 2024-08-09
time: 17:44
keywords: [rust, data:types, scalars, compound, variables] 
---

# Rust Data Types 

Every value in rust is of a certain data type, which tells rust what kind of 
data is being specified. We will look at the scalar and compound data types.

> These notes are based on the [Rust Book Section 3.2 Data Types](https://doc.rust-lang.org/book/ch03-02-data-types.html).

Rust is a **statically typed** language, which means that it must know the
types of all variables at compile time. Rust can usually infer types based on
the value. Sometimes you may have to annotate the type explicitly. 

## Compiler Error - Type Annotations Needed

Let's look at an example where rust cannot infer the type based on the value, 
and look at the compiler error for details. 

```rust
// Compiler Error; type annotations needed
fn main() {
    let guess = "42".parse().expect("Not a number!");
    println!("guess is: {guess}");
}
```

*Results:*
```
error[E0284]: type annotations needed
 --> temp.rs:3:9
  |
3 |     let guess = "42".parse().expect("Not a number!");
  |         ^^^^^        ----- type must be known at this point
  |
  = note: cannot satisfy `<_ as FromStr>::Err == _`
help: consider giving `guess` an explicit type
  |
3 |     let guess: /* Type */ = "42".parse().expect("Not a number!");
  |              ++++++++++++

error: aborting due to 1 previous error

For more information about this error, try `rustc --explain E0284`.
```

We can fix this code by adding a type annotation for the variable `guess`.

```rust
// Fix the error with a specific type annotation `u32`
fn main() {
    let guess: u32 = "42".parse().expect("Not a number!");
    println!("guess is: {guess}");
}
```

*Results:* `guess is: 42`

# Scalar Types

A scalar type represents a single value. Rust has four primary scalar types:

- integers.
- floating points.
- booleans.
- characters.

# Compound Types

Compound types can group multiple values into one type. Rust has two primitive
compound types: tuples and arrays. 

## The Tuple Type

A tuple is a general way of grouping together a number of values with different
types into one compound data type. 

> Tuples have a fixed length. Once they are declared, they cannot grow or shrink in size. 

We create a tuple by writing a comma-separated list of values inside parentheses.
Each position in the tuple has a type, and the types of the different values in 
the tuple don't have to be the same. 

### Tuple Example

```rust
// declaring a tuple with type annotations
fn main() {
    let tup: (i32, f64, u8) = (500, 6.4, 1);
    println!("{:?}", tup);
}
```

*Results:* `(500, 6.4, 1)`

### Destructure a Tuple

In the example above, the variable `tup` binds to the entire tuple. To get the 
individual values out of a tuple, we can use pattern matching to destructure
a tuple value. 

```rust
// destructure a tuple to get a value
fn main() {
    let tup: (i32, f64, u8) = (500, 6.4, 1);
    let (x, y, z) = tup;
    println!("the value of x is: {x}");

    // access a tuple element with `.` syntax
    let tup2: (i32, f64, u8) = (200, 5.4, 8);
    let v1 = tup2.0;
    let v2 = tup2.1;
    let v3 = tup2.2;
    println!("v3 is: {v3}");
}
```

*Results:*
```
the value of x is: 500
v3 is: 8
```

## The Array Type

Another way to have a collection of multiple values is with an `array`. Unlike
a tuple, every element of an array must have the same type. 

> Rust `array` type is fixed in length and allocated on the **stack** . 

If you need a data type to grow and shrink in size, consider using a `vector`.
Vectors are discussed in [Chapter 8](https://doc.rust-lang.org/book/ch08-01-vectors.html). 

```rust
// Declaring an array
fn main() {
    let a = [3, 8, 29];
    println!("the array 'a' is: {:?}", a);
}
```

*Results:* `the array 'a' is: [3, 8, 29]`

You write an array's type like this:

```rust
fn main() {
    let a: [i32; 5] = [4, 2, 8, 5, 10];
    println!("a is: {:?}", a);
}
```

*Results:* `a is: [4, 2, 8, 5, 10]`

You can instantiate an array with the same value for each element like this:

```rust
// instantiate an array with an initial value and then the length
fn main() {
    let a = [3; 5];
    println!("a is: {:?}", a);
}
```

*Results:* `a is: [3, 3, 3, 3, 3]`

### Accessing Array Elements

An array is a single chunk of memory with a known, fixed-size that can be 
allocated on the stack. You can access array elements like so:

```rust
// access array elements
fn main() {
    let a: [i8; 3] = [3, 9, 0];
    let v1 = a[0];
    println!("the first element of a is: {}", v1);
}
```

*Results:* `the first element of a is: 3`

Rust will produce a runtime error if you attempt to access an element that is 
out-of-bounds.

```rust
// Attempt to access an element past the length of the array
fn main() {
    let a: [i8; 3] = [3, 9, 0];
    let v1 = a[5];
    println!("the first element of a is: {}", v1);
}
```

*Results:*
```
error: this operation will panic at runtime
 --> temp.rs:4:14
  |
4 |     let v1 = a[5];
  |              ^^^^ index out of bounds: the length is 3 but the index is 5
  |
  = note: `#[deny(unconditional_panic)]` on by default

error: aborting due to 1 previous error

```

# Related `zk` Notes

- [rust book data types](65ml%20rust-book-data-types.md).
- [rust book variables and mutability](5cuu%20rust-book-variables-and-mutability.md).
- [rust literals and operators](jsl0%20rust-literals-and-operators.md).










