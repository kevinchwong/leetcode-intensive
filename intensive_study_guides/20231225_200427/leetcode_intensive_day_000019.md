
# Leetcode Intensive Tutorial Day 19 
> [Difficulty Score: 15]

> [Version: 20231225_200427]

## Courses overview of the day

- 225 Implement Stack using Queues [Easy]
  - 341 Flatten Nested List Iterator [Medium]
    - 173 Binary Search Tree Iterator [Medium]
    - 255 Verify Preorder Sequence in Binary Search Tree [Medium]
      - 105 Construct Binary Tree from Preorder and Inorder Traversal [Medium]
        - 106 Construct Binary Tree from Inorder and Postorder Traversal [Medium]
      - 331 Verify Preorder Serialization of a Binary Tree [Medium]
    - 251 Flatten 2D Vector [Medium]

#### Steps by steps

 - [1. From 225 Implement Stack using Queues [Easy] to 341 Flatten Nested List Iterator [Medium]](#1-from-225-implement-stack-using-queues-easy-to-341-flatten-nested-list-iterator-medium)

 - [2. From 341 Flatten Nested List Iterator [Medium] to 173 Binary Search Tree Iterator [Medium]](#2-from-341-flatten-nested-list-iterator-medium-to-173-binary-search-tree-iterator-medium)

 - [3. From 341 Flatten Nested List Iterator [Medium] to 255 Verify Preorder Sequence in Binary Search Tree [Medium]](#3-from-341-flatten-nested-list-iterator-medium-to-255-verify-preorder-sequence-in-binary-search-tree-medium)

 - [4. From 255 Verify Preorder Sequence in Binary Search Tree [Medium] to 105 Construct Binary Tree from Preorder and Inorder Traversal [Medium]](#4-from-255-verify-preorder-sequence-in-binary-search-tree-medium-to-105-construct-binary-tree-from-preorder-and-inorder-traversal-medium)

 - [5. From 105 Construct Binary Tree from Preorder and Inorder Traversal [Medium] to 106 Construct Binary Tree from Inorder and Postorder Traversal [Medium]](#5-from-105-construct-binary-tree-from-preorder-and-inorder-traversal-medium-to-106-construct-binary-tree-from-inorder-and-postorder-traversal-medium)

 - [6. From 255 Verify Preorder Sequence in Binary Search Tree [Medium] to 331 Verify Preorder Serialization of a Binary Tree [Medium]](#6-from-255-verify-preorder-sequence-in-binary-search-tree-medium-to-331-verify-preorder-serialization-of-a-binary-tree-medium)

 - [7. From 341 Flatten Nested List Iterator [Medium] to 251 Flatten 2D Vector [Medium]](#7-from-341-flatten-nested-list-iterator-medium-to-251-flatten-2d-vector-medium)

#### Summary


- 251 Flatten 2D Vector : Implement an iterator to flatten a 2D vector.
- 255 Verify Preorder Sequence in Binary Search Tree : The essence of this problem is to determine if a given array is a valid preorder traversal of a binary search tree.
- 331 Verify Preorder Serialization of a Binary Tree : The essence of this problem is to simulate the preorder traversal of a binary tree and check if the given preorder string is a valid serialization.
- 173 Binary Search Tree Iterator : Implement an iterator over a binary search tree using a stack to simulate the inorder traversal.
- 341 Flatten Nested List Iterator : Flatten a nested list using a stack
- 106 Construct Binary Tree from Inorder and Postorder Traversal : Given inorder and postorder traversal of a tree, construct the binary tree.
- 105 Construct Binary Tree from Preorder and Inorder Traversal : Given preorder and inorder traversal of a tree, construct the binary tree.
- 225 Implement Stack using Queues : Implementing a stack using queues.
> Similarity Diameter of these problems: 0.8581


---
# 1. From 225 Implement Stack using Queues [Easy] to 341 Flatten Nested List Iterator [Medium]
> Similarity Distance: 0.6995

### >> 225 Implement Stack using Queues [Easy]
Implement a stack using queues.
##### Sample input:
push(1), push(2), top(), pop(), empty()
##### Sample output:
null, null, 2, 2, false

##### Questions to ask to clarify requirements:
What should the stack do when popping or peeking an empty stack?

##### Optimal Python solution:
```python
class MyStack:
    def __init__(self):
        self.queue = []

    def push(self, x: int) -> None:
        self.queue.append(x)

    def pop(self) -> int:
        return self.queue.pop()

    def top(self) -> int:
        return self.queue[-1]

    def empty(self) -> bool:
        return len(self.queue) == 0
```
##### Time complexity:
Push: O(1), Pop: O(n), Top: O(1), Empty: O(1)
##### Space complexity:
O(n)
##### Notes:
1. Use a queue to implement a stack.
2. Push operation can be done by adding the element to the back of the queue.
3. Pop operation can be done by removing the element from the front of the queue.
4. Top operation can be done by returning the last element of the queue.
5. Empty operation can be done by checking if the queue is empty.
Use two queues to simulate stack operations.
The pop operation is not efficient as it requires rearranging the elements in the queue.
Using a list as a stack directly.
    
### >> 341 Flatten Nested List Iterator [Medium]
Implement an iterator to flatten a nested list of integers. Each element is either an integer or a list whose elements may also be integers or other lists.
##### Sample input:
[[1,1],2,[1,1]]
##### Sample output:
[1,1,2,1,1]

##### Questions to ask to clarify requirements:

- What is the maximum depth of the nested list?
- Can the nested list be empty?
- Can the nested list contain duplicates?

##### Optimal Python solution:
```python
class NestedIterator:
    def __init__(self, nestedList: [NestedInteger]):
        self.stack = nestedList[::-1]

    def next(self) -> int:
        return self.stack.pop().getInteger()

    def hasNext(self) -> bool:
        while self.stack:
            top = self.stack[-1]
            if top.isInteger():
                return True
            self.stack = self.stack[:-1] + top.getList()[::-1]
        return False
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- Use a stack to store the nested list in reverse order
- Use a while loop to iterate through the stack and flatten the list

- Use the NestedInteger class provided in the problem description
- Reverse the nested list before storing it in the stack

- Handling empty nested lists
- Handling nested lists with varying depths

- Using recursion to flatten the nested list
    
### >> Comparison: 225 Implement Stack using Queues [Easy] *VS* 341 Flatten Nested List Iterator [Medium]
> Similarity distance: 0.6995
##### Similarities

- Both questions involve data structures
- Both questions require implementing a specific functionality
- Both questions have a specific level of difficulty assigned to them
##### Differences

- 225 Implement Stack using Queues is an Easy level question, while 341 Flatten Nested List Iterator is a Medium level question
- 225 Implement Stack using Queues involves using queues to implement a stack, while 341 Flatten Nested List Iterator involves flattening a nested list and implementing an iterator
- 225 Implement Stack using Queues requires implementing push, pop, top, and empty operations, while 341 Flatten Nested List Iterator requires implementing hasNext and next operations
- 225 Implement Stack using Queues uses two queues, while 341 Flatten Nested List Iterator uses a stack and an iterator
##### New Insights in 341 Flatten Nested List Iterator [Medium]

- 225 Implement Stack using Queues teaches how to implement a stack using queues
- 341 Flatten Nested List Iterator teaches how to flatten a nested list and implement an iterator


---
# 2. From 341 Flatten Nested List Iterator [Medium] to 173 Binary Search Tree Iterator [Medium]
> Similarity Distance: 0.5690

### >> Reminder: 341 Flatten Nested List Iterator [Medium]
Implement an iterator to flatten a nested list of integers. Each element is either an integer or a list whose elements may also be integers or other lists.
##### Optimal Python solution:
```python
class NestedIterator:
    def __init__(self, nestedList: [NestedInteger]):
        self.stack = nestedList[::-1]

    def next(self) -> int:
        return self.stack.pop().getInteger()

    def hasNext(self) -> bool:
        while self.stack:
            top = self.stack[-1]
            if top.isInteger():
                return True
            self.stack = self.stack[:-1] + top.getList()[::-1]
        return False
```
Flatten a nested list using a stack
    
### >> 173 Binary Search Tree Iterator [Medium]
Implement an iterator over a binary search tree (BST). Your iterator will be initialized with the root node of a BST.
##### Sample input:

- ['BSTIterator', 'next', 'next', 'hasNext', 'next', 'hasNext', 'next', 'hasNext', 'next', 'hasNext']
- [[7, 3, 15, null, null, 9, 20]]
- [], [], [], [], [], [], [], [], [], []
##### Sample output:

- [null, 3, 7, true, 9, true, 15, true, 20, false]

##### Questions to ask to clarify requirements:

- Can the BST contain duplicate values?
- What should the iterator return if the BST is empty?
- Can the BST be modified after the iterator is initialized?

##### Optimal Python solution:
```python

- class BSTIterator:
-     def __init__(self, root: TreeNode):
-         self.stack = []
-         self._leftmost_inorder(root)
-     
-     def _leftmost_inorder(self, root):
-         while root:
-             self.stack.append(root)
-             root = root.left
-     
-     def next(self) -> int:
-         topmost_node = self.stack.pop()
-         if topmost_node.right:
-             self._leftmost_inorder(topmost_node.right)
-         return topmost_node.val
-     
-     def hasNext(self) -> bool:
-         return len(self.stack) > 0
```
##### Time complexity:
O(1) for both next() and hasNext()
##### Space complexity:
O(h), where h is the height of the BST
##### Notes:

- Use a stack to simulate the inorder traversal of the BST
- Initialize the stack with the leftmost node of the BST
- When next() is called, pop the topmost node from the stack and return its value
- If the topmost node has a right child, push the leftmost node of the right subtree onto the stack
- Use hasNext() to check if the stack is empty

- Use a stack to simulate the inorder traversal of the BST
- Initialize the stack with the leftmost node of the BST
- When next() is called, pop the topmost node from the stack and return its value
- If the topmost node has a right child, push the leftmost node of the right subtree onto the stack
- Use hasNext() to check if the stack is empty

- The stack is used to store the nodes in the inorder traversal order
- The _leftmost_inorder() function is used to push the leftmost nodes onto the stack

- Using recursion for inorder traversal
- Using a separate list to store the inorder traversal of the BST
    
### >> Comparison: 341 Flatten Nested List Iterator [Medium] *VS* 173 Binary Search Tree Iterator [Medium]
> Similarity distance: 0.5690
##### Similarities

- Both questions involve iterating through a nested data structure
- Both questions require implementing an iterator
##### Differences

- 341 Flatten Nested List Iterator: The nested data structure is a list of integers and lists
- 173 Binary Search Tree Iterator: The nested data structure is a binary search tree
- 341 Flatten Nested List Iterator: The iterator should flatten the nested list and return the integers in order
- 173 Binary Search Tree Iterator: The iterator should return the integers in the binary search tree in ascending order
##### New Insights in 173 Binary Search Tree Iterator [Medium]

- 341 Flatten Nested List Iterator: Understanding how to recursively flatten a nested list
- 173 Binary Search Tree Iterator: Understanding how to traverse a binary search tree in a specific order


---
# 3. From 341 Flatten Nested List Iterator [Medium] to 255 Verify Preorder Sequence in Binary Search Tree [Medium]
> Similarity Distance: 0.6630

### >> Reminder: 341 Flatten Nested List Iterator [Medium]
Implement an iterator to flatten a nested list of integers. Each element is either an integer or a list whose elements may also be integers or other lists.
##### Optimal Python solution:
```python
class NestedIterator:
    def __init__(self, nestedList: [NestedInteger]):
        self.stack = nestedList[::-1]

    def next(self) -> int:
        return self.stack.pop().getInteger()

    def hasNext(self) -> bool:
        while self.stack:
            top = self.stack[-1]
            if top.isInteger():
                return True
            self.stack = self.stack[:-1] + top.getList()[::-1]
        return False
```
Flatten a nested list using a stack
    
### >> 255 Verify Preorder Sequence in Binary Search Tree [Medium]
Given an array of unique integers preorder, return true if it is the preorder traversal of a binary search tree. Otherwise, return false.
##### Sample input:
[5,2,1,3,6]
##### Sample output:
true

##### Questions to ask to clarify requirements:

- Can the input array contain duplicates?
- Can we assume the input is always valid?
- What should we return if the input array is empty?

##### Optimal Python solution:
```python
def verifyPreorder(self, preorder: List[int]) -> bool:
    stack = []
    low = float('-inf')
    for num in preorder:
        if num < low:
            return False
        while stack and num > stack[-1]:
            low = stack.pop()
        stack.append(num)
    return True
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- The root of a binary search tree is always the first element in the preorder traversal.
- All elements to the left of the root in the preorder traversal are smaller than the root.
- All elements to the right of the root in the preorder traversal are greater than the root.

- Use a stack to keep track of the valid range of values for each subtree.
- Iterate through the preorder array and check if each element is within the valid range.
- Handle edge cases such as an empty input array or an array with duplicates.

- Using a stack to keep track of the valid range of values for each subtree.

- Using recursion to solve the problem.
    
### >> Comparison: 341 Flatten Nested List Iterator [Medium] *VS* 255 Verify Preorder Sequence in Binary Search Tree [Medium]
> Similarity distance: 0.6630
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve manipulating data structures.
- Both questions require iteration over elements.
- Both questions involve nested structures.
##### Differences

- 341 Flatten Nested List Iterator focuses on flattening a nested list and providing an iterator to access the elements.
- 255 Verify Preorder Sequence in Binary Search Tree focuses on verifying if a given sequence is a valid preorder traversal of a binary search tree.
- 341 Flatten Nested List Iterator deals with lists of integers, while 255 Verify Preorder Sequence in Binary Search Tree deals with binary search trees.
- 341 Flatten Nested List Iterator requires implementing an iterator, while 255 Verify Preorder Sequence in Binary Search Tree requires checking the validity of a sequence.
##### New Insights in 255 Verify Preorder Sequence in Binary Search Tree [Medium]

- 341 Flatten Nested List Iterator teaches how to flatten a nested list using recursion and stack.
- 255 Verify Preorder Sequence in Binary Search Tree teaches how to verify a preorder sequence using stack and binary search tree properties.


---
# 4. From 255 Verify Preorder Sequence in Binary Search Tree [Medium] to 105 Construct Binary Tree from Preorder and Inorder Traversal [Medium]
> Similarity Distance: 0.5943

### >> Reminder: 255 Verify Preorder Sequence in Binary Search Tree [Medium]
Given an array of unique integers preorder, return true if it is the preorder traversal of a binary search tree. Otherwise, return false.
##### Optimal Python solution:
```python
def verifyPreorder(self, preorder: List[int]) -> bool:
    stack = []
    low = float('-inf')
    for num in preorder:
        if num < low:
            return False
        while stack and num > stack[-1]:
            low = stack.pop()
        stack.append(num)
    return True
```
The essence of this problem is to determine if a given array is a valid preorder traversal of a binary search tree.
    
### >> 105 Construct Binary Tree from Preorder and Inorder Traversal [Medium]
Given preorder and inorder traversal of a tree, construct the binary tree.
##### Sample input:
[3,9,20,null,null,15,7]
[9,3,null,null,20,15,7]
##### Sample output:
[3,9,20,null,null,15,7]

##### Questions to ask to clarify requirements:

- Can the input contain duplicates?
- Can the input be empty?

##### Optimal Python solution:
```python
class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> TreeNode:
        if not preorder or not inorder:
            return None
        root_val = preorder.pop(0)
        root = TreeNode(root_val)
        root_index = inorder.index(root_val)
        root.left = self.buildTree(preorder, inorder[:root_index])
        root.right = self.buildTree(preorder, inorder[root_index+1:])
        return root
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- The first element in the preorder list is the root of the tree.
- The elements to the left of the root in the inorder list are the left subtree.
- The elements to the right of the root in the inorder list are the right subtree.

- Use a helper function to keep track of the current index in the preorder list.
- Use a dictionary to store the indices of the elements in the inorder list for faster lookup.

- Finding the index of the root in the inorder list

- Using a global variable to keep track of the current index in the preorder list
    
### >> Comparison: 255 Verify Preorder Sequence in Binary Search Tree [Medium] *VS* 105 Construct Binary Tree from Preorder and Inorder Traversal [Medium]
> Similarity distance: 0.5943
##### Similarities

- Both questions involve binary search trees.
- Both questions require analyzing a given sequence of nodes.
- Both questions have a medium difficulty level.
##### Differences

- Question 255 focuses on verifying if a given sequence is a valid preorder traversal of a binary search tree.
- Question 105 focuses on constructing a binary tree from given preorder and inorder traversals.
##### New Insights in 105 Construct Binary Tree from Preorder and Inorder Traversal [Medium]

- Question 255 teaches us how to verify the validity of a preorder traversal sequence.
- Question 105 teaches us how to construct a binary tree using preorder and inorder traversals.


---
# 5. From 105 Construct Binary Tree from Preorder and Inorder Traversal [Medium] to 106 Construct Binary Tree from Inorder and Postorder Traversal [Medium]
> Similarity Distance: 0.3248

### >> Reminder: 105 Construct Binary Tree from Preorder and Inorder Traversal [Medium]
Given preorder and inorder traversal of a tree, construct the binary tree.
##### Optimal Python solution:
```python
class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> TreeNode:
        if not preorder or not inorder:
            return None
        root_val = preorder.pop(0)
        root = TreeNode(root_val)
        root_index = inorder.index(root_val)
        root.left = self.buildTree(preorder, inorder[:root_index])
        root.right = self.buildTree(preorder, inorder[root_index+1:])
        return root
```
Given preorder and inorder traversal of a tree, construct the binary tree.
    
### >> 106 Construct Binary Tree from Inorder and Postorder Traversal [Medium]
Given inorder and postorder traversal of a tree, construct the binary tree.
##### Sample input:
[9,3,15,20,7]
[9,15,7,20,3]
##### Sample output:
[3,9,20,null,null,15,7]

##### Questions to ask to clarify requirements:

- Can the input contain duplicates?
- Can the input be empty?

##### Optimal Python solution:
```python
class Solution:
    def buildTree(self, inorder: List[int], postorder: List[int]) -> TreeNode:
        if not inorder or not postorder:
            return None
        root_val = postorder.pop()
        root = TreeNode(root_val)
        root_index = inorder.index(root_val)
        root.right = self.buildTree(inorder[root_index+1:], postorder)
        root.left = self.buildTree(inorder[:root_index], postorder)
        return root
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- The last element in the postorder list is the root of the tree.
- The elements to the left of the root in the inorder list are the left subtree.
- The elements to the right of the root in the inorder list are the right subtree.

- Use a helper function to keep track of the current index in the postorder list.
- Use a dictionary to store the indices of the elements in the inorder list for faster lookup.

- Finding the index of the root in the inorder list

- Using a global variable to keep track of the current index in the postorder list
    
### >> Comparison: 105 Construct Binary Tree from Preorder and Inorder Traversal [Medium] *VS* 106 Construct Binary Tree from Inorder and Postorder Traversal [Medium]
> Similarity distance: 0.3248
##### Similarities

- Both questions involve constructing a binary tree from given traversal sequences.
- Both questions have a medium difficulty level.
##### Differences

- Question 105 uses preorder and inorder traversal sequences, while question 106 uses inorder and postorder traversal sequences.
- In question 105, the root node is the first element in the preorder sequence, while in question 106, the root node is the last element in the postorder sequence.
- The order of traversal sequences is different in the two questions.
##### New Insights in 106 Construct Binary Tree from Inorder and Postorder Traversal [Medium]

- By understanding the relationship between preorder and inorder traversal sequences, we can construct a binary tree.
- By understanding the relationship between inorder and postorder traversal sequences, we can construct a binary tree.
- We can use recursion to solve both questions efficiently.


---
# 6. From 255 Verify Preorder Sequence in Binary Search Tree [Medium] to 331 Verify Preorder Serialization of a Binary Tree [Medium]
> Similarity Distance: 0.6250

### >> Reminder: 255 Verify Preorder Sequence in Binary Search Tree [Medium]
Given an array of unique integers preorder, return true if it is the preorder traversal of a binary search tree. Otherwise, return false.
##### Optimal Python solution:
```python
def verifyPreorder(self, preorder: List[int]) -> bool:
    stack = []
    low = float('-inf')
    for num in preorder:
        if num < low:
            return False
        while stack and num > stack[-1]:
            low = stack.pop()
        stack.append(num)
    return True
```
The essence of this problem is to determine if a given array is a valid preorder traversal of a binary search tree.
    
### >> 331 Verify Preorder Serialization of a Binary Tree [Medium]
One way to serialize a binary tree is to use preorder traversal. When we encounter a non-null node, we record the node's value. If it is a null node, we record using a sentinel value such as '#'. Given a string of comma-separated values preorder, return true if it is a correct preorder traversal serialization of a binary tree.
##### Sample input:
"9,3,4,#,#,1,#,#,2,#,6,#,#"
##### Sample output:
true

##### Questions to ask to clarify requirements:
What is the format of the input string? Can there be spaces between the values? Can there be leading or trailing commas?

##### Optimal Python solution:
```python
class Solution:
    def isValidSerialization(self, preorder: str) -> bool:
        slots = 1
        for node in preorder.split(','):
            slots -= 1
            if slots < 0:
                return False
            if node != '#':
                slots += 2
        return slots == 0
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Use a stack to simulate the preorder traversal
2. Keep track of the number of available slots
3. If a non-null node is encountered, add 2 slots
4. If a null node is encountered, subtract 1 slot
5. Return True if there are no remaining slots
1. Use the split() method to split the input string into a list of values
2. Use a stack to keep track of the nodes
3. Use a variable to keep track of the number of available slots
The number of slots is initially set to 1 because the root node does not consume a slot
Using recursion to simulate the preorder traversal
    
### >> Comparison: 255 Verify Preorder Sequence in Binary Search Tree [Medium] *VS* 331 Verify Preorder Serialization of a Binary Tree [Medium]
> Similarity distance: 0.6250
##### Similarities

- Both questions involve verifying the preorder sequence of a binary tree.
- Both questions are classified as medium difficulty.
##### Differences

- Question 255 involves verifying the preorder sequence in a binary search tree, while question 331 involves verifying the preorder serialization of a binary tree.
- In question 255, the input sequence represents a valid preorder traversal of a binary search tree, while in question 331, the input sequence represents a preorder serialization of a binary tree.
- Question 255 requires checking if the given sequence is a valid preorder traversal of a binary search tree, while question 331 requires checking if the given sequence is a valid preorder serialization of a binary tree.
##### New Insights in 331 Verify Preorder Serialization of a Binary Tree [Medium]

- Question 255: Understanding the properties of a binary search tree and how its preorder traversal behaves.
- Question 331: Understanding the concept of preorder serialization and how it represents a binary tree.


---
# 7. From 341 Flatten Nested List Iterator [Medium] to 251 Flatten 2D Vector [Medium]
> Similarity Distance: 0.6662

### >> Reminder: 341 Flatten Nested List Iterator [Medium]
Implement an iterator to flatten a nested list of integers. Each element is either an integer or a list whose elements may also be integers or other lists.
##### Optimal Python solution:
```python
class NestedIterator:
    def __init__(self, nestedList: [NestedInteger]):
        self.stack = nestedList[::-1]

    def next(self) -> int:
        return self.stack.pop().getInteger()

    def hasNext(self) -> bool:
        while self.stack:
            top = self.stack[-1]
            if top.isInteger():
                return True
            self.stack = self.stack[:-1] + top.getList()[::-1]
        return False
```
Flatten a nested list using a stack
    
### >> 251 Flatten 2D Vector [Medium]
Implement an iterator to flatten a 2D vector.
##### Sample input:

- [[1,2],[3],[4,5,6]]
##### Sample output:

- 1
- 2
- 3
- 4
- 5
- 6

##### Questions to ask to clarify requirements:

- What should the iterator return when there are no more elements?
- Can the input vector be empty?
- Can the input vector contain empty lists?

##### Optimal Python solution:
```python

- class Vector2D:
-     def __init__(self, v: List[List[int]]):
-         self.vector = v
-         self.row = 0
-         self.col = 0
-     def next(self) -> int:
-         self.hasNext()
-         val = self.vector[self.row][self.col]
-         self.col += 1
-         return val
-     def hasNext(self) -> bool:
-         while self.row < len(self.vector) and self.col == len(self.vector[self.row]):
-             self.row += 1
-             self.col = 0
-         return self.row < len(self.vector)
- 
- # Test case
- v = Vector2D([[1,2],[3],[4,5,6]])
- print(v.next())
- print(v.next())
- print(v.next())
- print(v.hasNext())
- print(v.next())
- print(v.hasNext())
- print(v.next())
- print(v.hasNext())
- print(v.next())
- print(v.hasNext())
- print(v.next())
- print(v.hasNext())
```
##### Time complexity:
O(1) for both next() and hasNext()
##### Space complexity:
O(1)
##### Notes:

- Use two pointers to keep track of the current row and column
- Skip empty lists in the input vector
- Return the next element in the vector when next() is called
- Check if there are more elements using hasNext()

- Use the two pointers technique to keep track of the current position in the 2D vector.
- Skip empty lists in the input vector to avoid unnecessary iterations.
- Return the next element in the vector when next() is called.
- Check if there are more elements using hasNext().

- Handling empty lists in the input vector
- Skipping empty lists when iterating

- Using additional data structures
- Iterating over the entire input vector in each call to next()
    
### >> Comparison: 341 Flatten Nested List Iterator [Medium] *VS* 251 Flatten 2D Vector [Medium]
> Similarity distance: 0.6662
##### Similarities

- Both questions involve flattening a nested data structure.
- Both questions require implementing an iterator to iterate through the flattened structure.
##### Differences

- Question 341 involves flattening a nested list, while question 251 involves flattening a 2D vector.
- Question 341 uses a recursive approach to flatten the nested list, while question 251 uses a two-pointer approach to flatten the 2D vector.
- Question 341 requires implementing the hasNext() method to check if there are more elements in the flattened list, while question 251 does not have a hasNext() method.
- Question 341 allows for arbitrary nesting of lists, while question 251 assumes a rectangular shape for the 2D vector.
##### New Insights in 251 Flatten 2D Vector [Medium]

- Question 341: The recursive approach can be implemented using a stack to handle nested lists.
- Question 251: The two-pointer approach can be implemented using two pointers to keep track of the current row and column in the 2D vector.

