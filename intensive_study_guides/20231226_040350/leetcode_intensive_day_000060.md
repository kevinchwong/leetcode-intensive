
# Leetcode Intensive Tutorial Day 60 
> [Difficulty Score: 29]

> [Version: 20231226_040350]

> [Including this day, you had studied : 520 leetcode problems]


## Courses overview of the day

- 276 Paint Fence [Easy]
  - 265 Paint House II [Hard]
    - 256 Paint House [Medium]
    - 517 Super Washing Machines [Hard]
  - 552 Student Attendance Record II [Hard]
    - 568 Maximum Vacation Days [Hard]
  - 361 Bomb Enemy [Medium]
    - 174 Dungeon Game [Hard]
    - 495 Teemo Attacking [Medium]
    - 433 Minimum Genetic Mutation [Medium]

#### Step by step

 - [1. From 276 Paint Fence [Easy] to 265 Paint House II [Hard]](#1-from-276-paint-fence-easy-to-265-paint-house-ii-hard))

 - [2. From 265 Paint House II [Hard] to 256 Paint House [Medium]](#2-from-265-paint-house-ii-hard-to-256-paint-house-medium))

 - [3. From 265 Paint House II [Hard] to 517 Super Washing Machines [Hard]](#3-from-265-paint-house-ii-hard-to-517-super-washing-machines-hard))

 - [4. From 276 Paint Fence [Easy] to 552 Student Attendance Record II [Hard]](#4-from-276-paint-fence-easy-to-552-student-attendance-record-ii-hard))

 - [5. From 552 Student Attendance Record II [Hard] to 568 Maximum Vacation Days [Hard]](#5-from-552-student-attendance-record-ii-hard-to-568-maximum-vacation-days-hard))

 - [6. From 276 Paint Fence [Easy] to 361 Bomb Enemy [Medium]](#6-from-276-paint-fence-easy-to-361-bomb-enemy-medium))

 - [7. From 361 Bomb Enemy [Medium] to 174 Dungeon Game [Hard]](#7-from-361-bomb-enemy-medium-to-174-dungeon-game-hard))

 - [8. From 361 Bomb Enemy [Medium] to 495 Teemo Attacking [Medium]](#8-from-361-bomb-enemy-medium-to-495-teemo-attacking-medium))

 - [9. From 361 Bomb Enemy [Medium] to 433 Minimum Genetic Mutation [Medium]](#9-from-361-bomb-enemy-medium-to-433-minimum-genetic-mutation-medium))

    

#### Summary


- 174 Dungeon Game : Use dynamic programming to find the minimum initial health to escape from the dungeon.
- 552 Student Attendance Record II : Use dynamic programming to calculate the number of attendance records for each day.
- 568 Maximum Vacation Days : The essence of this problem is to efficiently calculate the maximum number of vacation days for each week and city, considering the flights between cities.
- 495 Teemo Attacking : Iterate through time series and calculate total poisoned time.
- 256 Paint House : The essence of this problem is to find the minimum cost of painting all houses such that no two adjacent houses have the same color.
- 265 Paint House II : The essence of this problem is to find the minimum cost of painting all houses with different colors.
- 361 Bomb Enemy : Given a grid with walls, enemies, and empty cells, find the maximum number of enemies that can be killed using one bomb.
- 517 Super Washing Machines : The essence of this problem is to distribute the dresses evenly among the washing machines by passing dresses between adjacent machines.
- 276 Paint Fence : The essence of this problem is to use dynamic programming to calculate the total number of ways to paint the fence.
- 433 Minimum Genetic Mutation : Given two gene strings, start and end, and a list of bank strings, find the minimum number of mutations needed to mutate from start to end.
> Similarity Diameter of these problems: 0.8326


---
# 1. From 276 Paint Fence [Easy] to 265 Paint House II [Hard]
> Similarity Distance: 0.3955

### >> 276 Paint Fence [Easy]
You are painting a fence of n posts with k different colors. You are given the number of ways to paint the first two posts with the same color and with different colors. Write a function to calculate the total number of ways to paint the fence.
##### Sample input:
n = 3, k = 2
##### Sample output:
6

##### Questions to ask to clarify requirements:
Can the number of posts or colors be negative? Can the number of posts be zero?

##### Optimal Python solution:
```python
def numWays(n, k):
    if n == 0:
        return 0
    if n == 1:
        return k
    same = k
    diff = k * (k - 1)
    for i in range(3, n + 1):
        same, diff = diff, (same + diff) * (k - 1)
    return same + diff
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- The number of ways to paint the first two posts with the same color is k.
- The number of ways to paint the first two posts with different colors is k * (k - 1).
- Use dynamic programming to calculate the total number of ways to paint the fence.

- Make sure to handle the edge cases when the number of posts or colors is negative or zero.
- Use variables to store and update intermediate values to avoid recalculating them.

- Using dynamic programming to calculate the total number of ways to paint the fence.
- Updating the same and diff variables in each iteration.

- Using recursion to calculate the total number of ways to paint the fence.
- Using a brute force approach to calculate the total number of ways to paint the fence.
    
### >> 265 Paint House II [Hard]
There are a row of n houses, each house can be painted with one of the k colors. The cost of painting each house with a certain color is different. You have to paint all the houses such that no two adjacent houses have the same color. The cost of painting each house with a certain color is represented by an n x k cost matrix costs. Return the minimum cost to paint all houses.
##### Sample input:
[[1,5,3],[2,9,4]]
##### Sample output:
5

##### Questions to ask to clarify requirements:

- What is the maximum number of houses?
- What is the maximum number of colors?
- Can the cost matrix be empty?

##### Optimal Python solution:
```python
def minCostII(costs):
    if not costs:
        return 0
    n, k = len(costs), len(costs[0])
    dp = [[0] * k for _ in range(n)]
    for i in range(k):
        dp[0][i] = costs[0][i]
    for i in range(1, n):
        for j in range(k):
            dp[i][j] = min(dp[i - 1][:j] + dp[i - 1][j + 1:]) + costs[i][j]
    return min(dp[-1])
```
##### Time complexity:
O(n * k^2)
##### Space complexity:
O(n * k)
##### Notes:

- Use dynamic programming to solve the problem
- Maintain a 2D array to store the minimum cost of painting each house with a certain color
- Iterate through the houses and colors to calculate the minimum cost

- Break down the problem into smaller subproblems
- Optimize the solution by using memoization or tabulation

- Calculating the minimum cost for each house based on the previous house's color

- Using a brute force approach to calculate all possible combinations of colors
    
### >> Comparison: 276 Paint Fence [Easy] *VS* 265 Paint House II [Hard]
> Similarity distance: 0.3955
##### Similarities

- Both questions involve painting a fence or a house with different colors.
- Both questions require finding the number of ways to paint the fence or house.
- Both questions have constraints on adjacent colors that can be used.
##### Differences

- Question 276 is an easy level question, while question 265 is a hard level question.
- Question 276 involves painting a fence with two colors, while question 265 involves painting a house with k colors.
- Question 276 requires finding the total number of ways to paint the fence, while question 265 requires finding the minimum cost of painting the house.
##### New Insights in 265 Paint House II [Hard]

- Question 276 can be solved using dynamic programming with O(n) time complexity.
- Question 265 can be solved using dynamic programming with O(nk) time complexity.
- Question 265 requires a more advanced approach compared to question 276.


---
# 2. From 265 Paint House II [Hard] to 256 Paint House [Medium]
> Similarity Distance: 0.4073

### >> Reminder: 265 Paint House II [Hard]
There are a row of n houses, each house can be painted with one of the k colors. The cost of painting each house with a certain color is different. You have to paint all the houses such that no two adjacent houses have the same color. The cost of painting each house with a certain color is represented by an n x k cost matrix costs. Return the minimum cost to paint all houses.
##### Optimal Python solution:
```python
def minCostII(costs):
    if not costs:
        return 0
    n, k = len(costs), len(costs[0])
    dp = [[0] * k for _ in range(n)]
    for i in range(k):
        dp[0][i] = costs[0][i]
    for i in range(1, n):
        for j in range(k):
            dp[i][j] = min(dp[i - 1][:j] + dp[i - 1][j + 1:]) + costs[i][j]
    return min(dp[-1])
```
The essence of this problem is to find the minimum cost of painting all houses with different colors.
    
### >> 256 Paint House [Medium]
There are a row of n houses, each house can be painted with one of the three colors: red, blue, or green. The cost of painting each house with a certain color is different. You have to paint all the houses such that no two adjacent houses have the same color. The cost of painting each house with a certain color is represented by an n x 3 cost matrix costs. Return the minimum cost to paint all houses.
##### Sample input:
[[17,2,17],[16,16,5],[14,3,19]]
##### Sample output:
10

##### Questions to ask to clarify requirements:

- Can the cost matrix be empty?
- Can we assume the cost matrix is always valid?
- What should we return if the cost matrix has only one row?

##### Optimal Python solution:
```python
def minCost(self, costs: List[List[int]]) -> int:
    if not costs:
        return 0
    n = len(costs)
    dp = [[0] * 3 for _ in range(n)]
    dp[0] = costs[0]
    for i in range(1, n):
        dp[i][0] = costs[i][0] + min(dp[i-1][1], dp[i-1][2])
        dp[i][1] = costs[i][1] + min(dp[i-1][0], dp[i-1][2])
        dp[i][2] = costs[i][2] + min(dp[i-1][0], dp[i-1][1])
    return min(dp[-1])
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- The problem can be solved using dynamic programming.
- The minimum cost to paint all houses can be calculated by considering the minimum cost of painting the previous house and the current house.
- The minimum cost of painting the current house with a certain color is the cost of painting the current house with that color plus the minimum cost of painting the previous house with a different color.

- Use dynamic programming to solve the problem.
- Create a 2D array to store the minimum cost of painting each house with each color.
- Handle edge cases such as an empty cost matrix or a cost matrix with only one row.

- Using a 2D array to store the minimum cost of painting each house with each color.

- Using recursion to solve the problem.
    
### >> Comparison: 265 Paint House II [Hard] *VS* 256 Paint House [Medium]
> Similarity distance: 0.4073
##### Similarities

- Both questions involve painting houses with different colors.
- Both questions have a limited number of colors available.
- Both questions require minimizing the cost of painting all the houses.
##### Differences

- Question 265 allows painting each house with any color, but adjacent houses cannot be painted with the same color.
- Question 256 allows painting each house with any color, but adjacent houses cannot be painted with the same color, and each color has a different cost.
##### New Insights in 256 Paint House [Medium]

- Question 265 introduces the concept of adjacent houses and the restriction on painting them with the same color.
- Question 256 introduces the concept of different costs for each color.


---
# 3. From 265 Paint House II [Hard] to 517 Super Washing Machines [Hard]
> Similarity Distance: 0.6459

### >> Reminder: 265 Paint House II [Hard]
There are a row of n houses, each house can be painted with one of the k colors. The cost of painting each house with a certain color is different. You have to paint all the houses such that no two adjacent houses have the same color. The cost of painting each house with a certain color is represented by an n x k cost matrix costs. Return the minimum cost to paint all houses.
##### Optimal Python solution:
```python
def minCostII(costs):
    if not costs:
        return 0
    n, k = len(costs), len(costs[0])
    dp = [[0] * k for _ in range(n)]
    for i in range(k):
        dp[0][i] = costs[0][i]
    for i in range(1, n):
        for j in range(k):
            dp[i][j] = min(dp[i - 1][:j] + dp[i - 1][j + 1:]) + costs[i][j]
    return min(dp[-1])
```
The essence of this problem is to find the minimum cost of painting all houses with different colors.
    
### >> 517 Super Washing Machines [Hard]
You have n super washing machines on a line. Initially, each washing machine has some dresses or is empty. For each move, you could choose any m (1 ≤ m ≤ n) washing machines, and pass one dress of each washing machine to one of its adjacent washing machines at the same time. Given an integer array representing the number of dresses in each washing machine from left to right on the line, you should find the minimum number of moves to make all the washing machines have the same number of dresses. If it is not possible to do it, return -1.
##### Sample input:
[1,0,5]
##### Sample output:
3

##### Questions to ask to clarify requirements:

- What is the maximum number of dresses in a single washing machine?
- Can we only pass dresses to adjacent washing machines or can we pass them to any washing machine?
- Can we choose different number of washing machines in each move?

##### Optimal Python solution:
```python
def findMinMoves(machines):
    total = sum(machines)
    n = len(machines)
    if total % n != 0:
        return -1
    avg = total // n
    ans, cnt = 0, 0
    for num in machines:
        cnt += num - avg
        ans = max(ans, max(abs(cnt), num - avg))
    return ans
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- The total number of dresses must be divisible by the number of washing machines in order to have a solution.
- The minimum number of moves is the maximum of the absolute difference between the number of dresses in each machine and the average number of dresses.
- We can calculate the number of moves needed for each machine and take the maximum of those values.

- Use the formula to calculate the minimum number of moves.
- Optimize the solution by avoiding unnecessary calculations.

- Calculating the number of moves needed for each machine can be tricky.
- The maximum number of moves is the maximum of the absolute difference between the number of dresses in each machine and the average number of dresses.

- Avoid using extra space.
- Avoid unnecessary calculations.
    
### >> Comparison: 265 Paint House II [Hard] *VS* 517 Super Washing Machines [Hard]
> Similarity distance: 0.6459
##### Similarities

- Both questions are classified as 'Hard' level.
- Both questions involve optimizing a process.
- Both questions require finding the minimum number of operations to achieve a certain goal.
##### Differences

- Question 265 involves painting houses, while question 517 involves washing machines.
- Question 265 requires painting each house with a certain color, while question 517 requires distributing clothes evenly among the machines.
- Question 265 allows adjacent houses to be painted the same color, while question 517 requires the machines to have the same number of clothes after each operation.
- Question 265 has a fixed number of colors, while question 517 has a variable number of machines.
##### New Insights in 517 Super Washing Machines [Hard]

- Question 265 can be solved using dynamic programming and the concept of memoization.
- Question 517 can be solved using mathematical calculations and the concept of balancing.


---
# 4. From 276 Paint Fence [Easy] to 552 Student Attendance Record II [Hard]
> Similarity Distance: 0.5817

### >> Reminder: 276 Paint Fence [Easy]
You are painting a fence of n posts with k different colors. You are given the number of ways to paint the first two posts with the same color and with different colors. Write a function to calculate the total number of ways to paint the fence.
##### Optimal Python solution:
```python
def numWays(n, k):
    if n == 0:
        return 0
    if n == 1:
        return k
    same = k
    diff = k * (k - 1)
    for i in range(3, n + 1):
        same, diff = diff, (same + diff) * (k - 1)
    return same + diff
```
The essence of this problem is to use dynamic programming to calculate the total number of ways to paint the fence.
    
### >> 552 Student Attendance Record II [Hard]
You are given an integer n representing the number of days in a school year. The school has a strict attendance policy, which states that the student cannot be absent for more than one day in a row or be late for more than two consecutive days. Your task is to calculate the number of all possible attendance records of length n that can be generated for a student.
##### Sample input:
1
2
3

##### Sample output:
3
8
19


##### Questions to ask to clarify requirements:
What is the maximum value of n? Can n be negative or zero?

##### Optimal Python solution:
```python
def checkRecord(n):
    MOD = 10**9 + 7
    dp = [[0] * 3 for _ in range(2)]
    dp[0][0] = 1
    dp[0][1] = 1
    dp[0][2] = 0
    dp[1][0] = 1
    dp[1][1] = 0
    dp[1][2] = 0
    for i in range(2, n + 1):
        new_dp = [[0] * 3 for _ in range(2)]
        new_dp[0][0] = (dp[0][0] + dp[0][1] + dp[0][2]) % MOD
        new_dp[0][1] = dp[0][0]
        new_dp[0][2] = dp[0][1]
        new_dp[1][0] = (dp[0][0] + dp[0][1] + dp[0][2] + dp[1][0] + dp[1][1] + dp[1][2]) % MOD
        new_dp[1][1] = dp[1][0]
        new_dp[1][2] = dp[1][1]
        dp = new_dp
    return sum(dp[0] + dp[1]) % MOD

```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Use a 2D array to store the number of attendance records
2. Initialize the array with base cases
3. Use dynamic programming to calculate the number of records for each day
4. Return the sum of all records modulo 10^9 + 7
Break down the problem into smaller subproblems and use dynamic programming to solve them.
None
None
    
### >> Comparison: 276 Paint Fence [Easy] *VS* 552 Student Attendance Record II [Hard]
> Similarity distance: 0.5817
##### Similarities

- Both questions are related to counting and arranging elements.
- Both questions require finding a solution within a given constraint.
##### Differences

- 276 Paint Fence is an easy question, while 552 Student Attendance Record II is a hard question.
- 276 Paint Fence involves painting a fence with two colors, while 552 Student Attendance Record II involves counting valid attendance records for a student.
- 276 Paint Fence has a linear time complexity solution, while 552 Student Attendance Record II has a dynamic programming solution.
- 276 Paint Fence has a straightforward approach, while 552 Student Attendance Record II requires understanding and implementing a complex algorithm.
##### New Insights in 552 Student Attendance Record II [Hard]

- From 276 Paint Fence, we can learn how to count and arrange elements efficiently.
- From 552 Student Attendance Record II, we can learn how to solve complex counting problems using dynamic programming.


---
# 5. From 552 Student Attendance Record II [Hard] to 568 Maximum Vacation Days [Hard]
> Similarity Distance: 0.5640

### >> Reminder: 552 Student Attendance Record II [Hard]
You are given an integer n representing the number of days in a school year. The school has a strict attendance policy, which states that the student cannot be absent for more than one day in a row or be late for more than two consecutive days. Your task is to calculate the number of all possible attendance records of length n that can be generated for a student.
##### Optimal Python solution:
```python
def checkRecord(n):
    MOD = 10**9 + 7
    dp = [[0] * 3 for _ in range(2)]
    dp[0][0] = 1
    dp[0][1] = 1
    dp[0][2] = 0
    dp[1][0] = 1
    dp[1][1] = 0
    dp[1][2] = 0
    for i in range(2, n + 1):
        new_dp = [[0] * 3 for _ in range(2)]
        new_dp[0][0] = (dp[0][0] + dp[0][1] + dp[0][2]) % MOD
        new_dp[0][1] = dp[0][0]
        new_dp[0][2] = dp[0][1]
        new_dp[1][0] = (dp[0][0] + dp[0][1] + dp[0][2] + dp[1][0] + dp[1][1] + dp[1][2]) % MOD
        new_dp[1][1] = dp[1][0]
        new_dp[1][2] = dp[1][1]
        dp = new_dp
    return sum(dp[0] + dp[1]) % MOD

```
Use dynamic programming to calculate the number of attendance records for each day.
    
### >> 568 Maximum Vacation Days [Hard]
Given a list of flights, where flights[i][j] represents the maximum number of vacation days you can have when traveling from city i to city j, and a list of days, where days[i] represents the maximum number of vacation days you can have in city i, return the maximum number of vacation days you can have during the K weeks.
##### Sample input:
[[0,1,1],[1,0,1],[1,1,0]]
[[1,3,1],[6,0,3],[3,3,3]]
1
##### Sample output:
4

##### Questions to ask to clarify requirements:
Can the flights be cyclic? Can the number of cities and weeks be very large?

##### Optimal Python solution:
```python
def maxVacationDays(flights: List[List[int]], days: List[List[int]], K: int) -> int:
    N = len(flights)
    dp = [[float('-inf')] * N for _ in range(K + 1)]
    dp[0][0] = 0
    for week in range(1, K + 1):
        for city in range(N):
            for prev_city in range(N):
                if city == prev_city or flights[prev_city][city]:
                    dp[week][city] = max(dp[week][city], dp[week - 1][prev_city] + days[city][week - 1])
    return max(dp[K])
```
##### Time complexity:
O(K * N^2)
##### Space complexity:
O(K * N)
##### Notes:
Use dynamic programming to calculate the maximum number of vacation days for each week and city. Consider the flights between cities to determine the maximum number of vacation days.
Break down the problem into subproblems and use dynamic programming to solve them. Consider the flights between cities when calculating the maximum number of vacation days.
The trickiest part of this problem is to efficiently calculate the maximum number of vacation days for each week and city, considering the flights between cities.
Avoid using a brute force approach to calculate the maximum number of vacation days for each week and city.
    
### >> Comparison: 552 Student Attendance Record II [Hard] *VS* 568 Maximum Vacation Days [Hard]
> Similarity distance: 0.5640
##### Similarities

- Both questions are classified as 'Hard' level.
- Both questions involve dynamic programming.
- Both questions require finding the maximum value.
##### Differences

- Question 552 involves student attendance records, while question 568 involves vacation days.
- Question 552 has a constraint on the number of absences allowed, while question 568 has a constraint on the number of vacation days allowed.
- Question 552 has a constraint on the number of consecutive late days allowed, while question 568 does not have this constraint.
- Question 552 has a constraint on the number of days in the attendance record, while question 568 has a constraint on the number of weeks.
##### New Insights in 568 Maximum Vacation Days [Hard]

- Question 552 requires considering the number of absences and consecutive late days, which adds complexity to the problem.
- Question 568 requires considering the number of vacation days, which adds a different dimension to the problem.
- Both questions require finding the maximum value, but the constraints and variables involved are different.


---
# 6. From 276 Paint Fence [Easy] to 361 Bomb Enemy [Medium]
> Similarity Distance: 0.6243

### >> Reminder: 276 Paint Fence [Easy]
You are painting a fence of n posts with k different colors. You are given the number of ways to paint the first two posts with the same color and with different colors. Write a function to calculate the total number of ways to paint the fence.
##### Optimal Python solution:
```python
def numWays(n, k):
    if n == 0:
        return 0
    if n == 1:
        return k
    same = k
    diff = k * (k - 1)
    for i in range(3, n + 1):
        same, diff = diff, (same + diff) * (k - 1)
    return same + diff
```
The essence of this problem is to use dynamic programming to calculate the total number of ways to paint the fence.
    
### >> 361 Bomb Enemy [Medium]
Given a 2D grid, each cell is either a wall 'W', an enemy 'E' or empty '0' (the number zero), return the maximum enemies you can kill using one bomb.
##### Sample input:

- [['0','E','0','0'],['E','0','W','E'],['0','E','0','0']]
##### Sample output:

- 3

##### Questions to ask to clarify requirements:

- What is the maximum size of the grid?
- Can the grid be empty?
- Can there be multiple bombs?
- What is the maximum number of enemies in the grid?

##### Optimal Python solution:
```python

- def maxKilledEnemies(grid):
    if not grid or not grid[0]:
        return 0
    m, n = len(grid), len(grid[0])
    row_hits = 0
    col_hits = [0] * n
    max_kills = 0
    for i in range(m):
        for j in range(n):
            if j == 0 or grid[i][j-1] == 'W':
                row_hits = 0
                k = j
                while k < n and grid[i][k] != 'W':
                    if grid[i][k] == 'E':
                        row_hits += 1
                    k += 1
            if i == 0 or grid[i-1][j] == 'W':
                col_hits[j] = 0
                k = i
                while k < m and grid[k][j] != 'W':
                    if grid[k][j] == 'E':
                        col_hits[j] += 1
                    k += 1
            if grid[i][j] == '0':
                max_kills = max(max_kills, row_hits + col_hits[j])
    return max_kills
```
##### Time complexity:
O(m*n)
##### Space complexity:
O(n)
##### Notes:

- Use dynamic programming to store the number of enemies killed in each row and column
- Iterate through the grid and calculate the maximum kills for each empty cell
- Track the maximum kills using a variable

- Optimize the solution by avoiding unnecessary calculations
- Handle edge cases such as empty grid or grid with no enemies

- Handling the case when there are walls in the grid
- Optimizing the solution to avoid unnecessary calculations

- Brute force approach of checking all possible combinations
    
### >> Comparison: 276 Paint Fence [Easy] *VS* 361 Bomb Enemy [Medium]
> Similarity distance: 0.6243
##### Similarities

- Both questions involve counting and manipulating elements in a grid.
- Both questions require finding the maximum number of occurrences of a certain element.
- Both questions involve dynamic programming techniques.
##### Differences

- Paint Fence: Involves painting a fence with two different colors, with the constraint that no more than two adjacent fences can have the same color.
- Bomb Enemy: Involves placing bombs in a grid to maximize the number of enemies killed, with the constraint that a bomb can only be placed in an empty space.
##### New Insights in 361 Bomb Enemy [Medium]

- Paint Fence: The problem can be solved using a dynamic programming approach, where the number of ways to paint the fence at each position depends on the previous two positions.
- Bomb Enemy: The problem can be solved using a dynamic programming approach, where the number of enemies killed at each position depends on the previous positions.


---
# 7. From 361 Bomb Enemy [Medium] to 174 Dungeon Game [Hard]
> Similarity Distance: 0.6363

### >> Reminder: 361 Bomb Enemy [Medium]
Given a 2D grid, each cell is either a wall 'W', an enemy 'E' or empty '0' (the number zero), return the maximum enemies you can kill using one bomb.
##### Optimal Python solution:
```python

- def maxKilledEnemies(grid):
    if not grid or not grid[0]:
        return 0
    m, n = len(grid), len(grid[0])
    row_hits = 0
    col_hits = [0] * n
    max_kills = 0
    for i in range(m):
        for j in range(n):
            if j == 0 or grid[i][j-1] == 'W':
                row_hits = 0
                k = j
                while k < n and grid[i][k] != 'W':
                    if grid[i][k] == 'E':
                        row_hits += 1
                    k += 1
            if i == 0 or grid[i-1][j] == 'W':
                col_hits[j] = 0
                k = i
                while k < m and grid[k][j] != 'W':
                    if grid[k][j] == 'E':
                        col_hits[j] += 1
                    k += 1
            if grid[i][j] == '0':
                max_kills = max(max_kills, row_hits + col_hits[j])
    return max_kills
```
Given a grid with walls, enemies, and empty cells, find the maximum number of enemies that can be killed using one bomb.
    
### >> 174 Dungeon Game [Hard]
You are trapped in a 2D dungeon and need to find the minimum initial health to escape from the dungeon.
##### Sample input:

- [[-2,-3,3],[-5,-10,1],[10,30,-5]]
##### Sample output:

- 7

##### Questions to ask to clarify requirements:

- Can the dungeon contain negative values?
- What is the size of the dungeon?
- Can the player move diagonally in the dungeon?

##### Optimal Python solution:
```python

- class Solution:
-     def calculateMinimumHP(self, dungeon: List[List[int]]) -> int:
-         m, n = len(dungeon), len(dungeon[0])
-         dp = [[0] * n for _ in range(m)]
-         dp[-1][-1] = max(1, 1 - dungeon[-1][-1])
-         for i in range(m - 2, -1, -1):
-             dp[i][-1] = max(1, dp[i + 1][-1] - dungeon[i][-1])
-         for j in range(n - 2, -1, -1):
-             dp[-1][j] = max(1, dp[-1][j + 1] - dungeon[-1][j])
-         for i in range(m - 2, -1, -1):
-             for j in range(n - 2, -1, -1):
-                 dp[i][j] = max(1, min(dp[i + 1][j], dp[i][j + 1]) - dungeon[i][j])
-         return dp[0][0]
```
##### Time complexity:
O(m * n)
##### Space complexity:
O(m * n)
##### Notes:

- Use dynamic programming to find the minimum initial health
- Initialize the bottom-right cell of the dungeon with max(1, 1 - dungeon[-1][-1])
- Calculate the minimum initial health for the last column and last row
- For each cell, calculate the minimum initial health based on the minimum of the next cell in the same row and the next cell in the same column
- Return the minimum initial health for the top-left cell

- Use dynamic programming to find the minimum initial health
- Initialize the bottom-right cell of the dungeon with max(1, 1 - dungeon[-1][-1])
- Calculate the minimum initial health for the last column and last row
- For each cell, calculate the minimum initial health based on the minimum of the next cell in the same row and the next cell in the same column
- Return the minimum initial health for the top-left cell

- The minimum initial health can be negative
- The minimum initial health for a cell depends on the minimum of the next cell in the same row and the next cell in the same column

- Using a recursive approach
- Using a brute force approach to calculate the minimum initial health for each cell
    
### >> Comparison: 361 Bomb Enemy [Medium] *VS* 174 Dungeon Game [Hard]
> Similarity distance: 0.6363
##### Similarities

- Both questions involve a grid-based game scenario.
- Both questions require finding the maximum number of enemies that can be killed.
- Both questions involve making strategic decisions to maximize the score.
##### Differences

- 361 Bomb Enemy: The player can only place bombs, and the bombs explode in four directions.
- 174 Dungeon Game: The player can move in four directions and can also collect health potions.
- 361 Bomb Enemy: The player can kill multiple enemies with a single bomb.
- 174 Dungeon Game: The player's health decreases over time and can be replenished with potions.
- 361 Bomb Enemy: The player's score is determined by the number of enemies killed.
- 174 Dungeon Game: The player's score is determined by the amount of health remaining at the end.
##### New Insights in 174 Dungeon Game [Hard]

- 361 Bomb Enemy: The optimal strategy involves placing bombs strategically to maximize the number of enemies killed.
- 174 Dungeon Game: The optimal strategy involves planning the path to collect health potions and avoid enemies.
- 361 Bomb Enemy: The player needs to consider the blast radius of the bombs to kill multiple enemies.
- 174 Dungeon Game: The player needs to balance between collecting health potions and progressing towards the exit.


---
# 8. From 361 Bomb Enemy [Medium] to 495 Teemo Attacking [Medium]
> Similarity Distance: 0.6727

### >> Reminder: 361 Bomb Enemy [Medium]
Given a 2D grid, each cell is either a wall 'W', an enemy 'E' or empty '0' (the number zero), return the maximum enemies you can kill using one bomb.
##### Optimal Python solution:
```python

- def maxKilledEnemies(grid):
    if not grid or not grid[0]:
        return 0
    m, n = len(grid), len(grid[0])
    row_hits = 0
    col_hits = [0] * n
    max_kills = 0
    for i in range(m):
        for j in range(n):
            if j == 0 or grid[i][j-1] == 'W':
                row_hits = 0
                k = j
                while k < n and grid[i][k] != 'W':
                    if grid[i][k] == 'E':
                        row_hits += 1
                    k += 1
            if i == 0 or grid[i-1][j] == 'W':
                col_hits[j] = 0
                k = i
                while k < m and grid[k][j] != 'W':
                    if grid[k][j] == 'E':
                        col_hits[j] += 1
                    k += 1
            if grid[i][j] == '0':
                max_kills = max(max_kills, row_hits + col_hits[j])
    return max_kills
```
Given a grid with walls, enemies, and empty cells, find the maximum number of enemies that can be killed using one bomb.
    
### >> 495 Teemo Attacking [Medium]
In LOL world, there is a hero called Teemo and his attacking can make his enemy Ashe be in poisoned condition. Now, given the Teemo's attacking ascending time series towards Ashe and the poisoning time duration per Teemo's attacking, you need to output the total time that Ashe is in poisoned condition.
##### Sample input:
[1,4]
2
##### Sample output:
4

##### Questions to ask to clarify requirements:
What is the maximum length of the time series? Can the time series be empty?

##### Optimal Python solution:
```python
def findPoisonedDuration(timeSeries, duration):
    if not timeSeries:
        return 0
    total_time = 0
    for i in range(1, len(timeSeries)):
        total_time += min(timeSeries[i] - timeSeries[i-1], duration)
    total_time += duration
    return total_time
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Iterate through the time series and calculate the total poisoned time.
2. Add the duration to the total time for the last attack.
3. Return the total time.
None
None
None
    
### >> Comparison: 361 Bomb Enemy [Medium] *VS* 495 Teemo Attacking [Medium]
> Similarity distance: 0.6727
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve a game scenario.
- Both questions require finding the maximum number of enemies that can be killed.
- Both questions involve calculating the total time taken to kill enemies.
##### Differences

- 361 Bomb Enemy involves a grid where 'W' represents a wall and 'E' represents an enemy, while 495 Teemo Attacking involves an array where each element represents the duration of Teemo's attack.
- 361 Bomb Enemy requires placing a bomb at a specific position to kill enemies in its row and column, while 495 Teemo Attacking requires calculating the total time taken to kill enemies by Teemo's attacks.
- 361 Bomb Enemy involves a 2D grid traversal, while 495 Teemo Attacking involves iterating over an array.
- 361 Bomb Enemy has a time complexity of O(m*n), where m and n are the dimensions of the grid, while 495 Teemo Attacking has a time complexity of O(n), where n is the length of the array.
##### New Insights in 495 Teemo Attacking [Medium]

- 361 Bomb Enemy teaches us how to efficiently calculate the maximum number of enemies that can be killed by strategically placing bombs.
- 495 Teemo Attacking teaches us how to calculate the total time taken to kill enemies by considering the duration of Teemo's attacks.


---
# 9. From 361 Bomb Enemy [Medium] to 433 Minimum Genetic Mutation [Medium]
> Similarity Distance: 0.7183

### >> Reminder: 361 Bomb Enemy [Medium]
Given a 2D grid, each cell is either a wall 'W', an enemy 'E' or empty '0' (the number zero), return the maximum enemies you can kill using one bomb.
##### Optimal Python solution:
```python

- def maxKilledEnemies(grid):
    if not grid or not grid[0]:
        return 0
    m, n = len(grid), len(grid[0])
    row_hits = 0
    col_hits = [0] * n
    max_kills = 0
    for i in range(m):
        for j in range(n):
            if j == 0 or grid[i][j-1] == 'W':
                row_hits = 0
                k = j
                while k < n and grid[i][k] != 'W':
                    if grid[i][k] == 'E':
                        row_hits += 1
                    k += 1
            if i == 0 or grid[i-1][j] == 'W':
                col_hits[j] = 0
                k = i
                while k < m and grid[k][j] != 'W':
                    if grid[k][j] == 'E':
                        col_hits[j] += 1
                    k += 1
            if grid[i][j] == '0':
                max_kills = max(max_kills, row_hits + col_hits[j])
    return max_kills
```
Given a grid with walls, enemies, and empty cells, find the maximum number of enemies that can be killed using one bomb.
    
### >> 433 Minimum Genetic Mutation [Medium]
A gene string can be represented by an 8-character long string, with choices from 'A', 'C', 'G', and 'T'. Given two gene strings, start and end, and a list of bank strings, find the minimum number of mutations needed to mutate from start to end. If there is no such a mutation, return -1.
##### Sample input:

- "AACCGGTT"
- "AACCGGTA"
- ["AACCGGTA"]
##### Sample output:
1

##### Questions to ask to clarify requirements:

- Can we only mutate one character at a time?
- Can we use the same gene from the bank multiple times?
- Can we use the start and end genes from the bank?

##### Optimal Python solution:
```python

- from typing import List
- 
- def minMutation(start: str, end: str, bank: List[str]) -> int:
-     if end not in bank:
-         return -1
-     queue = [(start, 0)]
-     visited = set()
-     while queue:
-         gene, steps = queue.pop(0)
-         if gene == end:
-             return steps
-         for i in range(len(gene)):
-             for c in ['A', 'C', 'G', 'T']:
-                 new_gene = gene[:i] + c + gene[i+1:]
-                 if new_gene in bank and new_gene not in visited:
-                     visited.add(new_gene)
-                     queue.append((new_gene, steps+1))
-     return -1
```
##### Time complexity:
O(N^2 * M)
##### Space complexity:
O(N * M)
##### Notes:

- Use BFS to find the minimum number of mutations
- Generate all possible mutations by changing one character at a time
- Keep track of visited genes to avoid revisiting
- Return -1 if there is no mutation from start to end

- Use a set to keep track of visited genes for efficient lookup.
- Use a queue to perform BFS traversal.
- Generate all possible mutations by changing one character at a time.

- Handling the case when there is no mutation from start to end

- Using a recursive approach
    
### >> Comparison: 361 Bomb Enemy [Medium] *VS* 433 Minimum Genetic Mutation [Medium]
> Similarity distance: 0.7183
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve finding the optimal solution to a problem.
- Both questions require some form of traversal or search algorithm.
##### Differences

- 361 Bomb Enemy involves finding the maximum number of enemies that can be killed by placing a bomb in an empty cell of a grid.
- 433 Minimum Genetic Mutation involves finding the minimum number of mutations required to transform one string into another, given a set of valid mutations.
- 361 Bomb Enemy requires a grid traversal algorithm, while 433 Minimum Genetic Mutation requires a graph traversal algorithm.
##### New Insights in 433 Minimum Genetic Mutation [Medium]

- 361 Bomb Enemy teaches us how to optimize the traversal of a grid to find the maximum number of enemies that can be killed.
- 433 Minimum Genetic Mutation teaches us how to use graph traversal algorithms to find the minimum number of mutations required to transform one string into another.

