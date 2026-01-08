# 2D Arrays in C++

## 1. What is a 2D Array?

- A 2D array is an array of arrays.
- It stores data in rows and columns (matrix form).

## 2. Declaring a 2D Array

```cpp
int arr[3][3];
```

- First value → number of rows
- Second value → number of columns
- Size is fixed at compile time

## 3. Initializing a 2D Array

```cpp
int arr[3][3] = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```

## 4. Accessing Elements

```cpp
cout << arr[1][2];   // Output: 6
```

- Indexing starts from 0
- Syntax: arr[row][column]

## 5. Traversing a 2D Array

```cpp
for(int i = 0; i < 3; i++) {
    for(int j = 0; j < 3; j++) {
        cout << arr[i][j] << " ";
    }
    cout << endl;
}
```

## 6. Passing 2D Array to a Function

```cpp
void print(int arr[][3], int rows) {
    for(int i = 0; i < rows; i++) {
        for(int j = 0; j < 3; j++) {
            cout << arr[i][j] << " ";
        }
        cout << endl;
    }
}
```

## 7. Memory Representation

- Stored in row-major order.
- Rows are stored one after another in memory.

## 8. Limitations of 2D Arrays

- Size is fixed.
- Cannot resize at runtime.
- Less flexible for DSA problems.

## Summary

- 2D Array stores data in matrix form.
- Fixed size.
- Fast access but less flexible.
- Used when size is known beforehand.
