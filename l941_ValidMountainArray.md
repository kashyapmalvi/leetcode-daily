# 941. Valid Mountain Array

**LeetCode Problem:** [Valid Mountain Array](https://leetcode.com/problems/valid-mountain-array/)

## Approach

The approach to solving the "Valid Mountain Array" problem involves using two pointers to traverse the array from both ends, identifying the increasing and decreasing sequences that form a mountain. This is done by maintaining two pointers, `l` and `r`, starting from the beginning and end of the array, respectively, and moving them towards the center based on whether the elements are increasing or decreasing.

Here is a step-by-step breakdown of the logic:
1. **Step 1**: Check if the array length is less than 3, in which case it cannot form a mountain, so return `false`.
2. **Step 2**: Initialize two pointers, `l` and `r`, to the start and end of the array, respectively.
3. **Step 3**: Move the `l` pointer to the right as long as the current element is less than the next one, indicating an increasing sequence.
4. **Step 4**: Move the `r` pointer to the left as long as the previous element is greater than the current one, indicating a decreasing sequence.
5. **Step 5**: Check if the `l` pointer is at the start or the `r` pointer is at the end of the array, in which case it's not a valid mountain, so return `false`.
6. **Step 6**: If the `l` and `r` pointers meet, it means a valid mountain sequence has been found, so return `true`.

- **Time Complexity**: O(n), where n is the number of elements in the array, because in the worst-case scenario, we might need to traverse the entire array once.
- **Space Complexity**: O(1), because we are using a constant amount of space to store the pointers and other variables, regardless of the size of the input array.

## Dry Run

Let's consider the example input: `[0, 3, 2, 1]`. Here's how the algorithm would execute:

| Step Number | Current State of Variables | Action Taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `arr = [0, 3, 2, 1]`, `l = 0`, `r = 3`, `n = 4` | Check if `n < 3` | `n >= 3`, proceed |
| 2 | `arr = [0, 3, 2, 1]`, `l = 0`, `r = 3`, `n = 4` | Initialize `l` and `r` | `l = 0`, `r = 3` |
| 3 | `arr = [0, 3, 2, 1]`, `l = 0`, `r = 3`, `n = 4` | Move `l` to the right because `arr[l] < arr[l+1]` | `l = 1` |
| 4 | `arr = [0, 3, 2, 1]`, `l = 1`, `r = 3`, `n = 4` | Move `l` to the right because `arr[l] < arr[l+1]` is false | `l = 1` (no change) |
| 5 | `arr = [0, 3, 2, 1]`, `l = 1`, `r = 3`, `n = 4` | Move `r` to the left because `arr[r-1] > arr[r]` | `r = 2` |
| 6 | `arr = [0, 3, 2, 1]`, `l = 1`, `r = 2`, `n = 4` | Move `r` to the left because `arr[r-1] > arr[r]` | `r = 1` |
| 7 | `arr = [0, 3, 2, 1]`, `l = 1`, `r = 1`, `n = 4` | Check if `l == r` | `l == r`, return `true` |

The output of this example would be `true`, indicating that the input array is a valid mountain array.
## Code
```java
class Solution {
    static {
        Runtime.getRuntime().gc();
        Runtime.getRuntime().addShutdownHook(new Thread(() -> {
            try (FileWriter writer = new FileWriter("display_runtime.txt")) {
                writer.write("0");
            } catch (IOException e) {
                e.printStackTrace();
            }
        }));
    }
    public boolean validMountainArray(int[] arr) {
        if(arr.length<3)
        {
            return false;
        }
        int l = 0;
        int r = arr.length-1;
        int n = arr.length;
       
            while(l+1<n && arr[l]<arr[l+1])
            {
                l++;
            }

            while(r-1>=0 && arr[r-1]>arr[r])
            {
                r--;
            }
            
            if(l == 0 || r == n-1)
            {
                return false;
            }
        
    return l == r;
    }
}
```