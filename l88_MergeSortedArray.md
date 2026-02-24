# 88. Merge Sorted Array

**LeetCode Problem:** [Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)

## Approach
The approach used here is to first copy elements from array B to array A and then sort the resulting array A. Alternatively, a more efficient approach is used in the commented code, which merges the two sorted arrays by comparing elements from the end of both arrays and placing the larger one at the end of array A.

Here's a step-by-step breakdown of the more efficient approach:
1. **Step 1**: Initialize three pointers, `index` at the end of array A, `i` at the end of the non-zero elements in array A, and `j` at the end of array B.
2. **Step 2**: Compare the elements at `A[i]` and `B[j]`, and place the larger one at `A[index]`. Decrement `index` and the corresponding pointer.
3. **Step 3**: Repeat step 2 until one of the arrays is exhausted.
4. **Step 4**: If array B is not exhausted, copy its remaining elements to array A.

- **Time Complexity**: O((m + n) log(m + n)) for the sorting approach, and O(m + n) for the two-pointer approach.
- **Space Complexity**: O(1) for the two-pointer approach, as it only uses a constant amount of space.

## Dry Run
Let's take an example with `A = [1, 2, 3, 0, 0, 0]`, `m = 3`, `B = [2, 5, 6]`, and `n = 3`. The goal is to merge the two sorted arrays into the first array.

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `index = 5`, `i = 2`, `j = 2` | Initialize pointers | `A = [1, 2, 3, 0, 0, 0]` |
| 2 | `A[2] = 3`, `B[2] = 6` | Compare `A[i]` and `B[j]`, place `B[j]` at `A[index]` | `A = [1, 2, 3, 0, 0, 6]`, `index = 4`, `j = 1` |
| 3 | `A[2] = 3`, `B[1] = 5` | Compare `A[i]` and `B[j]`, place `B[j]` at `A[index]` | `A = [1, 2, 3, 0, 5, 6]`, `index = 3`, `j = 0` |
| 4 | `A[2] = 3`, `B[0] = 2` | Compare `A[i]` and `B[j]`, place `A[i]` at `A[index]` | `A = [1, 2, 3, 3, 5, 6]`, `index = 2`, `i = 1` |
| 5 | `A[1] = 2`, `B[0] = 2` | Compare `A[i]` and `B[j]`, place `A[i]` at `A[index]` | `A = [1, 2, 2, 3, 5, 6]`, `index = 1`, `i = 0` |
| 6 | `A[0] = 1`, `B[0] = 2` | Compare `A[i]` and `B[j]`, place `B[j]` at `A[index]` | `A = [1, 2, 2, 3, 5, 6]`, `index = 0`, `j = -1` |
| 7 | `A[0] = 1` | Place `A[i]` at `A[index]` | `A = [1, 2, 2, 3, 5, 6]` |

The final merged array is `[1, 2, 2, 3, 5, 6]`.
## Code
```java


class Solution {
    public void merge(int[] A, int m, int[] B, int n) {

      for(int i = 0,j = m; i<n;i++)
      {
        A[j] = B[i];
        j++;
      }

      Arrays.sort(A);
        
        
        
    }
}

// class Solution {
//     public void merge(int[] A, int m, int[] B, int n) {
//         int index = m+n-1;
//         int i = m-1;
//         int j = n-1;

//         while (i>=0&& j>=0)
//         {
//             if(A[i]>= B[j])
//             {
//                 A[index--]= A[i--];
//             }
//             else {
//                 A[index--] = B[j--];
//             }
//         }

//         while (j>=0)
//         {
//             A[index--] = B[j--];
//         }
        
//     }
// }
```