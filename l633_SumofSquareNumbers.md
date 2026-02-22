# 633. Sum of Square Numbers

**LeetCode Problem:** [Sum of Square Numbers](https://leetcode.com/problems/sum-of-square-numbers/)

## Approach

The approach to solving the "Sum of Square Numbers" problem involves using a two-pointer technique with a binary search-like strategy. This method iterates through possible square numbers that could sum up to the target number `c`.

Here's a step-by-step breakdown:
1. **Step 1**: Initialize two pointers, `l` and `r`, to represent the range of possible square numbers, where `l` starts at 0 and `r` is the square root of `c`.
2. **Step 2**: Calculate the sum of the squares of the numbers at the current `l` and `r` pointers.
3. **Step 3**: Compare the calculated sum to the target number `c`. If the sum equals `c`, return `true`.
4. **Step 4**: If the sum is greater than `c`, decrement `r` to reduce the sum.
5. **Step 5**: If the sum is less than `c`, increment `l` to increase the sum.
6. **Step 6**: Repeat steps 2-5 until `l` is greater than `r`. If no suitable pair is found, return `false`.

- **Time Complexity**: The time complexity of this solution is O(sqrt(c)) because in the worst-case scenario, the while loop runs until `l` exceeds `r`, which happens at most sqrt(c) times.
- **Space Complexity**: The space complexity is O(1) because the space used does not grow with the size of the input, only a constant amount of space is used to store the variables.

## Dry Run

Let's consider an example input `c = 5`. Here's how the algorithm executes:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `l = 0`, `r = 2` (since sqrt(5) is approximately 2.24) | Initialize pointers | - |
| 2 | `l = 0`, `r = 2` | Calculate sum `0*0 + 2*2 = 4` | Sum is less than `c` |
| 3 | `l = 1`, `r = 2` | Increment `l` because sum is less than `c` | - |
| 4 | `l = 1`, `r = 2` | Calculate sum `1*1 + 2*2 = 5` | Sum equals `c` |
| 5 | - | Return `true` because a suitable pair is found | `true` |

The algorithm terminates after finding a pair of square numbers (1 and 2) that sum up to the target number `c = 5`, returning `true`.
## Code
```java
class Solution {
    public boolean judgeSquareSum(int c) {

        long l = 0;
        long r =(long)Math.sqrt(c); 

        while(l<=r)
        {
            long sum = l*l + r*r;

            if(sum == c)
            {
                return true;
            }

            else if(sum >c)
            {
                r--;
            }

            else
            {
                l++;
            }

        }   
    
    return false;

    }
}
```