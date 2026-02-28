# 1572. Matrix Diagonal Sum

**LeetCode Problem:** [Matrix Diagonal Sum](https://leetcode.com/problems/matrix-diagonal-sum/)

## Approach
The approach to solving the "Matrix Diagonal Sum" problem involves iterating through the matrix and summing the elements on the primary and secondary diagonals. This is achieved by using a single loop to access elements on both diagonals.

1. **Step 1**: Initialize variables to keep track of the sum and the size of the matrix.
2. **Step 2**: Loop through the matrix, accessing elements on the primary diagonal (where the row index equals the column index) and the secondary diagonal (where the row index equals the size of the matrix minus the column index minus one).
3. **Step 3**: Add the elements on both diagonals to the sum.
4. **Step 4**: After the loop, check if the size of the matrix is odd. If it is, subtract the middle element (which was counted twice) from the sum.
5. **Step 5**: Return the final sum.

- **Time Complexity**: O(n), where n is the size of the matrix, because we are looping through the matrix once.
- **Space Complexity**: O(1), because we are using a constant amount of space to store the sum and the size of the matrix.

## Dry Run

Let's use the following example input:
```markdown
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
```

Here is the step-by-step execution:

| Step Number | Current State of Variables | Action Taken | Result/Output |
| --- | --- | --- | --- |
| 1 | sum = 0, size = 3 | Initialize variables | sum = 0, size = 3 |
| 2 | sum = 0, size = 3 | Add mat[0][0] and mat[0][2] to sum | sum = 1 + 3 = 4 |
| 3 | sum = 4, size = 3 | Add mat[1][1] and mat[1][1] to sum | sum = 4 + 5 + 5 = 14 |
| 4 | sum = 14, size = 3 | Add mat[2][2] and mat[2][0] to sum | sum = 14 + 9 + 7 = 30 |
| 5 | sum = 30, size = 3 | Check if size is odd, subtract mat[1][1] from sum | sum = 30 - 5 = 25 |
| 6 | sum = 25 | Return the final sum | Output: 25 |

The final output is 25, which is the sum of the elements on the primary and secondary diagonals of the matrix.
## Code
```java
class Solution {
    public int diagonalSum(int[][] mat) {

        int sum = 0;
        int size = mat.length;

        for(int i = 0; i<size;i++)
        {
            sum+= mat[i][i];
            sum+= mat[i][size-i-1]; 
        }

        if(size%2 !=0)
        {
            sum-= mat[size/2][size/2];
            return sum;
        }
        return sum;
        


        
    }
}
```