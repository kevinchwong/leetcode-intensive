
# Leetcode Intensive Tutorial Day 32 
> [Difficulty Score: 18]

> [Version: 20231225_200427]

## Courses overview of the day

- 453 Minimum Moves to Equal Array Elements [Easy]
  - 64 Minimum Path Sum [Medium]
    - 120 Triangle [Medium]
      - 124 Binary Tree Maximum Path Sum [Hard]
    - 63 Unique Paths II [Medium]
      - 576 Out of Boundary Paths [Medium]
      - 62 Unique Paths [Medium]
      - 463 Island Perimeter [Easy]
    - 396 Rotate Function [Medium]

#### Steps by steps

 - [1. From 453 Minimum Moves to Equal Array Elements [Easy] to 64 Minimum Path Sum [Medium]](#1-from-453-minimum-moves-to-equal-array-elements-easy-to-64-minimum-path-sum-medium)

 - [2. From 64 Minimum Path Sum [Medium] to 120 Triangle [Medium]](#2-from-64-minimum-path-sum-medium-to-120-triangle-medium)

 - [3. From 120 Triangle [Medium] to 124 Binary Tree Maximum Path Sum [Hard]](#3-from-120-triangle-medium-to-124-binary-tree-maximum-path-sum-hard)

 - [4. From 64 Minimum Path Sum [Medium] to 63 Unique Paths II [Medium]](#4-from-64-minimum-path-sum-medium-to-63-unique-paths-ii-medium)

 - [5. From 63 Unique Paths II [Medium] to 576 Out of Boundary Paths [Medium]](#5-from-63-unique-paths-ii-medium-to-576-out-of-boundary-paths-medium)

 - [6. From 63 Unique Paths II [Medium] to 62 Unique Paths [Medium]](#6-from-63-unique-paths-ii-medium-to-62-unique-paths-medium)

 - [7. From 63 Unique Paths II [Medium] to 463 Island Perimeter [Easy]](#7-from-63-unique-paths-ii-medium-to-463-island-perimeter-easy)

 - [8. From 64 Minimum Path Sum [Medium] to 396 Rotate Function [Medium]](#8-from-64-minimum-path-sum-medium-to-396-rotate-function-medium)

#### Summary


- 62 Unique Paths : The essence of this problem is to use dynamic programming to calculate the number of unique paths to reach each cell in the grid.
- 124 Binary Tree Maximum Path Sum : Recursion to calculate the maximum path sum for each node.
- 63 Unique Paths II : The essence of this problem is to count the number of unique paths from the top-left corner to the bottom-right corner of a grid with obstacles.
- 120 Triangle : The essence of this problem is to find the minimum path sum from top to bottom by choosing the minimum path sum from the adjacent elements in each row.
- 453 Minimum Moves to Equal Array Elements : The essence of this problem is to find the minimum element in the array and calculate the sum of differences between each element and the minimum element.
- 64 Minimum Path Sum : The essence of this problem is to find the minimum path sum from the top-left corner to the bottom-right corner of a grid.
- 396 Rotate Function : Mathematical formula, optimization
- 576 Out of Boundary Paths : Find the number of paths to move the ball out of the grid boundary using dynamic programming.
- 463 Island Perimeter : Given a grid representing land and water, determine the perimeter of the island.
> Similarity Diameter of these problems: 0.7192


---
# 1. From 453 Minimum Moves to Equal Array Elements [Easy] to 64 Minimum Path Sum [Medium]
> Similarity Distance: 0.5016

### >> 453 Minimum Moves to Equal Array Elements [Easy]
Given a non-empty integer array, find the minimum number of moves required to make all array elements equal, where a move is incrementing n - 1 elements by 1.
##### Sample input:
[1,2,3]
##### Sample output:
3

##### Questions to ask to clarify requirements:
What is the range of the input array? Can the array contain negative numbers?

##### Optimal Python solution:
```python
def minMoves(nums):
    min_num = min(nums)
    return sum(nums) - min_num * len(nums)
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
The minimum number of moves is equal to the sum of differences between each element and the minimum element.
Use the built-in min() function to find the minimum element in the array.
None
None
    
### >> 64 Minimum Path Sum [Medium]
Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right, which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.
##### Sample input:
[
  [1,3,1],
  [1,5,1],
  [4,2,1]
]
##### Sample output:
7

##### Questions to ask to clarify requirements:
Are there any constraints on the size of the grid? Can the grid contain negative numbers?

##### Optimal Python solution:
```python
class Solution:
    def minPathSum(self, grid: List[List[int]]) -> int:
        m, n = len(grid), len(grid[0])
        dp = [[0] * n for _ in range(m)]
        dp[0][0] = grid[0][0]
        for i in range(m):
            for j in range(n):
                if i > 0 and j > 0:
                    dp[i][j] = min(dp[i-1][j], dp[i][j-1]) + grid[i][j]
                elif i > 0:
                    dp[i][j] = dp[i-1][j] + grid[i][j]
                elif j > 0:
                    dp[i][j] = dp[i][j-1] + grid[i][j]
        return dp[m-1][n-1]
```
##### Time complexity:
O(m * n)
##### Space complexity:
O(m * n)
##### Notes:
1. Use dynamic programming to solve the problem.
2. Initialize a 2D array to store the minimum path sum to each cell.
3. Iterate through the grid and update the minimum path sum for each cell based on the previous cells.
4. Return the minimum path sum to the bottom-right corner of the grid.
1. Use a 2D array to store the minimum path sum to each cell.
2. Handle the edge cells in the grid separately.
3. Optimize the space complexity of the solution by using a 1D array instead of a 2D array.
1. Handling the edge cells in the grid.
2. Optimizing the space complexity of the solution.
1. Using recursion to solve the problem.
2. Ignoring the edge cells in the grid.
    
### >> Comparison: 453 Minimum Moves to Equal Array Elements [Easy] *VS* 64 Minimum Path Sum [Medium]
> Similarity distance: 0.5016
##### Similarities

- Both questions involve finding the minimum number of moves or steps to achieve a specific goal.
- Both questions require manipulating arrays or grids.
- Both questions have a dynamic programming solution approach.
##### Differences

- Question 453 involves finding the minimum number of moves to make all elements in an array equal.
- Question 64 involves finding the minimum path sum in a grid from the top-left to the bottom-right corner.
##### New Insights in 64 Minimum Path Sum [Medium]

- Question 453 teaches us how to minimize the difference between array elements by incrementing or decrementing them.
- Question 64 teaches us how to find the minimum path sum in a grid by considering the previous minimum path sums.


---
# 2. From 64 Minimum Path Sum [Medium] to 120 Triangle [Medium]
> Similarity Distance: 0.2646

### >> Reminder: 64 Minimum Path Sum [Medium]
Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right, which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.
##### Optimal Python solution:
```python
class Solution:
    def minPathSum(self, grid: List[List[int]]) -> int:
        m, n = len(grid), len(grid[0])
        dp = [[0] * n for _ in range(m)]
        dp[0][0] = grid[0][0]
        for i in range(m):
            for j in range(n):
                if i > 0 and j > 0:
                    dp[i][j] = min(dp[i-1][j], dp[i][j-1]) + grid[i][j]
                elif i > 0:
                    dp[i][j] = dp[i-1][j] + grid[i][j]
                elif j > 0:
                    dp[i][j] = dp[i][j-1] + grid[i][j]
        return dp[m-1][n-1]
```
The essence of this problem is to find the minimum path sum from the top-left corner to the bottom-right corner of a grid.
    
### >> 120 Triangle [Medium]
Given a triangle array, find the minimum path sum from top to bottom. Each step you may move to adjacent numbers on the row below.
##### Sample input:
[[2],[3,4],[6,5,7],[4,1,8,3]]
##### Sample output:
11

##### Questions to ask to clarify requirements:
Can we modify the input triangle array?

##### Optimal Python solution:
```python
class Solution:
    def minimumTotal(self, triangle: List[List[int]]) -> int:
        n = len(triangle)
        dp = triangle[-1]
        for i in range(n - 2, -1, -1):
            for j in range(i + 1):
                dp[j] = min(dp[j], dp[j + 1]) + triangle[i][j]
        return dp[0]
```
##### Time complexity:
O(n^2)
##### Space complexity:
O(n)
##### Notes:
1. The minimum path sum from top to bottom can be calculated using dynamic programming.
2. Start from the bottom row and calculate the minimum path sum for each element.
3. Use a 1D array to store the minimum path sum for each element in the current row.
4. Update the array by choosing the minimum path sum from the adjacent elements in the next row.
5. Return the minimum path sum for the top element.
Use a 1D array to store the minimum path sum for each element in the current row.
None
None
    
### >> Comparison: 64 Minimum Path Sum [Medium] *VS* 120 Triangle [Medium]
> Similarity distance: 0.2646
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve finding the minimum path sum.
- Both questions involve traversing a grid or triangle structure.
- Both questions require dynamic programming to solve efficiently.
##### Differences

- Question 64 involves a grid structure, while question 120 involves a triangle structure.
- Question 64 allows movement only rightwards or downwards, while question 120 allows movement in multiple directions.
- Question 64 requires finding the minimum path sum, while question 120 requires finding the minimum total from top to bottom.
- Question 64 has a grid of arbitrary size, while question 120 has a fixed triangle structure.
##### New Insights in 120 Triangle [Medium]

- Both questions can be solved using dynamic programming.
- Dynamic programming can be used to efficiently calculate the minimum path sum or minimum total in both questions.
- The optimal substructure property can be applied to both questions to break down the problem into smaller subproblems.
- Memoization or tabulation can be used to store and reuse intermediate results in both questions.


---
# 3. From 120 Triangle [Medium] to 124 Binary Tree Maximum Path Sum [Hard]
> Similarity Distance: 0.4234

### >> Reminder: 120 Triangle [Medium]
Given a triangle array, find the minimum path sum from top to bottom. Each step you may move to adjacent numbers on the row below.
##### Optimal Python solution:
```python
class Solution:
    def minimumTotal(self, triangle: List[List[int]]) -> int:
        n = len(triangle)
        dp = triangle[-1]
        for i in range(n - 2, -1, -1):
            for j in range(i + 1):
                dp[j] = min(dp[j], dp[j + 1]) + triangle[i][j]
        return dp[0]
```
The essence of this problem is to find the minimum path sum from top to bottom by choosing the minimum path sum from the adjacent elements in each row.
    
### >> 124 Binary Tree Maximum Path Sum [Hard]
Given a non-empty binary tree, find the maximum path sum. For this problem, a path is defined as any sequence of nodes from some starting node to any node in the tree along the parent-child connections. The path must contain at least one node and does not need to go through the root.
##### Sample input:
[1,2,3]
##### Sample output:
6

##### Questions to ask to clarify requirements:
Can the tree contain negative values?

##### Optimal Python solution:
```python
def maxPathSum(root):
    max_sum = float('-inf')
    def max_gain(node):
        nonlocal max_sum
        if not node:
            return 0
        left_gain = max(max_gain(node.left), 0)
        right_gain = max(max_gain(node.right), 0)
        current_sum = node.val + left_gain + right_gain
        max_sum = max(max_sum, current_sum)
        return node.val + max(left_gain, right_gain)
    max_gain(root)
    return max_sum
```
##### Time complexity:
O(n)
##### Space complexity:
O(h)
##### Notes:

- Use recursion to calculate the maximum path sum for each node
- Track the maximum path sum seen so far

- Break down the problem into smaller subproblems using recursion.
- Track the maximum path sum seen so far.

- Calculating the maximum path sum for each node using recursion

- Brute force approach of calculating the maximum path sum for each possible path
    
### >> Comparison: 120 Triangle [Medium] *VS* 124 Binary Tree Maximum Path Sum [Hard]
> Similarity distance: 0.4234
##### Similarities

- Both questions involve traversing a tree structure
- Both questions require finding the maximum sum/path
##### Differences

- Question 120 involves a triangle structure, while question 124 involves a binary tree
- Question 120 requires finding the minimum path sum, while question 124 requires finding the maximum path sum
- Question 120 has a medium difficulty level, while question 124 has a hard difficulty level
##### New Insights in 124 Binary Tree Maximum Path Sum [Hard]

- Question 120: The minimum path sum can be found by starting from the bottom and working upwards
- Question 124: The maximum path sum can be found by recursively calculating the maximum sum for each subtree


---
# 4. From 64 Minimum Path Sum [Medium] to 63 Unique Paths II [Medium]
> Similarity Distance: 0.4008

### >> Reminder: 64 Minimum Path Sum [Medium]
Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right, which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.
##### Optimal Python solution:
```python
class Solution:
    def minPathSum(self, grid: List[List[int]]) -> int:
        m, n = len(grid), len(grid[0])
        dp = [[0] * n for _ in range(m)]
        dp[0][0] = grid[0][0]
        for i in range(m):
            for j in range(n):
                if i > 0 and j > 0:
                    dp[i][j] = min(dp[i-1][j], dp[i][j-1]) + grid[i][j]
                elif i > 0:
                    dp[i][j] = dp[i-1][j] + grid[i][j]
                elif j > 0:
                    dp[i][j] = dp[i][j-1] + grid[i][j]
        return dp[m-1][n-1]
```
The essence of this problem is to find the minimum path sum from the top-left corner to the bottom-right corner of a grid.
    
### >> 63 Unique Paths II [Medium]
A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).
The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).
Now consider if some obstacles are added to the grids. How many unique paths would there be?

An obstacle and empty space is marked as 1 and 0 respectively in the grid.

Note: m and n will be at most 100.
##### Sample input:
[
  [0,0,0],
  [0,1,0],
  [0,0,0]
]
##### Sample output:
2

##### Questions to ask to clarify requirements:
Are there any constraints on the size of the grid? What should be returned if there is no path?

##### Optimal Python solution:
```python
class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid: List[List[int]]) -> int:
        m, n = len(obstacleGrid), len(obstacleGrid[0])
        dp = [[0] * n for _ in range(m)]
        dp[0][0] = 1 - obstacleGrid[0][0]
        for i in range(m):
            for j in range(n):
                if obstacleGrid[i][j] == 1:
                    continue
                if i > 0:
                    dp[i][j] += dp[i-1][j]
                if j > 0:
                    dp[i][j] += dp[i][j-1]
        return dp[m-1][n-1]
```
##### Time complexity:
O(m * n)
##### Space complexity:
O(m * n)
##### Notes:
1. Use dynamic programming to solve the problem.
2. Initialize a 2D array to store the number of unique paths to each cell.
3. Iterate through the grid and update the number of unique paths for each cell based on the previous cells.
4. Return the number of unique paths to the bottom-right corner of the grid.
1. Use a 2D array to store the number of unique paths to each cell.
2. Handle obstacles in the grid by skipping them in the iteration.
3. Optimize the space complexity of the solution by using a 1D array instead of a 2D array.
1. Handling obstacles in the grid.
2. Optimizing the space complexity of the solution.
1. Using recursion to solve the problem.
2. Ignoring the obstacle cells in the grid.
    
### >> Comparison: 64 Minimum Path Sum [Medium] *VS* 63 Unique Paths II [Medium]
> Similarity distance: 0.4008
##### Similarities

- Both questions are related to finding paths in a grid.
- Both questions have a constraint on moving only rightwards and downwards.
- Both questions require finding the minimum path or counting the number of unique paths.
##### Differences

- Minimum Path Sum focuses on finding the minimum sum of numbers along a path.
- Unique Paths II focuses on finding the number of unique paths with obstacles in the grid.
##### New Insights in 63 Unique Paths II [Medium]

- Minimum Path Sum can be solved using dynamic programming to find the optimal substructure.
- Unique Paths II can be solved using dynamic programming with an additional check for obstacles.


---
# 5. From 63 Unique Paths II [Medium] to 576 Out of Boundary Paths [Medium]
> Similarity Distance: 0.3594

### >> Reminder: 63 Unique Paths II [Medium]
A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).
The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).
Now consider if some obstacles are added to the grids. How many unique paths would there be?

An obstacle and empty space is marked as 1 and 0 respectively in the grid.

Note: m and n will be at most 100.
##### Optimal Python solution:
```python
class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid: List[List[int]]) -> int:
        m, n = len(obstacleGrid), len(obstacleGrid[0])
        dp = [[0] * n for _ in range(m)]
        dp[0][0] = 1 - obstacleGrid[0][0]
        for i in range(m):
            for j in range(n):
                if obstacleGrid[i][j] == 1:
                    continue
                if i > 0:
                    dp[i][j] += dp[i-1][j]
                if j > 0:
                    dp[i][j] += dp[i][j-1]
        return dp[m-1][n-1]
```
The essence of this problem is to count the number of unique paths from the top-left corner to the bottom-right corner of a grid with obstacles.
    
### >> 576 Out of Boundary Paths [Medium]
There is an m x n grid with a ball. The ball is initially at the position [startRow, startColumn]. You are allowed to move the ball to one of the four adjacent cells in the grid (possibly out of the grid crossing the grid boundary). You can apply at most maxMove moves to the ball. Return the number of paths to move the ball out of the grid boundary. Since the answer can be very large, return it modulo 109 + 7.
##### Sample input:
m = 2, n = 2, maxMove = 2, startRow = 0, startColumn = 0
##### Sample output:
6

##### Questions to ask to clarify requirements:

- What is the maximum number of moves allowed?
- What is the range of the grid?
- Can the ball move diagonally?
- What is the modulo value?

##### Optimal Python solution:
```python
def findPaths(m, n, maxMove, startRow, startColumn):
    MOD = 10 ** 9 + 7
    dp = [[[-1] * (maxMove + 1) for _ in range(n)] for _ in range(m)]

    def dfs(i, j, move):
        if i < 0 or i >= m or j < 0 or j >= n:
            return 1
        if move == 0:
            return 0
        if dp[i][j][move] != -1:
            return dp[i][j][move]
        dp[i][j][move] = (dfs(i - 1, j, move - 1) + dfs(i + 1, j, move - 1) + dfs(i, j - 1, move - 1) + dfs(i, j + 1, move - 1)) % MOD
        return dp[i][j][move]

    return dfs(startRow, startColumn, maxMove)
```
##### Time complexity:
O(m * n * maxMove)
##### Space complexity:
O(m * n * maxMove)
##### Notes:

- Use dynamic programming to store the number of paths for each cell and number of moves.
- Recursively calculate the number of paths for each cell using the adjacent cells.

- Use memoization to avoid redundant calculations.
- Use modular arithmetic to handle large numbers.

- None

- None
    
### >> Comparison: 63 Unique Paths II [Medium] *VS* 576 Out of Boundary Paths [Medium]
> Similarity distance: 0.3594
##### Similarities

- Both questions are related to finding paths in a grid.
- Both questions have a medium difficulty level.
##### Differences

- Unique Paths II deals with obstacles in the grid, while Out of Boundary Paths does not have obstacles.
- Unique Paths II requires counting the number of unique paths, while Out of Boundary Paths requires finding the number of paths that go out of the boundary.
- Unique Paths II allows movement only right and down, while Out of Boundary Paths allows movement in all four directions.
##### New Insights in 576 Out of Boundary Paths [Medium]

- Unique Paths II can be solved using dynamic programming to efficiently count the number of unique paths.
- Out of Boundary Paths can be solved using dynamic programming to efficiently find the number of paths that go out of the boundary.


---
# 6. From 63 Unique Paths II [Medium] to 62 Unique Paths [Medium]
> Similarity Distance: 0.4693

### >> Reminder: 63 Unique Paths II [Medium]
A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).
The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).
Now consider if some obstacles are added to the grids. How many unique paths would there be?

An obstacle and empty space is marked as 1 and 0 respectively in the grid.

Note: m and n will be at most 100.
##### Optimal Python solution:
```python
class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid: List[List[int]]) -> int:
        m, n = len(obstacleGrid), len(obstacleGrid[0])
        dp = [[0] * n for _ in range(m)]
        dp[0][0] = 1 - obstacleGrid[0][0]
        for i in range(m):
            for j in range(n):
                if obstacleGrid[i][j] == 1:
                    continue
                if i > 0:
                    dp[i][j] += dp[i-1][j]
                if j > 0:
                    dp[i][j] += dp[i][j-1]
        return dp[m-1][n-1]
```
The essence of this problem is to count the number of unique paths from the top-left corner to the bottom-right corner of a grid with obstacles.
    
### >> 62 Unique Paths [Medium]
A robot is located at the top-left corner of a m x n grid. The robot can only move either down or right at any point in time. How many unique paths are there to reach the bottom-right corner?
##### Sample input:
m = 3, n = 7
##### Sample output:
28

##### Questions to ask to clarify requirements:
1. Can the grid have negative dimensions? 2. Can the robot move diagonally?

##### Optimal Python solution:
```python
def uniquePaths(m, n):
    dp = [[1] * n] + [[1] + [0] * (n - 1) for _ in range(m - 1)]
    for i in range(1, m):
        for j in range(1, n):
            dp[i][j] = dp[i - 1][j] + dp[i][j - 1]
    return dp[-1][-1]
```
##### Time complexity:
O(m * n)
##### Space complexity:
O(m * n)
##### Notes:
1. Use dynamic programming to build a 2D grid. 2. Each cell represents the number of unique paths to reach that cell. 3. The number of unique paths to reach a cell is the sum of the number of unique paths to reach the cell above and the cell to the left.
1. Break down the problem into smaller subproblems. 2. Use dynamic programming to solve problems with overlapping subproblems.
1. Initializing the first row and column of the grid. 2. Handling edge cases when m or n is 0.
1. Using recursion. 2. Using brute force.
    
### >> Comparison: 63 Unique Paths II [Medium] *VS* 62 Unique Paths [Medium]
> Similarity distance: 0.4693
##### Similarities

- Both questions are related to finding the number of unique paths in a grid.
- Both questions have a grid with obstacles that cannot be crossed.
##### Differences

- Question 63 (Unique Paths II) allows for obstacles in the grid, while question 62 (Unique Paths) does not have any obstacles.
- In question 63, the obstacles are represented by '1' in the grid, while in question 62, the grid is obstacle-free.
- The goal in question 63 is to find the number of unique paths from the top-left corner to the bottom-right corner, considering the obstacles. In question 62, the goal is to find the number of unique paths from the top-left corner to the bottom-right corner without any obstacles.
##### New Insights in 62 Unique Paths [Medium]

- Question 63 introduces the concept of obstacles in the grid, which adds complexity to the problem.
- Both questions can be solved using dynamic programming techniques, but the approach for handling obstacles in question 63 requires additional considerations.


---
# 7. From 63 Unique Paths II [Medium] to 463 Island Perimeter [Easy]
> Similarity Distance: 0.5372

### >> Reminder: 63 Unique Paths II [Medium]
A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).
The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).
Now consider if some obstacles are added to the grids. How many unique paths would there be?

An obstacle and empty space is marked as 1 and 0 respectively in the grid.

Note: m and n will be at most 100.
##### Optimal Python solution:
```python
class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid: List[List[int]]) -> int:
        m, n = len(obstacleGrid), len(obstacleGrid[0])
        dp = [[0] * n for _ in range(m)]
        dp[0][0] = 1 - obstacleGrid[0][0]
        for i in range(m):
            for j in range(n):
                if obstacleGrid[i][j] == 1:
                    continue
                if i > 0:
                    dp[i][j] += dp[i-1][j]
                if j > 0:
                    dp[i][j] += dp[i][j-1]
        return dp[m-1][n-1]
```
The essence of this problem is to count the number of unique paths from the top-left corner to the bottom-right corner of a grid with obstacles.
    
### >> 463 Island Perimeter [Easy]
You are given a map in form of a two-dimensional integer grid where 1 represents land and 0 represents water. Grid cells are connected horizontally/vertically (not diagonally). The grid is completely surrounded by water, and there is exactly one island (i.e., one or more connected land cells). The island doesn't have "lakes" (water inside that isn't connected to the water around the island). One cell is a square with side length 1. The grid is rectangular, width and height don't exceed 100. Determine the perimeter of the island.
##### Sample input:
[[0,1,0,0],[1,1,1,0],[0,1,0,0],[1,1,0,0]]
##### Sample output:
16

##### Questions to ask to clarify requirements:

- What is the maximum size of the grid?
- Can the grid be empty?
- Can there be multiple islands in the grid?

##### Optimal Python solution:
```python
def islandPerimeter(grid):
    if not grid:
        return 0
    perimeter = 0
    rows, cols = len(grid), len(grid[0])
    for i in range(rows):
        for j in range(cols):
            if grid[i][j] == 1:
                perimeter += 4
                if i > 0 and grid[i-1][j] == 1:
                    perimeter -= 2
                if j > 0 and grid[i][j-1] == 1:
                    perimeter -= 2
    return perimeter
```
##### Time complexity:
O(m*n)
##### Space complexity:
O(1)
##### Notes:

- Iterate over each cell in the grid
- If the cell is land, add 4 to the perimeter
- If the cell is connected to another land cell, subtract 2 from the perimeter

- Use nested loops to iterate over each cell in the grid
- Use conditional statements to check if a cell is land or water

- Handling edge cases where the grid is empty or has no land cells

- Using recursion to solve the problem
    
### >> Comparison: 63 Unique Paths II [Medium] *VS* 463 Island Perimeter [Easy]
> Similarity distance: 0.5372
##### Similarities

- Both questions involve finding paths or perimeters in a grid.
- Both questions have constraints on the grid elements.
##### Differences

- Unique Paths II involves finding the number of unique paths from the top-left to the bottom-right of a grid, considering obstacles.
- Island Perimeter involves finding the perimeter of an island in a grid, where 1 represents land and 0 represents water.
##### New Insights in 463 Island Perimeter [Easy]

- Unique Paths II introduces the concept of dynamic programming to solve the problem efficiently.
- Island Perimeter requires counting the number of neighboring water cells for each land cell to calculate the perimeter.


---
# 8. From 64 Minimum Path Sum [Medium] to 396 Rotate Function [Medium]
> Similarity Distance: 0.5156

### >> Reminder: 64 Minimum Path Sum [Medium]
Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right, which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.
##### Optimal Python solution:
```python
class Solution:
    def minPathSum(self, grid: List[List[int]]) -> int:
        m, n = len(grid), len(grid[0])
        dp = [[0] * n for _ in range(m)]
        dp[0][0] = grid[0][0]
        for i in range(m):
            for j in range(n):
                if i > 0 and j > 0:
                    dp[i][j] = min(dp[i-1][j], dp[i][j-1]) + grid[i][j]
                elif i > 0:
                    dp[i][j] = dp[i-1][j] + grid[i][j]
                elif j > 0:
                    dp[i][j] = dp[i][j-1] + grid[i][j]
        return dp[m-1][n-1]
```
The essence of this problem is to find the minimum path sum from the top-left corner to the bottom-right corner of a grid.
    
### >> 396 Rotate Function [Medium]
Given an array of integers A and an integer k, find the maximum value of F(i) where F(i) = (A[0] * 0) + (A[1] * 1) + ... + (A[n-1] * (n-1)) and n is the length of A.
##### Sample input:
[4, 3, 2, 6]
##### Sample output:
26

##### Questions to ask to clarify requirements:
Can the array contain negative numbers? What is the maximum length of the array?

##### Optimal Python solution:
```python
def maxRotateFunction(A: List[int]) -> int:
    n = len(A)
    sum_A = sum(A)
    F = sum(i * A[i] for i in range(n))
    max_F = F
    for i in range(1, n):
        F += sum_A - n * A[n - i]
        max_F = max(max_F, F)
    return max_F
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
Use the formula F(i) = F(i-1) + sum(A) - n * A[n-i].
Use the sum of the array to optimize the calculation.
The maximum value can be negative.
Brute force approach to calculate F(i) for each rotation.
    
### >> Comparison: 64 Minimum Path Sum [Medium] *VS* 396 Rotate Function [Medium]
> Similarity distance: 0.5156
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve manipulating arrays.
- Both questions require finding the minimum/maximum value in a sequence.
- Both questions involve dynamic programming.
##### Differences

- Minimum Path Sum involves finding the minimum sum of a path in a grid, while Rotate Function involves finding the maximum value of a function.
- Minimum Path Sum involves moving only rightwards or downwards in the grid, while Rotate Function involves rotating an array and calculating the function value.
- Minimum Path Sum has a grid as input, while Rotate Function has an array as input.
- Minimum Path Sum has a single optimal solution, while Rotate Function may have multiple optimal solutions.
##### New Insights in 396 Rotate Function [Medium]

- Minimum Path Sum teaches us how to use dynamic programming to find the minimum sum of a path in a grid.
- Rotate Function teaches us how to calculate the maximum value of a function by rotating an array.
- Both questions provide insights into solving optimization problems using different techniques.

