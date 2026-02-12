# 905. Sort Array By Parity

**LeetCode Problem:** [Sort Array By Parity](https://leetcode.com/problems/sort-array-by-parity/)

## Approach
The approach to solving this problem involves using a two-pointer technique, where one pointer starts from the beginning of the array and the other from the end. The algorithm iteratively swaps elements to ensure that all even numbers are on the left side of the array and all odd numbers are on the right side. 

Here's a step-by-step breakdown:
1. **Step 1**: The algorithm first checks if the array has 0 or 1 elements. If so, it returns the array as it is already sorted by parity.
2. **Step 2**: It initializes two pointers, `l` and `r`, to the start and end of the array respectively.
3. **Step 3**: The algorithm then enters a loop that continues until `l` is no longer less than `r`.
4. **Step 4**: Inside the loop, it first moves the `l` pointer to the right until it finds an odd number or until `l` is no longer less than `r`.
5. **Step 5**: Next, it moves the `r` pointer to the left until it finds an even number or until `l` is no longer less than `r`.
6. **Step 6**: Once it finds an odd number on the left and an even number on the right, it swaps these two numbers.
7. **Step 7**: The `l` and `r` pointers are then moved towards each other, and the process repeats until `l` is no longer less than `r`.

- **Time Complexity**: The time complexity of this algorithm is O(n), where n is the number of elements in the array, because each element is potentially visited once.
- **Space Complexity**: The space complexity of this algorithm is O(1), because it only uses a constant amount of space to store the pointers and temporary swap variable.

## Dry Run
Let's take the input array `[3, 1, 2, 4]` as an example.

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `l = 0`, `r = 3`, `nums = [3, 1, 2, 4]` | Check if array has 0 or 1 elements | Continue to next step |
| 2 | `l = 0`, `r = 3`, `nums = [3, 1, 2, 4]` | Move `l` to the right until an odd number is not found | `l = 0` (already odd) |
| 3 | `l = 0`, `r = 3`, `nums = [3, 1, 2, 4]` | Move `r` to the left until an even number is found | `r = 3` (found even number) |
| 4 | `l = 0`, `r = 3`, `nums = [3, 1, 2, 4]` | Swap `nums[l]` and `nums[r]` | `nums = [4, 1, 2, 3]` |
| 5 | `l = 1`, `r = 2`, `nums = [4, 1, 2, 3]` | Move `l` to the right until an odd number is not found | `l = 1` (found odd number) |
| 6 | `l = 1`, `r = 2`, `nums = [4, 1, 2, 3]` | Move `r` to the left until an even number is found | `r = 2` (found even number) |
| 7 | `l = 1`, `r = 2`, `nums = [4, 1, 2, 3]` | Swap `nums[l]` and `nums[r]` | `nums = [4, 2, 1, 3]` |
| 8 | `l = 2`, `r = 1`, `nums = [4, 2, 1, 3]` | Check if `l` is less than `r` | Exit loop, `nums = [4, 2, 1, 3]` |

The final output of the algorithm is `[4, 2, 1, 3]`, which is the input array sorted by parity.
## Code
```java
class Solution {
    public int[] sortArrayByParity(int[] nums) {
        
        if(nums.length == 0||nums.length == 1)
        {
            return nums;
        }
        int l = 0;
        int r = nums.length-1;

        while (l<r) {

            while (l<r&&nums[l]%2 ==0) {
                l++;
            }
            
            while (l<r&&nums[r]%2 !=0) {
                r--;
            }

            int temp = nums[l];
            nums[l]  = nums[r];
            nums[r] = temp;
            l++;
            r--;
        }        
        
        return nums;
        
    }
}
```