# Peak Index in a Mountain Array

## Problem
We are given a mountain array arr of length n:
- First the values strictly increase to a peak.
- Then the values strictly decrease after the peak.
- We need to find the index of the peak element.
- Must solve in O(log n) time → use Binary Search.

### Example 1
Input:
```ini
arr = [0,1,0]
```

Output:
```ini
1
```
Explanation: arr[1] = 1 is the peak.

### Example 2
Input:
```ini
arr = [0,2,1,0]
```

Output:
```ini
1
```
Explanation: arr[1] = 2 is the peak.

### Intuition
- Mountain array has one peak where:
- arr[mid-1] < arr[mid] > arr[mid+1]
- Before the peak → array is increasing.
- After the peak → array is decreasing.

So we can use binary search:

#### 1. Check mid element:

- If arr[mid] is greater than both neighbors → return mid (this is the peak).
- If arr[mid] < arr[mid+1] → we are on the increasing slope, so move right (st = mid+1).
- Else → we are on the decreasing slope, so move left (end = mid-1).

### Dry Run (arr = [0,2,1,0])
- st=1, end=2
- mid=1 → arr[mid]=2
- arr[mid-1]=0 < 2 and arr[mid+1]=1 < 2 → condition satisfied return 1

### Code
```cpp
class Solution {
public:
    int peakIndexInMountainArray(vector<int>& arr) {
        int st = 1, end = arr.size() - 2; // peak cannot be at edges

        while(st <= end) {
            int mid = st + (end - st) / 2;

            // Peak condition
            if(arr[mid - 1] < arr[mid] && arr[mid] > arr[mid + 1]) {
                return mid;
            }
            // Move right (increasing slope)
            else if(arr[mid] < arr[mid + 1]) {
                st = mid + 1;
            }
            // Move left (decreasing slope)
            else {
                end = mid - 1;
            }
        }

        return -1; // should never reach for valid mountain array
    }
};
```

### Complexity
- Time Complexity: O(log n) → Binary Search.
- Space Complexity: O(1) → Only variables used.
