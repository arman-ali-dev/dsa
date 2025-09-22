# Bubble Sort

## What is Bubble Sort?
- Bubble Sort is a simple sorting algorithm.
- It compares two side-by-side elements.
- If they are in the wrong order → it swaps them.
- After each round, the largest element moves to the end (like a bubble moves up in water).

### How it Works (Steps)
1. Start from the first element.
2. Compare it with the next element.
3. If the first one is bigger → swap them.
4. Do this for the whole array.
5. Repeat the process until the array is sorted.

### Example
Input:
```ini
[5, 1, 4, 2, 8]
```
- Pass 1: [1, 4, 2, 5, 8]
- Pass 2: [1, 2, 4, 5, 8]
- Pass 3: [1, 2, 4, 5, 8] (already sorted)

Output:
```ini
[1, 2, 4, 5, 8]
```

### Code
```cpp
#include <bits/stdc++.h>
using namespace std;

void bubbleSort(vector<int>& arr) {
    int n = arr.size();
    for(int i = 0; i < n-1; i++) {
        bool swapped = false;
        for(int j = 0; j < n-i-1; j++) {
            if(arr[j] > arr[j+1]) {
                swap(arr[j], arr[j+1]);
                swapped = true;
            }
        }
        if(!swapped) break; // already sorted
    }
}

int main() {
    vector<int> arr = {5, 1, 4, 2, 8};
    bubbleSort(arr);

    for(int x : arr) cout << x << " ";
    return 0;
}
```

### Time Complexity
- Best Case (Already Sorted): O(n)
- Average Case: O(n²)
- Worst Case (Reverse Order): O(n²)

### Space Complexity
- O(1) → uses constant extra space

### Key Points
- Very easy to understand.
- Not good for large datasets (slow).
- It is stable (keeps order of equal elements).
