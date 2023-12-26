
# Leetcode Intensive Tutorial Day 47 
> [Difficulty Score: 23]

> [Version: 20231225_200427]

## Courses overview of the day

- 108 Convert Sorted Array to Binary Search Tree [Easy]
  - 536 Construct Binary Tree from String [Medium]
    - 297 Serialize and Deserialize Binary Tree [Hard]
    - 431 Encode N-ary Tree to Binary Tree [Hard]
      - 428 Serialize and Deserialize N-ary Tree [Hard]
  - 109 Convert Sorted List to Binary Search Tree [Medium]
  - 95 Unique Binary Search Trees II [Medium]
    - 96 Unique Binary Search Trees [Medium]
    - 333 Largest BST Subtree [Medium]

#### Steps by steps

 - [1. From 108 Convert Sorted Array to Binary Search Tree [Easy] to 536 Construct Binary Tree from String [Medium]](#1-from-108-convert-sorted-array-to-binary-search-tree-easy-to-536-construct-binary-tree-from-string-medium)

 - [2. From 536 Construct Binary Tree from String [Medium] to 297 Serialize and Deserialize Binary Tree [Hard]](#2-from-536-construct-binary-tree-from-string-medium-to-297-serialize-and-deserialize-binary-tree-hard)

 - [3. From 536 Construct Binary Tree from String [Medium] to 431 Encode N-ary Tree to Binary Tree [Hard]](#3-from-536-construct-binary-tree-from-string-medium-to-431-encode-n-ary-tree-to-binary-tree-hard)

 - [4. From 431 Encode N-ary Tree to Binary Tree [Hard] to 428 Serialize and Deserialize N-ary Tree [Hard]](#4-from-431-encode-n-ary-tree-to-binary-tree-hard-to-428-serialize-and-deserialize-n-ary-tree-hard)

 - [5. From 108 Convert Sorted Array to Binary Search Tree [Easy] to 109 Convert Sorted List to Binary Search Tree [Medium]](#5-from-108-convert-sorted-array-to-binary-search-tree-easy-to-109-convert-sorted-list-to-binary-search-tree-medium)

 - [6. From 108 Convert Sorted Array to Binary Search Tree [Easy] to 95 Unique Binary Search Trees II [Medium]](#6-from-108-convert-sorted-array-to-binary-search-tree-easy-to-95-unique-binary-search-trees-ii-medium)

 - [7. From 95 Unique Binary Search Trees II [Medium] to 96 Unique Binary Search Trees [Medium]](#7-from-95-unique-binary-search-trees-ii-medium-to-96-unique-binary-search-trees-medium)

 - [8. From 95 Unique Binary Search Trees II [Medium] to 333 Largest BST Subtree [Medium]](#8-from-95-unique-binary-search-trees-ii-medium-to-333-largest-bst-subtree-medium)

#### Summary


- 536 Construct Binary Tree from String : Construct a binary tree from its string representation by parsing the string character by character and using a stack to keep track of parent nodes.
- 108 Convert Sorted Array to Binary Search Tree : Convert a sorted array into a height-balanced binary search tree using recursion.
- 95 Unique Binary Search Trees II : The essence of the problem is to generate all structurally unique BSTs that store values 1 ... n.
- 428 Serialize and Deserialize N-ary Tree : The essence of this problem is to recursively serialize and deserialize an N-ary tree.
- 333 Largest BST Subtree : Find the largest BST subtree in a binary tree.
- 431 Encode N-ary Tree to Binary Tree : The essence of this problem is to find a way to represent the N-ary tree structure using a binary tree, and to be able to convert the binary tree back to the original N-ary tree structure.
- 297 Serialize and Deserialize Binary Tree : The essence of this problem is to design an algorithm to serialize and deserialize a binary tree.
- 109 Convert Sorted List to Binary Search Tree : Convert a sorted linked list to a height balanced BST.
- 96 Unique Binary Search Trees : The essence of the problem is to calculate the number of structurally unique BSTs that store values 1 ... n.
> Similarity Diameter of these problems: 0.8138


---
# 1. From 108 Convert Sorted Array to Binary Search Tree [Easy] to 536 Construct Binary Tree from String [Medium]
> Similarity Distance: 0.5123

### >> 108 Convert Sorted Array to Binary Search Tree [Easy]
Given an integer array nums where the elements are sorted in ascending order, convert it to a height-balanced binary search tree.
##### Sample input:
[-10,-3,0,5,9]
##### Sample output:
[0,-3,9,-10,null,5]

##### Questions to ask to clarify requirements:
What should be returned if the array is empty?

##### Optimal Python solution:
```python
class Solution:
    def sortedArrayToBST(self, nums: List[int]) -> TreeNode:
        if not nums:
            return None
        mid = len(nums) // 2
        root = TreeNode(nums[mid])
        root.left = self.sortedArrayToBST(nums[:mid])
        root.right = self.sortedArrayToBST(nums[mid+1:])
        return root
```
##### Time complexity:
O(n)
##### Space complexity:
O(log n)
##### Notes:
1. Use recursion to build the binary search tree
2. Choose the middle element of the array as the root
3. Recursively build the left and right subtrees
Remember to check if the array is empty before starting the conversion.
None
None
    
### >> 536 Construct Binary Tree from String [Medium]
Construct a binary tree from a string representation.
##### Sample input:
"4(2(3)(1))(6(5))"
##### Sample output:
[4,2,6,3,1,5]

##### Questions to ask to clarify requirements:
1. What is the format of the string representation?
2. Can the tree have duplicate values?
3. Can the string representation have extra parentheses?
4. Can the string representation have spaces?
5. Can the string representation have negative values?

##### Optimal Python solution:
```python
class Solution:
    def str2tree(self, s: str) -> TreeNode:
        if not s:
            return None
        stack = []
        i = 0
        while i < len(s):
            if s[i] == ')':
                stack.pop()
                i += 1
            elif s[i] == '(':
                i += 1
            else:
                j = i
                while j < len(s) and s[j] not in ['(', ')']:
                    j += 1
                val = int(s[i:j])
                node = TreeNode(val)
                if stack:
                    parent = stack[-1]
                    if not parent.left:
                        parent.left = node
                    else:
                        parent.right = node
                stack.append(node)
                i = j
        return stack[0]
```
##### Time complexity:
O(n), where n is the length of the string representation.
##### Space complexity:
O(h), where h is the height of the tree.
##### Notes:
1. Use a stack to keep track of parent nodes.
2. Parse the string representation character by character.
3. Create nodes for values encountered and connect them to their parent nodes.
1. Use a stack to keep track of parent nodes.
2. Handle invalid string representations gracefully.
3. Optimize the parsing algorithm for efficiency.
1. Handling invalid string representations.
2. Handling duplicate values in the tree.
3. Optimizing the parsing of the string representation.
1. Using recursion for parsing.
2. Using a fixed-length encoding scheme.
3. Using a linear search for finding parent nodes.
    
### >> Comparison: 108 Convert Sorted Array to Binary Search Tree [Easy] *VS* 536 Construct Binary Tree from String [Medium]
> Similarity distance: 0.5123
##### Similarities

- Both questions involve constructing a binary tree.
- Both questions require parsing a string or array to construct the binary tree.
- Both questions involve recursion to construct the binary tree.
##### Differences

- Question 108 requires constructing a binary search tree, while question 536 does not have this requirement.
- Question 108 requires the input array to be sorted, while question 536 does not have this requirement.
- Question 108 has a time complexity of O(n), while question 536 has a time complexity of O(n^2) in the worst case.
##### New Insights in 536 Construct Binary Tree from String [Medium]

- Question 108 teaches us how to construct a binary search tree from a sorted array efficiently.
- Question 536 teaches us how to construct a binary tree from a string representation.


---
# 2. From 536 Construct Binary Tree from String [Medium] to 297 Serialize and Deserialize Binary Tree [Hard]
> Similarity Distance: 0.5536

### >> Reminder: 536 Construct Binary Tree from String [Medium]
Construct a binary tree from a string representation.
##### Optimal Python solution:
```python
class Solution:
    def str2tree(self, s: str) -> TreeNode:
        if not s:
            return None
        stack = []
        i = 0
        while i < len(s):
            if s[i] == ')':
                stack.pop()
                i += 1
            elif s[i] == '(':
                i += 1
            else:
                j = i
                while j < len(s) and s[j] not in ['(', ')']:
                    j += 1
                val = int(s[i:j])
                node = TreeNode(val)
                if stack:
                    parent = stack[-1]
                    if not parent.left:
                        parent.left = node
                    else:
                        parent.right = node
                stack.append(node)
                i = j
        return stack[0]
```
Construct a binary tree from its string representation by parsing the string character by character and using a stack to keep track of parent nodes.
    
### >> 297 Serialize and Deserialize Binary Tree [Hard]
Design an algorithm to serialize and deserialize a binary tree. There is no restriction on how your serialization/deserialization algorithm should work. You just need to ensure that a binary tree can be serialized to a string and this string can be deserialized to the original tree structure.
##### Sample input:
1
2
3
null
null
4
5
null
null
null
null
##### Sample output:
[1,2,3,null,null,4,5]

##### Questions to ask to clarify requirements:
What is the expected input format for the binary tree? Can the tree be empty? Can the tree have duplicate values?

##### Optimal Python solution:
```python
class Codec:
    def serialize(self, root):
        if not root:
            return 'null'
        return str(root.val) + ',' + self.serialize(root.left) + ',' + self.serialize(root.right)

    def deserialize(self, data):
        def helper(data):
            val = next(data)
            if val == 'null':
                return None
            node = TreeNode(int(val))
            node.left = helper(data)
            node.right = helper(data)
            return node

        data = iter(data.split(','))
        return helper(data)
```
##### Time complexity:
O(N)
##### Space complexity:
O(N)
##### Notes:
1. Use a preorder traversal to serialize the binary tree.
2. Use recursion to deserialize the serialized string.
3. Use a marker to indicate null nodes in the serialized string.
Use a marker to indicate null nodes in the serialized string.
Handling null nodes in the serialized string
Using a level order traversal for serialization
    
### >> Comparison: 536 Construct Binary Tree from String [Medium] *VS* 297 Serialize and Deserialize Binary Tree [Hard]
> Similarity distance: 0.5536
##### Similarities

- Both questions involve binary trees.
- Both questions require string manipulation.
- Both questions involve tree traversal.
##### Differences

- Question 536 constructs a binary tree from a string representation, while question 297 serializes and deserializes a binary tree.
- Question 536 is medium difficulty, while question 297 is hard difficulty.
- Question 536 requires constructing a binary tree from a string, while question 297 requires serializing and deserializing a binary tree.
- Question 536 involves parsing a string to construct a binary tree, while question 297 involves converting a binary tree to a string representation.
##### New Insights in 297 Serialize and Deserialize Binary Tree [Hard]

- Question 536 teaches us how to construct a binary tree from a string representation.
- Question 297 teaches us how to serialize and deserialize a binary tree.
- Both questions provide insights into different aspects of working with binary trees.


---
# 3. From 536 Construct Binary Tree from String [Medium] to 431 Encode N-ary Tree to Binary Tree [Hard]
> Similarity Distance: 0.5609

### >> Reminder: 536 Construct Binary Tree from String [Medium]
Construct a binary tree from a string representation.
##### Optimal Python solution:
```python
class Solution:
    def str2tree(self, s: str) -> TreeNode:
        if not s:
            return None
        stack = []
        i = 0
        while i < len(s):
            if s[i] == ')':
                stack.pop()
                i += 1
            elif s[i] == '(':
                i += 1
            else:
                j = i
                while j < len(s) and s[j] not in ['(', ')']:
                    j += 1
                val = int(s[i:j])
                node = TreeNode(val)
                if stack:
                    parent = stack[-1]
                    if not parent.left:
                        parent.left = node
                    else:
                        parent.right = node
                stack.append(node)
                i = j
        return stack[0]
```
Construct a binary tree from its string representation by parsing the string character by character and using a stack to keep track of parent nodes.
    
### >> 431 Encode N-ary Tree to Binary Tree [Hard]
Given an N-ary tree, encode it into a binary tree and decode it back to the original N-ary tree structure.
##### Sample input:
root = [1,null,3,2,4,null,5,6]

Output:

[1,null,2,3,null,4,null,5,null,6]
##### Sample output:
root = [1,null,3,2,4,null,5,6]

##### Questions to ask to clarify requirements:
What is the maximum number of children a node can have in the N-ary tree? Can the N-ary tree be empty?

##### Optimal Python solution:
```python
class Codec:
    def encode(self, root):
        if not root:
            return None
        new_root = TreeNode(root.val)
        if root.children:
            new_root.left = self.encode(root.children[0])
        cur = new_root.left
        for i in range(1, len(root.children)):
            cur.right = self.encode(root.children[i])
            cur = cur.right
        return new_root

    def decode(self, root):
        if not root:
            return None
        new_root = Node(root.val, [])
        cur = root.left
        while cur:
            new_root.children.append(self.decode(cur))
            cur = cur.right
        return new_root
```
##### Time complexity:
The time complexity of the encoding and decoding process is O(N), where N is the number of nodes in the N-ary tree.
##### Space complexity:
The space complexity of the encoding and decoding process is O(N), where N is the number of nodes in the N-ary tree.
##### Notes:
1. Encode the N-ary tree into a binary tree by using the left child pointer to represent the first child of each node, and the right child pointer to represent the next sibling of each node.
2. Decode the binary tree back to the original N-ary tree by using the left child pointer to traverse the children of each node, and the right child pointer to traverse the siblings of each node.
3. The encoding and decoding process can be optimized by using a pre-order traversal of the N-ary tree.
4. The maximum number of children a node can have in the N-ary tree determines the maximum number of left child pointers that can be used in the binary tree encoding.
1. Use a recursive approach to encode and decode the N-ary tree.
2. Use a pre-order traversal of the N-ary tree to optimize the encoding and decoding process.
3. Take advantage of the properties of the binary tree data structure to simplify the encoding and decoding process.
The trickiest part of this problem is to come up with an efficient encoding and decoding process that preserves the structure of the N-ary tree.
Avoid using a post-order traversal of the N-ary tree for encoding and decoding, as it would require additional space to store the parent nodes of each node.
    
### >> Comparison: 536 Construct Binary Tree from String [Medium] *VS* 431 Encode N-ary Tree to Binary Tree [Hard]
> Similarity distance: 0.5609
##### Similarities

- Both questions involve constructing a binary tree from a given string representation.
- Both questions require understanding the structure and format of the input string.
- Both questions involve creating a binary tree based on the given rules.
##### Differences

- 536 Construct Binary Tree from String deals with a binary tree, while 431 Encode N-ary Tree to Binary Tree deals with an N-ary tree.
- 536 Construct Binary Tree from String uses parentheses to represent the tree structure, while 431 Encode N-ary Tree to Binary Tree uses a different encoding scheme.
- 536 Construct Binary Tree from String requires splitting the input string into substrings to construct the binary tree, while 431 Encode N-ary Tree to Binary Tree requires converting an N-ary tree to a binary tree.
- 536 Construct Binary Tree from String has a medium difficulty level, while 431 Encode N-ary Tree to Binary Tree has a hard difficulty level.
##### New Insights in 431 Encode N-ary Tree to Binary Tree [Hard]

- 536 Construct Binary Tree from String teaches us how to construct a binary tree from a string representation using recursion.
- 431 Encode N-ary Tree to Binary Tree teaches us how to encode an N-ary tree into a binary tree using a specific encoding scheme.
- Both questions provide insights into tree data structures and their representations.


---
# 4. From 431 Encode N-ary Tree to Binary Tree [Hard] to 428 Serialize and Deserialize N-ary Tree [Hard]
> Similarity Distance: 0.5442

### >> Reminder: 431 Encode N-ary Tree to Binary Tree [Hard]
Given an N-ary tree, encode it into a binary tree and decode it back to the original N-ary tree structure.
##### Optimal Python solution:
```python
class Codec:
    def encode(self, root):
        if not root:
            return None
        new_root = TreeNode(root.val)
        if root.children:
            new_root.left = self.encode(root.children[0])
        cur = new_root.left
        for i in range(1, len(root.children)):
            cur.right = self.encode(root.children[i])
            cur = cur.right
        return new_root

    def decode(self, root):
        if not root:
            return None
        new_root = Node(root.val, [])
        cur = root.left
        while cur:
            new_root.children.append(self.decode(cur))
            cur = cur.right
        return new_root
```
The essence of this problem is to find a way to represent the N-ary tree structure using a binary tree, and to be able to convert the binary tree back to the original N-ary tree structure.
    
### >> 428 Serialize and Deserialize N-ary Tree [Hard]
Design an algorithm to serialize and deserialize an N-ary tree.
##### Sample input:

- [1,null,3,2,4,null,5,6]
##### Sample output:

- [1,null,3,2,4,null,5,6]

##### Questions to ask to clarify requirements:

- What is the maximum number of children a node can have?
- Can the tree contain any other values besides integers?
- What should be returned if the tree is empty?

##### Optimal Python solution:
```python

- class Codec:
-     def serialize(self, root: 'Node') -> str:
-         if not root:
-             return ''
-         res = []
-         res.append(str(root.val))
-         res.append(str(len(root.children)))
-         for child in root.children:
-             res.append(self.serialize(child))
-         return ' '.join(res)
-     def deserialize(self, data: str) -> 'Node':
-         if not data:
-             return None
-         data = data.split()
-         val = int(data.pop(0))
-         num_children = int(data.pop(0))
-         root = Node(val, [])
-         for _ in range(num_children):
-             root.children.append(self.deserialize(data))
-         return root
- 
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- Use recursion to serialize and deserialize the tree
- Store the number of children for each node
- Use a delimiter to separate the values in the serialized string

- Use helper functions to serialize and deserialize the tree recursively.
- Handle the base case when the tree is empty.
- Store the number of children for each node to ensure correct deserialization.

- Handling empty tree
- Storing the number of children for each node

- Using a non-recursive approach
- Creating unnecessary nodes
    
### >> Comparison: 431 Encode N-ary Tree to Binary Tree [Hard] *VS* 428 Serialize and Deserialize N-ary Tree [Hard]
> Similarity distance: 0.5442
##### Similarities

- Both questions involve encoding and decoding an N-ary tree.
- Both questions are classified as 'Hard' level difficulty.
##### Differences

- Question 431 encodes an N-ary tree into a binary tree, while question 428 serializes and deserializes an N-ary tree.
- Question 431 uses a different approach to represent the N-ary tree as a binary tree compared to question 428.
- Question 431 requires converting the N-ary tree into a binary tree, while question 428 focuses on serializing and deserializing the N-ary tree.
##### New Insights in 428 Serialize and Deserialize N-ary Tree [Hard]

- Question 431 introduces a new insight into representing an N-ary tree as a binary tree.
- Question 428 provides a new insight into serializing and deserializing an N-ary tree.


---
# 5. From 108 Convert Sorted Array to Binary Search Tree [Easy] to 109 Convert Sorted List to Binary Search Tree [Medium]
> Similarity Distance: 0.5595

### >> Reminder: 108 Convert Sorted Array to Binary Search Tree [Easy]
Given an integer array nums where the elements are sorted in ascending order, convert it to a height-balanced binary search tree.
##### Optimal Python solution:
```python
class Solution:
    def sortedArrayToBST(self, nums: List[int]) -> TreeNode:
        if not nums:
            return None
        mid = len(nums) // 2
        root = TreeNode(nums[mid])
        root.left = self.sortedArrayToBST(nums[:mid])
        root.right = self.sortedArrayToBST(nums[mid+1:])
        return root
```
Convert a sorted array into a height-balanced binary search tree using recursion.
    
### >> 109 Convert Sorted List to Binary Search Tree [Medium]
Given the head of a singly linked list where elements are sorted in ascending order, convert it to a height balanced BST.
##### Sample input:
head = [-10,-3,0,5,9]
##### Sample output:
[0,-3,9,-10,null,5]

##### Questions to ask to clarify requirements:

- Can the linked list have duplicate elements?
- Can the linked list be empty?
- Can the linked list have negative numbers?

##### Optimal Python solution:
```python
class Solution:
    def sortedListToBST(self, head: ListNode) -> TreeNode:
        if not head:
            return None
        if not head.next:
            return TreeNode(head.val)
        slow, fast = head, head.next.next
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
        mid = slow.next
        slow.next = None
        root = TreeNode(mid.val)
        root.left = self.sortedListToBST(head)
        root.right = self.sortedListToBST(mid.next)
        return root
```
##### Time complexity:
O(nlogn)
##### Space complexity:
O(logn)
##### Notes:

- The middle element of the linked list will be the root of the BST.
- Recursively construct the left and right subtrees using the elements before and after the middle element.
- Use two pointers to find the middle element of the linked list.

- Use a helper function to find the middle element of the linked list.
- Handle the base cases of an empty linked list or a linked list with only one element.

- Finding the middle element of the linked list using two pointers.

- Converting the linked list to an array and then constructing the BST.
    
### >> Comparison: 108 Convert Sorted Array to Binary Search Tree [Easy] *VS* 109 Convert Sorted List to Binary Search Tree [Medium]
> Similarity distance: 0.5595
##### Similarities

- Both questions involve converting a sorted data structure (array or linked list) into a binary search tree.
- The resulting binary search tree should have balanced height.
##### Differences

- Question 108 uses a sorted array as input, while question 109 uses a sorted linked list.
- Question 108 has an easy difficulty level, while question 109 has a medium difficulty level.
- Question 108 allows for a more efficient solution using binary search, while question 109 requires a more complex approach using recursion and slow/fast pointers.
##### New Insights in 109 Convert Sorted List to Binary Search Tree [Medium]

- Both questions provide an opportunity to practice tree construction and traversal.
- Question 109 introduces the concept of slow and fast pointers to find the middle element of a linked list, which is useful in various other algorithms.


---
# 6. From 108 Convert Sorted Array to Binary Search Tree [Easy] to 95 Unique Binary Search Trees II [Medium]
> Similarity Distance: 0.5704

### >> Reminder: 108 Convert Sorted Array to Binary Search Tree [Easy]
Given an integer array nums where the elements are sorted in ascending order, convert it to a height-balanced binary search tree.
##### Optimal Python solution:
```python
class Solution:
    def sortedArrayToBST(self, nums: List[int]) -> TreeNode:
        if not nums:
            return None
        mid = len(nums) // 2
        root = TreeNode(nums[mid])
        root.left = self.sortedArrayToBST(nums[:mid])
        root.right = self.sortedArrayToBST(nums[mid+1:])
        return root
```
Convert a sorted array into a height-balanced binary search tree using recursion.
    
### >> 95 Unique Binary Search Trees II [Medium]
Given an integer n, generate all structurally unique BST's (binary search trees) that store values 1 ... n.
##### Sample input:
3
##### Sample output:
[[1,null,3,2],[3,2,null,1],[3,1,null,null,2],[2,1,3],[1,null,2,null,3]]

##### Questions to ask to clarify requirements:
What is the range of n? Can n be negative?

##### Optimal Python solution:
```python
class Solution:
    def generateTrees(self, n: int) -> List[TreeNode]:
        if n == 0:
            return []
        return self.generate(1, n)

    def generate(self, start, end):
        if start > end:
            return [None]
        res = []
        for i in range(start, end + 1):
            left_trees = self.generate(start, i - 1)
            right_trees = self.generate(i + 1, end)
            for left in left_trees:
                for right in right_trees:
                    root = TreeNode(i)
                    root.left = left
                    root.right = right
                    res.append(root)
        return res
```
##### Time complexity:
O(n^2)
##### Space complexity:
O(n)
##### Notes:
1. Use recursion to generate all possible BSTs
2. Use dynamic programming to store intermediate results
3. Use a nested loop to combine left and right subtrees
1. Use recursion to generate all possible combinations
2. Use dynamic programming to store intermediate results
3. Use a nested loop to combine left and right subtrees
1. Handling the base case when start > end
2. Combining left and right subtrees in a nested loop
1. Using a brute force approach to generate all possible BSTs
2. Not considering the base case when start > end
    
### >> Comparison: 108 Convert Sorted Array to Binary Search Tree [Easy] *VS* 95 Unique Binary Search Trees II [Medium]
> Similarity distance: 0.5704
##### Similarities

- Both questions involve constructing binary search trees.
- Both questions require working with sorted arrays.
- Both questions have a time complexity of O(n).
##### Differences

- Question 108 converts a sorted array into a binary search tree, while question 95 generates all unique binary search trees given a number of nodes.
- Question 108 has an easy difficulty level, while question 95 has a medium difficulty level.
- Question 108 only requires constructing a single binary search tree, while question 95 requires generating multiple unique binary search trees.
##### New Insights in 95 Unique Binary Search Trees II [Medium]

- Question 108 teaches us how to construct a binary search tree from a sorted array.
- Question 95 teaches us how to generate all unique binary search trees given a number of nodes.
- Both questions provide insights into working with binary search trees and sorted arrays.


---
# 7. From 95 Unique Binary Search Trees II [Medium] to 96 Unique Binary Search Trees [Medium]
> Similarity Distance: 0.5086

### >> Reminder: 95 Unique Binary Search Trees II [Medium]
Given an integer n, generate all structurally unique BST's (binary search trees) that store values 1 ... n.
##### Optimal Python solution:
```python
class Solution:
    def generateTrees(self, n: int) -> List[TreeNode]:
        if n == 0:
            return []
        return self.generate(1, n)

    def generate(self, start, end):
        if start > end:
            return [None]
        res = []
        for i in range(start, end + 1):
            left_trees = self.generate(start, i - 1)
            right_trees = self.generate(i + 1, end)
            for left in left_trees:
                for right in right_trees:
                    root = TreeNode(i)
                    root.left = left
                    root.right = right
                    res.append(root)
        return res
```
The essence of the problem is to generate all structurally unique BSTs that store values 1 ... n.
    
### >> 96 Unique Binary Search Trees [Medium]
Given n, how many structurally unique BST's (binary search trees) that store values 1 ... n?
##### Sample input:
3
##### Sample output:
5

##### Questions to ask to clarify requirements:
What is the range of n? Can n be negative?

##### Optimal Python solution:
```python
class Solution:
    def numTrees(self, n: int) -> int:
        dp = [0] * (n + 1)
        dp[0] = 1
        dp[1] = 1
        for i in range(2, n + 1):
            for j in range(1, i + 1):
                dp[i] += dp[j - 1] * dp[i - j]
        return dp[n]
```
##### Time complexity:
O(n^2)
##### Space complexity:
O(n)
##### Notes:
1. Use dynamic programming to store intermediate results
2. Use a nested loop to calculate the number of unique BSTs
1. Use dynamic programming to store intermediate results
2. Use a nested loop to calculate the number of unique BSTs
1. Initializing dp[0] and dp[1] to 1
2. Using a nested loop to calculate the number of unique BSTs
1. Using a brute force approach to calculate the number of unique BSTs
2. Not considering the base case when n = 0 or n = 1
    
### >> Comparison: 95 Unique Binary Search Trees II [Medium] *VS* 96 Unique Binary Search Trees [Medium]
> Similarity distance: 0.5086
##### Similarities

- Both questions are related to generating unique binary search trees.
- Both questions have a medium difficulty level.
##### Differences

- Question 95 focuses on generating all possible unique binary search trees given a number n.
- Question 96 focuses on counting the number of unique binary search trees that can be formed with n nodes.
##### New Insights in 96 Unique Binary Search Trees [Medium]

- Question 95 teaches us how to generate all possible unique binary search trees using recursion and dynamic programming.
- Question 96 teaches us how to count the number of unique binary search trees using the concept of Catalan numbers.


---
# 8. From 95 Unique Binary Search Trees II [Medium] to 333 Largest BST Subtree [Medium]
> Similarity Distance: 0.5968

### >> Reminder: 95 Unique Binary Search Trees II [Medium]
Given an integer n, generate all structurally unique BST's (binary search trees) that store values 1 ... n.
##### Optimal Python solution:
```python
class Solution:
    def generateTrees(self, n: int) -> List[TreeNode]:
        if n == 0:
            return []
        return self.generate(1, n)

    def generate(self, start, end):
        if start > end:
            return [None]
        res = []
        for i in range(start, end + 1):
            left_trees = self.generate(start, i - 1)
            right_trees = self.generate(i + 1, end)
            for left in left_trees:
                for right in right_trees:
                    root = TreeNode(i)
                    root.left = left
                    root.right = right
                    res.append(root)
        return res
```
The essence of the problem is to generate all structurally unique BSTs that store values 1 ... n.
    
### >> 333 Largest BST Subtree [Medium]
Given a binary tree, find the largest subtree which is a Binary Search Tree (BST), where largest means subtree with largest number of nodes in it.
##### Sample input:
[10,5,15,1,8,null,7]
##### Sample output:
3

##### Questions to ask to clarify requirements:

- What is the definition of a Binary Search Tree (BST)?
- Can the input tree be empty?
- Can the input tree have duplicate values?

##### Optimal Python solution:
```python
class Solution:
    def largestBSTSubtree(self, root: TreeNode) -> int:
        def dfs(node):
            if not node:
                return float('inf'), float('-inf'), 0
            left_min, left_max, left_count = dfs(node.left)
            right_min, right_max, right_count = dfs(node.right)
            if left_max < node.val < right_min:
                return min(left_min, node.val), max(right_max, node.val), left_count + right_count + 1
            else:
                return float('-inf'), float('inf'), max(left_count, right_count)
        return dfs(root)[2]
```
##### Time complexity:
O(N)
##### Space complexity:
O(N)
##### Notes:

- The largest BST subtree can be found using a depth-first search (DFS) approach.
- At each node, we check if the left subtree is a BST, the right subtree is a BST, and the current node value is between the maximum value of the left subtree and the minimum value of the right subtree.
- If the conditions are met, we update the minimum and maximum values of the subtree and return the count of nodes in the subtree.
- If the conditions are not met, we return -inf and inf to indicate that the subtree is not a BST.
- The largest BST subtree is the subtree with the maximum count of nodes.

- Use a depth-first search (DFS) approach to traverse the binary tree.
- Keep track of the minimum and maximum values of each subtree to check if it is a BST.
- Return the count of nodes in each subtree to find the largest BST subtree.

- Handling the case where the current node value is equal to the maximum value of the left subtree or the minimum value of the right subtree.

- Using an inefficient approach that checks all possible subtrees.
    
### >> Comparison: 95 Unique Binary Search Trees II [Medium] *VS* 333 Largest BST Subtree [Medium]
> Similarity distance: 0.5968
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve binary search trees (BST).
##### Differences

- Question 95 focuses on generating all unique BSTs given a range of numbers, while question 333 focuses on finding the largest BST subtree within a given binary tree.
- Question 95 requires generating all possible BSTs, while question 333 requires finding a specific subtree.
- Question 95 has a time complexity of O(n^2), while question 333 has a time complexity of O(n).
##### New Insights in 333 Largest BST Subtree [Medium]

- Question 95 teaches us how to generate all unique BSTs using recursion and dynamic programming.
- Question 333 teaches us how to find the largest BST subtree in a binary tree using a bottom-up approach.

