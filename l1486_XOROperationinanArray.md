# 1486. XOR Operation in an Array

**LeetCode Problem:** [XOR Operation in an Array](https://leetcode.com/problems/xor-operation-in-an-array/)

## Approach

The approach to solving the "XOR Operation in an Array" problem involves using a simple iterative method to calculate the XOR of all elements in the array. This is achieved by initializing a variable `k` with the first element of the array and then iteratively XORing it with the remaining elements.

Here is a step-by-step breakdown of the logic:
1. **Step 1**: Initialize the variable `k` with the first element of the array, which is `start`.
2. **Step 2**: Iterate through the remaining elements of the array, starting from the second element (index 1) to the nth element.
3. **Step 3**: In each iteration, calculate the next element in the array using the formula `start + 2*i`, where `i` is the current index.
4. **Step 4**: XOR the current value of `k` with the calculated next element and update `k` with the result.

- **Time Complexity**: The time complexity of this solution is O(n), where n is the number of elements in the array, because we are iterating through the array once.
- **Space Complexity**: The space complexity of this solution is O(1), because we are using a constant amount of space to store the variable `k` and the loop counter `i`.

## Dry Run

Let's take an example input `n = 5` and `start = 0`. Here's how the algorithm would execute:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | k = 0, i = 1, n = 5, start = 0 | Initialize k with start | k = 0 |
| 2 | k = 0, i = 1, n = 5, start = 0 | Calculate next element: start + 2*i = 0 + 2*1 = 2 | next element = 2 |
| 2 | k = 0, i = 1, n = 5, start = 0 | XOR k with next element: k ^ 2 = 0 ^ 2 = 2 | k = 2 |
| 3 | k = 2, i = 2, n = 5, start = 0 | Calculate next element: start + 2*i = 0 + 2*2 = 4 | next element = 4 |
| 3 | k = 2, i = 2, n = 5, start = 0 | XOR k with next element: k ^ 4 = 2 ^ 4 = 6 | k = 6 |
| 4 | k = 6, i = 3, n = 5, start = 0 | Calculate next element: start + 2*i = 0 + 2*3 = 6 | next element = 6 |
| 4 | k = 6, i = 3, n = 5, start = 0 | XOR k with next element: k ^ 6 = 6 ^ 6 = 0 | k = 0 |
| 5 | k = 0, i = 4, n = 5, start = 0 | Calculate next element: start + 2*i = 0 + 2*4 = 8 | next element = 8 |
| 5 | k = 0, i = 4, n = 5, start = 0 | XOR k with next element: k ^ 8 = 0 ^ 8 = 8 | k = 8 |

The final result is `k = 8`, which is the XOR of all elements in the array.
## Code
```java
class Solution {
    public int xorOperation(int n, int start) {
        int k = start;
        for(int i = 1;i<n;i++)
        {
            k ^=(start+2*i);
        }
        return k;
    }
}
```