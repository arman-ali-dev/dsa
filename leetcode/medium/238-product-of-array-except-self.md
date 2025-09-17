# Product of Array Except Self

## Problem
- We are given an integer array nums.
- We need to return another array answer such that:
- answer[i] = product of all elements in nums except nums[i].
- Condition:
- No division allowed.
- Must run in O(n) time.
- Extra space: O(1) (excluding output array).

### Example 1
Input:
```ini
nums = [1,2,3,4]
```

#### Explanation:
- answer[0] = 2 × 3 × 4 = 24
- answer[1] = 1 × 3 × 4 = 12
- answer[2] = 1 × 2 × 4 = 8
- answer[3] = 1 × 2 × 3 = 6

Output:
```ini
[24,12,8,6]
```

### Example 2
Input:
```ini
nums = [-1,1,0,-3,3]
```

#### Explanation:
- answer[0] = (1 × 0 × -3 × 3) = 0
- answer[1] = (-1 × 0 × -3 × 3) = 0
- answer[2] = (-1 × 1 × -3 × 3) = 9
- answer[3] = (-1 × 1 × 0 × 3) = 0
- answer[4] = (-1 × 1 × 0 × -3) = 0

Output:
```ini
[0,0,9,0,0]
```

## Intuition
We need product of all elements except self.
- If we know the prefix product (product of elements to the left) and the suffix product (product of elements to the right),
then for each index i:

```swift
answer[i] = prefix[i] × suffix[i]
```
But instead of storing full prefix and suffix arrays, we can optimize using:
- One forward pass (prefix multiplication).
- One backward pass (suffix multiplication).

### Approach
1. Initialize ans array with 1.
2. Left Pass:
    - Build prefix product → for each i, ans[i] = ans[i-1] * nums[i-1].
3. Right Pass:
    - Maintain suffix = 1.
    - Traverse from right to left.
    - Multiply ans[i] *= suffix, then update suffix *= nums[i].
4. Return ans.

### Dry Run (nums = [1,2,3,4])
Step 1: Prefix pass
```matlab
ans = [1,1,1,1]
ans[1] = ans[0]*nums[0] = 1*1 = 1
ans[2] = ans[1]*nums[1] = 1*2 = 2
ans[3] = ans[2]*nums[2] = 2*3 = 6
→ ans = [1,1,2,6]
```

Step 2: Suffix pass
```matlab
suffix=1
i=3 → ans[3]=6*1=6, suffix=4
i=2 → ans[2]=2*4=8, suffix=12
i=1 → ans[1]=1*12=12, suffix=24
i=0 → ans[0]=1*24=24
→ ans = [24,12,8,6]
```

Final Answer = [24,12,8,6]

### Final Answer = [24,12,8,6]
```cpp
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int n = nums.size();
        vector<int> ans(n, 1);

        // Step 1: Prefix product
        for(int i = 1; i < n; i++) {
            ans[i] = ans[i - 1] * nums[i - 1];
        }

        // Step 2: Suffix product
        int suffix = 1;
        for(int i = n - 1; i >= 0; i--) {
            ans[i] *= suffix;
            suffix *= nums[i];
        }

        return ans;
    }
};
```

### Complexity
- Time Complexity: O(n) (two passes).
- Space Complexity: O(1) (excluding output array).
