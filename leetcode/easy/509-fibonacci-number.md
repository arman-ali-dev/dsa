# 509. Fibonacci Number

## Problem Statement:

Given an integer n, return the nᵗʰ Fibonacci number.

The Fibonacci sequence is defined as:

- F(0) = 0
- F(1) = 1
- F(n) = F(n − 1) + F(n − 2) for n > 1

This means every number in the sequence is the sum of the previous two numbers.

- Example Sequence
  0, 1, 1, 2, 3, 5, 8, 13 ...

## Approach: Recursion

We directly use the mathematical definition of Fibonacci.

## Steps:

1. If n <= 1, return n (because we already know the values of F(0) and F(1))
2. (because we already know the values of F(0) and F(1))
   F(n) = F(n-1) + F(n-2)
3. The function calls itself recursively until it reaches the base cases (n = 0 or n = 1).

```c++
class Solution {
public:
    int fib(int n) {

        if(n <= 1) {
            return n;
        }

        return fib(n - 1) + fib(n - 2);
    }
};
```

## Example:

Input: n = 4</br>
Output: 3

### Time Complexity: O(2^n)

### Space Complexity: O(n)
