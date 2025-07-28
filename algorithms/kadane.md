# Kadane’s Algorithm

Kadane’s Algorithm is used to find the maximum sum of a contiguous subarray in linear time using a greedy approach.

## Logic:

At each index, decide whether to:

- Add it to the current subarray sum, or
- Start a new subarray from this number if the current subarray sum becomes negative.

## Formula:

```c++
currentSum = max(nums[i], currentSum + nums[i])
maxSum = max(maxSum, currentSum)
```

#### Time Complexity: O(n)

Space Complexity: O(1)
