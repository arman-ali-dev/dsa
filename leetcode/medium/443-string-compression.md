# 443. String Compression

## Problem Statement:

Given an array of characters chars, compress it using the following rules:<br/>

- For each group of consecutive repeating characters:
  - If the group length is 1, store only the character.
  - If the group length is greater than 1, store the character followed by the count.
- The compression must be done in-place inside the input array.
- Return the new length of the compressed array.

### Constraints:

1. 1 <= chars.length <= 2000
2. chars[i] can be a letter, digit, or symbol
3. Only constant extra space is allowed

### Intuition:

We need to compress consecutive repeating characters.
<br/>

To do this efficiently:

- Use one pointer to read characters
- Use another pointer to write the compressed result in the same array
  This way, we modify the input array directly without using extra space.

### Approach:

1. Initialize a write index idx to track where to write in the array.
2. Traverse the array using a loop.
3. For each character:
   - Count how many times it repeats consecutively.
4. Write the character to chars[idx].
5. If the count is greater than 1:
   - Convert the count to string.
   - Write each digit of the count into the array.
6. Resize the array to the new compressed length.
7. Return the value of idx.

```c++
class Solution {
public:
    int compress(vector<char>& chars) {
        int n = chars.size();
        int idx = 0;

        for (int i = 0; i < n; i++) {
            char ch = chars[i];
            int count = 0;

            while (i < n && chars[i] == ch) {
                count++;
                i++;
            }

            if (count == 1) {
                chars[idx++] = ch;
            } else {
                chars[idx++] = ch;
                string digits = to_string(count);
                for (char dig : digits) {
                    chars[idx++] = dig;
                }
            }

            i--;
        }

        chars.resize(idx);
        return idx;
    }
};

```

### Time Complexity:

- O(n) – Each character is processed only once.

### Space Complexity:

- O(1) – Only constant extra space is used (output is stored in the input array).

### Example:

Input: chars = ["a","a","b","b","c","c","c"]
Output: 6
Modified array (first 6 characters): ["a","2","b","2","c","3"]
