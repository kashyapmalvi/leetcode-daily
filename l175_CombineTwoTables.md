# 175. Combine Two Tables

**LeetCode Problem:** [Combine Two Tables](https://leetcode.com/problems/combine-two-tables/)

## Approach
The approach to solving the "Combine Two Tables" problem involves using a SQL left join to combine rows from the Person and Address tables based on the personId. This allows us to retrieve the desired information from both tables in a single query.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: The query starts by selecting the columns we want to retrieve, which are `firstName`, `lastName`, `city`, and `state`.
2. **Step 2**: It then specifies the tables we want to retrieve data from, which are the `Person` table (aliased as `p`) and the `Address` table (aliased as `a`).
3. **Step 3**: The query uses a left join to combine rows from the `Person` and `Address` tables based on the `personId` column, which is common to both tables.
4. **Step 4**: The left join ensures that all rows from the `Person` table are included in the results, even if there are no matching rows in the `Address` table.

- **Time Complexity**: The time complexity of this query is O(n), where n is the number of rows in the `Person` table, since we are performing a single pass through the table to retrieve the desired data.
- **Space Complexity**: The space complexity is also O(n), as we need to store the results of the query in memory.

## Dry Run
Let's consider an example where the `Person` table contains the following data:
| personId | firstName | lastName |
| --- | --- | --- |
| 1 | John | Doe |
| 2 | Jane | Smith |
| 3 | Bob | Johnson |

And the `Address` table contains the following data:
| personId | city | state |
| --- | --- | --- |
| 1 | New York | NY |
| 2 | Los Angeles | CA |

Here's the execution of the query in a step-by-step table format:
| Step Number | Current State of Variables | Action Taken | Result/Output |
| --- | --- | --- | --- |
| 1 | Person table: [(1, John, Doe), (2, Jane, Smith), (3, Bob, Johnson)] <br> Address table: [(1, New York, NY), (2, Los Angeles, CA)] | Select columns to retrieve | `firstName`, `lastName`, `city`, `state` |
| 2 | Person table: [(1, John, Doe), (2, Jane, Smith), (3, Bob, Johnson)] <br> Address table: [(1, New York, NY), (2, Los Angeles, CA)] | Perform left join on `personId` | Combined table: [(1, John, Doe, New York, NY), (2, Jane, Smith, Los Angeles, CA), (3, Bob, Johnson, NULL, NULL)] |
| 3 | Combined table: [(1, John, Doe, New York, NY), (2, Jane, Smith, Los Angeles, CA), (3, Bob, Johnson, NULL, NULL)] | Retrieve desired columns | Result: [(John, Doe, New York, NY), (Jane, Smith, Los Angeles, CA), (Bob, Johnson, NULL, NULL)] |

The final result is a table with the desired columns, where each row represents a person with their corresponding address information, if available.
## Code
```mysql
# Write your MySQL query statement belowselect 
select  p.firstName,p.lastName, a.city,a.state from Person p
  left join Address a   on p.personId = a.personId;
```