# 1672. Richest Customer Wealth

**LeetCode Problem:** [Richest Customer Wealth](https://leetcode.com/problems/richest-customer-wealth/)

## Approach
The approach to solving the "Richest Customer Wealth" problem involves iterating over each customer's accounts, calculating the total wealth of each customer, and keeping track of the maximum wealth found. This is achieved through a simple iterative process.

Here is a step-by-step breakdown:
1. **Step 1**: Initialize a variable `result` to store the maximum wealth found so far, starting with a value of 0.
2. **Step 2**: Iterate over each customer in the input array `arr`, where each customer is represented by an array of their account balances.
3. **Step 3**: For each customer, calculate the total wealth by summing up all their account balances.
4. **Step 4**: Update the `result` variable if the current customer's total wealth is greater than the previously found maximum wealth.
5. **Step 5**: After iterating over all customers, return the `result` variable, which now holds the maximum wealth found.

- **Time Complexity**: The time complexity of this solution is O(n*m), where n is the number of customers and m is the average number of accounts per customer, because we are iterating over each account of each customer once.
- **Space Complexity**: The space complexity is O(1), as we are using a constant amount of space to store the `result` variable and other loop variables, regardless of the input size.

## Dry Run
Let's consider an example input `arr = [[1,2,3], [3,2,1], [5,5,5]]`. Here's how the algorithm would execute:

| Step Number | Current State of Variables | Action Taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `result = 0`, `i = 0` | Initialize `sum` to 0, iterate over customer 0's accounts | `sum = 0` |
| 2 | `sum = 0`, `j = 0` | Add account balance to `sum` (1 + 0) | `sum = 1` |
| 3 | `sum = 1`, `j = 1` | Add account balance to `sum` (1 + 2) | `sum = 3` |
| 4 | `sum = 3`, `j = 2` | Add account balance to `sum` (3 + 3) | `sum = 6` |
| 5 | `sum = 6`, `i = 0` | Update `result` if `sum` is greater (6 > 0) | `result = 6` |
| 6 | `result = 6`, `i = 1` | Initialize `sum` to 0, iterate over customer 1's accounts | `sum = 0` |
| 7 | `sum = 0`, `j = 0` | Add account balance to `sum` (0 + 3) | `sum = 3` |
| 8 | `sum = 3`, `j = 1` | Add account balance to `sum` (3 + 2) | `sum = 5` |
| 9 | `sum = 5`, `j = 2` | Add account balance to `sum` (5 + 1) | `sum = 6` |
| 10 | `sum = 6`, `i = 1` | Update `result` if `sum` is greater (6 == 6) | `result = 6` (no change) |
| 11 | `result = 6`, `i = 2` | Initialize `sum` to 0, iterate over customer 2's accounts | `sum = 0` |
| 12 | `sum = 0`, `j = 0` | Add account balance to `sum` (0 + 5) | `sum = 5` |
| 13 | `sum = 5`, `j = 1` | Add account balance to `sum` (5 + 5) | `sum = 10` |
| 14 | `sum = 10`, `j = 2` | Add account balance to `sum` (10 + 5) | `sum = 15` |
| 15 | `sum = 15`, `i = 2` | Update `result` if `sum` is greater (15 > 6) | `result = 15` |
| 16 | `result = 15` | Return `result` as the final answer | Output: `15` |

The final output is `15`, which is the maximum wealth found among all customers.
## Code
```java
class Solution {
    public int maximumWealth(int[][] arr) {

            int result =0;
            for(int i =0;i<arr.length;i++)
            {
                int sum = 0;
                for(int j = 0; j<arr[i].length;j++)
                {
                    sum += arr[i][j];
                }
                result = Math.max(result, sum);
            }

            return result;

        
    }
}
```