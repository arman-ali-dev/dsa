# Power Function (myPow Implementation)

## Problem Statement
Implement a function to calculate where:

- x is a real number (double).
- n is an integer (can be positive, negative, or zero).
- The solution must be efficient (O(log n)), not the naive O(n).

### Code Explanation
```c++
class Solution {
public:
    double myPow(double x, int n) {
        long binaryForm = n; // store exponent in long to handle edge cases (-2^31)
        
        if(n < 0) {
            x = 1/x;               // take reciprocal for negative powers
            binaryForm = -binaryForm;
        }

        double ans = 1;            // result initialized to 1 (identity element)

        while(binaryForm > 0) {
            if(binaryForm % 2 == 1) {
                ans *= x;          // if current bit is 1, multiply answer by x
            }

            x  *= x;               // square the base
            binaryForm /= 2;       // reduce exponent by half
        }

        return ans;
    }
};
```

### Dry Run Example
Example 1: x = 2, n = 10
```
Step 1: n = 10 (even), x = 2
Step 2: x = 4, n = 5 (odd), ans = ans * 4 = 4
Step 3: x = 16, n = 2 (even)
Step 4: x = 256, n = 1 (odd), ans = 4 * 256 = 1024
Result = 1024
```

Example 2: x = 2, n = -3
```
Since n < 0:
x = 1/x = 0.5
n = -n = 3

Loop:
- n=3 (odd) → ans = ans * 0.5 = 0.5
- x=0.25, n=1 (odd) → ans = 0.5 * 0.25 = 0.125
Result = 0.125
```

### Complexity Analysis
- Time Complexity: O(log n) (because exponent is divided by 2 in each step).
- Space Complexity: O(1)
- (only a few extra variables used).

### Summary
- Problem solved using Binary Exponentiation.
- Handles both positive and negative exponents.
- Efficient solution with O(log n) time.
- Safe handling of integer overflow with long.
