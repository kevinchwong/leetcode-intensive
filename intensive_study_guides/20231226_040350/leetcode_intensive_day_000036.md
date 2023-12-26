
# Leetcode Intensive Tutorial Day 36 
> [Difficulty Score: 20]

> [Version: 20231226_040350]

> [Including this day, you had studied : 294 leetcode problems]


## Courses overview of the day

- 501 Find Mode in Binary Search Tree [Easy]
  - 538 Convert BST to Greater Tree [Medium]
    - 114 Flatten Binary Tree to Linked List [Medium]
      - 589 N-ary Tree Preorder Traversal [Medium]
        - 590 N-ary Tree Postorder Traversal [Easy]
          - 145 Binary Tree Postorder Traversal [Medium]
          - 117 Populating Next Right Pointers in Each Node II [Medium]
            - 515 Find Largest Value in Each Tree Row [Medium]
              - 513 Find Bottom Left Tree Value [Medium]
        - 144 Binary Tree Preorder Traversal [Medium]
        - 449 Serialize and Deserialize BST [Medium]

#### Step by step

 - [1. From 501 Find Mode in Binary Search Tree [Easy] to 538 Convert BST to Greater Tree [Medium]](#1-from-501-find-mode-in-binary-search-tree-easy-to-538-convert-bst-to-greater-tree-medium))

 - [2. From 538 Convert BST to Greater Tree [Medium] to 114 Flatten Binary Tree to Linked List [Medium]](#2-from-538-convert-bst-to-greater-tree-medium-to-114-flatten-binary-tree-to-linked-list-medium))

 - [3. From 114 Flatten Binary Tree to Linked List [Medium] to 589 N-ary Tree Preorder Traversal [Medium]](#3-from-114-flatten-binary-tree-to-linked-list-medium-to-589-n-ary-tree-preorder-traversal-medium))

 - [4. From 589 N-ary Tree Preorder Traversal [Medium] to 590 N-ary Tree Postorder Traversal [Easy]](#4-from-589-n-ary-tree-preorder-traversal-medium-to-590-n-ary-tree-postorder-traversal-easy))

 - [5. From 590 N-ary Tree Postorder Traversal [Easy] to 145 Binary Tree Postorder Traversal [Medium]](#5-from-590-n-ary-tree-postorder-traversal-easy-to-145-binary-tree-postorder-traversal-medium))

 - [6. From 590 N-ary Tree Postorder Traversal [Easy] to 117 Populating Next Right Pointers in Each Node II [Medium]](#6-from-590-n-ary-tree-postorder-traversal-easy-to-117-populating-next-right-pointers-in-each-node-ii-medium))

 - [7. From 117 Populating Next Right Pointers in Each Node II [Medium] to 515 Find Largest Value in Each Tree Row [Medium]](#7-from-117-populating-next-right-pointers-in-each-node-ii-medium-to-515-find-largest-value-in-each-tree-row-medium))

 - [8. From 515 Find Largest Value in Each Tree Row [Medium] to 513 Find Bottom Left Tree Value [Medium]](#8-from-515-find-largest-value-in-each-tree-row-medium-to-513-find-bottom-left-tree-value-medium))

 - [9. From 589 N-ary Tree Preorder Traversal [Medium] to 144 Binary Tree Preorder Traversal [Medium]](#9-from-589-n-ary-tree-preorder-traversal-medium-to-144-binary-tree-preorder-traversal-medium))

 - [10. From 589 N-ary Tree Preorder Traversal [Medium] to 449 Serialize and Deserialize BST [Medium]](#10-from-589-n-ary-tree-preorder-traversal-medium-to-449-serialize-and-deserialize-bst-medium))

    

#### Summary


- 117 Populating Next Right Pointers in Each Node II : Connect each node with its next right node using level order traversal.
- 449 Serialize and Deserialize BST : Design an algorithm to serialize and deserialize a binary search tree.
- 501 Find Mode in Binary Search Tree : The essence of this problem is to perform an inorder traversal of the BST and keep track of the previous node and the count of the current element to find the mode(s).
- 538 Convert BST to Greater Tree : The essence of this problem is to convert a BST to a Greater Tree by performing a reverse inorder traversal and updating each node's value.
- 590 N-ary Tree Postorder Traversal : The essence of this problem is to perform a postorder traversal of an n-ary tree using a stack.
- 515 Find Largest Value in Each Tree Row : Perform a level order traversal of a binary tree and track the maximum value in each row.
- 513 Find Bottom Left Tree Value : Perform a level order traversal and keep track of the leftmost value in each level.
- 114 Flatten Binary Tree to Linked List : Given a binary tree, flatten it to a linked list in-place.
- 589 N-ary Tree Preorder Traversal : The essence of this problem is to perform a preorder traversal of an n-ary tree using a stack.
- 144 Binary Tree Preorder Traversal : Finding the preorder traversal of a binary tree using a stack
- 145 Binary Tree Postorder Traversal : The essence of this problem is to perform postorder traversal of a binary tree iteratively using a stack.
> Similarity Diameter of these problems: 0.6531


---
# 1. From 501 Find Mode in Binary Search Tree [Easy] to 538 Convert BST to Greater Tree [Medium]
> Similarity Distance: 0.5091

### >> 501 Find Mode in Binary Search Tree [Easy]
Given a binary search tree (BST) with duplicates, find all the mode(s) (the most frequently occurred element) in the given BST.
##### Sample input:
[1,null,2,2]
##### Sample output:
[2]

##### Questions to ask to clarify requirements:
Are there any constraints on the input tree? Can the tree be empty?

##### Optimal Python solution:
```python
class Solution:
    def findMode(self, root: TreeNode) -> List[int]:
        if not root:
            return []
        self.prev = None
        self.count = 0
        self.max_count = 0
        self.modes = []
        self.inorder(root)
        return self.modes
    def inorder(self, node):
        if not node:
            return
        self.inorder(node.left)
        if node.val == self.prev:
            self.count += 1
        else:
            self.count = 1
        if self.count > self.max_count:
            self.max_count = self.count
            self.modes = [node.val]
        elif self.count == self.max_count:
            self.modes.append(node.val)
        self.prev = node.val
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Perform inorder traversal to visit all nodes in the BST.
2. Keep track of the previous node and the count of the current element.
3. Update the modes list and the maximum count whenever a new mode is found.
4. Return the modes list at the end.
Use a recursive approach to perform the inorder traversal and update the modes list.
The tricky part is to keep track of the previous node and the count of the current element while performing the inorder traversal.
Avoid using extra space to store the modes list.
    
### >> 538 Convert BST to Greater Tree [Medium]
Given the root of a Binary Search Tree (BST), convert it to a Greater Tree such that every key of the original BST is changed to the original key plus the sum of all keys greater than the original key in BST.
##### Sample input:
[4,1,6,0,2,5,7,null,null,null,3,null,null,null,8]
##### Sample output:
[30,36,21,36,35,26,15,null,null,null,33,null,null,null,8]

##### Questions to ask to clarify requirements:
Can the BST contain duplicate keys? What should be the output if the BST is empty?

##### Optimal Python solution:
```python
class Solution:
    def convertBST(self, root: TreeNode) -> TreeNode:
        def dfs(node, total):
            if not node:
                return total
            node.val += dfs(node.right, total)
            return dfs(node.left, node.val)
        dfs(root, 0)
        return root
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Perform a reverse inorder traversal of the BST.
2. Keep track of the running sum of keys.
3. Update each node's value by adding the running sum to the original key.
Use recursion to perform the reverse inorder traversal. Keep track of the running sum using a parameter passed by reference.
None
None
    
### >> Comparison: 501 Find Mode in Binary Search Tree [Easy] *VS* 538 Convert BST to Greater Tree [Medium]
> Similarity distance: 0.5091
##### Similarities

- Both questions involve binary search trees (BST).
- Both questions require traversing the BST.
- Both questions involve manipulating the values of the nodes in the BST.
##### Differences

- 501 Find Mode in Binary Search Tree focuses on finding the mode(s) in the BST, which is the value(s) that appear(s) most frequently.
- 538 Convert BST to Greater Tree focuses on converting the BST into a Greater Tree, where each node's value is updated to be the sum of all values greater than itself.
##### New Insights in 538 Convert BST to Greater Tree [Medium]

- 501 Find Mode in Binary Search Tree: The mode(s) can be found by performing an inorder traversal of the BST and keeping track of the count of each value.
- 538 Convert BST to Greater Tree: The Greater Tree can be constructed by performing a reverse inorder traversal of the BST and updating the node values.


---
# 2. From 538 Convert BST to Greater Tree [Medium] to 114 Flatten Binary Tree to Linked List [Medium]
> Similarity Distance: 0.5287

### >> Reminder: 538 Convert BST to Greater Tree [Medium]
Given the root of a Binary Search Tree (BST), convert it to a Greater Tree such that every key of the original BST is changed to the original key plus the sum of all keys greater than the original key in BST.
##### Optimal Python solution:
```python
class Solution:
    def convertBST(self, root: TreeNode) -> TreeNode:
        def dfs(node, total):
            if not node:
                return total
            node.val += dfs(node.right, total)
            return dfs(node.left, node.val)
        dfs(root, 0)
        return root
```
The essence of this problem is to convert a BST to a Greater Tree by performing a reverse inorder traversal and updating each node's value.
    
### >> 114 Flatten Binary Tree to Linked List [Medium]
Given a binary tree, flatten it to a linked list in-place.
##### Sample input:
[1,2,5,3,4,null,6]
##### Sample output:
[1,null,2,null,3,null,4,null,5,null,6]

##### Questions to ask to clarify requirements:
What should be returned if the binary tree is empty?

##### Optimal Python solution:
```python
class Solution:
    def flatten(self, root: TreeNode) -> None:
        if not root:
            return
        stack = [root]
        prev = None
        while stack:
            curr = stack.pop()
            if prev:
                prev.right = curr
                prev.left = None
            if curr.right:
                stack.append(curr.right)
            if curr.left:
                stack.append(curr.left)
            prev = curr
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use a stack to perform a pre-order traversal of the binary tree.
2. Keep track of the previous node to update the pointers.
3. Set the left child of each node to None and the right child to the next node in the pre-order traversal.
1. Use a stack to perform the pre-order traversal.
2. Keep track of the previous node to update the pointers.
3. Set the left child of each node to None and the right child to the next node in the pre-order traversal.
1. Be careful with updating the pointers of the previous node.
2. Set the left child of each node to None and the right child to the next node in the pre-order traversal.
Avoid using recursion to perform the pre-order traversal.
Avoid unnecessary backtracking by using a stack.
    
### >> Comparison: 538 Convert BST to Greater Tree [Medium] *VS* 114 Flatten Binary Tree to Linked List [Medium]
> Similarity distance: 0.5287
##### Similarities

- Both questions involve manipulating binary trees.
- Both questions have a medium difficulty level.
##### Differences

- 538 Convert BST to Greater Tree involves converting a binary search tree (BST) into a greater tree, where each node's value is updated to be the sum of all values greater than itself in the original BST.
- 114 Flatten Binary Tree to Linked List involves flattening a binary tree into a linked list, where the right child of each node is updated to point to the next node in the flattened structure.
##### New Insights in 114 Flatten Binary Tree to Linked List [Medium]

- 538 Convert BST to Greater Tree teaches us how to perform an in-order traversal of a binary search tree and update node values.
- 114 Flatten Binary Tree to Linked List teaches us how to flatten a binary tree using a recursive approach and update node pointers.


---
# 3. From 114 Flatten Binary Tree to Linked List [Medium] to 589 N-ary Tree Preorder Traversal [Medium]
> Similarity Distance: 0.3257

### >> Reminder: 114 Flatten Binary Tree to Linked List [Medium]
Given a binary tree, flatten it to a linked list in-place.
##### Optimal Python solution:
```python
class Solution:
    def flatten(self, root: TreeNode) -> None:
        if not root:
            return
        stack = [root]
        prev = None
        while stack:
            curr = stack.pop()
            if prev:
                prev.right = curr
                prev.left = None
            if curr.right:
                stack.append(curr.right)
            if curr.left:
                stack.append(curr.left)
            prev = curr
```
Given a binary tree, flatten it to a linked list in-place.
    
### >> 589 N-ary Tree Preorder Traversal [Medium]
Given an n-ary tree, return the preorder traversal of its nodes' values.
##### Sample input:
[1,null,3,2,4,null,5,6]
##### Sample output:
[1,3,5,6,2,4]

##### Questions to ask to clarify requirements:
What is the definition of an n-ary tree? What should be returned if the tree is empty?

##### Optimal Python solution:
```python
class Solution:
    def preorder(self, root: 'Node') -> List[int]:
        if not root:
            return []
        stack = [root]
        result = []
        while stack:
            node = stack.pop()
            result.append(node.val)
            stack.extend(node.children[::-1])
        return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use a stack to perform iterative preorder traversal.
2. Append the node's value to the result list.
3. Push the children of the node onto the stack in reverse order.
None
None
None
    
### >> Comparison: 114 Flatten Binary Tree to Linked List [Medium] *VS* 589 N-ary Tree Preorder Traversal [Medium]
> Similarity distance: 0.3257
##### Similarities

- Both questions involve traversing a tree structure
- Both questions have a medium difficulty level
##### Differences

- 114 Flatten Binary Tree to Linked List involves converting a binary tree into a linked list
- 589 N-ary Tree Preorder Traversal involves traversing an N-ary tree in a specific order
##### New Insights in 589 N-ary Tree Preorder Traversal [Medium]

- In 114 Flatten Binary Tree to Linked List, the tree is flattened by rearranging the nodes in a specific way
- In 589 N-ary Tree Preorder Traversal, the nodes are visited in a specific order


---
# 4. From 589 N-ary Tree Preorder Traversal [Medium] to 590 N-ary Tree Postorder Traversal [Easy]
> Similarity Distance: 0.1749

### >> Reminder: 589 N-ary Tree Preorder Traversal [Medium]
Given an n-ary tree, return the preorder traversal of its nodes' values.
##### Optimal Python solution:
```python
class Solution:
    def preorder(self, root: 'Node') -> List[int]:
        if not root:
            return []
        stack = [root]
        result = []
        while stack:
            node = stack.pop()
            result.append(node.val)
            stack.extend(node.children[::-1])
        return result
```
The essence of this problem is to perform a preorder traversal of an n-ary tree using a stack.
    
### >> 590 N-ary Tree Postorder Traversal [Easy]
Given an n-ary tree, return the postorder traversal of its nodes' values.
##### Sample input:
[1,null,3,2,4,null,5,6]
##### Sample output:
[5,6,3,2,4,1]

##### Questions to ask to clarify requirements:
What is the definition of an n-ary tree? What should be returned if the tree is empty?

##### Optimal Python solution:
```python
class Solution:
    def postorder(self, root: 'Node') -> List[int]:
        if not root:
            return []
        stack = [root]
        result = []
        while stack:
            node = stack.pop()
            result.append(node.val)
            stack.extend(node.children)
        return result[::-1]
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use a stack to perform iterative postorder traversal.
2. Append the node's value to the result list.
3. Push the children of the node onto the stack in the original order.
None
None
None
    
### >> Comparison: 589 N-ary Tree Preorder Traversal [Medium] *VS* 590 N-ary Tree Postorder Traversal [Easy]
> Similarity distance: 0.1749
##### Similarities

- Both questions involve traversing an N-ary tree
- Both questions require visiting each node in a specific order
##### Differences

- 589 is a medium difficulty question, while 590 is an easy difficulty question
- 589 requires a preorder traversal, while 590 requires a postorder traversal
- 589 returns the nodes in a specific order, while 590 returns the nodes in a different order
##### New Insights in 590 N-ary Tree Postorder Traversal [Easy]

- By solving these questions, we can learn how to traverse an N-ary tree
- We can learn how to implement preorder and postorder traversal algorithms
- We can learn how to visit each node in a specific order


---
# 5. From 590 N-ary Tree Postorder Traversal [Easy] to 145 Binary Tree Postorder Traversal [Medium]
> Similarity Distance: 0.3420

### >> Reminder: 590 N-ary Tree Postorder Traversal [Easy]
Given an n-ary tree, return the postorder traversal of its nodes' values.
##### Optimal Python solution:
```python
class Solution:
    def postorder(self, root: 'Node') -> List[int]:
        if not root:
            return []
        stack = [root]
        result = []
        while stack:
            node = stack.pop()
            result.append(node.val)
            stack.extend(node.children)
        return result[::-1]
```
The essence of this problem is to perform a postorder traversal of an n-ary tree using a stack.
    
### >> 145 Binary Tree Postorder Traversal [Medium]
Given the root of a binary tree, return the postorder traversal of its nodes' values.
##### Sample input:
[1,null,2,3]
##### Sample output:
[3,2,1]

##### Questions to ask to clarify requirements:
What is the definition of a binary tree? What is postorder traversal? Can the tree be empty?

##### Optimal Python solution:
```python
class Solution:
    def postorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        if not root:
            return []
        stack, output = [root, ], []
        while stack:
            root = stack.pop()
            if root is not None:
                output.append(root.val)
                if root.left is not None:
                    stack.append(root.left)
                if root.right is not None:
                    stack.append(root.right)
        return output[::-1]
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use a stack to perform postorder traversal iteratively
2. Append the root value to the output list
3. Push the left and right child of the root onto the stack
4. Reverse the output list to get the postorder traversal
Understand the order of visiting nodes in postorder traversal and the use of a stack
The order of appending the left and right child to the stack matters
Using recursion
    
### >> Comparison: 590 N-ary Tree Postorder Traversal [Easy] *VS* 145 Binary Tree Postorder Traversal [Medium]
> Similarity distance: 0.3420
##### Similarities

- Both questions involve traversing a tree in a postorder manner.
- Both questions require visiting the nodes in a specific order.
##### Differences

- 590 N-ary Tree Postorder Traversal deals with an N-ary tree, while 145 Binary Tree Postorder Traversal deals with a binary tree.
- 590 N-ary Tree Postorder Traversal uses an iterative approach, while 145 Binary Tree Postorder Traversal uses a recursive approach.
##### New Insights in 145 Binary Tree Postorder Traversal [Medium]

- 590 N-ary Tree Postorder Traversal introduces the concept of N-ary trees and how to traverse them in a postorder manner.
- 145 Binary Tree Postorder Traversal provides a different approach to traverse a binary tree in a postorder manner.


---
# 6. From 590 N-ary Tree Postorder Traversal [Easy] to 117 Populating Next Right Pointers in Each Node II [Medium]
> Similarity Distance: 0.4762

### >> Reminder: 590 N-ary Tree Postorder Traversal [Easy]
Given an n-ary tree, return the postorder traversal of its nodes' values.
##### Optimal Python solution:
```python
class Solution:
    def postorder(self, root: 'Node') -> List[int]:
        if not root:
            return []
        stack = [root]
        result = []
        while stack:
            node = stack.pop()
            result.append(node.val)
            stack.extend(node.children)
        return result[::-1]
```
The essence of this problem is to perform a postorder traversal of an n-ary tree using a stack.
    
### >> 117 Populating Next Right Pointers in Each Node II [Medium]
Given a binary tree, connect each node with its next right node. If there is no next right node, the next pointer should be set to NULL.
##### Sample input:
1
/ \
2   3
/ \   \
4   5   7
##### Sample output:
1
/ \
2 -> 3
/ \   \
4-> 5 -> 7

##### Questions to ask to clarify requirements:
What should be the return type of the function? Can the tree have more than two children per node?

##### Optimal Python solution:
```python
class Solution:
    def connect(self, root: 'Node') -> 'Node':
        if not root:
            return root
        queue = [root]
        while queue:
            size = len(queue)
            for i in range(size):
                node = queue.pop(0)
                if i < size - 1:
                    node.next = queue[0]
                if node.left:
                    queue.append(node.left)
                if node.right:
                    queue.append(node.right)
        return root
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use level order traversal to connect nodes
2. Use a queue to store nodes at each level
3. Connect each node to its next right node
4. Handle the last node in each level
5. Return the root of the modified tree
Use a queue to store nodes at each level.
Handling the last node in each level
Using recursion
    
### >> Comparison: 590 N-ary Tree Postorder Traversal [Easy] *VS* 117 Populating Next Right Pointers in Each Node II [Medium]
> Similarity distance: 0.4762
##### Similarities

- Both questions involve traversing a tree structure
- Both questions require visiting each node in a specific order
##### Differences

- 590 N-ary Tree Postorder Traversal is an easy level question, while 117 Populating Next Right Pointers in Each Node II is a medium level question
- 590 N-ary Tree Postorder Traversal involves an N-ary tree, while 117 Populating Next Right Pointers in Each Node II involves a binary tree
- 590 N-ary Tree Postorder Traversal requires a postorder traversal, while 117 Populating Next Right Pointers in Each Node II requires connecting nodes at the same level
##### New Insights in 117 Populating Next Right Pointers in Each Node II [Medium]

- In 590 N-ary Tree Postorder Traversal, we can use a recursive approach to traverse the tree in postorder
- In 117 Populating Next Right Pointers in Each Node II, we can use a level order traversal and connect nodes at the same level using a queue


---
# 7. From 117 Populating Next Right Pointers in Each Node II [Medium] to 515 Find Largest Value in Each Tree Row [Medium]
> Similarity Distance: 0.4531

### >> Reminder: 117 Populating Next Right Pointers in Each Node II [Medium]
Given a binary tree, connect each node with its next right node. If there is no next right node, the next pointer should be set to NULL.
##### Optimal Python solution:
```python
class Solution:
    def connect(self, root: 'Node') -> 'Node':
        if not root:
            return root
        queue = [root]
        while queue:
            size = len(queue)
            for i in range(size):
                node = queue.pop(0)
                if i < size - 1:
                    node.next = queue[0]
                if node.left:
                    queue.append(node.left)
                if node.right:
                    queue.append(node.right)
        return root
```
Connect each node with its next right node using level order traversal.
    
### >> 515 Find Largest Value in Each Tree Row [Medium]
Given the root of a binary tree, return an array of the largest value in each row of the tree (0-indexed).
##### Sample input:
[1,3,2,5,3,null,9]
##### Sample output:
[1,3,9]

##### Questions to ask to clarify requirements:

- Can the tree be empty?
- Can the tree have negative values?
- Can the tree have duplicate values?

##### Optimal Python solution:
```python
def largestValues(self, root: TreeNode) -> List[int]:
    if not root:
        return []
    queue = deque([root])
    result = []
    while queue:
        level_max = float('-inf')
        for _ in range(len(queue)):
            node = queue.popleft()
            level_max = max(level_max, node.val)
            if node.left:
                queue.append(node.left)
            if node.right:
                queue.append(node.right)
        result.append(level_max)
    return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(m)
##### Notes:

- Perform a level order traversal using a queue
- Track the maximum value in each row
- Add the maximum value to the result array

- Use a queue to perform level order traversal
- Track the maximum value in each row using a variable

- Using a queue to perform level order traversal
- Tracking the maximum value in each row

- Using recursion for tree traversal
    
### >> Comparison: 117 Populating Next Right Pointers in Each Node II [Medium] *VS* 515 Find Largest Value in Each Tree Row [Medium]
> Similarity distance: 0.4531
##### Similarities

- Both questions are medium difficulty level.
- Both questions involve traversing a binary tree.
- Both questions require finding values in each level of the tree.
##### Differences

- 117 Populating Next Right Pointers in Each Node II focuses on connecting nodes at the same level, while 515 Find Largest Value in Each Tree Row focuses on finding the largest value in each level.
- 117 Populating Next Right Pointers in Each Node II uses a next pointer to connect nodes, while 515 Find Largest Value in Each Tree Row uses a queue to traverse the tree.
- 117 Populating Next Right Pointers in Each Node II has a time complexity of O(n), while 515 Find Largest Value in Each Tree Row has a time complexity of O(n^2).
##### New Insights in 515 Find Largest Value in Each Tree Row [Medium]

- 117 Populating Next Right Pointers in Each Node II introduces the concept of connecting nodes at the same level using a next pointer.
- 515 Find Largest Value in Each Tree Row introduces the concept of finding the largest value in each level of a binary tree.


---
# 8. From 515 Find Largest Value in Each Tree Row [Medium] to 513 Find Bottom Left Tree Value [Medium]
> Similarity Distance: 0.4851

### >> Reminder: 515 Find Largest Value in Each Tree Row [Medium]
Given the root of a binary tree, return an array of the largest value in each row of the tree (0-indexed).
##### Optimal Python solution:
```python
def largestValues(self, root: TreeNode) -> List[int]:
    if not root:
        return []
    queue = deque([root])
    result = []
    while queue:
        level_max = float('-inf')
        for _ in range(len(queue)):
            node = queue.popleft()
            level_max = max(level_max, node.val)
            if node.left:
                queue.append(node.left)
            if node.right:
                queue.append(node.right)
        result.append(level_max)
    return result
```
Perform a level order traversal of a binary tree and track the maximum value in each row.
    
### >> 513 Find Bottom Left Tree Value [Medium]
Given the root of a binary tree, return the leftmost value in the last row of the tree.
##### Sample input:
[2,1,3]
##### Sample output:
1

##### Questions to ask to clarify requirements:
Are there any constraints on the size of the binary tree?

##### Optimal Python solution:
```python
def findBottomLeftValue(self, root):
    queue = [root]
    while queue:
        node = queue.pop(0)
        if node.right:
            queue.append(node.right)
        if node.left:
            queue.append(node.left)
    return node.val
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Perform a level order traversal of the tree
2. Keep track of the leftmost value in each level
3. Return the leftmost value in the last level
Use a queue to perform the level order traversal.
None
None
    
### >> Comparison: 515 Find Largest Value in Each Tree Row [Medium] *VS* 513 Find Bottom Left Tree Value [Medium]
> Similarity distance: 0.4851
##### Similarities

- Both questions involve traversing a binary tree
- Both questions require finding the maximum value in each row of the tree
##### Differences

- 515 Find Largest Value in Each Tree Row requires finding the largest value in each row, while 513 Find Bottom Left Tree Value requires finding the value of the bottom-left node
- 515 Find Largest Value in Each Tree Row uses a breadth-first search (BFS) algorithm, while 513 Find Bottom Left Tree Value uses a depth-first search (DFS) algorithm
##### New Insights in 513 Find Bottom Left Tree Value [Medium]

- 515 Find Largest Value in Each Tree Row: By using a BFS algorithm, we can efficiently find the largest value in each row of a binary tree
- 513 Find Bottom Left Tree Value: By using a DFS algorithm, we can efficiently find the value of the bottom-left node in a binary tree


---
# 9. From 589 N-ary Tree Preorder Traversal [Medium] to 144 Binary Tree Preorder Traversal [Medium]
> Similarity Distance: 0.3949

### >> Reminder: 589 N-ary Tree Preorder Traversal [Medium]
Given an n-ary tree, return the preorder traversal of its nodes' values.
##### Optimal Python solution:
```python
class Solution:
    def preorder(self, root: 'Node') -> List[int]:
        if not root:
            return []
        stack = [root]
        result = []
        while stack:
            node = stack.pop()
            result.append(node.val)
            stack.extend(node.children[::-1])
        return result
```
The essence of this problem is to perform a preorder traversal of an n-ary tree using a stack.
    
### >> 144 Binary Tree Preorder Traversal [Medium]
Given a binary tree, return the preorder traversal of its nodes' values.
##### Sample input:
[1,null,2,3]
##### Sample output:
[1,2,3]

##### Questions to ask to clarify requirements:
Can we modify the input binary tree? What should we do if the binary tree is empty?

##### Optimal Python solution:
```python
def preorderTraversal(self, root):
    if not root:
        return []
    stack, result = [root], []
    while stack:
        node = stack.pop()
        result.append(node.val)
        if node.right:
            stack.append(node.right)
        if node.left:
            stack.append(node.left)
    return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use a stack to simulate the recursive preorder traversal
2. Push the right child onto the stack before the left child
Use a stack to simulate recursive function calls
Simulating the recursive preorder traversal using a stack
Using recursion
    
### >> Comparison: 589 N-ary Tree Preorder Traversal [Medium] *VS* 144 Binary Tree Preorder Traversal [Medium]
> Similarity distance: 0.3949
##### Similarities

- Both questions involve traversing a tree in a preorder manner.
##### Differences

- 589 N-ary Tree Preorder Traversal deals with an N-ary tree, while 144 Binary Tree Preorder Traversal deals with a binary tree.
- In 589 N-ary Tree Preorder Traversal, each node can have multiple children, while in 144 Binary Tree Preorder Traversal, each node can have at most two children.
##### New Insights in 144 Binary Tree Preorder Traversal [Medium]

- In 589 N-ary Tree Preorder Traversal, we need to handle the multiple children of each node, which requires a different approach compared to 144 Binary Tree Preorder Traversal.
- Both questions provide an opportunity to practice tree traversal algorithms and understand the preorder traversal technique.


---
# 10. From 589 N-ary Tree Preorder Traversal [Medium] to 449 Serialize and Deserialize BST [Medium]
> Similarity Distance: 0.4419

### >> Reminder: 589 N-ary Tree Preorder Traversal [Medium]
Given an n-ary tree, return the preorder traversal of its nodes' values.
##### Optimal Python solution:
```python
class Solution:
    def preorder(self, root: 'Node') -> List[int]:
        if not root:
            return []
        stack = [root]
        result = []
        while stack:
            node = stack.pop()
            result.append(node.val)
            stack.extend(node.children[::-1])
        return result
```
The essence of this problem is to perform a preorder traversal of an n-ary tree using a stack.
    
### >> 449 Serialize and Deserialize BST [Medium]
Design an algorithm to serialize and deserialize a binary search tree. There is no restriction on how your serialization/deserialization algorithm should work. You just need to ensure that a binary search tree can be serialized to a string and this string can be deserialized to the original tree structure.
##### Sample input:
root = [2,1,3]
##### Sample output:
[2,1,3]

##### Questions to ask to clarify requirements:
What is the expected format of the serialized string? Can the tree contain duplicate values? Can the tree be empty?

##### Optimal Python solution:
```python
class Codec:
    def serialize(self, root):
        if not root:
            return 'None'
        return str(root.val) + ',' + self.serialize(root.left) + ',' + self.serialize(root.right)

    def deserialize(self, data):
        def helper(lower=float('-inf'), upper=float('inf')):
            if not data or data[0] < lower or data[0] > upper:
                return None
            val = data.popleft()
            root = TreeNode(val)
            root.left = helper(lower, val)
            root.right = helper(val, upper)
            return root

        data = collections.deque(int(val) for val in data.split(','))
        return helper()
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use preorder traversal to serialize the tree
2. Use a deque to store the serialized data
3. Use recursion to deserialize the tree
4. Use a helper function with lower and upper bounds to ensure the BST property
5. Time complexity: O(n) for both serialization and deserialization
6. Space complexity: O(n) for both serialization and deserialization
Use a deque to efficiently pop values during deserialization
Handling empty trees and duplicate values
Using a different traversal order for serialization
    
### >> Comparison: 589 N-ary Tree Preorder Traversal [Medium] *VS* 449 Serialize and Deserialize BST [Medium]
> Similarity distance: 0.4419
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve tree traversal.
- Both questions require understanding of tree data structures.
##### Differences

- 589 N-ary Tree Preorder Traversal involves traversing an N-ary tree in a pre-order manner, while 449 Serialize and Deserialize BST involves serializing and deserializing a binary search tree.
- 589 N-ary Tree Preorder Traversal uses a stack to keep track of nodes, while 449 Serialize and Deserialize BST uses a recursive approach.
- 589 N-ary Tree Preorder Traversal has a time complexity of O(n), where n is the number of nodes in the tree, while 449 Serialize and Deserialize BST has a time complexity of O(n) for serialization and O(nlogn) for deserialization, where n is the number of nodes in the tree.
##### New Insights in 449 Serialize and Deserialize BST [Medium]

- From 589 N-ary Tree Preorder Traversal, we can learn how to traverse an N-ary tree in a pre-order manner using a stack.
- From 449 Serialize and Deserialize BST, we can learn how to serialize and deserialize a binary search tree using a recursive approach.

