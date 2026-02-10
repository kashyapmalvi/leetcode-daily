# 1486. XOR Operation in an Array

**LeetCode Problem:** [XOR Operation in an Array](https://leetcode.com/problems/xor-operation-in-an-array/)

## Approach

The approach to solving the "XOR Operation in an Array" problem involves iterating through the array and performing XOR operations on each element. The solution starts with the initial value and then iteratively applies the XOR operation with the subsequent elements in the array.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Initialize the variable `k` with the starting value `start`.
2. **Step 2**: Iterate through the array from the second element to the nth element (since the first element is already considered in the initialization).
3. **Step 3**: In each iteration, perform an XOR operation between the current value of `k` and the current element in the array, which is calculated as `start + 2 * i`.
4. **Step 4**: Update the value of `k` with the result of the XOR operation.

- **Time Complexity**: The time complexity of this solution is O(n), where n is the number of elements in the array, since we are iterating through the array once.
- **Space Complexity**: The space complexity of this solution is O(1), since we are using a constant amount of space to store the variables, regardless of the size of the input.

## Dry Run

Let's consider an example input where `n = 5` and `start = 0`. Here's how the algorithm would execute:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `k = 0`, `i = 1` | Initialize `k` with `start` and start iteration | `k = 0` |
| 2 | `k = 0`, `i = 1` | Perform XOR operation: `k ^= (start + 2 * i)` = `0 ^= (0 + 2 * 1)` = `0 ^= 2` | `k = 2` |
| 3 | `k = 2`, `i = 2` | Perform XOR operation: `k ^= (start + 2 * i)` = `2 ^= (0 + 2 * 2)` = `2 ^= 4` | `k = 6` |
| 4 | `k = 6`, `i = 3` | Perform XOR operation: `k ^= (start + 2 * i)` = `6 ^= (0 + 2 * 3)` = `6 ^= 6` | `k = 0` |
| 5 | `k = 0`, `i = 4` | Perform XOR operation: `k ^= (start + 2 * i)` = `0 ^= (0 + 2 * 4)` = `0 ^= 8` | `k = 8` |

The final output of the algorithm would be `8`.
## Code
```java
class Solution {
    public int xorOperation(int n, int start) {
        int k = start;
        for(int i = 1;i<n;i++)
        {
            k ^=(start+2*i);
        }
        return k;
    }
}
```