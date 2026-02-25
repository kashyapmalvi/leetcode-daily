# 412. Fizz Buzz

**LeetCode Problem:** [Fizz Buzz](https://leetcode.com/problems/fizz-buzz/)

## Approach
The approach to solving the "Fizz Buzz" problem involves iterating through a range of numbers from 1 to n and checking each number for certain conditions. If a number is divisible by both 3 and 5, it appends "FizzBuzz" to the list; otherwise, it checks for divisibility by 3 or 5 and appends "Fizz" or "Buzz" accordingly, or the number itself if none of the conditions are met.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Initialize an empty ArrayList to store the results.
2. **Step 2**: Iterate through the numbers from 1 to n (inclusive) using a for loop.
3. **Step 3**: For each number, check if it is divisible by both 3 and 5.
4. **Step 4**: If the number is divisible by both, append "FizzBuzz" to the list.
5. **Step 5**: If not, check if the number is divisible by 3 and append "Fizz" if true.
6. **Step 6**: If the number is not divisible by 3, check if it is divisible by 5 and append "Buzz" if true.
7. **Step 7**: If none of the above conditions are met, append the number itself to the list as a string.
8. **Step 8**: After iterating through all numbers, return the list of results.

- **Time Complexity**: The time complexity of this solution is O(n), where n is the input number, because it involves a single loop that iterates n times.
- **Space Complexity**: The space complexity is also O(n), as in the worst-case scenario, the list will store n elements.

## Dry Run
Let's consider the example input n = 5. Here's how the algorithm would execute:

| Step Number | Current State of Variables | Action Taken | Result/Output |
| --- | --- | --- | --- |
| 1 | i = 1, al = [] | Initialize ArrayList | al = [] |
| 2 | i = 1, al = [] | Check conditions for i = 1 | al = ["1"] |
| 3 | i = 2, al = ["1"] | Check conditions for i = 2 | al = ["1", "2"] |
| 4 | i = 3, al = ["1", "2"] | Check conditions for i = 3, append "Fizz" | al = ["1", "2", "Fizz"] |
| 5 | i = 4, al = ["1", "2", "Fizz"] | Check conditions for i = 4 | al = ["1", "2", "Fizz", "4"] |
| 6 | i = 5, al = ["1", "2", "Fizz", "4"] | Check conditions for i = 5, append "Buzz" | al = ["1", "2", "Fizz", "4", "Buzz"] |

The final output for n = 5 would be ["1", "2", "Fizz", "4", "Buzz"].
## Code
```java
class Solution {
    public List<String> fizzBuzz(int n) {

        ArrayList<String> al = new ArrayList<>();

        for (int i = 1; i <= n; i++) {
            if (i % 3 == 0 && i % 5 == 0) {
                al.add("FizzBuzz");
            } else if (i % 3 == 0) {
                al.add("Fizz");
            } else if (i % 5 == 0) {
                al.add("Buzz");
            } else {
                al.add(String.valueOf(i));
            }
        }

        return al;
        
    }
}
```