# 434. Number of Segments in a String

**LeetCode Problem:** [Number of Segments in a String](https://leetcode.com/problems/number-of-segments-in-a-string/)

## Approach
The approach to solving the "Number of Segments in a String" problem involves iterating through the input string and counting the number of segments separated by spaces. This is achieved by checking each character in the string and incrementing a counter whenever a non-space character is encountered after a space or at the beginning of the string.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Initialize a counter variable `count` to 0, which will store the total number of segments in the string.
2. **Step 2**: Iterate through the input string `s` using a for loop, checking each character at index `i`.
3. **Step 3**: For each character, check if it is not a space (`s.charAt(i) != ' '`) and if it is either the first character in the string (`i == 0`) or if the previous character is a space (`s.charAt(i - 1) == ' '`).
4. **Step 4**: If the conditions in step 3 are met, increment the `count` variable by 1, indicating the start of a new segment.

- **Time Complexity**: The time complexity of this algorithm is O(n), where n is the length of the input string `s`, because it involves a single pass through the string.
- **Space Complexity**: The space complexity is O(1), which means the space required does not grow with the size of the input string, as it only uses a constant amount of space to store the counter variable.

## Dry Run
Let's consider the input string "Hello World" as an example. Here's how the algorithm would execute:

| Step Number | Current State of Variables | Action Taken | Result/Output |
|-------------|---------------------------|--------------|---------------|
| 1           | `count = 0`, `i = 0`      | Check `s.charAt(0)` | `count = 1` because 'H' is not a space and it's the first character |
| 2           | `count = 1`, `i = 1`      | Check `s.charAt(1)` | No action, 'e' is not the start of a new segment |
| 3           | `count = 1`, `i = 2`      | Check `s.charAt(2)` | No action, 'l' is not the start of a new segment |
| 4           | `count = 1`, `i = 3`      | Check `s.charAt(3)` | No action, 'l' is not the start of a new segment |
| 5           | `count = 1`, `i = 4`      | Check `s.charAt(4)` | No action, 'o' is not the start of a new segment |
| 6           | `count = 1`, `i = 5`      | Check `s.charAt(5)` | `count = 2` because ' ' is followed by 'W', which is not a space |
| 7           | `count = 2`, `i = 6`      | Check `s.charAt(6)` | No action, 'o' is not the start of a new segment |
| 8           | `count = 2`, `i = 7`      | Check `s.charAt(7)` | No action, 'r' is not the start of a new segment |
| 9           | `count = 2`, `i = 8`      | Check `s.charAt(8)` | No action, 'l' is not the start of a new segment |
| 10          | `count = 2`, `i = 9`      | Check `s.charAt(9)` | No action, 'd' is not the start of a new segment |
| 11          | `count = 2`, `i = 10`     | End of loop        | Return `count = 2` |

The final output for the input "Hello World" is 2, indicating that there are two segments in the string.
## Code
```java
class Solution {
    public int countSegments(String s) {
        
        int count = 0;
        for(int i = 0;i<s.length();i++)
        {
            if(s.charAt(i) != ' ' && (i == 0 || s.charAt(i - 1) == ' '))
            {
                count++;
            }
        }
        return count;
    }
}
```