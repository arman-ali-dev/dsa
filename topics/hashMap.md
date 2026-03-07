# HashMap in C++

## 1. What is a HashMap?

- HashMap is a data structure that stores data in key-value pairs.
- Each key is unique and maps to a specific value.
- It is part of the Java Collections Framework.

## 2. Declaring a HashMap

```java
import java.util.HashMap;

HashMap<Integer, String> map = new HashMap<>();
```

- Integer → key type
- String → value type
- map → HashMap variable name

## 3. Inserting Elements

Method 1 (Using put())

```cpp
map.put(1, "Apple");
map.put(2, "Mango");
map.put(3, "Banana");
```

## 4. Accessing Elements

```cpp
System.out.println(map.get(1));
```

## 5. Traversing a HashMap

```cpp
for (Map.Entry<Integer, String> entry : map.entrySet()) {
    System.out.println(entry.getKey() + " " + entry.getValue());
}
```

## 6. Time Complexity

| Operation | Time Complexity |
| --------- | --------------- |
| Insert    | O(1)            |
| Access    | O(1)            |
| Delete    | O(1)            |
| Search    | O(1)            |

## 7. Limitations of HashMap

- Elements ordered nahi hote.
- Keys unique honi chahiye.
- Worst case complexity O(n) ho sakti hai (hash collisions).
