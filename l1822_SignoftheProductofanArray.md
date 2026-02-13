# 1822. Sign of the Product of an Array

**LeetCode Problem:** [Sign of the Product of an Array](https://leetcode.com/problems/sign-of-the-product-of-an-array/)

## Approach
The approach to solving the "Sign of the Product of an Array" problem involves counting the number of zeros and negative numbers in the array. The sign of the product of the array can then be determined based on these counts.

Here is a step-by-step breakdown of the logic:
1. **Step 1**: Initialize two counters, `zerocount` and `nagitivecount`, to keep track of the number of zeros and negative numbers in the array, respectively.
2. **Step 2**: Iterate through each element in the array, checking if it is zero or negative. If it is zero, increment `zerocount`. If it is negative, increment `nagitivecount`.
3. **Step 3**: After iterating through the entire array, check if `zerocount` is greater than zero. If it is, return 0, as any number multiplied by zero is zero.
4. **Step 4**: If `zerocount` is zero, check if `nagitivecount` is even or odd. If it is even, return 1, as the product of an even number of negative numbers is positive. If it is odd, return -1, as the product of an odd number of negative numbers is negative.

- **Time Complexity**: The time complexity of this solution is O(n), where n is the number of elements in the array, as we only need to iterate through the array once.
- **Space Complexity**: The space complexity of this solution is O(1), as we only use a constant amount of space to store the two counters, regardless of the size of the input array.

## Dry Run
Let's use the input array `[3, 2, -1, 4]` as an example.

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `zerocount = 0`, `nagitivecount = 0` | Initialize counters | `zerocount = 0`, `nagitivecount = 0` |
| 2 | `zerocount = 0`, `nagitivecount = 0` | Check first element (3), it's positive, so do nothing | `zerocount = 0`, `nagitivecount = 0` |
| 3 | `zerocount = 0`, `nagitivecount = 0` | Check second element (2), it's positive, so do nothing | `zerocount = 0`, `nagitivecount = 0` |
| 4 | `zerocount = 0`, `nagitivecount = 0` | Check third element (-1), it's negative, so increment `nagitivecount` | `zerocount = 0`, `nagitivecount = 1` |
| 5 | `zerocount = 0`, `nagitivecount = 1` | Check fourth element (4), it's positive, so do nothing | `zerocount = 0`, `nagitivecount = 1` |
| 6 | `zerocount = 0`, `nagitivecount = 1` | Check if `zerocount` is greater than zero, it's not, so check if `nagitivecount` is even or odd | `zerocount = 0`, `nagitivecount = 1` |
| 7 | `zerocount = 0`, `nagitivecount = 1` | `nagitivecount` is odd, so return -1 | Output: `-1` |

The final output of the algorithm is `-1`, indicating that the product of the array is negative.
## Code
```java
class Solution {
    public int arraySign(int[] arr) {
        int zerocount = 0;
        int nagitivecount = 0;
        for(int i = 0;i<arr.length;i++)
        {
            if(arr[i] == 0)
            {
                zerocount++;
            }
            else if(arr[i]<0)
            {
                nagitivecount++;
            }            
        }
        if(zerocount>0)
        {
            return 0;
        }
        else if(nagitivecount %2 == 0)
        {
            return 1;
        }
        else {
            return -1;
        }





        
    }
}
```