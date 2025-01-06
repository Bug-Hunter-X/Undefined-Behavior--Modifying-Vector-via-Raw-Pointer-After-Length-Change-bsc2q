# Rust Undefined Behavior Example

This repository demonstrates a common source of undefined behavior in Rust: modifying a vector through a raw pointer after its length or capacity has changed.  The `bug.rs` file contains code that exhibits this behavior, while `bugSolution.rs` provides a safe alternative.

**Understanding the Problem:**

Rust's memory management relies heavily on ownership and borrowing.  When you obtain a raw pointer to the underlying data of a vector, you bypass Rust's safety checks. If the vector's internal structure changes (e.g., due to a `push()`, `pop()`, or reallocation), the pointer might become invalid, leading to crashes, data corruption, or other unpredictable outcomes. 

**Solution:**

The best way to avoid such issues is to use safe Rust mechanisms whenever possible.  Instead of directly manipulating raw pointers, leverage vector's built-in methods.