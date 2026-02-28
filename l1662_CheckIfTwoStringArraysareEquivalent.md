# 1662. Check If Two String Arrays are Equivalent

**LeetCode Problem:** [Check If Two String Arrays are Equivalent](https://leetcode.com/problems/check-if-two-string-arrays-are-equivalent/)

## Approach
The approach involves concatenating all strings in each array into a single string and then comparing the two resulting strings for equality. This is achieved using Java's `String.join()` method to concatenate the strings and the `equals()` method to compare the resulting strings.

Here is a step-by-step breakdown of the logic:
1. **Step 1**: The function `arrayStringsAreEqual` is called with two string arrays `s1` and `s2` as arguments.
2. **Step 2**: The `String.join()` method is used to concatenate all strings in `s1` into a single string `str1`, and all strings in `s2` into a single string `str2`.
3. **Step 3**: The `equals()` method is called on `str1` to compare it with `str2`, returning a boolean value indicating whether the two strings are equal.

- **Time Complexity**: The time complexity is O(n + m), where n and m are the total number of characters in `s1` and `s2` respectively, because the `String.join()` method iterates over all characters in the input arrays.
- **Space Complexity**: The space complexity is also O(n + m), as the `String.join()` method creates new strings that contain all characters from the input arrays.

## Dry Run

Let's consider an example input where `s1 = ["ab", "c"]` and `s2 = ["a", "bc"]`. Here is the execution in a structured table format:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `s1 = ["ab", "c"]`, `s2 = ["a", "bc"]` | Call `arrayStringsAreEqual(s1, s2)` | - |
| 2 | `s1 = ["ab", "c"]`, `s2 = ["a", "bc"]` | `str1 = String.join("", s1)` | `str1 = "abc"` |
| 3 | `s1 = ["ab", "c"]`, `s2 = ["a", "bc"]`, `str1 = "abc"` | `str2 = String.join("", s2)` | `str2 = "abc"` |
| 4 | `s1 = ["ab", "c"]`, `s2 = ["a", "bc"]`, `str1 = "abc"`, `str2 = "abc"` | `return str1.equals(str2)` | `return true` |

The final output of the function is `true`, indicating that the two input arrays are equivalent.
## Code
```java
class Solution {
    public boolean arrayStringsAreEqual(String[] s1, String[] s2) {

        String str1 = String.join("", s1);
        String str2 = String.join("", s2);

        return str1.equals(str2);
    
    }
}
```