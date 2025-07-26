# 53. Maximum Subarray

## Problem Statement:
Given an integer array nums, find the contiguous subarray which has the largest sum, and return its sum.

## Constraints:
  - 1 <= nums.length <= 10^5
  - -10^4 <= nums[i] <= 10^4

## Approach (Kadane’s Algorithm):
We need to find the subarray which gives the maximum sum.
### Key Idea:
  - Maintain a running sum: currSum
  - Keep track of the best sum so far: maxSum
  - If currSum ever becomes negative, it means continuing further with this subarray is harmful — so we reset currSum to 0.

### Steps:
#### 1. Initialize:
  - currSum = 0
  - maxSum = INT_MIN
#### 2. Traverse each element val in nums:
  - Add val to currSum
  - Update maxSum = max(maxSum, currSum)
  - If currSum < 0, reset currSum = 0

```c++
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int currSum = 0, maxSum = INT_MIN;

        for (int val : nums) {
            currSum += val;
            maxSum = max(currSum, maxSum);

            if (currSum < 0) {
                currSum = 0;
            }
        }

        return maxSum;
    }
};
```

#### Example:
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]<br/>
Output: 6<br/>
<br/>
Explanation: The subarray [4,-1,2,1] has the largest sum = 6.

#### Time Complexity:
O(n) → Only one pass through the array.

#### Space Complexity:
O(1) → Only two variables are used.

### Note:
This version of Kadane’s algorithm resets the sum to 0 whenever it becomes negative. It's helpful when at least one positive number is guaranteed (which the constraints ensure).
