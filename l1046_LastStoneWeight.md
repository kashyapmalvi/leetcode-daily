# 1046. Last Stone Weight

**LeetCode Problem:** [Last Stone Weight](https://leetcode.com/problems/last-stone-weight/)

## Approach
The approach to solving the "Last Stone Weight" problem involves utilizing a priority queue to efficiently manage the stones and their weights. This is achieved by maintaining a max heap, which allows for the heaviest stones to be retrieved and smashed first.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Create a max heap priority queue and populate it with the weights of all the stones.
2. **Step 2**: Enter a loop that continues until only one stone remains (or none, if all stones are smashed to zero weight).
3. **Step 3**: Inside the loop, remove the two heaviest stones from the priority queue and compare their weights.
4. **Step 4**: If the weights of the two stones are not equal, calculate the difference and add the resulting weight back to the priority queue.
5. **Step 5**: Once the loop exits, check if the priority queue is empty (indicating all stones were smashed to zero weight) and return 0; otherwise, return the weight of the last remaining stone.

- **Time Complexity**: The time complexity of this solution is O(n log n), where n is the number of stones. This is because each insertion and removal operation on the priority queue takes O(log n) time, and these operations are performed n times.
- **Space Complexity**: The space complexity is O(n), as in the worst case, all stones' weights need to be stored in the priority queue.

## Dry Run
Let's consider an example input: `stones = [2, 7, 4, 1, 8, 1]`. Here's how the algorithm would execute:

| Step Number | Current State of Variables | Action Taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `pq = []`, `stones = [2, 7, 4, 1, 8, 1]` | Populate priority queue with stone weights | `pq = [8, 7, 4, 2, 1, 1]` |
| 2 | `pq = [8, 7, 4, 2, 1, 1]` | Remove heaviest stones (8 and 7), calculate difference | `pq = [4, 4, 2, 1, 1]`, difference = 1, add to pq: `pq = [4, 4, 2, 1, 1, 1]` |
| 3 | `pq = [4, 4, 2, 1, 1, 1]` | Remove heaviest stones (4 and 4), calculate difference | `pq = [2, 1, 1, 1, 1]`, difference = 0, do not add to pq |
| 4 | `pq = [2, 1, 1, 1, 1]` | Remove heaviest stones (2 and 1), calculate difference | `pq = [1, 1, 1, 1]`, difference = 1, add to pq: `pq = [1, 1, 1, 1, 1]` |
| 5 | `pq = [1, 1, 1, 1, 1]` | Remove heaviest stones (1 and 1), calculate difference | `pq = [1, 1, 1]`, difference = 0, do not add to pq |
| 6 | `pq = [1, 1, 1]` | Remove heaviest stones (1 and 1), calculate difference | `pq = [1]`, difference = 0, do not add to pq |
| 7 | `pq = [1]` | Loop exits, return last stone's weight | `output = 1` |

The final output of the algorithm for the given input is `1`, which is the weight of the last remaining stone.
## Code
```java
class Solution {
    public int lastStoneWeight(int[] stones) {

   PriorityQueue <Integer> pq = new PriorityQueue<>(Collections.reverseOrder());
    for(int n : stones)
    {
        pq.add(n);
    }
    while(pq.size()>1)
    {
        int a = pq.poll();
        int b = pq.poll();

        if(a!=b)
        {
            pq.add(a-b);
        }
    }

    return pq.isEmpty() ? 0:pq.poll();

  }
}
```