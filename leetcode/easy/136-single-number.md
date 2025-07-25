# Single Number

## Problem Statement:

Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.<br/>
You must implement a solution with a linear runtime complexity and use only constant extra space.

### Constraints:

1. 1 <= nums.length <= 3 \* 10^4
2. -3 _ 10^4 <= nums[i] <= 3 _ 10^4
3. Every element appears twice, except for one.

### Intuition:

When we see "every element appears twice except one", we can think of using bitwise XOR.
  - a ^ 0 = a → any number XOR 0 is the number itself
  - XOR is commutative and associative:
  - That means:
      - a ^ b ^ a = b ^ (a ^ a) = b ^ 0 = b

<br/>
<br/>
So, if we XOR all elements in the array, the duplicate elements cancel out, and we’re left with the single number that appears once.

### Approach:
1. Initialize a variable ans with 0.
2. Traverse each element in the array and do ans ^= val.
3. After the loop, ans will hold the unique number.

```c++
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int ans = 0;
        for (int val : nums) {
            ans ^= val;
        }
        return ans;
    }
};
```

### Time Complexity:
  - O(n) – We iterate through the array only once.

### Space Complexity:
  - O(1) – We use only a single variable ans.

### Example:
Input: nums = [4,1,2,1,2]
Output: 4
