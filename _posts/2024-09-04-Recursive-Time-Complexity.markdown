---
title: Recursive Time Complexity
date: 2024-09-04 14:32:00
author: s1e7j
categories: [Programing, Time Complexity]
tags: [Time Complexity, Low Level Code, Recursion, Rust, Haskell, C]
description: How you can calculate the Time Complexity of a Recursive Function
comments: true
math: true
---


# Introducing Recursion

Imagine you were asked to calculate the factorial of a number. Then you search online and found
this definition:
$$
\begin{equation}
  f\left( n \right) :=
\begin{cases}
  n * f(n - 1) & n > 0\\
  1 & n = 1
\end{cases}
\end{equation}
$$

Thats Ok, you think about it for a minute and then came to something like this:

```rust
fn factorial(n: i32) -> i32 {
  return match n {
    0 => 1,
    _ => factorial(n - 1) * n,
  }
}
```

```haskell
factorial :: Int -> Int
factorial 0 = 1
factorial n = n * factorial (n - 1)
```

```c
int factorial(int n) {
  if (n == 0) {
  return 1;
  }
  return n * factorial(n - 1)
}
```
This is an almost one to one translation of the definition you found online.
Moreover, it is a nice first example of recursion. Recursion is define in mathematics
as a function that was 2 cases:

1. Base Case: A terminating scenario where if some condition are met then you return some value
2. Recursive Step: A way for reducing a problem into previous steps.

Let us look at the previous code and divide it in this two cases
```rust
fn factorial(n: i32) -> i32 {
  return match n {
    0 => 1, // Base
    _ => factorial(n - 1) * n, // Recursion
  }
}
```

```haskell
factorial :: Int -> Int
factorial 0 = 1 -- Base
factorial n = n * factorial (n - 1) -- Recursion
```

```c
int factorial(int n) {
  if (n == 0) {
    return 1; // Base
  }
  return n * factorial(n - 1) // Recursion
}
```

This a basic example. However, it is a good way to introduce recursion and
how to calculate it's time complexity.

# Time Complexity in Recursion


