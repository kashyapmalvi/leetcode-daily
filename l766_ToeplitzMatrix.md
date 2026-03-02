# 766. Toeplitz Matrix

**LeetCode Problem:** [Toeplitz Matrix](https://leetcode.com/problems/toeplitz-matrix/)

## Approach
The approach to solving the "Toeplitz Matrix" problem involves iterating through the 2D array and checking if each element is equal to the element diagonally below it. This is done by comparing `arr[i][j]` with `arr[i+1][j+1]` for all valid `i` and `j`.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Initialize variables `a` and `b` to store the number of rows and columns in the input 2D array `arr`.
2. **Step 2**: Iterate through each element in the array, excluding the last row and column, using nested for loops.
3. **Step 3**: Inside the loops, compare the current element `arr[i][j]` with the element diagonally below it `arr[i+1][j+1]`.
4. **Step 4**: If a pair of elements is found to be unequal, immediately return `false`, indicating that the matrix is not a Toeplitz matrix.
5. **Step 5**: If the loops complete without finding any unequal pairs, return `true`, indicating that the matrix is a Toeplitz matrix.

- **Time Complexity**: The time complexity is O(a*b), where `a` is the number of rows and `b` is the number of columns in the input array, since we are iterating through each element in the array once.
- **Space Complexity**: The space complexity is O(1), as we are only using a constant amount of space to store the variables `a` and `b`, and not using any data structures that scale with the input size.

## Dry Run
Let's consider the input `arr = [[1,2,3],[4,1,2],[7,4,1]]`. Here's the execution in a structured table format:

| Step Number | Current State of Variables | Action Taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `a = 3`, `b = 3` | Initialize variables | - |
| 2 | `i = 0`, `j = 0` | Start iterating through the array | - |
| 3 | `i = 0`, `j = 0` | Compare `arr[0][0]` with `arr[1][1]` | `arr[0][0] == arr[1][1]` is `1 == 1`, so continue |
| 4 | `i = 0`, `j = 1` | Compare `arr[0][1]` with `arr[1][2]` | `arr[0][1] == arr[1][2]` is `2 == 2`, so continue |
| 5 | `i = 1`, `j = 0` | Compare `arr[1][0]` with `arr[2][1]` | `arr[1][0] == arr[2][1]` is `4 == 4`, so continue |
| 6 | End of loops | No unequal pairs found | Return `true` |

The final output is `true`, indicating that the input matrix is a Toeplitz matrix.
## Code
```java
class Solution {
    public boolean isToeplitzMatrix(int[][] arr) {

        int a = arr.length;
        int b = arr[0].length;

        for(int i = 0;i<a-1;i++)
        {
            for(int j = 0; j<b-1;j++)
            {
                if(arr[i][j]!=arr[i+1][j+1])
                {
                    return false;
                }
             }
        }

        return true;
        
    }
}
```