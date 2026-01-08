# 74. Search a 2D Matrix

## Problem Statement:

You are given an m x n matrix with the following properties:

- Each row is sorted in non-decreasing order
- The first element of each row is greater than the last element of the previous row
  Given an integer target, return true if target exists in the matrix, otherwise return false.
  <br/>
  <br/>
  The solution must run in O(log(m \* n)) time.

### Constraints:

1. 1 <= m, n <= 100
2. -10⁴ <= matrix[i][j], target <= 10⁴

### Intuition:

Because of the given properties:

- Each row is sorted
- Rows themselves are ordered

The matrix behaves like a single sorted 1D array.
<br/>
So we can apply binary search.
<br/>
Instead of flattening the matrix, we do it in two steps:

1. Binary search on rows to find the correct row
2. Binary search inside that row

### Approach:

1. Perform binary search on rows:
   - Check if the target lies between the first and last element of a row
2. If such a row is found:
   - Perform binary search inside that row
3. If the target is found, return true
4. Otherwise, return false

```c++
class Solution {
public:
    bool searchInRow(vector<vector<int>> mat, int target, int row) {
        int st = 0, end = mat[0].size() - 1;

        while (st <= end) {
            int mid = st + (end - st) / 2;

            if (target == mat[row][mid]) {
                return true;
            } else if (target > mat[row][mid]) {
                st = mid + 1;
            } else {
                end = mid - 1;
            }
        }

        return false;
    }

    bool searchMatrix(vector<vector<int>>& mat, int target) {
        int m = mat.size(), n = mat[0].size();
        int stRow = 0, endRow = m - 1;

        while (stRow <= endRow) {
            int midRow = stRow + (endRow - stRow) / 2;

            if (target >= mat[midRow][0] && target <= mat[midRow][n - 1]) {
                return searchInRow(mat, target, midRow);
            } else if (target > mat[midRow][n - 1]) {
                stRow = midRow + 1;
            } else {
                endRow = midRow - 1;
            }
        }

        return false;
    }
};

```

### Time Complexity:

- Row binary search: O(log m)
- Column binary search: O(log n)
- O(log(m \* n))

### Space Complexity:

O(1): No extra space used

### Example:

Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]] target = 3
Output: true
