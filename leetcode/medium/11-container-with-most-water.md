# Container With Most Water

## Problem
- We are given an integer array height of size n.
- Each element height[i] represents the height of a vertical line at position i.
- Together with the x-axis, two of these lines can form a container.
- Our goal is to find the maximum water that can be stored between two lines.
- Note: Container sides must be vertical (no slanting allowed).

![Container's Graph](https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/17/question_11.jpg)

### Example 1

Input:
```ini
height = [1,8,6,2,5,4,8,3,7]
```
Best choice:
- Line at index 1 (height=8)
- Line at index 8 (height=7)
- Width = 8 - 1 = 7
- Height = min(8,7) = 7
- Area = 7 × 7 = 49

Output
``ini
49
`
### Example 2

Input:
```ini
height = [1,1]
```
- Only two lines: width = 1, height = 1
- Area = 1 × 1 = 1

Output:
```ini
1
```

### Intuition
- Water stored between two lines depends on:
- Width = distance between lines
- Height = min(height[left], height[right])
- So, Area = width × min(height[left], height[right])
- We need to maximize this area.

### Naive Approach (Brute Force)
- Check all pairs of lines (i, j)
- Compute area = (j - i) × min(height[i], height[j])
- Keep track of maximum
- Time Complexity: O(n²) → Too slow for large n

### Optimal Approach (Two Pointer)
- Place two pointers:
- lp = 0 (left)
- rp = n-1 (right)
- Compute area with these two lines.
- Move the pointer pointing to the smaller line inward:
- Because moving the taller line won’t help (height limited by smaller one).
- Repeat until lp < rp.
- Keep updating maxWater.

### Dry Run (height = [1,8,6,2,5,4,8,3,7])
- Start: left=0, right=8 → width=8, minHeight=1 → area=8
- Move left (smaller line).
- Now left=1, right=8 → width=7, minHeight=7 → area=49 ✅
- Keep checking, maximum stays 49.

### Code
```c++
class Solution {
public:
    int maxArea(vector<int>& height) {
        int maxWater = 0;
        int lp = 0, rp = height.size() - 1;

        while(lp < rp) {
            int w = rp - lp; // width
            int h = min(height[lp], height[rp]); // height
            int currWater = w * h; // area
            maxWater = max(maxWater, currWater);

            // move the smaller height pointer
            if(height[lp] < height[rp]) 
                lp++;
            else 
                rp--;
        }

        return maxWater;
    }
};
```

### Complexity
- Time Complexity: O(n) → Each line is checked once.
- Space Complexity: O(1) → Only a few variables used.
