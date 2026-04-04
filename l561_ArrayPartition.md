# 561. Array Partition

**LeetCode Problem:** [Array Partition](https://leetcode.com/problems/array-partition/)

## Approach
The approach to solving the "Array Partition" problem involves sorting the input array and then summing up the smaller elements of each pair. This is done to minimize the sum of the pairs, as the problem requires.

Here is a step-by-step breakdown of the logic:
1. **Step 1**: Sort the input array in ascending order to pair the smallest numbers together.
2. **Step 2**: Initialize a variable to store the sum of the pairs.
3. **Step 3**: Iterate through the sorted array, stepping by 2 each time to consider each pair.
4. **Step 4**: In each iteration, add the smaller element of the pair (which is the current element) to the sum.
5. **Step 5**: After iterating through the entire array, return the calculated sum.

- **Time Complexity**: The time complexity of this solution is O(n log n) due to the sorting operation, where n is the number of elements in the input array.
- **Space Complexity**: The space complexity is O(1) if the sorting is done in-place, or O(n) if a new sorted array is created, where n is the number of elements in the input array.

## Dry Run
Let's consider the example input `nums = [1, 4, 3, 2]`.

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `nums = [1, 4, 3, 2]` | Sort the array | `nums = [1, 2, 3, 4]` |
| 2 | `nums = [1, 2, 3, 4]`, `result = 0` | Initialize result variable | `result = 0` |
| 3 | `nums = [1, 2, 3, 4]`, `result = 0`, `i = 0` | Iterate through the array, add `nums[0]` to result | `result = 1` |
| 4 | `nums = [1, 2, 3, 4]`, `result = 1`, `i = 2` | Iterate through the array, add `nums[2]` to result | `result = 1 + 3 = 4` |
| 5 | `nums = [1, 2, 3, 4]`, `result = 4` | Return the result | `Output = 4` |

The final output of the algorithm for the input `[1, 4, 3, 2]` is `4`, which is the sum of the smaller elements of each pair.
## Code
```java
class Solution {
    public int arrayPairSum(int[] nums) {
        Arrays.sort(nums);
                int result = 0;
                        for(int i = 0;i<nums.length;i+=2)
                                {
                                            result+=nums[i];
                                                    }
                                                            return result;
    }
}
```