# 136. Single Number

## Problem Statement:

Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.<br/>
You must implement a solution with a linear runtime complexity and use only constant extra space.

### Constraints:

1. 1 <= nums.length <= 3 \* 10^4
2. -3 _ 10^4 <= nums[i] <= 3 _ 10^4
3. Every element appears twice, except for one.

### Intuition:

When we see "every element appears twice except one", we can think of using bitwise XOR.
