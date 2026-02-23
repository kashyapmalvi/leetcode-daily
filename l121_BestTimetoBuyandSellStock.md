# 121. Best Time to Buy and Sell Stock

**LeetCode Problem:** [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

## Approach
The approach to solving this problem involves iterating through the array of stock prices, keeping track of the minimum price encountered so far, and updating the maximum profit that can be achieved. The algorithm iterates through the prices, updating the minimum price and maximum profit as it finds better opportunities.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Initialize the minimum price (`minPrice`) to the first price in the array and the maximum profit (`maxProfit`) to 0.
2. **Step 2**: Iterate through the array of prices, starting from the second price (index 1).
3. **Step 3**: For each price, check if it's less than the current minimum price. If it is, update the minimum price.
4. **Step 4**: If the current price is not less than the minimum price, calculate the potential profit by subtracting the minimum price from the current price.
5. **Step 5**: If the calculated profit is greater than the current maximum profit, update the maximum profit.
6. **Step 6**: After iterating through all prices, return the maximum profit found.

- **Time Complexity**: The time complexity of this algorithm is O(n), where n is the number of prices in the array, because it involves a single pass through the array.
- **Space Complexity**: The space complexity is O(1), because it uses a constant amount of space to store the minimum price and maximum profit, regardless of the size of the input array.

## Dry Run
Let's consider an example input: `prices = [7, 1, 5, 3, 6, 4]`.

Here's a step-by-step execution of the algorithm:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `minPrice = 7`, `maxProfit = 0` | Initialize variables | - |
| 2 | `minPrice = 7`, `maxProfit = 0` | Check if `prices[1] = 1` is less than `minPrice`. Update `minPrice` to 1. | `minPrice = 1`, `maxProfit = 0` |
| 3 | `minPrice = 1`, `maxProfit = 0` | Calculate profit for `prices[2] = 5`. `profit = 5 - 1 = 4`. Update `maxProfit` to 4. | `minPrice = 1`, `maxProfit = 4` |
| 4 | `minPrice = 1`, `maxProfit = 4` | Check if `prices[3] = 3` is less than `minPrice`. No update. Calculate profit for `prices[3] = 3`. `profit = 3 - 1 = 2`. No update to `maxProfit`. | `minPrice = 1`, `maxProfit = 4` |
| 5 | `minPrice = 1`, `maxProfit = 4` | Calculate profit for `prices[4] = 6`. `profit = 6 - 1 = 5`. Update `maxProfit` to 5. | `minPrice = 1`, `maxProfit = 5` |
| 6 | `minPrice = 1`, `maxProfit = 5` | Check if `prices[5] = 4` is less than `minPrice`. No update. Calculate profit for `prices[5] = 4`. `profit = 4 - 1 = 3`. No update to `maxProfit`. | `minPrice = 1`, `maxProfit = 5` |
| 7 | `minPrice = 1`, `maxProfit = 5` | Return `maxProfit` | Output: `5` |

The final output of the algorithm for the input `prices = [7, 1, 5, 3, 6, 4]` is `5`, which is the maximum possible profit that can be achieved by buying and selling the stock.
## Code
```java
class Solution {
    public int maxProfit(int[] prices) {
        int minPrice = prices[0];   
        int maxProfit = 0;          

        for (int i = 1; i < prices.length; i++) {
            if (prices[i] < minPrice) {
                minPrice = prices[i];
            } 
            else {
                int profit = prices[i] - minPrice;
                if (profit > maxProfit) {
                    maxProfit = profit;
                }
            }
        }
        return maxProfit;
    }
}

```