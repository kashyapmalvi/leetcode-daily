# 349. Intersection of Two Arrays

**LeetCode Problem:** [Intersection of Two Arrays](https://leetcode.com/problems/intersection-of-two-arrays/)

## Approach
The approach to solving the "Intersection of Two Arrays" problem involves using two HashSet data structures to efficiently find the common elements between two input arrays. This is achieved by iterating through the arrays and utilizing the set's constant time complexity for adding and checking elements.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Create two HashSet instances, `set1` and `result`, to store unique elements from the first array and the intersection result, respectively.
2. **Step 2**: Iterate through the first array (`nums1`) and add each element to `set1`.
3. **Step 3**: Iterate through the second array (`nums2`) and check if each element exists in `set1`. If an element is found, add it to the `result` set.
4. **Step 4**: Create a new integer array (`arr`) with a size equal to the number of elements in the `result` set.
5. **Step 5**: Iterate through the `result` set and populate the `arr` array with its elements.

- **Time Complexity**: The time complexity of this solution is O(n + m), where n and m are the sizes of the input arrays `nums1` and `nums2`, respectively. This is because each element in both arrays is processed once.
- **Space Complexity**: The space complexity is also O(n + m), as in the worst-case scenario, all elements from both arrays could be stored in the sets and the resulting array.

## Dry Run
Let's consider an example with input arrays `nums1 = [1, 2, 2, 1]` and `nums2 = [2, 2]`.

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `set1 = {}`, `result = {}` | Initialize sets | `set1 = {}`, `result = {}` |
| 2 | `set1 = {}`, `result = {}` | Add elements from `nums1` to `set1`: `[1, 2, 2, 1]` | `set1 = {1, 2}`, `result = {}` |
| 3 | `set1 = {1, 2}`, `result = {}` | Iterate through `nums2` and add common elements to `result`: `[2, 2]` | `set1 = {1, 2}`, `result = {2}` |
| 4 | `set1 = {1, 2}`, `result = {2}` | Create array `arr` with size equal to `result.size()`: `1` | `arr = new int[1]` |
| 5 | `arr = new int[1]`, `result = {2}` | Populate `arr` with elements from `result` | `arr = [2]` |

The final output of the algorithm for the given input arrays is `[2]`, which represents the intersection of the two arrays.
## Code
```java
class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {

        HashSet <Integer> set1 = new HashSet<>();
        HashSet <Integer> result = new HashSet<>();

            for(int j : nums1)
            {
                set1.add(j);
            }

            for(int i : nums2)
            {
                if(set1.contains(i))
                {
                    result.add(i);
                }
            }
        int arr[] = new int [result.size()];
        int i = 0;

        for(int k : result)
        {
            arr[i++] = k;
        } 

  return arr;

        
    }
}
```