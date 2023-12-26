
# Leetcode Intensive Tutorial Day 44 
> [Difficulty Score: 22]

> [Version: 20231226_040350]

> [Including this day, you had studied : 367 leetcode problems]


## Courses overview of the day

- 200 Number of Islands [Medium]
  - 547 Friend Circles [Medium]
    - 508 Most Frequent Subtree Sum [Medium]
      - 113 Path Sum II [Medium]
        - 437 Path Sum III [Medium]
          - 129 Sum Root to Leaf Numbers [Medium]
          - 302 Smallest Rectangle Enclosing Black Pixels [Hard]
          - 133 Clone Graph [Medium]
          - 130 Surrounded Regions [Medium]
  - 417 Pacific Atlantic Water Flow [Medium]

#### Step by step

 - [1. From 200 Number of Islands [Medium] to 547 Friend Circles [Medium]](#1-from-200-number-of-islands-medium-to-547-friend-circles-medium))

 - [2. From 547 Friend Circles [Medium] to 508 Most Frequent Subtree Sum [Medium]](#2-from-547-friend-circles-medium-to-508-most-frequent-subtree-sum-medium))

 - [3. From 508 Most Frequent Subtree Sum [Medium] to 113 Path Sum II [Medium]](#3-from-508-most-frequent-subtree-sum-medium-to-113-path-sum-ii-medium))

 - [4. From 113 Path Sum II [Medium] to 437 Path Sum III [Medium]](#4-from-113-path-sum-ii-medium-to-437-path-sum-iii-medium))

 - [5. From 437 Path Sum III [Medium] to 129 Sum Root to Leaf Numbers [Medium]](#5-from-437-path-sum-iii-medium-to-129-sum-root-to-leaf-numbers-medium))

 - [6. From 437 Path Sum III [Medium] to 302 Smallest Rectangle Enclosing Black Pixels [Hard]](#6-from-437-path-sum-iii-medium-to-302-smallest-rectangle-enclosing-black-pixels-hard))

 - [7. From 437 Path Sum III [Medium] to 133 Clone Graph [Medium]](#7-from-437-path-sum-iii-medium-to-133-clone-graph-medium))

 - [8. From 437 Path Sum III [Medium] to 130 Surrounded Regions [Medium]](#8-from-437-path-sum-iii-medium-to-130-surrounded-regions-medium))

 - [9. From 200 Number of Islands [Medium] to 417 Pacific Atlantic Water Flow [Medium]](#9-from-200-number-of-islands-medium-to-417-pacific-atlantic-water-flow-medium))

    

#### Summary


- 200 Number of Islands : The essence of this problem is to perform a depth-first search (DFS) on the grid and count the number of connected components.
- 302 Smallest Rectangle Enclosing Black Pixels : The essence of the problem is to find the minimum area of a rectangle that encloses all black pixels in the image.
- 417 Pacific Atlantic Water Flow : Given a matrix representing the height of each cell, find the cells that can flow to both the Pacific and Atlantic oceans.
- 133 Clone Graph : The essence of the problem is to clone a connected undirected graph using depth-first search (DFS) and recursion.
- 437 Path Sum III : The essence of this problem is to find paths in a binary tree that sum to a given value.
- 129 Sum Root to Leaf Numbers : The essence of the problem is to find the sum of all root-to-leaf numbers in a binary tree.
- 113 Path Sum II : Given a binary tree and a sum, find all root-to-leaf paths where each path's sum equals the given sum.
- 547 Friend Circles : Finding connected components in a graph using DFS
- 130 Surrounded Regions : The essence of the problem is to capture all regions surrounded by 'X' in a 2D board by flipping all 'O's into 'X's.
- 508 Most Frequent Subtree Sum : The most frequent subtree sum is the sum of all the node values formed by the subtree rooted at a node.
> Similarity Diameter of these problems: 0.7464


---
# 1. From 200 Number of Islands [Medium] to 547 Friend Circles [Medium]
> Similarity Distance: 0.4451

### >> 200 Number of Islands [Medium]
Given a 2d grid map of '1's (land) and '0's (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.
##### Sample input:
[['1','1','1','1','0'],['1','1','0','1','0'],['1','1','0','0','0'],['0','0','0','0','0']]
##### Sample output:
1

##### Questions to ask to clarify requirements:
None

##### Optimal Python solution:
```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        if not grid:
            return 0
        m, n = len(grid), len(grid[0])
        count = 0
        for i in range(m):
            for j in range(n):
                if grid[i][j] == '1':
                    self.dfs(grid, i, j)
                    count += 1
        return count

    def dfs(self, grid, i, j):
        if i < 0 or i >= len(grid) or j < 0 or j >= len(grid[0]) or grid[i][j] != '1':
            return
        grid[i][j] = '0'
        self.dfs(grid, i + 1, j)
        self.dfs(grid, i - 1, j)
        self.dfs(grid, i, j + 1)
        self.dfs(grid, i, j - 1)
```
##### Time complexity:
O(m * n)
##### Space complexity:
O(m * n)
##### Notes:
Use DFS to traverse the grid and mark visited islands as '0'. Count the number of times DFS is called.
None
None
None
    
### >> 547 Friend Circles [Medium]
There are N students in a class. Some of them are friends, while some are not. Their friendship is transitive in nature. You are given a N*N matrix M representing the friend relationship between students in the class. If M[i][j] = 1, then the ith and jth students are direct friends with each other, otherwise not. You need to count the number of friend circles among all the students.
##### Sample input:
[[1,1,0],[1,1,0],[0,0,1]]
##### Sample output:
2

##### Questions to ask to clarify requirements:

- What is the maximum number of students in the class?
- Can there be any students who are not friends with anyone?

##### Optimal Python solution:
```python
class Solution:
    def findCircleNum(self, M: List[List[int]]) -> int:
        def dfs(i):
            for j in range(len(M)):
                if M[i][j] == 1 and j not in visited:
                    visited.add(j)
                    dfs(j)
        visited = set()
        count = 0
        for i in range(len(M)):
            if i not in visited:
                dfs(i)
                count += 1
        return count
```
##### Time complexity:
O(N^2)
##### Space complexity:
O(N)
##### Notes:

- Use depth-first search (DFS) to find connected components
- Count the number of times DFS is called to find the number of friend circles

- Use a set to keep track of visited students during DFS

- Identifying connected components using DFS

- Using breadth-first search (BFS) instead of DFS
    
### >> Comparison: 200 Number of Islands [Medium] *VS* 547 Friend Circles [Medium]
> Similarity distance: 0.4451
##### Similarities

- Both questions involve finding connected components in a graph.
- Both questions can be solved using depth-first search (DFS) or breadth-first search (BFS).
##### Differences

- Number of Islands focuses on finding the number of distinct islands in a 2D grid, where an island is a group of connected '1' cells.
- Friend Circles focuses on finding the number of distinct friend circles in a given matrix, where a friend circle is a group of people who are directly or indirectly connected.
##### New Insights in 547 Friend Circles [Medium]

- Number of Islands: The solution involves iterating through the grid and performing DFS or BFS to mark visited cells and count the number of islands.
- Friend Circles: The solution involves iterating through the matrix and performing DFS or BFS to find connected components and count the number of friend circles.


---
# 2. From 547 Friend Circles [Medium] to 508 Most Frequent Subtree Sum [Medium]
> Similarity Distance: 0.4755

### >> Reminder: 547 Friend Circles [Medium]
There are N students in a class. Some of them are friends, while some are not. Their friendship is transitive in nature. You are given a N*N matrix M representing the friend relationship between students in the class. If M[i][j] = 1, then the ith and jth students are direct friends with each other, otherwise not. You need to count the number of friend circles among all the students.
##### Optimal Python solution:
```python
class Solution:
    def findCircleNum(self, M: List[List[int]]) -> int:
        def dfs(i):
            for j in range(len(M)):
                if M[i][j] == 1 and j not in visited:
                    visited.add(j)
                    dfs(j)
        visited = set()
        count = 0
        for i in range(len(M)):
            if i not in visited:
                dfs(i)
                count += 1
        return count
```
Finding connected components in a graph using DFS
    
### >> 508 Most Frequent Subtree Sum [Medium]
Given the root of a tree, you are asked to find the most frequent subtree sum. The subtree sum of a node is defined as the sum of all the node values formed by the subtree rooted at that node (including the node itself). So what is the most frequent subtree sum value? If there is a tie, return all the values with the highest frequency in any order.
##### Sample input:
[5,2,-3]

##### Sample output:
[2,-3,4]


##### Questions to ask to clarify requirements:
What is the format of the tree input? Can the tree be empty?

##### Optimal Python solution:
```python
class Solution:
    def findFrequentTreeSum(self, root: TreeNode) -> List[int]:
        def dfs(node):
            if not node:
                return 0
            s = node.val + dfs(node.left) + dfs(node.right)
            count[s] += 1
            return s
        count = collections.Counter()
        dfs(root)
        max_count = max(count.values())
        return [s for s, c in count.items() if c == max_count]

```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. The subtree sum of a node is the sum of all the node values formed by the subtree rooted at that node.
2. Use a depth-first search (DFS) to calculate the subtree sum for each node.
3. Use a counter to keep track of the frequency of each subtree sum.
4. Find the maximum frequency and return all the subtree sums with that frequency.
1. Use recursion to implement the depth-first search (DFS).
2. Use a counter to count the frequency of each subtree sum.
3. Use the max() function to find the maximum frequency.
4. Use a list comprehension to filter the subtree sums with the maximum frequency.
None
None
    
### >> Comparison: 547 Friend Circles [Medium] *VS* 508 Most Frequent Subtree Sum [Medium]
> Similarity distance: 0.4755
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve analyzing relationships between elements in a data structure.
- Both questions require traversing a graph or tree structure.
- Both questions involve counting or identifying certain patterns or properties.
##### Differences

- 547 Friend Circles involves finding the number of connected components in an undirected graph.
- 508 Most Frequent Subtree Sum involves finding the most frequent sum of subtrees in a binary tree.
- 547 Friend Circles uses a graph representation, while 508 Most Frequent Subtree Sum uses a tree representation.
- 547 Friend Circles requires using a depth-first search (DFS) algorithm, while 508 Most Frequent Subtree Sum can be solved using a depth-first search or breadth-first search (BFS) algorithm.
##### New Insights in 508 Most Frequent Subtree Sum [Medium]

- 547 Friend Circles teaches us how to identify connected components in an undirected graph.
- 508 Most Frequent Subtree Sum teaches us how to calculate the sum of subtrees in a binary tree and find the most frequent sum.


---
# 3. From 508 Most Frequent Subtree Sum [Medium] to 113 Path Sum II [Medium]
> Similarity Distance: 0.4476

### >> Reminder: 508 Most Frequent Subtree Sum [Medium]
Given the root of a tree, you are asked to find the most frequent subtree sum. The subtree sum of a node is defined as the sum of all the node values formed by the subtree rooted at that node (including the node itself). So what is the most frequent subtree sum value? If there is a tie, return all the values with the highest frequency in any order.
##### Optimal Python solution:
```python
class Solution:
    def findFrequentTreeSum(self, root: TreeNode) -> List[int]:
        def dfs(node):
            if not node:
                return 0
            s = node.val + dfs(node.left) + dfs(node.right)
            count[s] += 1
            return s
        count = collections.Counter()
        dfs(root)
        max_count = max(count.values())
        return [s for s, c in count.items() if c == max_count]

```
The most frequent subtree sum is the sum of all the node values formed by the subtree rooted at a node.
    
### >> 113 Path Sum II [Medium]
Given a binary tree and a sum, find all root-to-leaf paths where each path's sum equals the given sum.
##### Sample input:
[5,4,8,11,null,13,4,7,2,null,null,5,1]
22
##### Sample output:
[[5,4,11,2],[5,8,4,5]]

##### Questions to ask to clarify requirements:
What should be returned if the binary tree is empty? Can the binary tree have negative values?

##### Optimal Python solution:
```python
class Solution:
    def pathSum(self, root: TreeNode, sum: int) -> List[List[int]]:
        if not root:
            return []
        res = []
        self.dfs(root, sum, [], res)
        return res

    def dfs(self, node, target, path, res):
        if not node:
            return
        if not node.left and not node.right and node.val == target:
            res.append(path + [node.val])
        self.dfs(node.left, target - node.val, path + [node.val], res)
        self.dfs(node.right, target - node.val, path + [node.val], res)
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use depth-first search (DFS) to traverse the binary tree.
2. Keep track of the current path and the remaining sum at each node.
3. Append the current path to the result if the node is a leaf and the remaining sum is 0.
1. Use a helper function to perform the DFS.
2. Pass the current path as a parameter to avoid unnecessary backtracking.
3. Use a list to store the result instead of a global variable.
1. Be careful with the base case when the node is None.
2. Append the current path to the result only when the node is a leaf and the remaining sum is 0.
Avoid using a global variable to store the result.
Avoid unnecessary backtracking by passing the current path as a parameter.
    
### >> Comparison: 508 Most Frequent Subtree Sum [Medium] *VS* 113 Path Sum II [Medium]
> Similarity distance: 0.4476
##### Similarities

- Both questions are related to tree traversal and involve calculating the sum of values in subtrees.
- Both questions have a medium difficulty level on LeetCode.
##### Differences

- 508 Most Frequent Subtree Sum: This question requires finding the most frequent subtree sum in a given binary tree.
- 113 Path Sum II: This question requires finding all root-to-leaf paths in a binary tree that sum up to a given target value.
##### New Insights in 113 Path Sum II [Medium]

- 508 Most Frequent Subtree Sum: The new insight in this question is to use a recursive approach to calculate the subtree sums and keep track of their frequencies.
- 113 Path Sum II: The new insight in this question is to use backtracking to explore all possible paths from the root to the leaves and check if their sum matches the target value.


---
# 4. From 113 Path Sum II [Medium] to 437 Path Sum III [Medium]
> Similarity Distance: 0.3433

### >> Reminder: 113 Path Sum II [Medium]
Given a binary tree and a sum, find all root-to-leaf paths where each path's sum equals the given sum.
##### Optimal Python solution:
```python
class Solution:
    def pathSum(self, root: TreeNode, sum: int) -> List[List[int]]:
        if not root:
            return []
        res = []
        self.dfs(root, sum, [], res)
        return res

    def dfs(self, node, target, path, res):
        if not node:
            return
        if not node.left and not node.right and node.val == target:
            res.append(path + [node.val])
        self.dfs(node.left, target - node.val, path + [node.val], res)
        self.dfs(node.right, target - node.val, path + [node.val], res)
```
Given a binary tree and a sum, find all root-to-leaf paths where each path's sum equals the given sum.
    
### >> 437 Path Sum III [Medium]
You are given a binary tree in which each node contains an integer value. Find the number of paths that sum to a given value. The path does not need to start or end at the root or a leaf, but it must go downwards (traveling only from parent nodes to child nodes).
##### Sample input:
[10,5,-3,3,2,null,11,3,-2,null,1]
##### Sample output:
3

##### Questions to ask to clarify requirements:
Can the path start or end at any node? Can the path go in any direction (upwards or downwards)?

##### Optimal Python solution:
```python
class Solution:
    def pathSum(self, root: TreeNode, sum: int) -> int:
        if not root:
            return 0
        return self.dfs(root, sum) + self.pathSum(root.left, sum) + self.pathSum(root.right, sum)

    def dfs(self, node, target):
        if not node:
            return 0
        return int(node.val == target) + self.dfs(node.left, target - node.val) + self.dfs(node.right, target - node.val)
```
##### Time complexity:
O(n^2)
##### Space complexity:
O(n)
##### Notes:
1. Use depth-first search (DFS) to traverse the tree.
2. Keep track of the current sum and the number of paths found.
3. Recursively check each node and its children to find paths that sum to the target value.
4. Return the total number of paths found.
Use a recursive approach to traverse the tree and keep track of the current sum and the number of paths found.
The path does not need to start or end at the root or a leaf.
Avoid using a brute force approach that checks all possible paths.
    
### >> Comparison: 113 Path Sum II [Medium] *VS* 437 Path Sum III [Medium]
> Similarity distance: 0.3433
##### Similarities

- Both questions are related to finding paths in a binary tree that sum up to a given target value.
- Both questions have a similar structure and require traversing the binary tree to find the paths.
##### Differences

- 113 Path Sum II requires finding all the paths that sum up to the target value, while 437 Path Sum III requires finding the number of paths that sum up to the target value.
- 113 Path Sum II returns the actual paths as a result, while 437 Path Sum III returns the count of paths as a result.
- 113 Path Sum II allows paths to start and end at any node, while 437 Path Sum III requires paths to start at the root node.
- 113 Path Sum II has a time complexity of O(n^2) in the worst case, while 437 Path Sum III has a time complexity of O(n^2) in the average case.
##### New Insights in 437 Path Sum III [Medium]

- Both questions require a recursive approach to traverse the binary tree and keep track of the current path and its sum.
- Both questions can be solved using depth-first search (DFS) technique.
- Both questions can benefit from using a hashmap to store the running sum and its frequency.
- Both questions can be optimized by using memoization to avoid redundant calculations.


---
# 5. From 437 Path Sum III [Medium] to 129 Sum Root to Leaf Numbers [Medium]
> Similarity Distance: 0.3649

### >> Reminder: 437 Path Sum III [Medium]
You are given a binary tree in which each node contains an integer value. Find the number of paths that sum to a given value. The path does not need to start or end at the root or a leaf, but it must go downwards (traveling only from parent nodes to child nodes).
##### Optimal Python solution:
```python
class Solution:
    def pathSum(self, root: TreeNode, sum: int) -> int:
        if not root:
            return 0
        return self.dfs(root, sum) + self.pathSum(root.left, sum) + self.pathSum(root.right, sum)

    def dfs(self, node, target):
        if not node:
            return 0
        return int(node.val == target) + self.dfs(node.left, target - node.val) + self.dfs(node.right, target - node.val)
```
The essence of this problem is to find paths in a binary tree that sum to a given value.
    
### >> 129 Sum Root to Leaf Numbers [Medium]
Given a binary tree containing digits from 0-9 only, each root-to-leaf path could represent a number. Find the total sum of all root-to-leaf numbers.
##### Sample input:
[1,2,3]
##### Sample output:
25

##### Questions to ask to clarify requirements:
1. Can the binary tree be empty?
2. Can the binary tree have negative numbers?
3. Can the binary tree have more than one root-to-leaf path?

##### Optimal Python solution:
```python
class Solution:
    def sumNumbers(self, root: TreeNode) -> int:
        def dfs(node, curr_sum):
            if not node:
                return 0
            curr_sum = curr_sum * 10 + node.val
            if not node.left and not node.right:
                return curr_sum
            return dfs(node.left, curr_sum) + dfs(node.right, curr_sum)
        return dfs(root, 0)
```
##### Time complexity:
O(n)
##### Space complexity:
O(h)
##### Notes:
1. Use depth-first search (DFS) to traverse the binary tree.
2. Keep track of the current sum of the root-to-leaf path.
3. Return the sum of all root-to-leaf numbers.
1. Use recursion to implement depth-first search (DFS).
2. Handle the base case when the node is None.
3. Use a helper function to perform the DFS traversal.
1. Handling the case when the binary tree is empty.
2. Handling the case when the binary tree has negative numbers.
1. Avoid using breadth-first search (BFS) as it is not necessary for this problem.
2. Avoid using a global variable to store the sum.
    
### >> Comparison: 437 Path Sum III [Medium] *VS* 129 Sum Root to Leaf Numbers [Medium]
> Similarity distance: 0.3649
##### Similarities

- Both questions are medium difficulty level.
- Both questions involve binary trees.
- Both questions require calculating sums.
- Both questions involve traversing the tree.
- Both questions require finding paths from root to leaf nodes.
##### Differences

- Question 437 involves finding the number of paths in the tree that sum up to a given target, while question 129 involves finding the sum of all root-to-leaf numbers in the tree.
- Question 437 allows paths to start and end at any node, while question 129 only considers paths from root to leaf nodes.
- Question 437 requires counting the number of paths, while question 129 requires calculating the sum of the numbers.
- Question 437 can have negative numbers in the tree, while question 129 assumes non-negative numbers.
##### New Insights in 129 Sum Root to Leaf Numbers [Medium]

- Question 437 introduces the concept of counting paths in a binary tree that sum up to a target value.
- Question 129 introduces the concept of calculating the sum of all root-to-leaf numbers in a binary tree.
- Both questions provide insights into tree traversal and recursive algorithms.


---
# 6. From 437 Path Sum III [Medium] to 302 Smallest Rectangle Enclosing Black Pixels [Hard]
> Similarity Distance: 0.5319

### >> Reminder: 437 Path Sum III [Medium]
You are given a binary tree in which each node contains an integer value. Find the number of paths that sum to a given value. The path does not need to start or end at the root or a leaf, but it must go downwards (traveling only from parent nodes to child nodes).
##### Optimal Python solution:
```python
class Solution:
    def pathSum(self, root: TreeNode, sum: int) -> int:
        if not root:
            return 0
        return self.dfs(root, sum) + self.pathSum(root.left, sum) + self.pathSum(root.right, sum)

    def dfs(self, node, target):
        if not node:
            return 0
        return int(node.val == target) + self.dfs(node.left, target - node.val) + self.dfs(node.right, target - node.val)
```
The essence of this problem is to find paths in a binary tree that sum to a given value.
    
### >> 302 Smallest Rectangle Enclosing Black Pixels [Hard]
Given an image consisting only of black and white pixels, find the minimum area of a rectangle that encloses all black pixels.
##### Sample input:
[["0","0","1","0"],["0","1","1","0"],["0","1","0","0"]]
##### Sample output:
6

##### Questions to ask to clarify requirements:

- Can the image contain multiple disconnected black pixels?
- Can the image contain white pixels inside the rectangle?

##### Optimal Python solution:
```python
class Solution:
    def minArea(self, image: List[List[str]], x: int, y: int) -> int:
        def search(image, left, right, top, bottom, direction):
            if left > right or top > bottom:
                return 0
            if direction == 'left':
                for i in range(top, bottom + 1):
                    for j in range(left, right + 1):
                        if image[i][j] == '1':
                            return search(image, left, j - 1, top, bottom, 'up')
            elif direction == 'up':
                for j in range(left, right + 1):
                    for i in range(top, bottom + 1):
                        if image[i][j] == '1':
                            return search(image, left, right, top, i - 1, 'right')
            elif direction == 'right':
                for i in range(bottom, top - 1, -1):
                    for j in range(left, right + 1):
                        if image[i][j] == '1':
                            return search(image, j + 1, right, top, bottom, 'down')
            elif direction == 'down':
                for j in range(right, left - 1, -1):
                    for i in range(top, bottom + 1):
                        if image[i][j] == '1':
                            return search(image, left, right, i + 1, bottom, 'left')
            return (right - left + 1) * (bottom - top + 1)
        m, n = len(image), len(image[0])
        return search(image, 0, n - 1, 0, m - 1, 'left')
```
##### Time complexity:
O(N * log(M) + M * log(N))
##### Space complexity:
O(1)
##### Notes:

- Use binary search and DFS to find the boundaries of the rectangle
- Calculate the area of the rectangle

- Use binary search to find the boundaries of the rectangle
- Use DFS to search for black pixels

- How to efficiently find the boundaries of the rectangle?

- Using a brute force approach to search for the boundaries of the rectangle
    
### >> Comparison: 437 Path Sum III [Medium] *VS* 302 Smallest Rectangle Enclosing Black Pixels [Hard]
> Similarity distance: 0.5319
##### Similarities

- Both questions involve traversing a binary tree.
- Both questions require finding a specific sum or target value.
##### Differences

- Path Sum III involves finding paths in the tree that sum up to the target value, while Smallest Rectangle Enclosing Black Pixels involves finding the smallest rectangle that encloses all black pixels in a binary matrix.
- Path Sum III is a medium difficulty question, while Smallest Rectangle Enclosing Black Pixels is a hard difficulty question.
- Path Sum III requires counting the number of paths that sum up to the target value, while Smallest Rectangle Enclosing Black Pixels requires finding the coordinates of the rectangle.
##### New Insights in 302 Smallest Rectangle Enclosing Black Pixels [Hard]

- Path Sum III introduces the concept of counting paths in a binary tree that sum up to a target value.
- Smallest Rectangle Enclosing Black Pixels introduces the concept of finding the smallest rectangle that encloses all black pixels in a binary matrix.


---
# 7. From 437 Path Sum III [Medium] to 133 Clone Graph [Medium]
> Similarity Distance: 0.5596

### >> Reminder: 437 Path Sum III [Medium]
You are given a binary tree in which each node contains an integer value. Find the number of paths that sum to a given value. The path does not need to start or end at the root or a leaf, but it must go downwards (traveling only from parent nodes to child nodes).
##### Optimal Python solution:
```python
class Solution:
    def pathSum(self, root: TreeNode, sum: int) -> int:
        if not root:
            return 0
        return self.dfs(root, sum) + self.pathSum(root.left, sum) + self.pathSum(root.right, sum)

    def dfs(self, node, target):
        if not node:
            return 0
        return int(node.val == target) + self.dfs(node.left, target - node.val) + self.dfs(node.right, target - node.val)
```
The essence of this problem is to find paths in a binary tree that sum to a given value.
    
### >> 133 Clone Graph [Medium]
Given a reference of a node in a connected undirected graph, return a deep copy (clone) of the graph. Each node in the graph contains a val (int) and a list (List[Node]) of its neighbors.
##### Sample input:
[[2,4],[1,3],[2,4],[1,3]]
##### Sample output:
[[2,4],[1,3],[2,4],[1,3]]

##### Questions to ask to clarify requirements:
1. Can the graph have cycles? 2. Can the graph be disconnected? 3. Can the node values be negative? 4. Can the node have duplicate neighbors?

##### Optimal Python solution:
```python
class Solution:
    def cloneGraph(self, node: 'Node') -> 'Node':
        if not node:
            return None
        visited = {}
        def dfs(node):
            if node in visited:
                return visited[node]
            clone = Node(node.val, [])
            visited[node] = clone
            for neighbor in node.neighbors:
                clone.neighbors.append(dfs(neighbor))
            return clone
        return dfs(node)
```
##### Time complexity:
O(N + M)
##### Space complexity:
O(N)
##### Notes:
1. Use depth-first search (DFS) to traverse the graph. 2. Use a dictionary to keep track of visited nodes and their clones. 3. Recursively clone each node and its neighbors.
1. Use a dictionary to keep track of visited nodes and their clones. 2. Use recursion to clone each node and its neighbors. 3. Handle cycles in the graph by checking if a node has already been visited before cloning it.
1. Handling cycles in the graph. 2. Cloning duplicate neighbors.
1. Using breadth-first search (BFS) instead of depth-first search (DFS). 2. Using a stack instead of recursion.
    
### >> Comparison: 437 Path Sum III [Medium] *VS* 133 Clone Graph [Medium]
> Similarity distance: 0.5596
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve traversing a graph-like structure.
- Both questions require finding paths that satisfy certain conditions.
##### Differences

- Path Sum III involves a binary tree, while Clone Graph involves an undirected graph.
- Path Sum III requires finding paths with a specific sum, while Clone Graph requires creating a deep copy of the graph.
- Path Sum III allows paths to start and end at any node, while Clone Graph requires cloning the entire graph.
##### New Insights in 133 Clone Graph [Medium]

- Path Sum III can be solved using a recursive approach with backtracking.
- Clone Graph can be solved using a depth-first search or breadth-first search algorithm.
- Both questions require understanding graph traversal and recursion.


---
# 8. From 437 Path Sum III [Medium] to 130 Surrounded Regions [Medium]
> Similarity Distance: 0.6011

### >> Reminder: 437 Path Sum III [Medium]
You are given a binary tree in which each node contains an integer value. Find the number of paths that sum to a given value. The path does not need to start or end at the root or a leaf, but it must go downwards (traveling only from parent nodes to child nodes).
##### Optimal Python solution:
```python
class Solution:
    def pathSum(self, root: TreeNode, sum: int) -> int:
        if not root:
            return 0
        return self.dfs(root, sum) + self.pathSum(root.left, sum) + self.pathSum(root.right, sum)

    def dfs(self, node, target):
        if not node:
            return 0
        return int(node.val == target) + self.dfs(node.left, target - node.val) + self.dfs(node.right, target - node.val)
```
The essence of this problem is to find paths in a binary tree that sum to a given value.
    
### >> 130 Surrounded Regions [Medium]
Given a 2D board containing 'X' and 'O' (the letter O), capture all regions surrounded by 'X'. A region is captured by flipping all 'O's into 'X's in that surrounded region.
##### Sample input:
[['X','X','X','X'],['X','O','O','X'],['X','X','O','X'],['X','O','X','X']]
##### Sample output:
[['X','X','X','X'],['X','X','X','X'],['X','X','X','X'],['X','O','X','X']]

##### Questions to ask to clarify requirements:
1. Can the board be empty?
2. Can the board have dimensions greater than 1000x1000?
3. Can the board contain characters other than 'X' and 'O'?

##### Optimal Python solution:
```python
class Solution:
    def solve(self, board: List[List[str]]) -> None:
        if not board:
            return
        m, n = len(board), len(board[0])
        def dfs(i, j):
            if i < 0 or i >= m or j < 0 or j >= n or board[i][j] != 'O':
                return
            board[i][j] = '#'
            dfs(i-1, j)
            dfs(i+1, j)
            dfs(i, j-1)
            dfs(i, j+1)
        for i in range(m):
            dfs(i, 0)
            dfs(i, n-1)
        for j in range(n):
            dfs(0, j)
            dfs(m-1, j)
        for i in range(m):
            for j in range(n):
                if board[i][j] == 'O':
                    board[i][j] = 'X'
                elif board[i][j] == '#':
                    board[i][j] = 'O'
```
##### Time complexity:
O(m * n)
##### Space complexity:
O(m * n)
##### Notes:
1. Use depth-first search (DFS) to traverse the board.
2. Mark the 'O' cells that are not surrounded by 'X' with a special character.
3. Flip all remaining 'O' cells to 'X' and restore the special character to 'O'.
1. Use recursion to implement depth-first search (DFS).
2. Handle the base case when the cell is out of bounds or already visited.
3. Use a helper function to perform the DFS traversal.
1. Handling the case when the board is empty.
2. Handling the case when the board has dimensions greater than 1000x1000.
1. Avoid using breadth-first search (BFS) as it is not necessary for this problem.
2. Avoid using a global variable to store the visited cells.
    
### >> Comparison: 437 Path Sum III [Medium] *VS* 130 Surrounded Regions [Medium]
> Similarity distance: 0.6011
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve traversing a grid or tree structure.
- Both questions require some form of path or region manipulation.
- Both questions involve checking for certain conditions.
##### Differences

- Question 437 involves a binary tree structure, while question 130 involves a 2D grid structure.
- Question 437 requires finding paths that sum up to a given target, while question 130 requires identifying regions that are not surrounded by 'X'.
- Question 437 involves counting the number of paths that satisfy the condition, while question 130 involves modifying the grid to mark the surrounded regions.
- Question 437 can have negative values in the tree nodes, while question 130 only deals with 'O' and 'X' characters in the grid.
##### New Insights in 130 Surrounded Regions [Medium]

- Question 437 introduces the concept of counting paths in a binary tree, which can be solved using recursion and backtracking.
- Question 130 introduces the concept of identifying surrounded regions in a 2D grid, which can be solved using depth-first search (DFS) or breadth-first search (BFS).


---
# 9. From 200 Number of Islands [Medium] to 417 Pacific Atlantic Water Flow [Medium]
> Similarity Distance: 0.5709

### >> Reminder: 200 Number of Islands [Medium]
Given a 2d grid map of '1's (land) and '0's (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.
##### Optimal Python solution:
```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        if not grid:
            return 0
        m, n = len(grid), len(grid[0])
        count = 0
        for i in range(m):
            for j in range(n):
                if grid[i][j] == '1':
                    self.dfs(grid, i, j)
                    count += 1
        return count

    def dfs(self, grid, i, j):
        if i < 0 or i >= len(grid) or j < 0 or j >= len(grid[0]) or grid[i][j] != '1':
            return
        grid[i][j] = '0'
        self.dfs(grid, i + 1, j)
        self.dfs(grid, i - 1, j)
        self.dfs(grid, i, j + 1)
        self.dfs(grid, i, j - 1)
```
The essence of this problem is to perform a depth-first search (DFS) on the grid and count the number of connected components.
    
### >> 417 Pacific Atlantic Water Flow [Medium]
Given an m x n matrix of non-negative integers representing the height of each unit cell in a continent, the "Pacific ocean" touches the left and top edges of the matrix and the "Atlantic ocean" touches the right and bottom edges. Water can only flow in four directions (up, down, left, or right) from a cell to another one with height equal or lower. Find the list of grid coordinates where water can flow to both the Pacific and Atlantic oceans.
##### Sample input:

- [[1,2,2,3,5],[3,2,3,4,4],[2,4,5,3,1],[6,7,1,4,5],[5,1,1,2,4]]
##### Sample output:

- [[0,4],[1,3],[1,4],[2,2],[3,0],[3,1],[4,0]]

##### Questions to ask to clarify requirements:

- Can the matrix be empty?
- Can the matrix have empty rows?
- Can the matrix have empty columns?
- Can the matrix contain negative integers?
- Can the matrix have duplicate heights?

##### Optimal Python solution:
```python

- from typing import List
- 
- class Solution:
-     def pacificAtlantic(self, matrix: List[List[int]]) -> List[List[int]]:
-         if not matrix or not matrix[0]:
-             return []
-         m, n = len(matrix), len(matrix[0])
-         pacific = set()
-         atlantic = set()
-         directions = [(0, 1), (0, -1), (1, 0), (-1, 0)]
- 
-         def dfs(i, j, ocean):
-             ocean.add((i, j))
-             for dx, dy in directions:
-                 x, y = i + dx, j + dy
-                 if x < 0 or x >= m or y < 0 or y >= n or (x, y) in ocean or matrix[x][y] < matrix[i][j]:
-                     continue
-                 dfs(x, y, ocean)
- 
-         for i in range(m):
-             dfs(i, 0, pacific)
-             dfs(i, n - 1, atlantic)
-         for j in range(n):
-             dfs(0, j, pacific)
-             dfs(m - 1, j, atlantic)
- 
-         return list(pacific & atlantic)
```
##### Time complexity:
O(m * n)
##### Space complexity:
O(m * n)
##### Notes:

- Use DFS to find the cells that can flow to the Pacific ocean
- Use DFS to find the cells that can flow to the Atlantic ocean
- Return the intersection of the two sets of cells

- Use sets to store the cells that can flow to the Pacific and Atlantic oceans
- Use DFS to explore the matrix

- Using two sets to store the cells that can flow to the Pacific and Atlantic oceans

- Using a visited matrix to track visited cells
    
### >> Comparison: 200 Number of Islands [Medium] *VS* 417 Pacific Atlantic Water Flow [Medium]
> Similarity distance: 0.5709
##### Similarities

- Both questions involve traversing a 2D grid.
- Both questions require identifying connected components.
- Both questions involve checking for water flow from one side to another.
##### Differences

- Number of Islands focuses on identifying separate islands in the grid.
- Pacific Atlantic Water Flow focuses on identifying cells where water can flow from the Pacific Ocean to the Atlantic Ocean.
##### New Insights in 417 Pacific Atlantic Water Flow [Medium]

- Number of Islands: We can use depth-first search (DFS) or breadth-first search (BFS) to solve the problem.
- Pacific Atlantic Water Flow: We can use a depth-first search (DFS) approach to solve the problem.

