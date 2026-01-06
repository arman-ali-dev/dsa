# 125. Reverse Words in a String

## Problem Statement:

Given a string s, reverse the order of words in the string.<br/>
A word is defined as a sequence of non-space characters.<br/>
The returned string:

- Must not contain leading or trailing spaces
- Must contain only one space between words

### Constraints:

1. 1 <= s.length <= 10⁴
2. s contains English letters, digits, and spaces
3. There is at least one word in s

### Intuition:

We want to reverse the order of words, not the characters inside the words.
<br/>

A simple approach is:

1. Reverse the entire string
2. Extract each word
3. Reverse each word individually
4. Build the final answer with single spaces

### Approach:

1. Reverse the whole string s
2. Traverse the string character by character
3. Extract each word (characters until space)
4. Reverse the extracted word
5. Append it to the answer string with a single space
6. Remove the extra leading space before returning the result

```c++
class Solution {
public:
    string reverseWords(string s) {
        reverse(s.begin(), s.end());
        int n = s.length();

        string ans = "";

        for (int i = 0; i < n; i++) {
            string word = "";

            while (i < n && s[i] != ' ') {
                word += s[i];
                i++; 
            }

            reverse(word.begin(), word.end());

            if (word.length() > 0) {
                ans += " " + word;
            }
        }

        return ans.substr(1);
    }
};
```

### Time Complexity:

- O(n) – Each character is processed a constant number of times.

### Space Complexity:

- O(1) – Extra space is used for the result string.

### Example:

Input: s = " hello world "
Output: "world hello"
