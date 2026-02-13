# 1464. Maximum Product of Two Elements in an Array

**LeetCode Problem:** [Maximum Product of Two Elements in an Array](https://leetcode.com/problems/maximum-product-of-two-elements-in-an-array/)

## Approach

The approach to solve this problem involves finding the two largest elements in the array, then returning the product of these two numbers minus one. This is because the problem asks for the maximum product of two elements in the array after subtracting one from each element.

Here is a step-by-step breakdown of the logic:
1. **Step 1**: Initialize two variables, `l` and `sl`, to store the largest and second-largest elements in the array, respectively.
2. **Step 2**: Iterate through the array, and for each element, check if it is larger than the current largest element `l`. If it is, update `sl` to be the old `l`, and update `l` to be the current element.
3. **Step 3**: If the current element is not larger than `l` but is larger than `sl`, update `sl` to be the current element.
4. **Step 4**: After iterating through the entire array, return the product of `l-1` and `sl-1`, which represents the maximum product of two elements in the array after subtracting one from each element.

- **Time Complexity**: The time complexity of this solution is O(n), where n is the number of elements in the array, because we only need to iterate through the array once.
- **Space Complexity**: The space complexity of this solution is O(1), because we only use a constant amount of space to store the variables `l` and `sl`, regardless of the size of the input array.

## Dry Run

Let's use the example input `arr = [3, 4, 5, 2]`. Here's how the algorithm would execute:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `l = 0`, `sl = 0` | Initialize variables | `l = 0`, `sl = 0` |
| 2 | `l = 0`, `sl = 0` | Check if `arr[0] = 3` is larger than `l = 0`. Update `l` to be `3`. | `l = 3`, `sl = 0` |
| 3 | `l = 3`, `sl = 0` | Check if `arr[1] = 4` is larger than `l = 3`. Update `sl` to be `3` and `l` to be `4`. | `l = 4`, `sl = 3` |
| 4 | `l = 4`, `sl = 3` | Check if `arr[2] = 5` is larger than `l = 4`. Update `sl` to be `4` and `l` to be `5`. | `l = 5`, `sl = 4` |
| 5 | `l = 5`, `sl = 4` | Check if `arr[3] = 2` is larger than `sl = 4`. It is not, so do nothing. | `l = 5`, `sl = 4` |
| 6 | `l = 5`, `sl = 4` | Return the product of `l-1` and `sl-1`, which is `(5-1) * (4-1) = 12`. | Output: `12` |

The final output of the algorithm is `12`, which is the maximum product of two elements in the array after subtracting one from each element.
## Code
```java
class Solution {
    public int maxProduct(int[] arr) {
        int l=0;
        int sl=0;

        for(int i = 0; i<arr.length;i++)
        {
            if(arr[i]>l)
            {
                sl = l;
                l = arr[i];
            }
            else if(arr[i]>sl)
            {
                sl = arr[i];
            }
        }

        return (l-1) * (sl-1); 

        
    }
}
```