
# Leetcode Intensive Tutorial Day 34 
> [Difficulty Score: 18]

> [Version: 20231226_040350]

> [Including this day, you had studied : 275 leetcode problems]


## Courses overview of the day

- 404 Sum of Left Leaves [Easy]
  - 390 Elimination Game [Medium]
    - 450 Delete Node in a BST [Medium]
      - 237 Delete Node in a Linked List [Easy]
  - 236 Lowest Common Ancestor of a Binary Tree [Medium]
    - 235 Lowest Common Ancestor of a Binary Search Tree [Easy]
  - 69 Sqrt(x) [Medium]
    - 367 Valid Perfect Square [Easy]
      - 319 Bulb Switcher [Medium]
    - 492 Construct the Rectangle [Easy]
  - 558 Quad Tree Intersection [Easy]
    - 427 Construct Quad Tree [Medium]

#### Step by step

 - [1. From 404 Sum of Left Leaves [Easy] to 390 Elimination Game [Medium]](#1-from-404-sum-of-left-leaves-easy-to-390-elimination-game-medium))

 - [2. From 390 Elimination Game [Medium] to 450 Delete Node in a BST [Medium]](#2-from-390-elimination-game-medium-to-450-delete-node-in-a-bst-medium))

 - [3. From 450 Delete Node in a BST [Medium] to 237 Delete Node in a Linked List [Easy]](#3-from-450-delete-node-in-a-bst-medium-to-237-delete-node-in-a-linked-list-easy))

 - [4. From 404 Sum of Left Leaves [Easy] to 236 Lowest Common Ancestor of a Binary Tree [Medium]](#4-from-404-sum-of-left-leaves-easy-to-236-lowest-common-ancestor-of-a-binary-tree-medium))

 - [5. From 236 Lowest Common Ancestor of a Binary Tree [Medium] to 235 Lowest Common Ancestor of a Binary Search Tree [Easy]](#5-from-236-lowest-common-ancestor-of-a-binary-tree-medium-to-235-lowest-common-ancestor-of-a-binary-search-tree-easy))

 - [6. From 404 Sum of Left Leaves [Easy] to 69 Sqrt(x) [Medium]](#6-from-404-sum-of-left-leaves-easy-to-69-sqrtx-medium))

 - [7. From 69 Sqrt(x) [Medium] to 367 Valid Perfect Square [Easy]](#7-from-69-sqrtx-medium-to-367-valid-perfect-square-easy))

 - [8. From 367 Valid Perfect Square [Easy] to 319 Bulb Switcher [Medium]](#8-from-367-valid-perfect-square-easy-to-319-bulb-switcher-medium))

 - [9. From 69 Sqrt(x) [Medium] to 492 Construct the Rectangle [Easy]](#9-from-69-sqrtx-medium-to-492-construct-the-rectangle-easy))

 - [10. From 404 Sum of Left Leaves [Easy] to 558 Quad Tree Intersection [Easy]](#10-from-404-sum-of-left-leaves-easy-to-558-quad-tree-intersection-easy))

 - [11. From 558 Quad Tree Intersection [Easy] to 427 Construct Quad Tree [Medium]](#11-from-558-quad-tree-intersection-easy-to-427-construct-quad-tree-medium))

    

#### Summary


- 404 Sum of Left Leaves : Recursion is used to traverse the tree and find the left leaves, and the sum of the left leaves is calculated.
- 427 Construct Quad Tree : The essence of this problem is to recursively divide the grid into smaller quadrants and construct the quad tree based on the values of the quadrants.
- 319 Bulb Switcher : The essence of this problem is to find the number of square roots of a given number.
- 558 Quad Tree Intersection : Return a quad tree that represents the logical OR of two quad trees.
- 367 Valid Perfect Square : Binary search is used to find the square root of a number.
- 390 Elimination Game : Use recursion to simulate the elimination process.
- 450 Delete Node in a BST : Delete a node with a given key in a binary search tree.
- 236 Lowest Common Ancestor of a Binary Tree : Finding the lowest common ancestor of two nodes in a binary tree using recursion.
- 237 Delete Node in a Linked List : The essence of this question is to understand how to delete a node from a linked list without accessing the head of the list.
- 492 Construct the Rectangle : Find the width and height of a rectangular space given the total number of pixels and the width-to-height ratio.
- 235 Lowest Common Ancestor of a Binary Search Tree : Finding the lowest common ancestor of two nodes in a binary search tree using recursion.
- 69 Sqrt(x) : Binary search
> Similarity Diameter of these problems: 0.8085


---
# 1. From 404 Sum of Left Leaves [Easy] to 390 Elimination Game [Medium]
> Similarity Distance: 0.4636

### >> 404 Sum of Left Leaves [Easy]
Find the sum of all left leaves in a given binary tree.
##### Sample input:
[3,9,20,null,null,15,7]
##### Sample output:
24

##### Questions to ask to clarify requirements:

- What should be considered as a left leaf?
- Can the tree be empty?
- Can the tree have only one node?

##### Optimal Python solution:
```python
def sumOfLeftLeaves(root):
    if not root:
        return 0
    if root.left and not root.left.left and not root.left.right:
        return root.left.val + sumOfLeftLeaves(root.right)
    return sumOfLeftLeaves(root.left) + sumOfLeftLeaves(root.right)
```
##### Time complexity:
O(n)
##### Space complexity:
O(h)
##### Notes:

- Use recursion to traverse the tree
- Check if a node is a left leaf
- Sum the values of all left leaves

- Start with a simple example and try to find the pattern
- Use a helper function to handle the recursion

- Identifying the left leaves in the tree

- Using a global variable to store the sum
    
### >> 390 Elimination Game [Medium]
You have a list of integers from 1 to n, starting from left to right. You repeatedly eliminate the first and the last element of the list until there is only one element left. Return the last remaining element.
##### Sample input:
9
##### Sample output:
6

##### Questions to ask to clarify requirements:
What should be the output if n is less than or equal to 0?

##### Optimal Python solution:
```python
class Solution:
    def lastRemaining(self, n: int) -> int:
        left = True
        remaining = n
        step = 1
        head = 1
        while remaining > 1:
            if left or remaining % 2 == 1:
                head += step
            remaining //= 2
            step *= 2
            left = not left
        return head
```
##### Time complexity:
O(log n)
##### Space complexity:
O(1)
##### Notes:
Use recursion to simulate the elimination process.
None
None
None
    
### >> Comparison: 404 Sum of Left Leaves [Easy] *VS* 390 Elimination Game [Medium]
> Similarity distance: 0.4636
##### Similarities

- Both questions are from the LeetCode platform.
- Both questions involve manipulating numbers.
- Both questions have a specific goal to achieve.
##### Differences

- 404 Sum of Left Leaves is an Easy level question, while 390 Elimination Game is a Medium level question.
- 404 Sum of Left Leaves involves binary trees, while 390 Elimination Game involves a game of elimination.
- 404 Sum of Left Leaves requires finding the sum of the left leaves in a binary tree, while 390 Elimination Game requires finding the last remaining number after a series of elimination steps.
##### New Insights in 390 Elimination Game [Medium]

- 404 Sum of Left Leaves teaches us how to traverse a binary tree and identify left leaves.
- 390 Elimination Game teaches us how to simulate a game of elimination and find the last remaining number.


---
# 2. From 390 Elimination Game [Medium] to 450 Delete Node in a BST [Medium]
> Similarity Distance: 0.4789

### >> Reminder: 390 Elimination Game [Medium]
You have a list of integers from 1 to n, starting from left to right. You repeatedly eliminate the first and the last element of the list until there is only one element left. Return the last remaining element.
##### Optimal Python solution:
```python
class Solution:
    def lastRemaining(self, n: int) -> int:
        left = True
        remaining = n
        step = 1
        head = 1
        while remaining > 1:
            if left or remaining % 2 == 1:
                head += step
            remaining //= 2
            step *= 2
            left = not left
        return head
```
Use recursion to simulate the elimination process.
    
### >> 450 Delete Node in a BST [Medium]
Given a root node reference of a BST and a key, delete the node with the given key in the BST. Return the root node reference (possibly updated) of the BST.
##### Sample input:
root = [5,3,6,2,4,null,7]
key = 3
##### Sample output:
[5,4,6,2,null,null,7]

##### Questions to ask to clarify requirements:
What should be done if the key is not found in the tree? Can the tree be empty?

##### Optimal Python solution:
```python
class Solution:
    def deleteNode(self, root, key):
        if not root:
            return None
        if key < root.val:
            root.left = self.deleteNode(root.left, key)
        elif key > root.val:
            root.right = self.deleteNode(root.right, key)
        else:
            if not root.left:
                return root.right
            if not root.right:
                return root.left
            min_node = self.findMin(root.right)
            root.val = min_node.val
            root.right = self.deleteNode(root.right, min_node.val)
        return root

    def findMin(self, node):
        while node.left:
            node = node.left
        return node
```
##### Time complexity:
O(h)
##### Space complexity:
O(h)
##### Notes:
1. Use recursion to find the node to delete
2. Handle three cases: node has no children, node has one child, node has two children
3. Use the findMin function to find the minimum value in the right subtree
4. Time complexity: O(h), where h is the height of the tree
5. Space complexity: O(h) for the recursive call stack
Use recursion to simplify the deletion process
Handling nodes with two children
Using an iterative approach for finding the minimum value in the right subtree
    
### >> Comparison: 390 Elimination Game [Medium] *VS* 450 Delete Node in a BST [Medium]
> Similarity distance: 0.4789
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve manipulating data structures.
- Both questions require a good understanding of algorithms and problem-solving skills.
##### Differences

- 390 Elimination Game involves a game-like scenario where numbers are eliminated based on a specific pattern.
- 450 Delete Node in a BST involves deleting a node from a binary search tree while maintaining the binary search tree property.
##### New Insights in 450 Delete Node in a BST [Medium]

- 390 Elimination Game: The insight gained from this question is understanding the pattern of elimination and finding a mathematical approach to solve it efficiently.
- 450 Delete Node in a BST: The insight gained from this question is understanding how to handle the deletion of a node in a binary search tree and maintaining the binary search tree property.


---
# 3. From 450 Delete Node in a BST [Medium] to 237 Delete Node in a Linked List [Easy]
> Similarity Distance: 0.4246

### >> Reminder: 450 Delete Node in a BST [Medium]
Given a root node reference of a BST and a key, delete the node with the given key in the BST. Return the root node reference (possibly updated) of the BST.
##### Optimal Python solution:
```python
class Solution:
    def deleteNode(self, root, key):
        if not root:
            return None
        if key < root.val:
            root.left = self.deleteNode(root.left, key)
        elif key > root.val:
            root.right = self.deleteNode(root.right, key)
        else:
            if not root.left:
                return root.right
            if not root.right:
                return root.left
            min_node = self.findMin(root.right)
            root.val = min_node.val
            root.right = self.deleteNode(root.right, min_node.val)
        return root

    def findMin(self, node):
        while node.left:
            node = node.left
        return node
```
Delete a node with a given key in a binary search tree.
    
### >> 237 Delete Node in a Linked List [Easy]
Write a function to delete a node in a singly-linked list. You will not be given access to the head of the list, instead you will be given access to the node to be deleted directly.
##### Sample input:
4
5
1
9
node = 5
##### Sample output:
4
1
9

##### Questions to ask to clarify requirements:
What is the range of values for the nodes? Can the node to be deleted be the last node in the list?

##### Optimal Python solution:
```python
def deleteNode(node):
    node.val = node.next.val
    node.next = node.next.next
```
##### Time complexity:
O(1)
##### Space complexity:
O(1)
##### Notes:
The given node is guaranteed to be in the linked list except the tail node. The value of the node to be deleted can be modified instead of deleting the node itself.
Remember that you are not given access to the head of the list, so you cannot traverse the list from the beginning.
The trick is to modify the value of the node to be deleted instead of deleting the node itself.
Avoid trying to access the head of the linked list.
    
### >> Comparison: 450 Delete Node in a BST [Medium] *VS* 237 Delete Node in a Linked List [Easy]
> Similarity distance: 0.4246
##### Similarities

- Both questions involve deleting a node from a data structure.
- Both questions require updating the links or references to maintain the structure of the data.
- Both questions have a time complexity of O(log n) or O(n) depending on the implementation.
##### Differences

- 450 Delete Node in a BST is a medium-level question, while 237 Delete Node in a Linked List is an easy-level question.
- 450 Delete Node in a BST involves deleting a node from a binary search tree, while 237 Delete Node in a Linked List involves deleting a node from a singly linked list.
- 450 Delete Node in a BST requires finding the node to be deleted based on its value and maintaining the binary search tree property, while 237 Delete Node in a Linked List requires finding the node to be deleted based on its value and updating the links to bypass the node.
- 450 Delete Node in a BST may require rearranging the remaining nodes to maintain the binary search tree property, while 237 Delete Node in a Linked List only requires updating the links to bypass the node.
##### New Insights in 237 Delete Node in a Linked List [Easy]

- 450 Delete Node in a BST teaches us how to delete a node from a binary search tree while maintaining its properties.
- 237 Delete Node in a Linked List teaches us how to delete a node from a linked list by updating the links.


---
# 4. From 404 Sum of Left Leaves [Easy] to 236 Lowest Common Ancestor of a Binary Tree [Medium]
> Similarity Distance: 0.4825

### >> Reminder: 404 Sum of Left Leaves [Easy]
Find the sum of all left leaves in a given binary tree.
##### Optimal Python solution:
```python
def sumOfLeftLeaves(root):
    if not root:
        return 0
    if root.left and not root.left.left and not root.left.right:
        return root.left.val + sumOfLeftLeaves(root.right)
    return sumOfLeftLeaves(root.left) + sumOfLeftLeaves(root.right)
```
Recursion is used to traverse the tree and find the left leaves, and the sum of the left leaves is calculated.
    
### >> 236 Lowest Common Ancestor of a Binary Tree [Medium]
Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.
##### Sample input:

- root = [3,5,1,6,2,0,8,null,null,7,4]
- p = 5
- q = 1
##### Sample output:
3

##### Questions to ask to clarify requirements:

- Can we assume that the given nodes are present in the tree?
- What should be returned if one of the nodes is not present in the tree?

##### Optimal Python solution:
```python

- def lowestCommonAncestor(root, p, q):
-     if root is None or root == p or root == q:
-         return root
-     left = lowestCommonAncestor(root.left, p, q)
-     right = lowestCommonAncestor(root.right, p, q)
-     if left and right:
-         return root
-     return left or right
```
##### Time complexity:
O(N)
##### Space complexity:
O(N)
##### Notes:

- The lowest common ancestor is the node that is common to both given nodes and is the lowest node in the tree.
- The given tree is a binary tree, so there is no order of values in the nodes.

- Make sure to handle the case when one of the nodes is not present in the tree.
- Use the property of the binary tree to optimize the solution.

- Handling the case when one of the nodes is not present in the tree.

- Using extra space for storing the path from root to the given nodes.
    
### >> Comparison: 404 Sum of Left Leaves [Easy] *VS* 236 Lowest Common Ancestor of a Binary Tree [Medium]
> Similarity distance: 0.4825
##### Similarities

- Both questions involve binary trees.
- Both questions require traversing the tree.
- Both questions have a recursive solution.
##### Differences

- 404 Sum of Left Leaves is an easy level question, while 236 Lowest Common Ancestor of a Binary Tree is a medium level question.
- 404 Sum of Left Leaves requires calculating the sum of left leaves in a binary tree, while 236 Lowest Common Ancestor of a Binary Tree requires finding the lowest common ancestor of two nodes in a binary tree.
##### New Insights in 236 Lowest Common Ancestor of a Binary Tree [Medium]

- 404 Sum of Left Leaves teaches us how to identify and calculate the sum of left leaves in a binary tree.
- 236 Lowest Common Ancestor of a Binary Tree teaches us how to find the lowest common ancestor of two nodes in a binary tree.


---
# 5. From 236 Lowest Common Ancestor of a Binary Tree [Medium] to 235 Lowest Common Ancestor of a Binary Search Tree [Easy]
> Similarity Distance: 0.0570

### >> Reminder: 236 Lowest Common Ancestor of a Binary Tree [Medium]
Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.
##### Optimal Python solution:
```python

- def lowestCommonAncestor(root, p, q):
-     if root is None or root == p or root == q:
-         return root
-     left = lowestCommonAncestor(root.left, p, q)
-     right = lowestCommonAncestor(root.right, p, q)
-     if left and right:
-         return root
-     return left or right
```
Finding the lowest common ancestor of two nodes in a binary tree using recursion.
    
### >> 235 Lowest Common Ancestor of a Binary Search Tree [Easy]
Given a binary search tree (BST), find the lowest common ancestor (LCA) of two given nodes in the BST.
##### Sample input:

- root = [6,2,8,0,4,7,9,null,null,3,5]
- p = 2
- q = 8
##### Sample output:
6

##### Questions to ask to clarify requirements:

- Can we assume that the given nodes are present in the BST?
- What should be returned if one of the nodes is not present in the BST?

##### Optimal Python solution:
```python

- def lowestCommonAncestor(root, p, q):
-     if root.val > p.val and root.val > q.val:
-         return lowestCommonAncestor(root.left, p, q)
-     elif root.val < p.val and root.val < q.val:
-         return lowestCommonAncestor(root.right, p, q)
-     else:
-         return root
```
##### Time complexity:
O(log N)
##### Space complexity:
O(1)
##### Notes:

- The lowest common ancestor is the node that is common to both given nodes and is the lowest node in the tree.
- The given tree is a binary search tree, so the values of nodes in the left subtree are less than the root value, and the values of nodes in the right subtree are greater than the root value.

- Make sure to handle the case when one of the nodes is not present in the BST.
- Use the property of the binary search tree to optimize the solution.

- Handling the case when one of the nodes is not present in the BST.

- Using extra space for storing the path from root to the given nodes.
    
### >> Comparison: 236 Lowest Common Ancestor of a Binary Tree [Medium] *VS* 235 Lowest Common Ancestor of a Binary Search Tree [Easy]
> Similarity distance: 0.0570
##### Similarities

- Both questions involve finding the lowest common ancestor of two nodes in a binary tree.
- Both questions require traversing the binary tree to find the common ancestor.
##### Differences

- Question 236 is a medium-level problem, while question 235 is an easy-level problem.
- Question 236 allows for any binary tree, while question 235 assumes a binary search tree.
- Question 236 has a more complex solution compared to question 235.
- Question 236 requires additional checks to handle cases where the nodes are not present in the tree.
##### New Insights in 235 Lowest Common Ancestor of a Binary Search Tree [Easy]

- Question 236 introduces the concept of finding the lowest common ancestor in a general binary tree.
- Question 236 requires a recursive approach to handle all possible cases.


---
# 6. From 404 Sum of Left Leaves [Easy] to 69 Sqrt(x) [Medium]
> Similarity Distance: 0.5224

### >> Reminder: 404 Sum of Left Leaves [Easy]
Find the sum of all left leaves in a given binary tree.
##### Optimal Python solution:
```python
def sumOfLeftLeaves(root):
    if not root:
        return 0
    if root.left and not root.left.left and not root.left.right:
        return root.left.val + sumOfLeftLeaves(root.right)
    return sumOfLeftLeaves(root.left) + sumOfLeftLeaves(root.right)
```
Recursion is used to traverse the tree and find the left leaves, and the sum of the left leaves is calculated.
    
### >> 69 Sqrt(x) [Medium]
Implement int sqrt(int x).
##### Sample input:
4
8
##### Sample output:
2
2

##### Questions to ask to clarify requirements:
What should be returned if x is negative?

##### Optimal Python solution:
```python
class Solution:
    def mySqrt(self, x: int) -> int:
        if x == 0:
            return 0
        left, right = 1, x
        while left <= right:
            mid = (left + right) // 2
            if mid * mid > x:
                right = mid - 1
            else:
                left = mid + 1
        return right
```
##### Time complexity:
O(log(x))
##### Space complexity:
O(1)
##### Notes:
1. Use binary search to find the square root.
2. Start with left = 1 and right = x.
3. Update left and right based on the comparison of mid * mid and x.
4. Return right as the square root.
1. Be careful with the termination condition of the binary search loop.
2. Use integer arithmetic to avoid floating point errors.
None
None
    
### >> Comparison: 404 Sum of Left Leaves [Easy] *VS* 69 Sqrt(x) [Medium]
> Similarity distance: 0.5224
##### Similarities

- Both questions are from LeetCode.
- Both questions have a difficulty level assigned to them.
- Both questions require mathematical calculations.
- Both questions have a specific input and output format.
##### Differences

- 404 Sum of Left Leaves is an easy level question, while 69 Sqrt(x) is a medium level question.
- 404 Sum of Left Leaves involves binary trees, while 69 Sqrt(x) involves mathematical calculations.
- 404 Sum of Left Leaves requires finding the sum of left leaves in a binary tree, while 69 Sqrt(x) requires finding the square root of a given number.
- 404 Sum of Left Leaves has a time complexity of O(n), while 69 Sqrt(x) has a time complexity of O(log(x)).
##### New Insights in 69 Sqrt(x) [Medium]

- From 404 Sum of Left Leaves, we can learn how to traverse a binary tree and identify left leaves.
- From 69 Sqrt(x), we can learn how to calculate the square root of a number using binary search.


---
# 7. From 69 Sqrt(x) [Medium] to 367 Valid Perfect Square [Easy]
> Similarity Distance: 0.1811

### >> Reminder: 69 Sqrt(x) [Medium]
Implement int sqrt(int x).
##### Optimal Python solution:
```python
class Solution:
    def mySqrt(self, x: int) -> int:
        if x == 0:
            return 0
        left, right = 1, x
        while left <= right:
            mid = (left + right) // 2
            if mid * mid > x:
                right = mid - 1
            else:
                left = mid + 1
        return right
```
Binary search
    
### >> 367 Valid Perfect Square [Easy]
Given a positive integer num, write a function which returns True if num is a perfect square else False.
##### Sample input:
16
14
##### Sample output:
True
False

##### Questions to ask to clarify requirements:
What is the range of the input? Can the input be negative?

##### Optimal Python solution:
```python
class Solution:
    def isPerfectSquare(self, num: int) -> bool:
        left = 1
        right = num
        while left <= right:
            mid = (left + right) // 2
            if mid * mid == num:
                return True
            elif mid * mid < num:
                left = mid + 1
            else:
                right = mid - 1
        return False
```
##### Time complexity:
O(log n)
##### Space complexity:
O(1)
##### Notes:
1. Use binary search to find the square root of the number.
2. If the square of the mid value is equal to the number, return True.
3. If the square of the mid value is less than the number, update the left pointer.
4. If the square of the mid value is greater than the number, update the right pointer.
5. If the left pointer is greater than the right pointer, return False.
1. Be careful with the termination condition of the binary search loop.
2. Handle the case when the input is 1 separately.
None
None
    
### >> Comparison: 69 Sqrt(x) [Medium] *VS* 367 Valid Perfect Square [Easy]
> Similarity distance: 0.1811
##### Similarities

- Both questions involve finding the square root of a number.
##### Differences

- Question 69 is rated as medium difficulty, while question 367 is rated as easy difficulty.
- Question 69 requires implementing a square root function, while question 367 requires checking if a number is a perfect square.
- Question 69 allows the use of built-in functions, while question 367 requires a solution without using built-in functions.
##### New Insights in 367 Valid Perfect Square [Easy]

- Question 69 can be solved using binary search, while question 367 can be solved using a mathematical property of perfect squares.


---
# 8. From 367 Valid Perfect Square [Easy] to 319 Bulb Switcher [Medium]
> Similarity Distance: 0.5261

### >> Reminder: 367 Valid Perfect Square [Easy]
Given a positive integer num, write a function which returns True if num is a perfect square else False.
##### Optimal Python solution:
```python
class Solution:
    def isPerfectSquare(self, num: int) -> bool:
        left = 1
        right = num
        while left <= right:
            mid = (left + right) // 2
            if mid * mid == num:
                return True
            elif mid * mid < num:
                left = mid + 1
            else:
                right = mid - 1
        return False
```
Binary search is used to find the square root of a number.
    
### >> 319 Bulb Switcher [Medium]
There are n bulbs that are initially off. You first turn on all the bulbs, then you turn off every second bulb. On the third round, you toggle every third bulb (turning on if it's off or turning off if it's on). For the i-th round, you toggle every i bulb. For the n-th round, you only toggle the last bulb. Return the number of bulbs that are on after n rounds.
##### Sample input:
3
5
10
##### Sample output:
1
2
3

##### Questions to ask to clarify requirements:
1. Can the number of bulbs be zero? 2. Can the number of rounds be zero? 3. Can the number of bulbs and rounds be negative?

##### Optimal Python solution:
```python
class Solution:
    def bulbSwitch(self, n: int) -> int:
        return int(n ** 0.5)
```
##### Time complexity:
O(1)
##### Space complexity:
O(1)
##### Notes:
1. The bulbs that are toggled an odd number of times will be on, while the bulbs that are toggled an even number of times will be off. 2. The number of times a bulb is toggled is equal to the number of its divisors. 3. The number of divisors of a number is equal to the number of its square roots.
None
None
None
    
### >> Comparison: 367 Valid Perfect Square [Easy] *VS* 319 Bulb Switcher [Medium]
> Similarity distance: 0.5261
##### Similarities

- Both questions involve manipulating numbers.
- Both questions require determining a specific property of the given numbers.
##### Differences

- Question 367 is classified as Easy, while question 319 is classified as Medium.
- Question 367 involves checking if a number is a perfect square, while question 319 involves toggling the state of bulbs.
- Question 367 requires mathematical calculations, while question 319 requires logical operations.
- Question 367 has a straightforward solution using binary search, while question 319 has a more complex solution involving factors of the given number.
##### New Insights in 319 Bulb Switcher [Medium]

- Question 367 teaches us how to efficiently check if a number is a perfect square using binary search.
- Question 319 teaches us how to determine the number of bulbs that are on after a certain number of toggles.


---
# 9. From 69 Sqrt(x) [Medium] to 492 Construct the Rectangle [Easy]
> Similarity Distance: 0.5113

### >> Reminder: 69 Sqrt(x) [Medium]
Implement int sqrt(int x).
##### Optimal Python solution:
```python
class Solution:
    def mySqrt(self, x: int) -> int:
        if x == 0:
            return 0
        left, right = 1, x
        while left <= right:
            mid = (left + right) // 2
            if mid * mid > x:
                right = mid - 1
            else:
                left = mid + 1
        return right
```
Binary search
    
### >> 492 Construct the Rectangle [Easy]
A web developer needs to know the width and height of a rectangular space on the screen. You are given the total number of pixels available on the screen and the ratio of width to height. Write a function to construct the width and height of the rectangular space in pixels such that the width is greater than or equal to the height.
##### Sample input:
area = 4
##### Sample output:
[2, 2]

##### Questions to ask to clarify requirements:

- Can the width and height be floating-point numbers?
- Can the width and height be negative?
- What is the maximum value of the area?

##### Optimal Python solution:
```python
class Solution:
    def constructRectangle(self, area: int) -> List[int]:
        width = int(math.sqrt(area))
        while area % width != 0:
            width -= 1
        return [area // width, width]
```
##### Time complexity:
O(sqrt(area))
##### Space complexity:
O(1)
##### Notes:

- Use the square root of the area to find the initial width
- Iterate backwards from the initial width to find the width that evenly divides the area

- Use the math.sqrt() function to find the square root of a number
- Start the iteration from the square root of the area

- Finding the width that evenly divides the area

- Avoid using a brute force approach to find the width
    
### >> Comparison: 69 Sqrt(x) [Medium] *VS* 492 Construct the Rectangle [Easy]
> Similarity distance: 0.5113
##### Similarities

- Both questions involve mathematical calculations.
- Both questions require finding a specific value.
##### Differences

- Question 69 is a medium-level question, while question 492 is an easy-level question.
- Question 69 involves finding the square root of a number, while question 492 involves constructing a rectangle.
- Question 69 requires using a mathematical algorithm, while question 492 requires logical thinking.
- Question 69 has a time complexity of O(log(x)), while question 492 has a time complexity of O(sqrt(x)).
##### New Insights in 492 Construct the Rectangle [Easy]

- Question 69 teaches us how to efficiently find the square root of a number using binary search.
- Question 492 teaches us how to construct a rectangle with the given area using the minimum possible difference in length and width.


---
# 10. From 404 Sum of Left Leaves [Easy] to 558 Quad Tree Intersection [Easy]
> Similarity Distance: 0.5645

### >> Reminder: 404 Sum of Left Leaves [Easy]
Find the sum of all left leaves in a given binary tree.
##### Optimal Python solution:
```python
def sumOfLeftLeaves(root):
    if not root:
        return 0
    if root.left and not root.left.left and not root.left.right:
        return root.left.val + sumOfLeftLeaves(root.right)
    return sumOfLeftLeaves(root.left) + sumOfLeftLeaves(root.right)
```
Recursion is used to traverse the tree and find the left leaves, and the sum of the left leaves is calculated.
    
### >> 558 Quad Tree Intersection [Easy]
Given two quad trees representing binary trees, return a quad tree that represents the logical OR (or union) of the two trees.
##### Sample input:
tree1 = [[T, T, T, T, T, T, T, T], [T, T, T, T, T, T, T, T], [T, T, T, T, T, T, T, T], [T, T, T, T, T, T, T, T], [T, T, T, T, T, T, T, T], [T, T, T, T, T, T, T, T], [T, T, T, T, T, T, T, T], [T, T, T, T, T, T, T, T]]
tree2 = [[F, F, F, F, F, F, F, F], [F, F, F, F, F, F, F, F], [F, F, F, F, F, F, F, F], [F, F, F, F, F, F, F, F], [F, F, F, F, F, F, F, F], [F, F, F, F, F, F, F, F], [F, F, F, F, F, F, F, F], [F, F, F, F, F, F, F, F]]
##### Sample output:
[[T, T, T, T, T, T, T, T]]

##### Questions to ask to clarify requirements:
What is the definition of a quad tree? Can the input trees be empty?

##### Optimal Python solution:
```python
def intersect(quadTree1, quadTree2):
    if quadTree1.isLeaf:
        return quadTree1 if quadTree1.val else quadTree2
    elif quadTree2.isLeaf:
        return quadTree2 if quadTree2.val else quadTree1
    else:
        topLeft = intersect(quadTree1.topLeft, quadTree2.topLeft)
        topRight = intersect(quadTree1.topRight, quadTree2.topRight)
        bottomLeft = intersect(quadTree1.bottomLeft, quadTree2.bottomLeft)
        bottomRight = intersect(quadTree1.bottomRight, quadTree2.bottomRight)
        if topLeft.isLeaf and topRight.isLeaf and bottomLeft.isLeaf and bottomRight.isLeaf and topLeft.val == topRight.val == bottomLeft.val == bottomRight.val:
            return Node(topLeft.val, True, None, None, None, None)
        else:
            return Node(False, False, topLeft, topRight, bottomLeft, bottomRight)
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Check if either quad tree is a leaf
2. Recursively intersect the corresponding quadrants
3. Combine the intersected quadrants
No specific tips
No tricky parts
No specific pitfalls
    
### >> Comparison: 404 Sum of Left Leaves [Easy] *VS* 558 Quad Tree Intersection [Easy]
> Similarity distance: 0.5645
##### Similarities

- Both questions are classified as 'Easy' level.
- Both questions involve tree data structures.
- Both questions require traversal of the tree.
- Both questions involve some form of computation or calculation.
##### Differences

- 404 Sum of Left Leaves focuses on finding the sum of all left leaves in a binary tree.
- 558 Quad Tree Intersection focuses on finding the intersection of two quad trees.
- 404 Sum of Left Leaves requires identifying and summing the values of left leaves.
- 558 Quad Tree Intersection requires merging and simplifying quad trees to find the intersection.
##### New Insights in 558 Quad Tree Intersection [Easy]

- 404 Sum of Left Leaves teaches us how to identify and sum the values of left leaves in a binary tree.
- 558 Quad Tree Intersection teaches us how to merge and simplify quad trees to find the intersection.


---
# 11. From 558 Quad Tree Intersection [Easy] to 427 Construct Quad Tree [Medium]
> Similarity Distance: 0.4951

### >> Reminder: 558 Quad Tree Intersection [Easy]
Given two quad trees representing binary trees, return a quad tree that represents the logical OR (or union) of the two trees.
##### Optimal Python solution:
```python
def intersect(quadTree1, quadTree2):
    if quadTree1.isLeaf:
        return quadTree1 if quadTree1.val else quadTree2
    elif quadTree2.isLeaf:
        return quadTree2 if quadTree2.val else quadTree1
    else:
        topLeft = intersect(quadTree1.topLeft, quadTree2.topLeft)
        topRight = intersect(quadTree1.topRight, quadTree2.topRight)
        bottomLeft = intersect(quadTree1.bottomLeft, quadTree2.bottomLeft)
        bottomRight = intersect(quadTree1.bottomRight, quadTree2.bottomRight)
        if topLeft.isLeaf and topRight.isLeaf and bottomLeft.isLeaf and bottomRight.isLeaf and topLeft.val == topRight.val == bottomLeft.val == bottomRight.val:
            return Node(topLeft.val, True, None, None, None, None)
        else:
            return Node(False, False, topLeft, topRight, bottomLeft, bottomRight)
```
Return a quad tree that represents the logical OR of two quad trees.
    
### >> 427 Construct Quad Tree [Medium]
Given a n * n matrix grid of 0's and 1's only. We want to represent the grid with a Quad-Tree.
##### Sample input:

- [[0,1],[1,0]]
##### Sample output:

- [[0,1],[1,0],[1,1],[1,1],[1,0]]

##### Questions to ask to clarify requirements:

- What is the maximum size of the grid?
- Can the grid contain any other values besides 0 and 1?
- What should be returned if the grid is empty?

##### Optimal Python solution:
```python

- class Solution:
-     def construct(self, grid: List[List[int]]) -> 'Node':
-         def dfs(x, y, n):
-             if n == 1:
-                 return Node(grid[x][y] == 1, True, None, None, None, None)
-             n //= 2
-             a = dfs(x, y, n)
-             b = dfs(x, y + n, n)
-             c = dfs(x + n, y, n)
-             d = dfs(x + n, y + n, n)
-             if a.isLeaf and b.isLeaf and c.isLeaf and d.isLeaf and a.val == b.val == c.val == d.val:
-                 return Node(a.val, True, None, None, None, None)
-             else:
-                 return Node(False, False, a, b, c, d)
-         return dfs(0, 0, len(grid))
- 
```
##### Time complexity:
O(n^2)
##### Space complexity:
O(n^2)
##### Notes:

- Use recursion to divide the grid into smaller quadrants
- Check if all quadrants are leaf nodes with the same value
- Return the root node of the quad tree

- Use helper functions to divide the grid into quadrants and construct the quad tree recursively.
- Handle the base case when the size of the grid is 1.
- Check if all quadrants are leaf nodes with the same value to determine if they can be merged into a single leaf node.

- Handling empty grid
- Checking if all quadrants are leaf nodes

- Using a non-recursive approach
- Creating unnecessary nodes
    
### >> Comparison: 558 Quad Tree Intersection [Easy] *VS* 427 Construct Quad Tree [Medium]
> Similarity distance: 0.4951
##### Similarities

- Both questions involve quad trees.
- Both questions require the intersection of two quad trees.
##### Differences

- Question 558 is classified as Easy, while question 427 is classified as Medium.
- Question 558 asks for the intersection of two quad trees, while question 427 asks for the construction of a quad tree.
- Question 558 has a time complexity of O(n), while question 427 has a time complexity of O(n^2).
##### New Insights in 427 Construct Quad Tree [Medium]

- Question 558 introduces the concept of quad trees and their intersection.
- Question 427 introduces the concept of constructing a quad tree from a given matrix.

