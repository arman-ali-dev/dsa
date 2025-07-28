# 169. Mejority Element

## Problem Statement:

Given an array nums of size n, return the majority element — the element that appears more than ⌊n / 2⌋ times. It is guaranteed that a majority element always exists in the array.

## Approach: Moore’s Voting Algorithm

## Logic:

We maintain:

- A freq counter (to track the balance)
- A current ans (candidate for majority)
  At each element:
- If freq == 0, we pick the current number as the new ans
- If current element == ans, we increase freq
- Else, we decrease freq

The idea is: every time we see a non-majority element, it cancels out a majority vote. Since majority element appears more than half the time, it will survive all cancellations.

```c++
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int freq = 0, ans = 0;

        for(int i = 0; i < nums.size(); i++) {
            if(freq == 0) {
                ans = nums[i];
            }

            if (ans == nums[i]) {
                freq++;
            } else {
                freq--;
            }
        }

        return ans;
    }
};
```

## Example:

Input: nums = [3,2,3]</br>
Output: 3
<br/>
<br/>
Input: nums = [2,2,1,1,1,2,2]<br/>
Output: 2

### Time Complexity: O(n)

### Space Complexity: O(1)
