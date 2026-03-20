# 3731. Find Missing Elements

**LeetCode Problem:** [Find Missing Elements](https://leetcode.com/problems/find-missing-elements/)

## Approach

The approach used in the provided Java solution involves finding the minimum and maximum values in the input array, then iterating over this range to identify missing elements by checking if each value exists in the original array. This is achieved through a helper function that performs a linear search for a given value within the array.

1. **Step 1**: Find the minimum and maximum values in the input array to determine the range of numbers that need to be checked for missing elements.
2. **Step 2**: Create an empty list to store the missing elements.
3. **Step 3**: Iterate over the range from the minimum to the maximum value found in Step 1.
4. **Step 4**: For each number in the range, use the `search` function to check if it exists in the original array.
5. **Step 5**: If a number is not found in the array (i.e., `search` returns `false`), add it to the list of missing elements.
6. **Step 6**: After checking all numbers in the range, return the list of missing elements.

- **Time Complexity**: The time complexity of this solution is O(n^2) due to the nested loop structure (one loop in the `findMissingElements` method and another implicit loop in the `search` method), where n is the number of elements in the input array.
- **Space Complexity**: The space complexity is O(n) for storing the missing elements in the list, where n is the number of missing elements.

## Dry Run

Let's consider the input array `arr = [1, 2, 4, 6]`.

| Step Number | Current State of Variables | Action Taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `arr = [1, 2, 4, 6]`, `min = undefined`, `max = undefined` | Find `min` and `max` in `arr` | `min = 1`, `max = 6` |
| 2 | `min = 1`, `max = 6`, `al = []` | Initialize empty list `al` for missing elements | `al = []` |
| 3 | `i = 1`, `min = 1`, `max = 6`, `al = []` | Check if `1` exists in `arr` | `1` exists, `al = []` |
| 4 | `i = 2`, `min = 1`, `max = 6`, `al = []` | Check if `2` exists in `arr` | `2` exists, `al = []` |
| 5 | `i = 3`, `min = 1`, `max = 6`, `al = []` | Check if `3` exists in `arr` | `3` does not exist, `al = [3]` |
| 6 | `i = 4`, `min = 1`, `max = 6`, `al = [3]` | Check if `4` exists in `arr` | `4` exists, `al = [3]` |
| 7 | `i = 5`, `min = 1`, `max = 6`, `al = [3]` | Check if `5` exists in `arr` | `5` does not exist, `al = [3, 5]` |
| 8 | `i = 6`, `min = 1`, `max = 6`, `al = [3, 5]` | Check if `6` exists in `arr` (last iteration) | `5` does not exist but we moved to 6 which exists, `al = [3, 5]` |

The final output will be `[3, 5]`, which are the missing elements in the sequence from 1 to 6.
## Code
```java
class Solution { 
    static boolean search (int arr[],int value)
    {
        for(int i =0;i<arr.length;i++)
        {
            if(arr[i] == value)
            {
                return true;
            }
        }
        return false;

    }
    public List<Integer> findMissingElements(int[] arr) {
        int max = arr[0];
        int min = arr[0];
        for(int i = 1; i<arr.length;i++)
        {
            if(arr[i]>max)
            {
                max = arr[i];
            }
            else if(arr[i]<min){
                min = arr[i];
            }
        }
        // System.out.println(min + " " + max);
        
        ArrayList <Integer> al = new ArrayList<>();

        for(int i = min;i<max;i++)
        {
            if(!search(arr,i))
            {
                al.add(i);
            }
        }

        return al;
        
    }
}
```