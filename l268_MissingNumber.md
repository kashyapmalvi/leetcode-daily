# 268. Missing Number

**LeetCode Problem:** [Missing Number](https://leetcode.com/problems/missing-number/)

## Approach
The approach to solving the "Missing Number" problem involves calculating the sum of all numbers in the range from 0 to n (where n is the length of the input array) and then subtracting the sum of the numbers in the input array to find the missing number. This is based on the mathematical formula for the sum of an arithmetic series.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Calculate the sum of all numbers in the input array.
2. **Step 2**: Calculate the length of the input array (denoted as n).
3. **Step 3**: Use the formula n*(n+1)/2 to calculate the sum of all numbers in the range from 0 to n.
4. **Step 4**: Subtract the sum of the numbers in the input array from the sum calculated in Step 3 to find the missing number.

- **Time Complexity**: The time complexity of this solution is O(n), where n is the length of the input array, because we need to iterate over all elements in the array once.
- **Space Complexity**: The space complexity is O(1), which means the space required does not change with the size of the input array, making it constant.

## Dry Run
Let's take the input array `[0, 1, 3]` as an example to demonstrate the algorithm.

| Step Number | Current State of Variables | Action Taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `arrsum = 0`, `nums = [0, 1, 3]` | Initialize `arrsum` to 0 and start iterating over `nums` to calculate `arrsum`. | `arrsum = 0` |
| 2 | `i = 0`, `nums[0] = 0`, `arrsum = 0` | Add `nums[0]` to `arrsum`. | `arrsum = 0 + 0 = 0` |
| 3 | `i = 1`, `nums[1] = 1`, `arrsum = 0` | Add `nums[1]` to `arrsum`. | `arrsum = 0 + 1 = 1` |
| 4 | `i = 2`, `nums[2] = 3`, `arrsum = 1` | Add `nums[2]` to `arrsum`. | `arrsum = 1 + 3 = 4` |
| 5 | `n = nums.length = 3`, `arrsum = 4` | Calculate `n` and the sum of the range `0 to n` using `n*(n+1)/2`. | `sum = 3*(3+1)/2 = 6` |
| 6 | `sum = 6`, `arrsum = 4` | Subtract `arrsum` from `sum` to find the missing number. | `ans = sum - arrsum = 6 - 4 = 2` |
| 7 | `ans = 2` | Return `ans` as the missing number. | Output: `2` |

This dry run demonstrates how the algorithm calculates the missing number in the input array `[0, 1, 3]` to be `2`.
## Code
```java
class Solution {
    public int missingNumber(int[] nums) {
        int arrsum=0;
        for(int i = 0; i<nums.length; i++)
        {
            arrsum +=nums[i];
        }
        int n = nums.length;
        int sum = n*(n+1)/2;
        int ans = sum -arrsum;

        return ans;



        
        
    }
}
```