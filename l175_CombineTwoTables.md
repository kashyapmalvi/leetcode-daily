# 175. Combine Two Tables

**LeetCode Problem:** [Combine Two Tables](https://leetcode.com/problems/combine-two-tables/)

## Approach
The approach to solving the "Combine Two Tables" problem in MySQL involves using a left join operation to combine rows from the Person and Address tables based on a common column, which is the personId. This allows us to retrieve data from both tables in a single query.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: The query starts by selecting the columns we want to retrieve, which are firstName, lastName, city, and state, from the Person (p) and Address (a) tables.
2. **Step 2**: A left join operation is performed on the Person and Address tables based on the condition that the personId in the Person table matches the personId in the Address table.
3. **Step 3**: The left join returns all the rows from the Person table and the matching rows from the Address table. If there are no matches in the Address table, the result will contain NULL values for the Address columns.

- **Time Complexity**: The time complexity of this query is O(n), where n is the number of rows in the Person table, since we are performing a single pass through the table.
- **Space Complexity**: The space complexity is also O(n), as we need to store the results of the join operation, which can potentially contain all the rows from the Person table.

## Dry Run
Let's consider an example where the Person table contains the following data:
| personId | firstName | lastName |
| --- | --- | --- |
| 1 | John | Doe |
| 2 | Jane | Smith |
| 3 | Bob | Johnson |

And the Address table contains the following data:
| personId | city | state |
| --- | --- | --- |
| 1 | New York | NY |
| 2 | Los Angeles | CA |

Here's the execution of the query in a step-by-step table format:

| Step Number | Current State of Variables | Action Taken | Result/Output |
| --- | --- | --- | --- |
| 1 | Person table and Address table | Select columns from Person and Address tables | Selected columns: firstName, lastName, city, state |
| 2 | Person table and Address table | Perform left join on Person and Address tables based on personId | Joined table with matching rows from Address table |
| 3 | Joined table | Return all rows from Person table and matching rows from Address table | Result set: [(1, John, Doe, New York, NY), (2, Jane, Smith, Los Angeles, CA), (3, Bob, Johnson, NULL, NULL)] |

Note that the result set contains all the rows from the Person table, with the matching rows from the Address table. If there are no matches in the Address table (like for personId 3), the result set contains NULL values for the Address columns.
## Code
```mysql
 
select  p.firstName,p.lastName, a.city,a.state from Person p
  left join Address a   on p.personId = a.personId;
```