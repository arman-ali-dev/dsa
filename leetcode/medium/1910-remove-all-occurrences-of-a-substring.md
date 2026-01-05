# 1910. Remove All Occurrences of a Substring

## Problem Statement:

Given two strings s and part, repeatedly remove the leftmost occurrence of the substring part from s until s no longer contains part.<br/>
Return the final string after all removals.<br/>
A substring is a contiguous sequence of characters in a string.

### Constraints:

1. 1 <= s.length <= 1000
2. 1 <= part.length <= 1000
3. s and part consist only of lowercase English letters

### Intuition:

We are asked to remove a substring again and again until it does not exist anymore.<br/>
C++ provides useful string methods:

- find() to locate a substring
- erase() to remove a portion of the string
  <br/>
  <br/>
  We can use a loop that:
- keeps checking whether part exists in s
- removes it whenever found

### Approach:

1. Use a while loop to repeat the process.
2. Inside the loop:
   - Find the index of the leftmost occurrence of part in s.
   - Remove part starting from that index.
3. Stop when part is no longer found in s.
4. Return the final string.

```c++
class Solution {
public:
    string removeOccurrences(string s, string part) {
        while (s.length() > 0 && s.find(part) < s.length()) {
            s.erase(s.find(part), part.length());
        }
        return s;
    }
};
```

### Time Complexity:

- O(n²) in the worst case
  Because find() and erase() can take O(n), and they are used inside a loop.

### Space Complexity:

- O(1) - No extra data structures are used.

### Example:

Input: s = "daabcbaabcbc" part = "abc"
Output: "dab"
