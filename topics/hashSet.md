# HashSet in Java

## 1. What is a HashSet?

- HashSet is a data structure that stores only unique elements.
- It is part of the Java Collections Framework.
- It does not allow duplicate values.
- Elements unordered hote hain.

Example:

```txt
Input:  [1, 2, 3, 2, 4, 1]

HashSet:
1, 2, 3, 4
```

## 2. Declaring a HashSet

```java
import java.util.HashSet;

HashSet<Integer> set = new HashSet<>();
```

- Integer → element type
- set → HashSet variable name

## 3. Inserting Elements

Method 1 (Using put())

```cpp
map.put(1, "Apple");
map.put(2, "Mango");
map.put(3, "Banana");
```

## 4. Accessing Elements

HashSet me index nahi hota, isliye direct access nahi kar sakte.

Traversal karna padta hai.

```cpp
for(int num : set){
    System.out.println(num);
}
```

## 5. Time Complexity

| Operation | Time Complexity |
| --------- | --------------- |
| Insert    | O(1)            |
| Search    | O(1)            |
| Delete    | O(1)            |

## 6. Limitations of HashMap

- Elements unordered hote hain.
- Duplicate values allow nahi karta.
- Index based access possible nahi hai.
