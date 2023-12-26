
# Leetcode Intensive Tutorial Day 1 
> [Difficulty Score: 10]

> [Version: 20231226_040350]

> [Including this day, you had studied : 7 leetcode problems]


## Courses overview of the day

- 572 Subtree of Another Tree [Easy]
  - 100 Same Tree [Easy]
    - 250 Count Univalue Subtrees [Medium]
    - 98 Validate Binary Search Tree [Medium]
    - 101 Symmetric Tree [Easy]
    - 545 Boundary of Binary Tree [Medium]
    - 226 Invert Binary Tree [Easy]

#### Step by step

 - [1. From 572 Subtree of Another Tree [Easy] to 100 Same Tree [Easy]](#1-from-572-subtree-of-another-tree-easy-to-100-same-tree-easy))

 - [2. From 100 Same Tree [Easy] to 250 Count Univalue Subtrees [Medium]](#2-from-100-same-tree-easy-to-250-count-univalue-subtrees-medium))

 - [3. From 100 Same Tree [Easy] to 98 Validate Binary Search Tree [Medium]](#3-from-100-same-tree-easy-to-98-validate-binary-search-tree-medium))

 - [4. From 100 Same Tree [Easy] to 101 Symmetric Tree [Easy]](#4-from-100-same-tree-easy-to-101-symmetric-tree-easy))

 - [5. From 100 Same Tree [Easy] to 545 Boundary of Binary Tree [Medium]](#5-from-100-same-tree-easy-to-545-boundary-of-binary-tree-medium))

 - [6. From 100 Same Tree [Easy] to 226 Invert Binary Tree [Easy]](#6-from-100-same-tree-easy-to-226-invert-binary-tree-easy))

    

#### Summary


- 572 Subtree of Another Tree : Given two binary trees, check if one tree is a subtree of another tree.
- 545 Boundary of Binary Tree : The essence of the problem is to find the boundary values of a binary tree in the required order without duplicate nodes.
- 101 Symmetric Tree : The essence of the problem is to determine if a binary tree is symmetric by comparing the values of nodes and the mirror reflection of their subtrees.
- 98 Validate Binary Search Tree : The essence of this problem is to determine if a binary tree satisfies the properties of a binary search tree.
- 226 Invert Binary Tree : Inverting a binary tree.
- 250 Count Univalue Subtrees : Count the number of uni-value subtrees in a binary tree.
- 100 Same Tree : Check if two binary trees are the same by comparing their nodes recursively.
> Similarity Diameter of these problems: 0.6399


---
# 1. From 572 Subtree of Another Tree [Easy] to 100 Same Tree [Easy]
> Similarity Distance: 0.3645

### >> 572 Subtree of Another Tree [Easy]
Given two binary trees, check if one tree is a subtree of another tree.
##### Sample input:
[3,4,5,1,2,null,null,null,null,0]
[4,1,2]
##### Sample output:
true

##### Questions to ask to clarify requirements:

- Can the trees be empty?
- Can the trees have duplicate values?
- What is the maximum number of nodes in the trees?

##### Optimal Python solution:
```python
def isSubtree(s, t):
    if s is None:
        return False
    if isSameTree(s, t):
        return True
    return isSubtree(s.left, t) or isSubtree(s.right, t)

def isSameTree(p, q):
    if p is None and q is None:
        return True
    if p is None or q is None:
        return False
    return p.val == q.val and isSameTree(p.left, q.left) and isSameTree(p.right, q.right)
```
##### Time complexity:
O(m * n)
##### Space complexity:
O(n)
##### Notes:

- Check if the trees are the same
- Recursively check if the left and right subtrees of the larger tree are the same as the smaller tree

- Use recursion to check if the trees are the same.
- Handle the case when the trees are empty by returning False.
- Optimize the solution by checking if the trees are the same before recursively checking the subtrees.

- Handling the case when the trees are empty

- Using a brute force approach to check if the trees are the same
    
### >> 100 Same Tree [Easy]
Given two binary trees, write a function to check if they are the same or not.
##### Sample input:

- [1,2,3]
- [1,2,3]
##### Sample output:

- true

##### Questions to ask to clarify requirements:

- Can we assume that the trees are binary trees?
- Can we modify the trees?
- Can we use extra space?

##### Optimal Python solution:
```python

- class Solution:
-     def isSameTree(self, p: TreeNode, q: TreeNode) -> bool:
-         if not p and not q:
-             return True
-         if not p or not q or p.val != q.val:
-             return False
-         return self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)
```
##### Time complexity:
O(n)
##### Space complexity:
O(h)
##### Notes:

- Use recursive approach to compare nodes
- Check if values of nodes are equal
- Recursively compare left and right subtrees

- Use a recursive function to compare nodes
- Handle cases with different tree structures
- Optimize the space complexity if needed

- Handling cases with different tree structures

- Modifying the trees
- Using extra space
    
### >> Comparison: 572 Subtree of Another Tree [Easy] *VS* 100 Same Tree [Easy]
> Similarity distance: 0.3645
##### Similarities

- Both questions are related to trees and involve comparing two trees.
- Both questions have a binary tree as input.
- Both questions require checking if one tree is a subtree of another tree.
##### Differences

- Question 572 requires checking if one tree is a subtree of another tree, while question 100 requires checking if two trees are identical.
- Question 572 allows the subtree to be any part of the larger tree, while question 100 requires the trees to be identical in structure and node values.
- Question 572 has a time complexity of O(m*n), where m and n are the number of nodes in the two trees, while question 100 has a time complexity of O(n), where n is the number of nodes in the tree.
##### New Insights in 100 Same Tree [Easy]

- Question 572 can be solved using a recursive approach by checking if the current nodes of the two trees are equal and then recursively checking if the left and right subtrees are equal.
- Question 100 can also be solved using a recursive approach by checking if the current nodes of the two trees are equal and then recursively checking if the left and right subtrees are equal.
- Both questions can be solved using a depth-first search (DFS) approach.


---
# 2. From 100 Same Tree [Easy] to 250 Count Univalue Subtrees [Medium]
> Similarity Distance: 0.3896

### >> Reminder: 100 Same Tree [Easy]
Given two binary trees, write a function to check if they are the same or not.
##### Optimal Python solution:
```python

- class Solution:
-     def isSameTree(self, p: TreeNode, q: TreeNode) -> bool:
-         if not p and not q:
-             return True
-         if not p or not q or p.val != q.val:
-             return False
-         return self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)
```
Check if two binary trees are the same by comparing their nodes recursively.
    
### >> 250 Count Univalue Subtrees [Medium]
Given a binary tree, count the number of uni-value subtrees. A uni-value subtree means all nodes of the subtree have the same value.
##### Sample input:

- [5,1,5,5,5,null,5]
##### Sample output:

- 4

##### Questions to ask to clarify requirements:

- Can the binary tree be empty?
- Can the binary tree have duplicate values?
- Should the root node be counted as a uni-value subtree?

##### Optimal Python solution:
```python

- class Solution:
-     def countUnivalSubtrees(self, root: TreeNode) -> int:
-         self.count = 0
-         self.is_unival(root)
-         return self.count
-     def is_unival(self, node):
-         if not node:
-             return True
-         left_unival = self.is_unival(node.left)
-         right_unival = self.is_unival(node.right)
-         if (left_unival and right_unival and
-             (not node.left or node.left.val == node.val) and
-             (not node.right or node.right.val == node.val)):
-             self.count += 1
-             return True
-         return False
```
##### Time complexity:
O(n)
##### Space complexity:
O(h)
##### Notes:

- Count the number of uni-value subtrees
- Recursively check if a subtree is uni-value
- Increment count if a subtree is uni-value

- Use a helper function to keep track of the count
- Use recursion to traverse the tree

- Handling the case where the left or right subtree is None
- Incrementing the count only if the current node is a uni-value subtree

- Using global variables
- Using nested loops
    
### >> Comparison: 100 Same Tree [Easy] *VS* 250 Count Univalue Subtrees [Medium]
> Similarity distance: 0.3896
##### Similarities

- Both questions involve traversing a binary tree.
- Both questions require checking the values of nodes in the tree.
##### Differences

- Question 100 checks if two trees are structurally identical, while question 250 counts the number of subtrees that have the same value for all nodes.
- Question 100 is classified as an easy problem, while question 250 is classified as a medium problem.
- Question 100 requires comparing two trees, while question 250 requires counting subtrees.
- Question 100 has a time complexity of O(n), while question 250 has a time complexity of O(n^2).
##### New Insights in 250 Count Univalue Subtrees [Medium]

- Question 100 can be solved using a recursive approach, where we compare the values of corresponding nodes in the two trees.
- Question 250 can be solved using a recursive approach, where we check if the current subtree is a univalue subtree and recursively check its left and right subtrees.


---
# 3. From 100 Same Tree [Easy] to 98 Validate Binary Search Tree [Medium]
> Similarity Distance: 0.4822

### >> Reminder: 100 Same Tree [Easy]
Given two binary trees, write a function to check if they are the same or not.
##### Optimal Python solution:
```python

- class Solution:
-     def isSameTree(self, p: TreeNode, q: TreeNode) -> bool:
-         if not p and not q:
-             return True
-         if not p or not q or p.val != q.val:
-             return False
-         return self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)
```
Check if two binary trees are the same by comparing their nodes recursively.
    
### >> 98 Validate Binary Search Tree [Medium]
Given the root of a binary tree, determine if it is a valid binary search tree (BST).
##### Sample input:
[2,1,3]
##### Sample output:
true

##### Questions to ask to clarify requirements:
Can the binary tree have duplicate values? Can we assume the input is a valid binary tree?

##### Optimal Python solution:
```python
class Solution:
    def isValidBST(self, root: TreeNode) -> bool:
        def helper(node, lower=float('-inf'), upper=float('inf')):
            if not node:
                return True
            val = node.val
            if val <= lower or val >= upper:
                return False
            if not helper(node.right, val, upper):
                return False
            if not helper(node.left, lower, val):
                return False
            return True
        return helper(root)
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use a helper function to recursively check if each node satisfies the BST property.
2. Keep track of the lower and upper bounds for each node.
3. Use the BST property to determine the bounds for the left and right subtrees.
4. Return True if all nodes satisfy the BST property, otherwise return False.
1. Use a helper function to recursively check if each node satisfies the BST property.
2. Keep track of the lower and upper bounds for each node.
3. Use the BST property to determine the bounds for the left and right subtrees.
1. Be careful with the lower and upper bounds for each node.
2. Handle the case when the binary tree has duplicate values.
1. Avoid using an inorder traversal to check if the tree is a valid BST, as it may require additional space.
2. Avoid using a brute force approach to check if each node satisfies the BST property.
    
### >> Comparison: 100 Same Tree [Easy] *VS* 98 Validate Binary Search Tree [Medium]
> Similarity distance: 0.4822
##### Similarities

- Both questions involve binary trees.
- Both questions require traversing the tree.
- Both questions involve comparing values in the tree nodes.
##### Differences

- Question 100 checks if two trees are structurally identical, while question 98 checks if a tree is a valid binary search tree.
- Question 100 requires comparing the values of corresponding nodes in the two trees, while question 98 requires checking the ordering of values in the tree.
- Question 100 has an easy difficulty level, while question 98 has a medium difficulty level.
##### New Insights in 98 Validate Binary Search Tree [Medium]

- Question 100 teaches us how to compare the structure of two trees.
- Question 98 teaches us how to validate the ordering of values in a binary search tree.
- Both questions provide practice in tree traversal and comparison techniques.


---
# 4. From 100 Same Tree [Easy] to 101 Symmetric Tree [Easy]
> Similarity Distance: 0.4861

### >> Reminder: 100 Same Tree [Easy]
Given two binary trees, write a function to check if they are the same or not.
##### Optimal Python solution:
```python

- class Solution:
-     def isSameTree(self, p: TreeNode, q: TreeNode) -> bool:
-         if not p and not q:
-             return True
-         if not p or not q or p.val != q.val:
-             return False
-         return self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)
```
Check if two binary trees are the same by comparing their nodes recursively.
    
### >> 101 Symmetric Tree [Easy]
Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).
##### Sample input:
[1,2,2,3,4,4,3]
##### Sample output:
true

##### Questions to ask to clarify requirements:
Are empty trees considered symmetric?

##### Optimal Python solution:
```python
class Solution:
    def isSymmetric(self, root: TreeNode) -> bool:
        def isMirror(t1, t2):
            if not t1 and not t2:
                return True
            if not t1 or not t2:
                return False
            return (t1.val == t2.val) and isMirror(t1.left, t2.right) and isMirror(t1.right, t2.left)
        return isMirror(root, root)
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- The tree is symmetric if the left subtree is a mirror reflection of the right subtree.
- Two trees are a mirror reflection of each other if: 1. Their two roots have the same value. 2. The right subtree of each tree is a mirror reflection of the left subtree of the other tree.
Use a helper function to check if two trees are mirror reflections of each other.
The recursive function isMirror takes two trees as arguments and checks if they are mirror reflections of each other.
Avoid using additional data structures.
    
### >> Comparison: 100 Same Tree [Easy] *VS* 101 Symmetric Tree [Easy]
> Similarity distance: 0.4861
##### Similarities

- Both questions are related to binary trees.
- Both questions are classified as easy difficulty level.
##### Differences

- Question 100 checks if two binary trees are structurally identical, while question 101 checks if a binary tree is symmetric.
- Question 100 compares the entire tree structure, while question 101 compares the left and right subtrees of each node.
- Question 100 requires comparing the values of each node, while question 101 only requires checking the symmetry of the tree.
##### New Insights in 101 Symmetric Tree [Easy]

- Question 100 can be solved using recursion by comparing the left and right subtrees of each node.
- Question 101 can be solved using recursion by comparing the left and right subtrees of each node and checking their symmetry.


---
# 5. From 100 Same Tree [Easy] to 545 Boundary of Binary Tree [Medium]
> Similarity Distance: 0.5139

### >> Reminder: 100 Same Tree [Easy]
Given two binary trees, write a function to check if they are the same or not.
##### Optimal Python solution:
```python

- class Solution:
-     def isSameTree(self, p: TreeNode, q: TreeNode) -> bool:
-         if not p and not q:
-             return True
-         if not p or not q or p.val != q.val:
-             return False
-         return self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)
```
Check if two binary trees are the same by comparing their nodes recursively.
    
### >> 545 Boundary of Binary Tree [Medium]
Given a binary tree, return the values of its boundary in anti-clockwise direction starting from root. The boundary includes left boundary, leaves, and right boundary in order without duplicate nodes.
##### Sample input:
[1,null,2,3,4]
##### Sample output:
[1,3,4,2]

##### Questions to ask to clarify requirements:
What should be the order of the boundary values? What should be included in the boundary?

##### Optimal Python solution:
```python
class Solution:
    def boundaryOfBinaryTree(self, root: TreeNode) -> List[int]:
        if not root:
            return []
        if not root.left and not root.right:
            return [root.val]
        left_boundary = self.get_left_boundary(root.left)
        right_boundary = self.get_right_boundary(root.right)
        leaves = self.get_leaves(root)
        return [root.val] + left_boundary + leaves + right_boundary

    def get_left_boundary(self, node):
        if not node or (not node.left and not node.right):
            return []
        left_boundary = [node.val]
        if node.left:
            left_boundary += self.get_left_boundary(node.left)
        else:
            left_boundary += self.get_left_boundary(node.right)
        return left_boundary

    def get_right_boundary(self, node):
        if not node or (not node.left and not node.right):
            return []
        right_boundary = [node.val]
        if node.right:
            right_boundary += self.get_right_boundary(node.right)
        else:
            right_boundary += self.get_right_boundary(node.left)
        return right_boundary

    def get_leaves(self, node):
        if not node:
            return []
        if not node.left and not node.right:
            return [node.val]
        return self.get_leaves(node.left) + self.get_leaves(node.right)
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. The boundary of a binary tree includes the left boundary, leaves, and right boundary.
2. The left boundary is the path from the root to the leftmost leaf.
3. The right boundary is the path from the root to the rightmost leaf.
4. The leaves are the nodes without any children.
5. The boundary values should be returned in anti-clockwise direction starting from the root.
6. The boundary values should not contain any duplicate nodes.
1. Use a recursive approach to traverse the binary tree.
2. Handle the base cases separately.
3. Avoid duplicate nodes in the boundary by checking if a node has already been included.
1. Handling the case when the root has no left or right child.
2. Handling the case when the left or right boundary is empty.
3. Avoiding duplicate nodes in the boundary.
1. Avoid using recursion for each boundary type separately.
2. Avoid using a separate function for each boundary type.
    
### >> Comparison: 100 Same Tree [Easy] *VS* 545 Boundary of Binary Tree [Medium]
> Similarity distance: 0.5139
##### Similarities

- Both questions involve binary trees.
- Both questions require traversing the tree.
- Both questions involve comparing nodes in the tree.
##### Differences

- Question 100 is classified as Easy, while question 545 is classified as Medium.
- Question 100 requires checking if two trees are identical, while question 545 requires finding the boundary of a binary tree.
- Question 100 has a time complexity of O(n), while question 545 has a time complexity of O(n^2).
##### New Insights in 545 Boundary of Binary Tree [Medium]

- Question 100 can be solved using recursion by comparing the nodes of the two trees.
- Question 545 requires traversing the tree in a specific order to find the boundary nodes.


---
# 6. From 100 Same Tree [Easy] to 226 Invert Binary Tree [Easy]
> Similarity Distance: 0.5204

### >> Reminder: 100 Same Tree [Easy]
Given two binary trees, write a function to check if they are the same or not.
##### Optimal Python solution:
```python

- class Solution:
-     def isSameTree(self, p: TreeNode, q: TreeNode) -> bool:
-         if not p and not q:
-             return True
-         if not p or not q or p.val != q.val:
-             return False
-         return self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)
```
Check if two binary trees are the same by comparing their nodes recursively.
    
### >> 226 Invert Binary Tree [Easy]
Invert a binary tree.
##### Sample input:
[4,2,7,1,3,6,9]
##### Sample output:
[4,7,2,9,6,3,1]

##### Questions to ask to clarify requirements:
What should the inverted tree look like?

##### Optimal Python solution:
```python
def invertTree(self, root: TreeNode) -> TreeNode:
    if root is None:
        return None
    root.left, root.right = self.invertTree(root.right), self.invertTree(root.left)
    return root
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Invert a binary tree by swapping the left and right child of each node.
2. Recursively invert the left and right subtrees.
Use recursion to invert the binary tree.
The inversion can be done recursively by swapping the left and right child of each node.
Inverting the tree by manually rearranging the nodes.
    
### >> Comparison: 100 Same Tree [Easy] *VS* 226 Invert Binary Tree [Easy]
> Similarity distance: 0.5204
##### Similarities

- Both questions are related to binary trees.
- Both questions have a recursive solution.
- Both questions have a time complexity of O(n).
##### Differences

- Question 100 checks if two binary trees are structurally identical, while question 226 inverts a binary tree.
- Question 100 compares the values of corresponding nodes, while question 226 swaps the left and right child of each node.
- Question 100 returns true if the trees are the same, while question 226 modifies the original tree and returns the inverted tree.
##### New Insights in 226 Invert Binary Tree [Easy]

- Question 100 can be solved by comparing the values of corresponding nodes and recursively checking the left and right subtrees.
- Question 226 can be solved by swapping the left and right child of each node and recursively inverting the left and right subtrees.

