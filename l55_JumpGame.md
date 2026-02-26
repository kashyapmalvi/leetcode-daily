# 55. Jump Game

**LeetCode Problem:** [Jump Game](https://leetcode.com/problems/jump-game/)

## Approach

The approach used in this solution is a greedy algorithm that starts from the end of the array and works its way backwards, keeping track of the farthest position that can be reached. This approach takes advantage of the fact that if a position can be reached, then all positions before it can also be reached if they have a large enough jump value.

Here is a step-by-step breakdown of the logic:
1. **Step 1**: Initialize the farthest position (`fp`) to the last index of the array, which is `nums.length-1`.
2. **Step 2**: Iterate through the array from the second last element to the first element.
3. **Step 3**: For each element, check if the current index plus the jump value is greater than or equal to the farthest position (`fp`).
4. **Step 4**: If the condition is met, update the farthest position (`fp`) to the current index.
5. **Step 5**: After iterating through the entire array, check if the farthest position (`fp`) is equal to 0, which means the first element can be reached.

- **Time Complexity**: The time complexity of this solution is O(n), where n is the number of elements in the array, because we are iterating through the array once.
- **Space Complexity**: The space complexity of this solution is O(1), because we are using a constant amount of space to store the farthest position (`fp`) and the loop variable (`i`).

## Dry Run

Let's take the example input `nums = [2,3,1,1,4]`. Here is the execution of the algorithm:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `fp = 4`, `i = 3` | Initialize `fp` and start iteration | `fp = 4` |
| 2 | `fp = 4`, `i = 3` | Check if `i + nums[i] >= fp` (3 + 1 >= 4) | `fp` remains 4 |
| 3 | `fp = 4`, `i = 2` | Check if `i + nums[i] >= fp` (2 + 1 >= 4) | `fp` remains 4 |
| 4 | `fp = 4`, `i = 1` | Check if `i + nums[i] >= fp` (1 + 3 >= 4) | `fp` updated to 1 |
| 5 | `fp = 1`, `i = 0` | Check if `i + nums[i] >= fp` (0 + 2 >= 1) | `fp` updated to 0 |
| 6 | `fp = 0` | Check if `fp == 0` | Returns `true` |

The final output is `true`, indicating that we can jump to the last index from the first index.
## Code
```java
class Solution {
    public boolean canJump(int[] nums) {

        int fp = nums.length-1;

        for(int i = nums.length-2;i>=0;i--)
        {
            if(i+nums[i] >=fp)
            {
                fp = i;
            }
        }


    return fp == 0;


        
    }
}
```