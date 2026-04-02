# 412. Fizz Buzz

**LeetCode Problem:** [Fizz Buzz](https://leetcode.com/problems/fizz-buzz/)

## Approach
The approach to solving the Fizz Buzz problem involves iterating through numbers from 1 to n and checking each number for specific divisibility conditions to determine the output string. This is achieved through a simple loop with conditional statements.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Initialize an empty list `res` to store the output strings.
2. **Step 2**: Start a loop from 1 to `n` (inclusive) using the variable `i`.
3. **Step 3**: For each `i`, check if it is divisible by 15 (i.e., `i % 15 == 0`). If true, add "FizzBuzz" to the `res` list.
4. **Step 4**: If `i` is not divisible by 15, check if it is divisible by 3. If true, add "Fizz" to the `res` list.
5. **Step 5**: If `i` is neither divisible by 15 nor 3, check if it is divisible by 5. If true, add "Buzz" to the `res` list.
6. **Step 6**: If none of the above conditions are met, add the string representation of `i` to the `res` list.
7. **Step 7**: After the loop completes, return the `res` list containing the output strings.

- **Time Complexity**: The time complexity is O(n) because the algorithm iterates through the numbers from 1 to n once.
- **Space Complexity**: The space complexity is also O(n) as in the worst-case scenario, the algorithm stores all numbers from 1 to n as strings in the output list.

## Dry Run
Let's consider an example input `n = 5`. Here's the step-by-step execution:

| Step Number | Current State of Variables | Action Taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `res = []`, `i = 1` | Check divisibility conditions for `i = 1` | `res = ["1"]` |
| 2 | `res = ["1"]`, `i = 2` | Check divisibility conditions for `i = 2` | `res = ["1", "2"]` |
| 3 | `res = ["1", "2"]`, `i = 3` | `i` is divisible by 3, add "Fizz" | `res = ["1", "2", "Fizz"]` |
| 4 | `res = ["1", "2", "Fizz"]`, `i = 4` | Check divisibility conditions for `i = 4` | `res = ["1", "2", "Fizz", "4"]` |
| 5 | `res = ["1", "2", "Fizz", "4"]`, `i = 5` | `i` is divisible by 5, add "Buzz" | `res = ["1", "2", "Fizz", "4", "Buzz"]` |

After the loop completes, the function returns `res = ["1", "2", "Fizz", "4", "Buzz"]`.
## Code
```java
class Solution {
    public List<String> fizzBuzz(int n) {
         List<String> res = new ArrayList<>();

        for (int i = 1; i <= n; i++) {
            if (i % 15 == 0) {
                res.add("FizzBuzz");
            } else if (i % 3 == 0) {
                res.add("Fizz");
            } else if (i % 5 == 0) {
                res.add("Buzz");
            } else {
                res.add(String.valueOf(i));
            }
        }

        return res;        
    }
}
```