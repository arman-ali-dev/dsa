# Vectors

Vectors are dynamic arrays in C++ STL (Standard Template Library). Used widely in DSA due to their flexibility and efficiency.

---

## Header File

```cpp
#include <vector>
```

## Vector Declaration & Initialization

```cpp
std::vector<int> v;                     // empty vector
std::vector<int> v(5);                  // size 5, default 0
std::vector<int> v(5, 10);              // size 5, all 10
std::vector<int> v = {1, 2, 3, 4};      // initializer list
```

## C++ Vector Functions

| Function       | Usage Example      | Description                   |
| -------------- | ------------------ | ----------------------------- |
| `push_back(x)` | `v.push_back(10);` | Add element at end            |
| `pop_back()`   | `v.pop_back();`    | Remove last element           |
| `size()`       | `v.size();`        | Current number of elements    |
| `clear()`      | `v.clear();`       | Remove all elements           |
| `empty()`      | `v.empty();`       | Check if vector is empty      |
| `front()`      | `v.front();`       | First element                 |
| `back()`       | `v.back();`        | Last element                  |
| `at(i)`        | `v.at(2);`         | Element at index `i` (safe)   |
| `v[i]`         | `v[2];`            | Element at index `i` (faster) |

## Time Complexities of Vector Operations

| Operation       | Time Complexity |
| --------------- | --------------- |
| Access by index | O(1)            |
| Insertion (end) | O(1) amortized  |
| Deletion (end)  | O(1)            |
| Insertion (mid) | O(n)            |
| Deletion (mid)  | O(n)            |
