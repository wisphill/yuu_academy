---
layout: post
description: Some notes about the references feature of the Rust
---
#rust #ownership #references

### About the Stack and Heap
Rust has its own way to manage the memory efficiently, to control the data that can be pushed into the `Stack memory` or `Heap memory`. As we know about the `Stack and Heap`, and they are two different memories in the RAM. If the stack memory requires some data that needs to have fixed and known size, in the meanwhile, the heap memory can be store some data with dynamic size, complicated data structure. 

So normally, some scalar data types such as `i32, i64, uint32, float, double`, `literal string` are stored on Stack and be easier to be cloned to be another data in the stack memory to be assigned to another variable.

In Rust, `String` type is much more complex than scalar type and it's almost controlled under the heap memory.

### Mutable and Immutable
The default of variable definition is immutable in Rust. 
```rust
let x = 1; // immutable assigning
x = 2; // throw error here because of assigning immutable variable
// error[E0384]: cannot assign twice to immutable variable `x`
```
if we want to change the value of x
```rust
let mut x = 1; // mutable assigning
x = 3; // it's okay
```

### Ownership rules
1. Each value in Rust has an owner
2. Each value has `only one` owner at a time
3. If the owner goes out of scope, so the value will be dropped and free in the memory.

### Move data assignee
Let's take an example
```rust
let x = String::from("mom");
let y = x;
print("{:?}", x); // throw error because of borrowing of moved value `x`, the ownership has been changed
```
1. The string value `mom` has a dynamic size and be stored in the HEAP memory and its ownership is `x` variable
2. The assignee is changed to y and now y is the new ownership and it has a pointer point to the value `mom`
So we call this as the value of `x` has been moved

Stack (has the presentation of x and y, and here is y after the moved)

| name | value |
| ---- | ----- |
| ptr  | 0x3   |
| len  | 10    |
| cap  | 10    |

Heap (value)

| index | value |
| ----- | ----- |
| 0x3   | m     |
| 4     | o     |
| 5     | m     |
### Ownership and function
