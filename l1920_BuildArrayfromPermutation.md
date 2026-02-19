# 1920. Build Array from Permutation

**LeetCode Problem:** [Build Array from Permutation](https://leetcode.com/problems/build-array-from-permutation/)

## Approach

The approach to solving the "Build Array from Permutation" problem involves creating a new array where each element at index `i` is the value of the element at index `nums[i]` in the input array. This is achieved through a simple iteration over the input array.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Initialize an empty result array with the same length as the input array `nums`.
2. **Step 2**: Iterate over the input array `nums` using a for loop, where `i` represents the current index.
3. **Step 3**: For each index `i`, use the value of `nums[i]` as an index to access the corresponding element in the `nums` array and assign it to the `result` array at index `i`.

- **Time Complexity**: The time complexity of this solution is O(n), where n is the length of the input array, because it involves a single pass through the array.
- **Space Complexity**: The space complexity is O(n) as well, since a new array of the same length as the input array is created.

## Dry Run

Let's consider the example input `nums = [0, 2, 1, 5, 3, 4]`. Here's how the algorithm executes:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `result = [0, 0, 0, 0, 0, 0]`, `i = 0` | Access `nums[nums[0]]` and assign to `result[0]` | `result = [nums[0], 0, 0, 0, 0, 0]` = `[0, 0, 0, 0, 0, 0]` |
| 2 | `result = [0, 0, 0, 0, 0, 0]`, `i = 1` | Access `nums[nums[1]]` and assign to `result[1]` | `result = [0, nums[2], 0, 0, 0, 0]` = `[0, 1, 0, 0, 0, 0]` |
| 3 | `result = [0, 1, 0, 0, 0, 0]`, `i = 2` | Access `nums[nums[2]]` and assign to `result[2]` | `result = [0, 1, nums[1], 0, 0, 0]` = `[0, 1, 1, 0, 0, 0]` |
| 4 | `result = [0, 1, 1, 0, 0, 0]`, `i = 3` | Access `nums[nums[3]]` and assign to `result[3]` | `result = [0, 1, 1, nums[5], 0, 0]` = `[0, 1, 1, 4, 0, 0]` |
| 5 | `result = [0, 1, 1, 4, 0, 0]`, `i = 4` | Access `nums[nums[4]]` and assign to `result[4]` | `result = [0, 1, 1, 4, nums[3], 0]` = `[0, 1, 1, 4, 5, 0]` |
| 6 | `result = [0, 1, 1, 4, 5, 0]`, `i = 5` | Access `nums[nums[5]]` and assign to `result[5]` | `result = [0, 1, 1, 4, 5, nums[4]]` = `[0, 1, 1, 4, 5, 3]` |

The final output is `[0, 1, 1, 4, 5, 3]`.
## Code
```java
class Solution {
    public int[] buildArray(int[] nums) {

        int result[] = new int [nums.length];

        for(int i = 0; i<nums.length;i++)
        {
            result[i] = nums[nums[i]];
        }
        return result;
        
    }
}
```