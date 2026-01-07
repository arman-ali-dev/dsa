# 7. Reverse Integer

## Problem Statement:

Given a signed 32-bit integer x, return x with its digits reversed.<br/>

- If reversing x causes it to go outside the 32-bit signed integer range [-2³¹, 2³¹ - 1], return 0.
- No 64-bit integers are allowed.

### Constraints:

1. -2³¹ <= x <= 2³¹ - 1

### Intuition:

We can reverse the integer digit by digit using modulo and division.
<br/>

Steps:

1. Extract the last digit using x % 10.
2. Append it to a new number rev.
3. Remove the last digit from x using integer division x /= 10.
4. Before appending, check for overflow:
5. rev \* 10 + digit should not exceed INT_MAX or go below INT_MIN.

### Approach:

1. Initialize rev = 0 to store the reversed number.
2. While x != 0:
   - Extract last digit r = x % 10.
   - Check for potential overflow:
     - If rev > INT_MAX / 10 or (rev == INT_MAX/10 and r > 7) → return 0
     - If rev < INT_MIN / 10 or (rev == INT_MIN/10 and r < -8) → return 0
   - Update rev = rev \* 10 + r.
   - Remove the last digit from x: x /= 10.
3. Return rev.

```c++
class Solution {
public:
    int reverse(int x) {
        int r = 0, rev = 0;

        while (x != 0) {
            r = x % 10;

            if (rev > INT_MAX/10 || (rev == INT_MAX/10 && r > 7)) return 0;
            if (rev < INT_MIN/10 || (rev == INT_MIN/10 && r < -8)) return 0;

            rev = rev * 10 + r;
            x /= 10;
        }

        return rev;
    }
};
```

### Time Complexity:

- O(log₁₀ n) – Each iteration removes one digit from x.

### Space Complexity:

- O(1) – Only a few integer variables are used.

### Example:

Input: x = 123
Output: 321
