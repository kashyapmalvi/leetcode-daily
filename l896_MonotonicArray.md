# 896. Monotonic Array

**LeetCode Problem:** [Monotonic Array](https://leetcode.com/problems/monotonic-array/)

## Approach

The approach to solving the "Monotonic Array" problem involves initializing two flags to track whether the array is increasing or decreasing, then iterating through the array to update these flags based on the comparison of adjacent elements. The function returns true if the array is either increasing or decreasing, and false otherwise.

Here is a step-by-step breakdown of the logic:
1. **Step 1**: Initialize two boolean variables, `in` and `de`, to true, assuming the array could be either increasing or decreasing.
2. **Step 2**: Iterate through the array starting from the second element (index 1), comparing each element with its previous one.
3. **Step 3**: If an element is less than its previous one, set `de` to false, indicating the array is not decreasing.
4. **Step 4**: If an element is greater than its previous one, set `in` to false, indicating the array is not increasing.
5. **Step 5**: After iterating through the entire array, return true if either `in` or `de` is still true, indicating the array is monotonic.

- **Time Complexity**: The time complexity is O(n), where n is the number of elements in the array, because we are making a single pass through the array.
- **Space Complexity**: The space complexity is O(1), because we are using a constant amount of space to store the flags and loop variables, regardless of the size of the input array.

## Dry Run

Let's use the input array `[1, 2, 2, 3]` as an example to demonstrate the algorithm.

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `in = true`, `de = true` | Initialize variables | - |
| 2 | `in = true`, `de = true` | Compare `arr[1]` (2) and `arr[0]` (1), `arr[1] > arr[0]`, so set `in` to false is not needed, but since `arr[1]` is not less than `arr[0]`, `de` remains true. However, the correct action is to set `in` to false when `arr[i] < arr[i-1]`, which doesn't happen here. The comparison result should lead to no change in `de` but since `arr[1] > arr[0]`, `in` should be set to false if we were checking for strictly increasing, but we're checking for non-decreasing or non-increasing, so the correct interpretation in this step should reflect that `de` remains true because the condition for `de` to be set to false isn't met. The condition for `in` to be set to false isn't met in the context of this specific comparison but `in` should be set to false when a decrease is detected, which isn't the case here. | `in = false` (due to a greater value, but in the context of allowing equals, `in` would be more accurately described as remaining true if we were strictly checking for increases, but since we allow equals, and the next step clarifies the action based on comparison) |
| 3 | `in = true`, `de = true` | Compare `arr[2]` (2) and `arr[1]` (2), `arr[2] == arr[1]`, so no change to `in` or `de`. | No change |
| 4 | `in = true`, `de = true` | Compare `arr[3]` (3) and `arr[2]` (2), `arr[3] > arr[2]`, so set `in` to false is the incorrect interpretation in this context since `in` should reflect if the array isn't increasing, but since we're allowing equals and checking for non-decreasing or non-increasing, `in` should actually remain true here because it's about the array not being strictly increasing but can be non-decreasing. However, given our logic, when `arr[i] > arr[i-1]`, it means `in` should be false if we were checking for strictly decreasing, but since `arr[i] > arr[i-1]`, `in` should actually remain true because the array is non-decreasing. The correct interpretation should be that since `arr[3] > arr[2]`, and we're checking for non-decreasing, `de` remains true, and because there's an increase, `in` should actually be set to false if we were strictly checking for decreases, but since we allow equals and are checking for non-decreasing or non-increasing, the correct action is `in` remains true if considering non-decreasing but is set to false if strictly checking for decreases, which isn't the case here. The logic here should clarify that since `arr[3] > arr[2]`, we're seeing an increase, which means the array isn't strictly decreasing, so `de` remains true, and since we allow equals, `in` remains true as well because the condition for `in` to be set to false (a decrease) isn't met. | `in = true`, `de = true` (reflecting the comparison result correctly in the context of non-decreasing or non-increasing) |
| 5 | `in = true`, `de = true` | Return `in || de` | Returns `true` because `de` is true |

This example demonstrates how the algorithm works for an array that is non-decreasing, thus returning true.
## Code
```java
class Solution {
    public boolean isMonotonic(int[] arr) {

        boolean in = true;
        boolean de = true;

        for(int i = 1; i<arr.length;i++)
        {
            if(arr[i]<arr[i-1])
            {
                de = false;
            }
            else if(arr[i]>arr[i-1])
            {
                in = false;
            }
        }

        return in || de;

         
    }
}
```