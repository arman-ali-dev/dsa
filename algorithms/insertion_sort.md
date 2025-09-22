# Selection Sort
## What is Selection Sort?

- Selection Sort is a simple sorting algorithm.
- It works by finding the smallest element from the unsorted part of the array and putting it at the correct position.
- This process is repeated until the whole array is sorted.

### How it Works (Steps)
1. Start from the first index.
2. Find the smallest element in the array from index i to end.
3. Swap it with the element at index i.
4. Move to the next index and repeat.
5. Continue until the array is fully sorted.

### Example
Input:
```ini
[64, 25, 12, 22, 11]
```
- Step 1: Smallest is 11 → swap with 64 → [11, 25, 12, 22, 64]
- Step 2: Smallest from index 1..end is 12 → swap with 25 → [11, 12, 25, 22, 64]
- Step 3: Smallest from index 2..end is 22 → swap with 25 → [11, 12, 22, 25, 64]
- Step 4: Already sorted → [11, 12, 22, 25, 64]

Output:
```ini
[11, 12, 22, 25, 64]
```

```cpp
#include <bits/stdc++.h>
using namespace std;

void selectionSort(vector<int>& arr) {
    int n = arr.size();
    for(int i = 0; i < n-1; i++) {
        int minIndex = i;
        for(int j = i+1; j < n; j++) {
            if(arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }
        swap(arr[i], arr[minIndex]);
    }
}

int main() {
    vector<int> arr = {64, 25, 12, 22, 11};
    selectionSort(arr);

    for(int x : arr) cout << x << " ";
    return 0;
}
```

### Time Complexity
- Best Case: O(n²)
- Average Case: O(n²)
- Worst Case: O(n²)

### Space Complexity
- O(1) → in-place algorithm

### Key Points
- Easy to implement.
- Always does (n-1) swaps, so number of swaps is small.
- But it is slower than efficient algorithms like Merge Sort or Quick Sort.
- Not stable (equal elements’ order may change).
