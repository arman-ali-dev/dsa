# 240. Search a 2D Matrix II

## Problem Statement:

You are given an m x n matrix where:

- Each row is sorted in ascending order (left to right)
- Each column is sorted in ascending order (top to bottom)

<br/>
<br/>
Given an integer target, return true if it exists in the matrix, otherwise return false.

### Constraints:

1. 1 <= m, n <= 300
2. -10⁹ <= matrix[i][j], target <= 10⁹
3. Each row and each column is sorted in ascending order

### Intuition:

Because:

- Rows are sorted left to right
- Columns are sorted top to bottom

We can start from the top-right corner:
<br/>

- If the current value is greater than target, move left
- If the current value is smaller than target, move down

This way, we eliminate one row or one column at each step.

### Approach:

1. Start from the top-right cell (0, n-1)
2. While the row and column indices are valid:
   - If the current value equals target, return true
   - If the current value is greater than target, move left
   - If the current value is smaller than target, move down
3. If the search ends without finding the target, return false

```c++
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& mat, int target) {
        int m = mat.size(), n = mat[0].size();
        int r = 0, c = n - 1;

        while (r < m && c >= 0) {
            if (target == mat[r][c]) {
                return true;
            } else if (target < mat[r][c]) {
                c--;
            } else {
                r++;
            }
        }

        return false;
    }
};
```

### Time Complexity:

- O(m + n) At most, we move m steps down and n steps left.

### Space Complexity:

O(1): No extra space used

### Example:

Input: matrix = [[1,4,7,11,15],[2,5,8,12,19],[3,6,9,16,22],[10,13,14,17,24],[18,21,23,26,30]] target = 5
Output: true
