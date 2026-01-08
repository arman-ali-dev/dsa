# 2D Vectors in C++

## 1. What is a 2D Vector?

- A 2D vector is a vector of vectors.
- It is a dynamic version of a 2D array.

## 2. 2. Declaring a 2D Vector

```cpp
vector<vector<int>> v;
```

- Size can change at runtime.

## 3. Initializing a 2D Vector

```cpp
vector<vector<int>> v = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```

## 4. Dynamic Size Initialization

```cpp
vector<vector<int>> v(3, vector<int>(4, 0));
```

- 3 rows
- 4 columns
- All values initialized to 0

## 5. Accessing Elements

```cpp
cout << v[1][2];   // Output: 6
```

## 6. Traversing a 2D Vector

```cpp
for(int i = 0; i < v.size(); i++) {
    for(int j = 0; j < v[i].size(); j++) {
        cout << v[i][j] << " ";
    }
    cout << endl;
}
```

## 7. Adding Rows Dynamically

```cpp
vector<int> temp;
temp.push_back(10);
temp.push_back(20);

v.push_back(temp);
```
https://www.magicbricks.com/blog/cost-of-living-in-vadodara/142611.html#:~:text=relevance%20of%20cost.-,Cost%20of%20Living%20%E2%80%93%20Overview,food%2C%20accommodation%2C%20and%20lifestyle.
## 8. Passing 2D Vector to a Function

```cpp
void print(vector<vector<int>>& v) {
    for(int i = 0; i < v.size(); i++) {
        for(int j = 0; j < v[i].size(); j++) {
            cout << v[i][j] << " ";
        }
        cout << endl;
    }
}
```

## 9. Advantages of 2D Vectors

- Dynamic size.
- Easy to resize.
- Widely used in DSA & competitive programming.

## 10. Disadvantages of 2D Vectors

- Slightly slower than arrays.
- Uses more memory.

## Summary

- 2D Vector = dynamic 2D array.
- Size can change at runtime.
- Best choice for DSA problems.
- Easier to pass into functions.
