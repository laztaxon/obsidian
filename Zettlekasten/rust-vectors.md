---
id: rust-vectors
aliases: []
tags: []
date: "2024-03-21"
title: Rust Vectors
---
vector = dynamic array
### What is a vector in Rust?
Vectors are one of the most-used Rust data structures. In other programming
languages, they'd simply be called Arrays, but since Rust operates on a
bit of a lower level, an array in Rust is stored on the stack (meaning it
can't grow or shrink, and the size needs to be known at compile time),
and a Vector is stored in the heap (where these restrictions do not apply).

### Difference between an array and a vector in Rust
- An array is a fixed-size data structure that stores elements of the same data type contiguously in memory.
-  A vector is a dynamic array-like data structure that can resize itself automatically to accommodate new elements and is often associated with higher-level programming languages like C++.

#### Examples of a vector in Rust
```rust
vec![1, 2, 3, 4, 5]
```
[[rust-iterate-over-vector-values]]
