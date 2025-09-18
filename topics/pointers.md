# Pointers in C++

## 1. What is a Pointer?
- A **pointer** is a variable that stores the **memory address** of another variable.
- Instead of holding a direct value (like `int x = 10;`), it holds the *address* where the value is stored.

```cpp
int x = 10;
int* p = &x;   // p stores the address of x

// &x → gives the address of x.
// *p → gives the value stored at that address (dereferencing).
```

## 2. Declaring a Pointer
```cpp
int* ptr;     // pointer to int
char* cptr;   // pointer to char
float* fptr;  // pointer to float
```
- * is used in declaration to show that variable is a pointer.
 
## 3. Using Pointers
```cpp
int a = 5;
int* p = &a;

cout << "Value of a: " << a << endl;       // 5
cout << "Address of a: " << &a << endl;    // e.g. 0x61ff08
cout << "Pointer p: " << p << endl;        // address of a
cout << "Value at *p: " << *p << endl;     // 5 (dereferencing)
```

## 4. Null Pointer
- A pointer that does not point to any memory.
```cpp
int* ptr = NULL;  // or nullptr (C++11+)
```
- Always initialize pointers, otherwise they may point to random memory (dangling pointer).

## 5. Pointer Arithmetic
- Pointers can be increased/decreased.
- When incremented, they move to the next memory block of their data type.

```cpp
int arr[3] = {10, 20, 30};
int* p = arr;  // same as &arr[0]

cout << *p << endl;     // 10
cout << *(p+1) << endl; // 20
cout << *(p+2) << endl; // 30
```
- p+1 moves pointer to the next integer (not next byte).

## 6. Pointers and Arrays
- Array name itself acts like a pointer (points to the first element).

```cpp
int arr[3] = {1, 2, 3};
int* p = arr;

cout << arr[0] << " " << p[0] << endl;  // both 1
```

## 7. Pointer to Pointer
- A pointer can also store the address of another pointer.
```cpp
int x = 10;
int* p = &x;      // pointer to int
int** q = &p;     // pointer to pointer

cout << **q;      // 10
```

## 8. Pointers and Functions
- Pass by Value
```cpp
void change(int x) {
    x = 20;
}

int main() {
    int a = 10;
    change(a);
    cout << a;   // still 10
}
```

- Pass by Pointer
```cpp
void change(int* p) {
    *p = 20;
}

int main() {
    int a = 10;
    change(&a);
    cout << a;   // now 20
}
```
- Using pointers, we can modify original variables.

## 9. Dynamic Memory Allocation
- We can allocate memory at runtime using new and free using delete.

```cpp
int* p = new int;   // allocate memory
*p = 100;

cout << *p;         // 100

delete p;           // free memory
```

- Dynamic Array
```cpp
int* arr = new int[5];   // array of 5 integers

for (int i = 0; i < 5; i++) arr[i] = i+1;

delete[] arr;            // free array memory
```

## 10. Common Issues with Pointers
- Dangling Pointer → pointer pointing to freed memory.
- Memory Leak → not freeing memory allocated with new.
- Wild Pointer → uninitialized pointer pointing to random memory.
- Always use delete for every new to avoid leaks.
- Initialize unused pointers to nullptr.

## Summary
- Pointer = variable storing memory address of another variable.
- & → address-of operator, * → dereference operator.
- Can perform arithmetic (p+1, p-1).
- Arrays and pointers are closely related.
- Useful in functions (pass by reference) and dynamic memory allocation.
- Handle carefully → improper use causes bugs like memory leaks or crashes.
