# 1752. Check if Array Is Sorted and Rotated

**LeetCode Problem:** [Check if Array Is Sorted and Rotated](https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/)

## Approach
The approach to solving the "Check if Array Is Sorted and Rotated" problem involves iterating through the array and checking for the number of rotations or "peaks" where an element is greater than the next one. This is done by maintaining a count of such instances.

Here is a step-by-step breakdown of the logic:
1. **Step 1**: Initialize a counter variable `count` to 0, which will keep track of the number of times the current element is greater than the next one.
2. **Step 2**: Iterate through the array using a for loop, comparing each element with the next one (wrapping around to the start of the array when reaching the end).
3. **Step 3**: If the current element is greater than the next one, increment the `count` variable.
4. **Step 4**: After iterating through the entire array, return whether the `count` is less than or equal to 1, indicating if the array is sorted and rotated.

- **Time Complexity**: O(n), where n is the number of elements in the array, because we are iterating through the array once.
- **Space Complexity**: O(1), because we are using a constant amount of space to store the `count` variable.

## Dry Run
Let's consider the example input `nums = [3, 4, 5, 1, 2]`. Here's how the algorithm would execute:

| Step number | Current state of variables | Action taken | Result/Output |
|-------------|----------------------------|--------------|--------------|
| 1           | `count = 0`, `i = 0`       | Compare `nums[0]` and `nums[1]` | `count` remains 0 because `nums[0] < nums[1]` |
| 2           | `count = 0`, `i = 1`       | Compare `nums[1]` and `nums[2]` | `count` remains 0 because `nums[1] < nums[2]` |
| 3           | `count = 0`, `i = 2`       | Compare `nums[2]` and `nums[3]` | `count` becomes 1 because `nums[2] > nums[3]` |
| 4           | `count = 1`, `i = 3`       | Compare `nums[3]` and `nums[4]` | `count` remains 1 because `nums[3] < nums[4]` |
| 5           | `count = 1`, `i = 4`       | Compare `nums[4]` and `nums[0]` | `count` remains 1 because `nums[4] > nums[0]` is not true for this problem's definition of rotation |
| Final       | `count = 1`               | Return whether `count` is less than or equal to 1 | Returns `true` because `count` is 1 |
## Code
```java
class Solution {
    public boolean check(int[] nums) {
            
              int count = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] > nums[(i + 1) % nums.length]) {
                count++;
            }
        }
        return count <= 1;
    }

    }

```