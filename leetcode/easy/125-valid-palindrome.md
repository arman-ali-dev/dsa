# 125. Valid Palindrome

## Problem Statement:

A string is a palindrome if, after converting all uppercase letters to lowercase and removing all non-alphanumeric characters, it reads the same forward and backward.<br/>
You must implement a solution with a linear runtime complexity and use only constant extra space. Given a string s, return true if it is a palindrome, otherwise return false. Alphanumeric characters include letters and numbers.

### Constraints:

1. 1 <= s.length <= 2 \* 10^5
2. s consists only of printable ASCII characters
 
### Intuition:

To check whether the string is a palindrome, we only need to compare characters from the start and the end.

- We must ignore non-alphanumeric characters
- We must ignore case differences
  Using the two pointer technique, we can compare valid characters without creating a new string.

<br/>
<br/>
So, if we XOR all elements in the array, the duplicate elements cancel out, and we’re left with the single number that appears once.

### Approach:

1. Initialize two pointers:

   - st at the beginning of the string
   - end at the end of the string

2. While st < end:
   - If s[st] is not alphanumeric, move st forward
   - If s[end] is not alphanumeric, move end backward
3. Convert both characters to lowercase and compare them
4. If they are not equal, return false
5. If the loop completes, return true

```c++
class Solution {
public:
    bool isPalindrome(string s) {
        int st = 0, end = s.length() - 1;

        while (st < end) {
            if (!isalnum(s[st])) {
                st++;
                continue;
            }

            if (!isalnum(s[end])) {
                end--;
                continue;
            }

            if (tolower(s[st]) != tolower(s[end])) {
                return false;
            }

            st++;
            end--;
        }

        return true;
    }
};

```

### Time Complexity:

- O(n) – Each character is checked at most once.

### Space Complexity:

- O(1) – No extra space is used.

### Example:

Input: s = "A man, a plan, a canal: Panama"
Output: true
