
# Leetcode Intensive Tutorial Day 3 
> [Difficulty Score: 10]

> [Version: 20231226_040350]

> [Including this day, you had studied : 21 leetcode problems]


## Courses overview of the day

- 110 Balanced Binary Tree [Easy]
  - 222 Count Complete Tree Nodes [Medium]
    - 111 Minimum Depth of Binary Tree [Easy]
      - 112 Path Sum [Easy]
        - 156 Binary Tree Upside Down [Medium]
  - 366 Find Leaves of Binary Tree [Medium]
  - 563 Binary Tree Tilt [Easy]

#### Step by step

 - [1. From 110 Balanced Binary Tree [Easy] to 222 Count Complete Tree Nodes [Medium]](#1-from-110-balanced-binary-tree-easy-to-222-count-complete-tree-nodes-medium))

 - [2. From 222 Count Complete Tree Nodes [Medium] to 111 Minimum Depth of Binary Tree [Easy]](#2-from-222-count-complete-tree-nodes-medium-to-111-minimum-depth-of-binary-tree-easy))

 - [3. From 111 Minimum Depth of Binary Tree [Easy] to 112 Path Sum [Easy]](#3-from-111-minimum-depth-of-binary-tree-easy-to-112-path-sum-easy))

 - [4. From 112 Path Sum [Easy] to 156 Binary Tree Upside Down [Medium]](#4-from-112-path-sum-easy-to-156-binary-tree-upside-down-medium))

 - [5. From 110 Balanced Binary Tree [Easy] to 366 Find Leaves of Binary Tree [Medium]](#5-from-110-balanced-binary-tree-easy-to-366-find-leaves-of-binary-tree-medium))

 - [6. From 110 Balanced Binary Tree [Easy] to 563 Binary Tree Tilt [Easy]](#6-from-110-balanced-binary-tree-easy-to-563-binary-tree-tilt-easy))

    

#### Summary


- 366 Find Leaves of Binary Tree : The essence of the problem is to collect and remove all leaves of a binary tree, repeating the process until the tree is empty.
- 156 Binary Tree Upside Down : Turn a binary tree upside down and return the new root.
- 110 Balanced Binary Tree : Determine if a binary tree is height-balanced.
- 222 Count Complete Tree Nodes : The essence of this problem is to count the number of nodes in a complete binary tree.
- 563 Binary Tree Tilt : Calculate the tilt of a binary tree by finding the absolute difference between the sum of all left subtree node values and all right subtree node values.
- 112 Path Sum : The essence of this problem is to determine if there is a root-to-leaf path in the binary tree that sums up to the given sum using a recursive approach.
- 111 Minimum Depth of Binary Tree : The essence of this problem is to find the minimum depth of a binary tree using a recursive approach.
> Similarity Diameter of these problems: 0.7458


---
# 1. From 110 Balanced Binary Tree [Easy] to 222 Count Complete Tree Nodes [Medium]
> Similarity Distance: 0.4916

### >> 110 Balanced Binary Tree [Easy]
Given a binary tree, determine if it is height-balanced.
##### Sample input:
[3,9,20,null,null,15,7]
##### Sample output:
true

##### Questions to ask to clarify requirements:

- Can the binary tree have duplicate elements?
- Can the binary tree be empty?

##### Optimal Python solution:
```python
class Solution:
    def isBalanced(self, root: TreeNode) -> bool:
        def check_height(node):
            if not node:
                return 0
            left_height = check_height(node.left)
            right_height = check_height(node.right)
            if left_height == -1 or right_height == -1 or abs(left_height - right_height) > 1:
                return -1
            return max(left_height, right_height) + 1
        return check_height(root) != -1
```
##### Time complexity:
O(n)
##### Space complexity:
O(logn)
##### Notes:

- A height-balanced binary tree is a binary tree in which the left and right subtrees of every node differ in height by at most 1.
- Use recursion to calculate the height of each subtree and check if the difference is greater than 1.

- Use a helper function to calculate the height of each subtree.
- Handle the base cases of an empty tree or a tree with only one node.

- Calculating the height of each subtree using recursion.

- Calculating the height of each subtree using a separate function for each subtree.
    
### >> 222 Count Complete Tree Nodes [Medium]
Given a complete binary tree, count the number of nodes.
##### Sample input:

- [1,2,3,4,5,6]
##### Sample output:

- 6

##### Questions to ask to clarify requirements:

- What is the definition of a complete binary tree?
- Can the tree be empty?

##### Optimal Python solution:
```python

- def countNodes(root):
    if not root:
        return 0
    left_height = getLeftHeight(root)
    right_height = getRightHeight(root)
    if left_height == right_height:
        return (1 << left_height) - 1
    else:
        return countNodes(root.left) + countNodes(root.right) + 1

def getLeftHeight(root):
    height = 0
    while root:
        height += 1
        root = root.left
    return height

def getRightHeight(root):
    height = 0
    while root:
        height += 1
        root = root.right
    return height
- class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

root = TreeNode(1)
root.left = TreeNode(2)
root.right = TreeNode(3)
root.left.left = TreeNode(4)
root.left.right = TreeNode(5)
root.right.left = TreeNode(6)
print(countNodes(root))
```
##### Time complexity:
O(log^2(n))
##### Space complexity:
O(log(n))
##### Notes:

- Use recursion to count the number of nodes
- Get the height of the left and right subtrees
- If the heights are equal, the tree is complete
- If the heights are not equal, recursively count the nodes in the left and right subtrees

- Break down the problem into smaller subproblems.
- Use recursion to solve tree-related problems.
- Optimize the solution by calculating the heights of the subtrees.

- Calculating the height of the left and right subtrees

- Counting the nodes in each subtree separately
    
### >> Comparison: 110 Balanced Binary Tree [Easy] *VS* 222 Count Complete Tree Nodes [Medium]
> Similarity distance: 0.4916
##### Similarities

- Both questions involve binary trees.
- Both questions require counting nodes in a tree.
##### Differences

- 110 Balanced Binary Tree is an easy level question, while 222 Count Complete Tree Nodes is a medium level question.
- 110 Balanced Binary Tree checks if a binary tree is balanced, while 222 Count Complete Tree Nodes counts the number of nodes in a complete binary tree.
- 110 Balanced Binary Tree uses a recursive approach to check the balance, while 222 Count Complete Tree Nodes uses a binary search approach to count the nodes.
##### New Insights in 222 Count Complete Tree Nodes [Medium]

- 110 Balanced Binary Tree teaches us how to check if a binary tree is balanced by comparing the heights of its left and right subtrees.
- 222 Count Complete Tree Nodes teaches us how to count the number of nodes in a complete binary tree efficiently using a binary search approach.


---
# 2. From 222 Count Complete Tree Nodes [Medium] to 111 Minimum Depth of Binary Tree [Easy]
> Similarity Distance: 0.5649

### >> Reminder: 222 Count Complete Tree Nodes [Medium]
Given a complete binary tree, count the number of nodes.
##### Optimal Python solution:
```python

- def countNodes(root):
    if not root:
        return 0
    left_height = getLeftHeight(root)
    right_height = getRightHeight(root)
    if left_height == right_height:
        return (1 << left_height) - 1
    else:
        return countNodes(root.left) + countNodes(root.right) + 1

def getLeftHeight(root):
    height = 0
    while root:
        height += 1
        root = root.left
    return height

def getRightHeight(root):
    height = 0
    while root:
        height += 1
        root = root.right
    return height
- class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

root = TreeNode(1)
root.left = TreeNode(2)
root.right = TreeNode(3)
root.left.left = TreeNode(4)
root.left.right = TreeNode(5)
root.right.left = TreeNode(6)
print(countNodes(root))
```
The essence of this problem is to count the number of nodes in a complete binary tree.
    
### >> 111 Minimum Depth of Binary Tree [Easy]
Given a binary tree, find its minimum depth.
##### Sample input:
[3,9,20,null,null,15,7]
##### Sample output:
2

##### Questions to ask to clarify requirements:
What is the definition of minimum depth of a binary tree?

##### Optimal Python solution:
```python
class Solution:
    def minDepth(self, root: TreeNode) -> int:
        if not root:
            return 0
        if not root.left:
            return self.minDepth(root.right) + 1
        if not root.right:
            return self.minDepth(root.left) + 1
        return min(self.minDepth(root.left), self.minDepth(root.right)) + 1
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.
Make sure to handle the base cases where the root is null or has no left or right child.
The minimum depth is not the same as the height of the tree.
Avoid using a breadth-first search (BFS) approach.
    
### >> Comparison: 222 Count Complete Tree Nodes [Medium] *VS* 111 Minimum Depth of Binary Tree [Easy]
> Similarity distance: 0.5649
##### Similarities

- Both questions are related to binary trees.
- Both questions require traversing the binary tree to find a specific property.
##### Differences

- Question 222 requires counting the number of nodes in a complete binary tree, while question 111 requires finding the minimum depth of a binary tree.
- Question 222 has a medium difficulty level, while question 111 has an easy difficulty level.
##### New Insights in 111 Minimum Depth of Binary Tree [Easy]

- Question 222: Counting the number of nodes in a complete binary tree can be done efficiently by utilizing the properties of complete binary trees.
- Question 111: Finding the minimum depth of a binary tree can be done using a depth-first search or a breadth-first search algorithm.


---
# 3. From 111 Minimum Depth of Binary Tree [Easy] to 112 Path Sum [Easy]
> Similarity Distance: 0.5231

### >> Reminder: 111 Minimum Depth of Binary Tree [Easy]
Given a binary tree, find its minimum depth.
##### Optimal Python solution:
```python
class Solution:
    def minDepth(self, root: TreeNode) -> int:
        if not root:
            return 0
        if not root.left:
            return self.minDepth(root.right) + 1
        if not root.right:
            return self.minDepth(root.left) + 1
        return min(self.minDepth(root.left), self.minDepth(root.right)) + 1
```
The essence of this problem is to find the minimum depth of a binary tree using a recursive approach.
    
### >> 112 Path Sum [Easy]
Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.
##### Sample input:
[5,4,8,11,null,13,4,7,2,null,null,null,1]
22
##### Sample output:
True

##### Questions to ask to clarify requirements:
What is the definition of a root-to-leaf path?

##### Optimal Python solution:
```python
class Solution:
    def hasPathSum(self, root: TreeNode, sum: int) -> bool:
        if not root:
            return False
        if not root.left and not root.right:
            return sum == root.val
        return self.hasPathSum(root.left, sum - root.val) or self.hasPathSum(root.right, sum - root.val)
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
A root-to-leaf path is a path from the root node to any leaf node in the tree.
Make sure to handle the base cases where the root is null or has no left and right child.
The sum can be negative.
Avoid using a breadth-first search (BFS) approach.
    
### >> Comparison: 111 Minimum Depth of Binary Tree [Easy] *VS* 112 Path Sum [Easy]
> Similarity distance: 0.5231
##### Similarities

- Both questions are classified as 'Easy' level on LeetCode.
- Both questions involve binary trees.
- Both questions require finding a specific property of the binary tree.
##### Differences

- 111 Minimum Depth of Binary Tree: This question asks for the minimum depth of a binary tree, which is the number of nodes along the shortest path from the root node to the nearest leaf node.
- 112 Path Sum: This question asks whether there exists a root-to-leaf path in the binary tree where the sum of node values equals a given target sum.
##### New Insights in 112 Path Sum [Easy]

- 111 Minimum Depth of Binary Tree: The minimum depth of a binary tree can be found by performing a depth-first search (DFS) traversal and keeping track of the depth at each node.
- 112 Path Sum: The existence of a root-to-leaf path with a given sum can be determined by performing a depth-first search (DFS) traversal and subtracting the node values from the target sum at each step.


---
# 4. From 112 Path Sum [Easy] to 156 Binary Tree Upside Down [Medium]
> Similarity Distance: 0.6469

### >> Reminder: 112 Path Sum [Easy]
Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.
##### Optimal Python solution:
```python
class Solution:
    def hasPathSum(self, root: TreeNode, sum: int) -> bool:
        if not root:
            return False
        if not root.left and not root.right:
            return sum == root.val
        return self.hasPathSum(root.left, sum - root.val) or self.hasPathSum(root.right, sum - root.val)
```
The essence of this problem is to determine if there is a root-to-leaf path in the binary tree that sums up to the given sum using a recursive approach.
    
### >> 156 Binary Tree Upside Down [Medium]
Given the root of a binary tree, turn the tree upside down and return the new root.
##### Sample input:

- [1,2,3,4,5]
##### Sample output:

- [4,5,2,null,null,3,1]

##### Questions to ask to clarify requirements:
What should be returned if the root is null or if the root has no left child?

##### Optimal Python solution:
```python

- def upsideDownBinaryTree(root):
-     if not root or not root.left:
-         return root
-     new_root = upsideDownBinaryTree(root.left)
-     root.left.left = root.right
-     root.left.right = root
-     root.left = None
-     root.right = None
-     return new_root
```
##### Time complexity:
O(n)
##### Space complexity:
O(h)
##### Notes:

- Recursively call the function on the left child until reaching the leftmost leaf node.
- Set the new root as the left child of the current root.
- Update the left and right pointers of the current root and set them to None.
Handle the base cases when the root is null or when the root has no left child.
None
None
    
### >> Comparison: 112 Path Sum [Easy] *VS* 156 Binary Tree Upside Down [Medium]
> Similarity distance: 0.6469
##### Similarities

- Both questions involve binary trees.
- Both questions require traversing the tree in a specific manner.
##### Differences

- 112 Path Sum is an easy level question, while 156 Binary Tree Upside Down is a medium level question.
- 112 Path Sum involves finding a path in the tree that sums up to a given target, while 156 Binary Tree Upside Down involves flipping the binary tree upside down.
- 112 Path Sum requires checking if a path exists, while 156 Binary Tree Upside Down requires modifying the structure of the tree.
- 112 Path Sum can be solved using recursion, while 156 Binary Tree Upside Down requires a specific algorithm.
##### New Insights in 156 Binary Tree Upside Down [Medium]

- In 112 Path Sum, we can use a recursive approach to traverse the tree and keep track of the current sum.
- In 156 Binary Tree Upside Down, we can use a bottom-up approach to flip the tree by modifying the left and right pointers of each node.


---
# 5. From 110 Balanced Binary Tree [Easy] to 366 Find Leaves of Binary Tree [Medium]
> Similarity Distance: 0.5291

### >> Reminder: 110 Balanced Binary Tree [Easy]
Given a binary tree, determine if it is height-balanced.
##### Optimal Python solution:
```python
class Solution:
    def isBalanced(self, root: TreeNode) -> bool:
        def check_height(node):
            if not node:
                return 0
            left_height = check_height(node.left)
            right_height = check_height(node.right)
            if left_height == -1 or right_height == -1 or abs(left_height - right_height) > 1:
                return -1
            return max(left_height, right_height) + 1
        return check_height(root) != -1
```
Determine if a binary tree is height-balanced.
    
### >> 366 Find Leaves of Binary Tree [Medium]
Given a binary tree, collect a tree's nodes as if you were doing this: Collect and remove all leaves, repeat until the tree is empty.
##### Sample input:
root = [1,2,3,4,5]
##### Sample output:
[[4,5,3],[2],[1]]

##### Questions to ask to clarify requirements:
1. Can we assume that the binary tree is non-empty? 2. Can we assume that the binary tree is a valid binary tree? 3. Can we assume that the binary tree is a binary search tree? 4. Can we assume that the values of the nodes are unique?

##### Optimal Python solution:
```python
def findLeaves(root: TreeNode) -> List[List[int]]:
    def dfs(node):
        if not node:
            return -1
        left_height = dfs(node.left)
        right_height = dfs(node.right)
        height = max(left_height, right_height) + 1
        if height == len(result):
            result.append([])
        result[height].append(node.val)
        return height
    result = []
    dfs(root)
    return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. The problem can be solved using depth-first search (DFS) and recursion. 2. The height of a node in the tree represents its level in the result list. 3. The result list is initialized as an empty list. 4. The result list is updated during the DFS traversal of the tree.
1. Use a recursive helper function to calculate the height of each node. 2. Initialize the result list as an empty list. 3. Update the result list during the DFS traversal of the tree. 4. Handle edge cases where the binary tree is empty or has only one node.
1. The solution uses a recursive helper function to calculate the height of each node. 2. The result list is updated during the DFS traversal of the tree.
1. Avoid using a breadth-first search (BFS) approach to solve the problem. 2. Avoid using an iterative solution instead of recursion.
    
### >> Comparison: 110 Balanced Binary Tree [Easy] *VS* 366 Find Leaves of Binary Tree [Medium]
> Similarity distance: 0.5291
##### Similarities

- Both questions involve binary trees.
- Both questions require determining the balance of a binary tree.
##### Differences

- 110 Balanced Binary Tree is an easy level question, while 366 Find Leaves of Binary Tree is a medium level question.
- 110 Balanced Binary Tree requires checking if a binary tree is balanced, while 366 Find Leaves of Binary Tree requires finding the leaves of a binary tree.
- 110 Balanced Binary Tree can be solved using recursion, while 366 Find Leaves of Binary Tree requires a different approach.
##### New Insights in 366 Find Leaves of Binary Tree [Medium]

- 110 Balanced Binary Tree teaches us how to check if a binary tree is balanced.
- 366 Find Leaves of Binary Tree teaches us how to find the leaves of a binary tree.


---
# 6. From 110 Balanced Binary Tree [Easy] to 563 Binary Tree Tilt [Easy]
> Similarity Distance: 0.5658

### >> Reminder: 110 Balanced Binary Tree [Easy]
Given a binary tree, determine if it is height-balanced.
##### Optimal Python solution:
```python
class Solution:
    def isBalanced(self, root: TreeNode) -> bool:
        def check_height(node):
            if not node:
                return 0
            left_height = check_height(node.left)
            right_height = check_height(node.right)
            if left_height == -1 or right_height == -1 or abs(left_height - right_height) > 1:
                return -1
            return max(left_height, right_height) + 1
        return check_height(root) != -1
```
Determine if a binary tree is height-balanced.
    
### >> 563 Binary Tree Tilt [Easy]
Given the root of a binary tree, return the sum of every tree node's tilt.
The tilt of a tree node is the absolute difference between the sum of all left subtree node values and all right subtree node values.
If a node does not have a left child, then the sum of the left subtree node values is treated as 0.
The rule is similar if there the node does not have a right child.
##### Sample input:
[1,2,3]
##### Sample output:
1

##### Questions to ask to clarify requirements:

- What is the definition of tilt in this context?
- How should the tilt be calculated if a node does not have a left or right child?

##### Optimal Python solution:
```python
class Solution:
    def findTilt(self, root: TreeNode) -> int:
        self.tilt = 0
        def dfs(node):
            if not node:
                return 0
            left_sum = dfs(node.left)
            right_sum = dfs(node.right)
            self.tilt += abs(left_sum - right_sum)
            return node.val + left_sum + right_sum
        dfs(root)
        return self.tilt
```
##### Time complexity:
O(n)
##### Space complexity:
O(h)
##### Notes:

- The tilt of a tree node is the absolute difference between the sum of all left subtree node values and all right subtree node values.
- If a node does not have a left child, then the sum of the left subtree node values is treated as 0.
- The rule is similar if there the node does not have a right child.

- Use a helper function to calculate the sum of a subtree.
- Initialize the tilt to 0 before calling the helper function.
- Use recursion to traverse the tree.

- Recursion

- Iterative solution
    
### >> Comparison: 110 Balanced Binary Tree [Easy] *VS* 563 Binary Tree Tilt [Easy]
> Similarity distance: 0.5658
##### Similarities

- Both questions are related to binary trees.
- Both questions have an easy difficulty level.
##### Differences

- 110 Balanced Binary Tree focuses on checking if a binary tree is balanced, while 563 Binary Tree Tilt focuses on calculating the tilt of a binary tree.
- 110 Balanced Binary Tree uses a recursive approach to check the balance, while 563 Binary Tree Tilt uses a post-order traversal to calculate the tilt.
- 110 Balanced Binary Tree requires calculating the height of each subtree, while 563 Binary Tree Tilt requires calculating the sum of tilt for each node.
##### New Insights in 563 Binary Tree Tilt [Easy]

- 110 Balanced Binary Tree: The height of a balanced binary tree is the maximum height of its left and right subtrees plus one.
- 563 Binary Tree Tilt: The tilt of a binary tree is the absolute difference between the sum of left subtree values and the sum of right subtree values.

