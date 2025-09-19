# Search in Rotated Sorted Array

## Problem

- We are given a sorted array nums (in ascending order, unique elements), but it may be rotated at some pivot index k.
- We need to search for a given target in nums.
- If found → return its index.
- If not found → return -1.
- Must run in O(log n) → means we must use Binary Search.

### Example 1
Input:
```ini
nums = [4,5,6,7,0,1,2], target = 0
```

Output:
```ini
4
```
Explanation: target 0 is at index 4.

### Example 2
Input:
```ini
nums = [4,5,6,7,0,1,2], target = 3
```
Output:
```ini
-1
```
Explanation: target 3 is not present.

### Example 3
Input:
```ini
nums = [1], target = 0
```

Output: 
```ini
-1
```

## Intuition
- Normal binary search won’t directly work, because array is rotated.
- But in any rotated sorted array:
- At least one half (left or right) is always sorted.
- So at each step:
- Check which half is sorted (left..mid or mid..right).
- Decide if the target lies inside that sorted half:
- If yes → move search inside that half.
- If no → move search to the other half.
- This way we still reduce the search space by half → O(log n).

### Approach (Step by Step)
1. Initialize two pointers: st = 0, end = n-1.
2. While st <= end:
     - Find mid = st + (end - st)/2.
     - If nums[mid] == target → return mid.
     - If left half is sorted (nums[st] <= nums[mid]):
         - If target lies in [nums[st], nums[mid]] → move end = mid - 1.
         - Else → move st = mid + 1.
     - Else (right half is sorted):
     - If target lies in [nums[mid], nums[end]] → move st = mid + 1.
     - Else → move end = mid - 1.
3. If not found → return -1.

### Dry Run
Input: nums = [4,5,6,7,0,1,2], target = 0
- st=0, end=6 → mid=3 → nums[mid]=7
    - Left half [4,5,6,7] is sorted
    - Target=0 not in this range → move right → st=4
- st=4, end=6 → mid=5 → nums[mid]=1
    - Left half [0,1] is sorted
    - Target=0 lies here → move end=4
- st=4, end=4 → mid=4 → nums[mid]=0 ✅ found
- Answer = 4

### Code
```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int st = 0, end = nums.size() - 1;

        while(st <= end) {
            int mid = st + (end - st) / 2;

            if(nums[mid] == target) return mid;

            // Left half is sorted
            if(nums[st] <= nums[mid]) {
                if(nums[st] <= target && target < nums[mid]) {
                    end = mid - 1;
                } else {
                    st = mid + 1;
                }
            }
            // Right half is sorted
            else {
                if(nums[mid] < target && target <= nums[end]) {
                    st = mid + 1;
                } else {
                    end = mid - 1;
                }
            }
        }

        return -1;
    }
};
```

## Complexity
- Time Complexity: O(log n) → standard binary search steps.
- Space Complexity: O(1)
