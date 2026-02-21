# 520. Detect Capital

**LeetCode Problem:** [Detect Capital](https://leetcode.com/problems/detect-capital/)

## Approach

The approach used to solve the "Detect Capital" problem involves iterating over each character in the input string and checking if it is uppercase or lowercase. The algorithm then determines if the string is in a valid capitalization format based on the count of uppercase characters.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Convert the input string into a character array to easily access each character.
2. **Step 2**: Check if the first character of the string is uppercase and increment the count of uppercase characters if it is.
3. **Step 3**: Iterate over the rest of the characters in the string, checking if each character is uppercase and incrementing the count if it is.
4. **Step 4**: After counting all uppercase characters, check if the entire string is uppercase, lowercase, or if only the first character is uppercase.
5. **Step 5**: Based on the count of uppercase characters and their positions, determine if the string is in a valid capitalization format.

- **Time Complexity**: The time complexity of this algorithm is O(n), where n is the length of the input string, because it involves a single pass over the string.
- **Space Complexity**: The space complexity is O(n) as well, because the algorithm creates a character array of the same length as the input string.

## Dry Run

Let's use the input string "USA" as an example to demonstrate the algorithm.

| Step Number | Current State of Variables | Action Taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `s = "USA"`, `arr = ['U', 'S', 'A']`, `c = 0` | Convert string to character array | `arr = ['U', 'S', 'A']` |
| 2 | `arr[0] = 'U'`, `c = 0` | Check if first character is uppercase, increment count | `c = 1` |
| 3 | `arr[1] = 'S'`, `c = 1` | Check if second character is uppercase, increment count | `c = 2` |
| 4 | `arr[2] = 'A'`, `c = 2` | Check if third character is uppercase, increment count | `c = 3` |
| 5 | `c = 3`, `arr.length = 3` | Check if entire string is uppercase | `return true` |

The final output of the algorithm for the input string "USA" is `true`, indicating that the string is in a valid capitalization format.
## Code
```java
class Solution {

    public static boolean fun(char s)
    {
         return Character.isUpperCase(s);
    }
    public boolean detectCapitalUse(String s) {

        

        int c = 0;
        char arr[] = s.toCharArray();

        if(fun(arr[0]))
        {
            c++;
        }

        for(int i = 1;i<arr.length;i++)
        {
            if(fun(arr[i]))
            {
                c++;
            }
        }       
        if(arr.length == c)
        {
            return true;
        } 
        else if (c == 0)
        {
            return true;
        }
        
        if(c == 1 && fun(arr[0])) 
        {
            return true;
        }
      
        
        return false;
    }
}
```