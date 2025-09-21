# Single Element in a Sorted Array

## Problem
- We are given a sorted array where:
- Every element appears exactly twice,
- Except for one element which appears only once.
- We must return that single element.

#### Constraints:
- Must run in O(log n) time → binary search required.
- Must use O(1) space.

### Example 1
Input:
```ini
nums = [1,1,2,3,3,4,4,8,8]
```

Output:
```ini
2
```

### Example 2
Input:
```ini
nums = [3,3,7,7,10,11,11]
```

Output:
```ini
10
```
Explanation: Only 10 appears once.

## Intuition
- Array is sorted, so duplicate elements appear next to each other.
- If array had no "single" element → pairs would be at even/odd indices:
```ini
[a,a,b,b,c,c,...]
 0 1 2 3 4 5
```
- But when the single element appears, it breaks this pairing pattern.
- Idea: Use binary search to check where the mismatch happens.


### Approach
1. Handle small cases:
- If array length = 1 → return first element.
- If nums[0] != nums[1] → return nums[0].
- If nums[n-1] != nums[n-2] → return nums[n-1].

2. Binary Search:
- Compute mid.
- If nums[mid] is not equal to its neighbors → that’s the single element.
- Otherwise, use index parity to decide direction:
- If mid is even:
- Pair should start at mid.
- If nums[mid] == nums[mid-1] → single element is on the right.
- If mid is odd:
- Pair should end at mid.
- If nums[mid] == nums[mid-1] → single element is on the right.
- Else → single element is on the left.

3. Continue binary search until you find the single element.

### Dry Run (nums = [1,1,2,3,3,4,4,8,8])
- st=0, end=8
- mid=4 → nums[4]=3
- nums[4] == nums[3] → pair is correct → move right → st=5
- st=5, end=8
- mid=6 → nums[6]=4
- nums[6]==nums[5] → pair is correct → move right → st=7
- st=7, end=8
- mid=7 → nums[7]=8
- nums[7]==nums[8] → pair is correct → move left → end=6
- Now loop ends → answer found earlier: 2

### Code
```cpp
class Solution {
public:
    int singleNonDuplicate(vector<int>& nums) {
        int n = nums.size();
        if(n == 1) return nums[0];

        int st = 0, end = n - 1;

        while(st <= end) {
            int mid = st + (end - st) / 2;

            // Edge cases
            if(mid == 0 && nums[0] != nums[1]) return nums[0];
            if(mid == n - 1 && nums[n - 1] != nums[n - 2]) return nums[n - 1];

            // Found single element
            if(nums[mid] != nums[mid - 1] && nums[mid] != nums[mid + 1]) 
                return nums[mid];

            // Check pattern with parity
            if(mid % 2 == 0) {
                if(nums[mid] == nums[mid - 1]) {
                    st = mid + 2;  // move right
                } else {
                    end = mid - 1; // move left
                }
            } else {
                if(nums[mid] == nums[mid - 1]) {
                    st = mid + 1;  // move right
                } else {
                    end = mid - 1; // move left
                }
            }
        }
        return -1; // should never happen
    }
};
```

### Complexity
- Time Complexity: O(log n) → binary search.
- Space Complexity: O(1).
