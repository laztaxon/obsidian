---
id: rust-iterate-over-vector-values
aliases:
  - rust-iterate-over-vector-values
tags:
  - rust
  - vectors
  - for-loops
---
there's a few ways to do this but in practice:
1. we define the vector with let
2. we use a for loop to iterate over the vector

### Using a for loop and iter(most common)
This is the most common way to iterate over the elements of a vector. The iter() method returns an iterator over the immutable references to the vector elements.
```rust
let numbers = vec![1, 2, 3, 4, 5];
for num in numbers.iter() {
    println!("{}", num); // Prints 1, 2, 3, 4, 5
}
```
### using a for loop and iter_mut
modifies elemenets while iterating over the vector
```rust
let mut numbers = vec![1, 2, 3, 4, 5];

for num in numbers.iter_mut() {
    *num *= 2; // Multiply each element by 2
}

println!("{:?}", numbers); // Prints [2, 4, 6, 8, 10]
```
