# 1394. Find Lucky Integer in an Array

**LeetCode Problem:** [Find Lucky Integer in an Array](https://leetcode.com/problems/find-lucky-integer-in-an-array/)

## Approach
The approach to solve this problem involves creating a frequency array to store the occurrence of each number in the input array, and then iterating through the frequency array in descending order to find the first number that matches its frequency. This approach ensures that the largest lucky integer is found if multiple lucky integers exist.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Create a frequency array `freq` of size 501 to store the occurrence of each number in the input array `arr`.
2. **Step 2**: Iterate through the input array `arr` and increment the corresponding index in the frequency array `freq` for each number.
3. **Step 3**: Iterate through the frequency array `freq` in descending order, starting from the largest possible number (500).
4. **Step 4**: For each number `i` in the frequency array, check if the frequency `freq[i]` matches the number `i` itself. If a match is found, return the number `i` as the largest lucky integer.

- **Time Complexity**: The time complexity of this solution is O(n + m), where n is the size of the input array and m is the size of the frequency array (which is 501 in this case). Since m is a constant, the time complexity can be simplified to O(n).
- **Space Complexity**: The space complexity of this solution is O(m), where m is the size of the frequency array (which is 501 in this case). This is because we need to store the frequency of each number in the input array.

## Dry Run
Let's consider an example input `arr = [2, 2, 3, 4]`. Here's the step-by-step execution of the algorithm:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `arr = [2, 2, 3, 4]`, `freq = [0, 0, 0, 0, ...]` | Initialize frequency array `freq` | `freq = [0, 0, 0, 0, ...]` |
| 2 | `arr = [2, 2, 3, 4]`, `freq = [0, 0, 0, 0, ...]` | Iterate through `arr` and update `freq` | `freq = [0, 0, 2, 1, 1, ...]` |
| 3 | `arr = [2, 2, 3, 4]`, `freq = [0, 0, 2, 1, 1, ...]` | Iterate through `freq` in descending order | Start checking from `i = 500` |
| 4 | `arr = [2, 2, 3, 4]`, `freq = [0, 0, 2, 1, 1, ...]`, `i = 4` | Check if `freq[i] == i` | `freq[4] == 1`, not a match |
| 5 | `arr = [2, 2, 3, 4]`, `freq = [0, 0, 2, 1, 1, ...]`, `i = 3` | Check if `freq[i] == i` | `freq[3] == 1`, not a match |
| 6 | `arr = [2, 2, 3, 4]`, `freq = [0, 0, 2, 1, 1, ...]`, `i = 2` | Check if `freq[i] == i` | `freq[2] == 2`, match found |
| 7 | `arr = [2, 2, 3, 4]`, `freq = [0, 0, 2, 1, 1, ...]`, `i = 2` | Return the lucky integer | Output: `2` |

The algorithm returns `2` as the largest lucky integer in the input array `arr = [2, 2, 3, 4]`.
## Code
```java
class Solution {
    public int findLucky(int[] arr) {
        int[] freq = new int[501];

        for (int num : arr) {
            freq[num]++;
        }

        for (int i = 500; i >= 1; i--) {
            if (freq[i] == i) {
                return i;
            }
        }

        return -1;
    }
}
```