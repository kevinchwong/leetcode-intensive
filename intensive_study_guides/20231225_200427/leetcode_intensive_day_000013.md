
# Leetcode Intensive Tutorial Day 13 
> [Difficulty Score: 14]

> [Version: 20231225_200427]

## Courses overview of the day

- 102 Binary Tree Level Order Traversal [Medium]
  - 116 Populating Next Right Pointers in Each Node [Medium]
    - 94 Binary Tree Inorder Traversal [Medium]
      - 510 Inorder Successor in BST II [Medium]
        - 285 Inorder Successor in BST [Medium]
  - 314 Binary Tree Vertical Order Traversal [Medium]
    - 199 Binary Tree Right Side View [Medium]

#### Steps by steps

 - [1. From 102 Binary Tree Level Order Traversal [Medium] to 116 Populating Next Right Pointers in Each Node [Medium]](#1-from-102-binary-tree-level-order-traversal-medium-to-116-populating-next-right-pointers-in-each-node-medium)

 - [2. From 116 Populating Next Right Pointers in Each Node [Medium] to 94 Binary Tree Inorder Traversal [Medium]](#2-from-116-populating-next-right-pointers-in-each-node-medium-to-94-binary-tree-inorder-traversal-medium)

 - [3. From 94 Binary Tree Inorder Traversal [Medium] to 510 Inorder Successor in BST II [Medium]](#3-from-94-binary-tree-inorder-traversal-medium-to-510-inorder-successor-in-bst-ii-medium)

 - [4. From 510 Inorder Successor in BST II [Medium] to 285 Inorder Successor in BST [Medium]](#4-from-510-inorder-successor-in-bst-ii-medium-to-285-inorder-successor-in-bst-medium)

 - [5. From 102 Binary Tree Level Order Traversal [Medium] to 314 Binary Tree Vertical Order Traversal [Medium]](#5-from-102-binary-tree-level-order-traversal-medium-to-314-binary-tree-vertical-order-traversal-medium)

 - [6. From 314 Binary Tree Vertical Order Traversal [Medium] to 199 Binary Tree Right Side View [Medium]](#6-from-314-binary-tree-vertical-order-traversal-medium-to-199-binary-tree-right-side-view-medium)

#### Summary


- 102 Binary Tree Level Order Traversal : The essence of the problem is to perform a level order traversal of a binary tree using a queue to keep track of the nodes at each level.
- 285 Inorder Successor in BST : The in-order successor of a node in a binary search tree is the next node in the in-order traversal.
- 199 Binary Tree Right Side View : The essence of this problem is to perform a level order traversal of the binary tree and keep track of the last node in each level.
- 116 Populating Next Right Pointers in Each Node : The essence of the problem is to connect the nodes in a perfect binary tree using the next pointers.
- 510 Inorder Successor in BST II : The essence of this problem is to find the in-order successor of a node in a binary search tree.
- 94 Binary Tree Inorder Traversal : The essence of the problem is to perform inorder traversal of a binary tree.
- 314 Binary Tree Vertical Order Traversal : The essence of this problem is to perform a level order traversal of the binary tree and store the nodes in each column.
> Similarity Diameter of these problems: 0.5579


---
# 1. From 102 Binary Tree Level Order Traversal [Medium] to 116 Populating Next Right Pointers in Each Node [Medium]
> Similarity Distance: 0.3334

### >> 102 Binary Tree Level Order Traversal [Medium]
Given a binary tree, return the level order traversal of its nodes' values. (ie, from left to right, level by level).
##### Sample input:
[3,9,20,null,null,15,7]
##### Sample output:
[[3],[9,20],[15,7]]

##### Questions to ask to clarify requirements:
Are empty trees considered in the level order traversal?

##### Optimal Python solution:
```python
class Solution:
    def levelOrder(self, root: TreeNode) -> List[List[int]]:
        if not root:
            return []
        queue = [root]
        result = []
        while queue:
            level = []
            for _ in range(len(queue)):
                node = queue.pop(0)
                level.append(node.val)
                if node.left:
                    queue.append(node.left)
                if node.right:
                    queue.append(node.right)
            result.append(level)
        return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- Perform a level order traversal of the binary tree.
- Use a queue to keep track of the nodes at each level.
- Pop nodes from the queue and add their values to the result list.
- Add the left and right children of each node to the queue.
Use a queue to perform a level order traversal of a binary tree.
The queue is used to keep track of the nodes at each level.
Avoid using recursion.
    
### >> 116 Populating Next Right Pointers in Each Node [Medium]
You are given a perfect binary tree where all leaves are on the same level, and every parent has two children. Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to NULL.
##### Sample input:
1
##### Sample output:
1

##### Questions to ask to clarify requirements:
Can the input tree be empty? Can the tree have more than two children for each parent?

##### Optimal Python solution:
```python
class Node:
    def __init__(self, val=0, left=None, right=None, next=None):
        self.val = val
        self.left = left
        self.right = right
        self.next = next

def connect(root: 'Node') -> 'Node':
    if not root:
        return root
    leftmost = root
    while leftmost.left:
        head = leftmost
        while head:
            head.left.next = head.right
            if head.next:
                head.right.next = head.next.left
            head = head.next
        leftmost = leftmost.left
    return root
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Use a level-order traversal to connect the nodes.
2. Use a while loop to iterate through each level.
3. Use a nested while loop to connect the nodes at each level.
4. Update the leftmost node for the next level.
1. Use a queue to store the nodes at each level.
2. Use a dummy node to mark the end of each level.
3. Update the next pointers of the nodes at each level.
The tricky part is connecting the nodes at each level.
Avoid using recursion as it can be inefficient for large trees.
    
### >> Comparison: 102 Binary Tree Level Order Traversal [Medium] *VS* 116 Populating Next Right Pointers in Each Node [Medium]
> Similarity distance: 0.3334
##### Similarities

- Both questions involve traversing a binary tree
- Both questions have a medium difficulty level
##### Differences

- 102 Binary Tree Level Order Traversal focuses on level order traversal and returns the nodes at each level as separate sublists
- 116 Populating Next Right Pointers in Each Node focuses on connecting each node to its right neighbor in the same level using next pointers
##### New Insights in 116 Populating Next Right Pointers in Each Node [Medium]

- 102 Binary Tree Level Order Traversal teaches us how to traverse a binary tree in a level order manner
- 116 Populating Next Right Pointers in Each Node teaches us how to connect nodes in a binary tree using next pointers


---
# 2. From 116 Populating Next Right Pointers in Each Node [Medium] to 94 Binary Tree Inorder Traversal [Medium]
> Similarity Distance: 0.3441

### >> Reminder: 116 Populating Next Right Pointers in Each Node [Medium]
You are given a perfect binary tree where all leaves are on the same level, and every parent has two children. Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to NULL.
##### Optimal Python solution:
```python
class Node:
    def __init__(self, val=0, left=None, right=None, next=None):
        self.val = val
        self.left = left
        self.right = right
        self.next = next

def connect(root: 'Node') -> 'Node':
    if not root:
        return root
    leftmost = root
    while leftmost.left:
        head = leftmost
        while head:
            head.left.next = head.right
            if head.next:
                head.right.next = head.next.left
            head = head.next
        leftmost = leftmost.left
    return root
```
The essence of the problem is to connect the nodes in a perfect binary tree using the next pointers.
    
### >> 94 Binary Tree Inorder Traversal [Medium]
Given the root of a binary tree, return the inorder traversal of its nodes' values.
##### Sample input:
[1,null,2,3]
##### Sample output:
[1,3,2]

##### Questions to ask to clarify requirements:
What is the maximum number of nodes in the binary tree? Can the binary tree be empty?

##### Optimal Python solution:
```python
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        def inorder(node):
            if node:
                inorder(node.left)
                res.append(node.val)
                inorder(node.right)
        res = []
        inorder(root)
        return res
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use recursion to perform inorder traversal.
2. Use a helper function to recursively traverse the binary tree.
3. Use a list to store the inorder traversal result.
4. Use a condition to check if the current node is not None.
5. Use recursion to traverse the left subtree.
6. Use recursion to traverse the right subtree.
7. Use a condition to append the current node value to the result list.
1. Use recursion to perform inorder traversal.
2. Use a helper function to recursively traverse the binary tree.
3. Use a list to store the inorder traversal result.
4. Use a condition to check if the current node is not None.
5. Use recursion to traverse the left subtree.
6. Use recursion to traverse the right subtree.
7. Use a condition to append the current node value to the result list.
1. Handling empty binary tree.
2. Handling binary tree with only one node.
3. Handling binary tree with multiple nodes.
1. Avoid using a non-recursive approach to perform inorder traversal.
2. Avoid using a separate function to traverse the binary tree.
3. Avoid using a separate list to store the inorder traversal result.
4. Avoid using a separate condition to check if the current node is not None.
5. Avoid using a separate recursion to traverse the left subtree.
6. Avoid using a separate recursion to traverse the right subtree.
7. Avoid using a separate condition to append the current node value to the result list.
    
### >> Comparison: 116 Populating Next Right Pointers in Each Node [Medium] *VS* 94 Binary Tree Inorder Traversal [Medium]
> Similarity distance: 0.3441
##### Similarities

- Both questions are medium difficulty level.
- Both questions involve binary trees.
- Both questions require traversing the binary tree in a specific order.
##### Differences

- 116 Populating Next Right Pointers in Each Node focuses on connecting each node to its next right node in the same level, while 94 Binary Tree Inorder Traversal focuses on visiting the nodes in the inorder traversal order.
- 116 Populating Next Right Pointers in Each Node uses a level order traversal approach, while 94 Binary Tree Inorder Traversal uses an inorder traversal approach.
- 116 Populating Next Right Pointers in Each Node modifies the original tree structure by adding next right pointers, while 94 Binary Tree Inorder Traversal only outputs the node values in a specific order.
##### New Insights in 94 Binary Tree Inorder Traversal [Medium]

- 116 Populating Next Right Pointers in Each Node introduces the concept of connecting nodes at the same level using next right pointers.
- 94 Binary Tree Inorder Traversal introduces the concept of visiting nodes in the inorder traversal order.


---
# 3. From 94 Binary Tree Inorder Traversal [Medium] to 510 Inorder Successor in BST II [Medium]
> Similarity Distance: 0.4807

### >> Reminder: 94 Binary Tree Inorder Traversal [Medium]
Given the root of a binary tree, return the inorder traversal of its nodes' values.
##### Optimal Python solution:
```python
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        def inorder(node):
            if node:
                inorder(node.left)
                res.append(node.val)
                inorder(node.right)
        res = []
        inorder(root)
        return res
```
The essence of the problem is to perform inorder traversal of a binary tree.
    
### >> 510 Inorder Successor in BST II [Medium]
Given a node in a binary search tree, find the in-order successor of that node in the BST. If the given node has no in-order successor, return null.
##### Sample input:
5
3
6
2
4
null
null
1
null
##### Sample output:
6
5
null
3
null

##### Questions to ask to clarify requirements:
What is the structure of the binary search tree? Can the given node be null?

##### Optimal Python solution:
```python
class Solution:
    def inorderSuccessor(self, node: 'Node') -> 'Node':
        if node.right:
            node = node.right
            while node.left:
                node = node.left
            return node
        while node.parent and node.parent.right == node:
            node = node.parent
        return node.parent
```
##### Time complexity:
O(h)
##### Space complexity:
O(1)
##### Notes:
1. In-order successor of a node in a binary search tree is the node that comes after the given node in the in-order traversal.
2. If the given node has a right child, the in-order successor is the leftmost node in the right subtree.
3. If the given node does not have a right child, the in-order successor is the first ancestor whose left child is also an ancestor of the given node.
4. Time complexity: O(h), where h is the height of the tree.
1. Start with the given node.
2. If the given node has a right child, find the leftmost node in the right subtree.
3. Otherwise, find the first ancestor whose left child is also an ancestor of the given node.
4. Return the in-order successor.
None
None
    
### >> Comparison: 94 Binary Tree Inorder Traversal [Medium] *VS* 510 Inorder Successor in BST II [Medium]
> Similarity distance: 0.4807
##### Similarities

- Both questions involve binary trees and require performing an inorder traversal.
##### Differences

- Question 94 is about performing an inorder traversal on a binary tree and returning the values in a list.
- Question 510 is about finding the inorder successor of a given node in a binary search tree.
- Question 510 also involves modifying the binary search tree by adding, deleting, or modifying nodes.
##### New Insights in 510 Inorder Successor in BST II [Medium]

- In both questions, the inorder traversal follows the left subtree, then the current node, and finally the right subtree.
- Question 510 introduces the concept of finding the inorder successor, which is the smallest node greater than the given node.


---
# 4. From 510 Inorder Successor in BST II [Medium] to 285 Inorder Successor in BST [Medium]
> Similarity Distance: 0.4349

### >> Reminder: 510 Inorder Successor in BST II [Medium]
Given a node in a binary search tree, find the in-order successor of that node in the BST. If the given node has no in-order successor, return null.
##### Optimal Python solution:
```python
class Solution:
    def inorderSuccessor(self, node: 'Node') -> 'Node':
        if node.right:
            node = node.right
            while node.left:
                node = node.left
            return node
        while node.parent and node.parent.right == node:
            node = node.parent
        return node.parent
```
The essence of this problem is to find the in-order successor of a node in a binary search tree.
    
### >> 285 Inorder Successor in BST [Medium]
Given a binary search tree and a node in it, find the in-order successor of that node in the BST.
##### Sample input:
root = [2,1,3], p = 1
##### Sample output:
2

##### Questions to ask to clarify requirements:
What is the definition of an in-order successor in a binary search tree?

##### Optimal Python solution:
```python
class Solution:
    def inorderSuccessor(self, root: 'TreeNode', p: 'TreeNode') -> 'TreeNode':
        if p.right:
            p = p.right
            while p.left:
                p = p.left
            return p
        stack, inorder = [], float('-inf')
        while stack or root:
            while root:
                stack.append(root)
                root = root.left
            root = stack.pop()
            if inorder == p.val:
                return root
            inorder = root.val
            root = root.right
        return None
```
##### Time complexity:
O(h)
##### Space complexity:
O(h)
##### Notes:
1. If the node has a right child, then the in-order successor is the leftmost node in the right subtree.
2. If the node does not have a right child, then the in-order successor is the first ancestor whose left child is also an ancestor of the node.
3. Use a stack to perform an in-order traversal of the tree.
Use a stack to perform an in-order traversal of a binary tree.
The in-order successor can be the right child of the node, or an ancestor of the node.
Avoid using recursion for the in-order traversal.
    
### >> Comparison: 510 Inorder Successor in BST II [Medium] *VS* 285 Inorder Successor in BST [Medium]
> Similarity distance: 0.4349
##### Similarities

- Both questions are related to finding the inorder successor in a binary search tree (BST).
- Both questions have a medium difficulty level.
##### Differences

- Question 510 is an extension of question 285, providing additional constraints.
- Question 510 allows the input tree to have duplicate values, while question 285 assumes distinct values.
- Question 510 requires the solution to handle the case when the given node has a right child.
- Question 285 assumes that the given node does not have a right child.
##### New Insights in 285 Inorder Successor in BST [Medium]

- Question 510 introduces the concept of handling duplicate values in a BST.
- Question 510 provides an opportunity to enhance the solution to handle the case when the given node has a right child.


---
# 5. From 102 Binary Tree Level Order Traversal [Medium] to 314 Binary Tree Vertical Order Traversal [Medium]
> Similarity Distance: 0.3755

### >> Reminder: 102 Binary Tree Level Order Traversal [Medium]
Given a binary tree, return the level order traversal of its nodes' values. (ie, from left to right, level by level).
##### Optimal Python solution:
```python
class Solution:
    def levelOrder(self, root: TreeNode) -> List[List[int]]:
        if not root:
            return []
        queue = [root]
        result = []
        while queue:
            level = []
            for _ in range(len(queue)):
                node = queue.pop(0)
                level.append(node.val)
                if node.left:
                    queue.append(node.left)
                if node.right:
                    queue.append(node.right)
            result.append(level)
        return result
```
The essence of the problem is to perform a level order traversal of a binary tree using a queue to keep track of the nodes at each level.
    
### >> 314 Binary Tree Vertical Order Traversal [Medium]
Given a binary tree, return the vertical order traversal of its nodes' values. (ie, from top to bottom, column by column).

If two nodes are in the same row and column, the order should be from left to right.

Example:

Input: [3,9,20,null,null,15,7]

   3
  /\
 /  \
 9  20
    /\
   /  \
  15   7

Output:

[
  [9],
  [3,15],
  [20],
  [7]
]
##### Sample input:
[3,9,20,null,null,15,7]
##### Sample output:
[
  [9],
  [3,15],
  [20],
  [7]
]

##### Questions to ask to clarify requirements:
What should be the output format? Can the tree have duplicate values?

##### Optimal Python solution:
```python
class Solution:
    def verticalOrder(self, root: TreeNode) -> List[List[int]]:
        if not root:
            return []
        column_table = collections.defaultdict(list)
        queue = collections.deque([(root, 0)])
        while queue:
            node, column = queue.popleft()
            column_table[column].append(node.val)
            if node.left:
                queue.append((node.left, column - 1))
            if node.right:
                queue.append((node.right, column + 1))
        return [column_table[i] for i in sorted(column_table)]
```
##### Time complexity:
O(nlogn)
##### Space complexity:
O(n)
##### Notes:
1. Perform a level order traversal of the binary tree.
2. Use a queue to keep track of the nodes and their corresponding columns.
3. Use a dictionary to store the nodes in each column.
4. Sort the columns and return the nodes in each column as the result.
1. Use a queue to perform a level order traversal of the binary tree.
2. Use a dictionary to store the nodes in each column.
3. Sort the columns and return the nodes in each column as the result.
None
None
    
### >> Comparison: 102 Binary Tree Level Order Traversal [Medium] *VS* 314 Binary Tree Vertical Order Traversal [Medium]
> Similarity distance: 0.3755
##### Similarities

- Both questions involve traversing a binary tree
- Both questions require visiting each node in a specific order
##### Differences

- 102 Binary Tree Level Order Traversal: Traverse the tree level by level, from left to right
- 314 Binary Tree Vertical Order Traversal: Traverse the tree vertically, from top to bottom
##### New Insights in 314 Binary Tree Vertical Order Traversal [Medium]

- 102 Binary Tree Level Order Traversal: Maintain a queue to keep track of nodes at each level
- 314 Binary Tree Vertical Order Traversal: Maintain a map to group nodes by their vertical positions


---
# 6. From 314 Binary Tree Vertical Order Traversal [Medium] to 199 Binary Tree Right Side View [Medium]
> Similarity Distance: 0.4781

### >> Reminder: 314 Binary Tree Vertical Order Traversal [Medium]
Given a binary tree, return the vertical order traversal of its nodes' values. (ie, from top to bottom, column by column).

If two nodes are in the same row and column, the order should be from left to right.

Example:

Input: [3,9,20,null,null,15,7]

   3
  /\
 /  \
 9  20
    /\
   /  \
  15   7

Output:

[
  [9],
  [3,15],
  [20],
  [7]
]
##### Optimal Python solution:
```python
class Solution:
    def verticalOrder(self, root: TreeNode) -> List[List[int]]:
        if not root:
            return []
        column_table = collections.defaultdict(list)
        queue = collections.deque([(root, 0)])
        while queue:
            node, column = queue.popleft()
            column_table[column].append(node.val)
            if node.left:
                queue.append((node.left, column - 1))
            if node.right:
                queue.append((node.right, column + 1))
        return [column_table[i] for i in sorted(column_table)]
```
The essence of this problem is to perform a level order traversal of the binary tree and store the nodes in each column.
    
### >> 199 Binary Tree Right Side View [Medium]
Given a binary tree, imagine yourself standing on the right side of it, return the values of the nodes you can see ordered from top to bottom.
##### Sample input:
[1,2,3,null,5,null,4]
##### Sample output:
[1,3,4]

##### Questions to ask to clarify requirements:
None

##### Optimal Python solution:
```python
class Solution:
    def rightSideView(self, root: TreeNode) -> List[int]:
        if not root:
            return []
        queue = deque([root])
        result = []
        while queue:
            level_size = len(queue)
            for i in range(level_size):
                node = queue.popleft()
                if i == level_size - 1:
                    result.append(node.val)
                if node.left:
                    queue.append(node.left)
                if node.right:
                    queue.append(node.right)
        return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
Use BFS to traverse the tree level by level. Keep track of the last node in each level.
None
None
None
    
### >> Comparison: 314 Binary Tree Vertical Order Traversal [Medium] *VS* 199 Binary Tree Right Side View [Medium]
> Similarity distance: 0.4781
##### Similarities

- Both questions involve traversing a binary tree
- Both questions require keeping track of the vertical order of nodes
##### Differences

- 314 Binary Tree Vertical Order Traversal returns the nodes in vertical order, while 199 Binary Tree Right Side View returns the nodes on the right side of the tree
- 314 Binary Tree Vertical Order Traversal uses a breadth-first search (BFS) approach, while 199 Binary Tree Right Side View uses a depth-first search (DFS) approach
##### New Insights in 199 Binary Tree Right Side View [Medium]

- 314 Binary Tree Vertical Order Traversal introduces the concept of vertical order traversal, which can be useful in various tree-related problems
- 199 Binary Tree Right Side View provides a different perspective on tree traversal by focusing on the right side of the tree

