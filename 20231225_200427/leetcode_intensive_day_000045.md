
# Leetcode Intensive Tutorial Day 45 
> [Difficulty Score: 22]

> [Version: 20231225_200427]

## Courses overview of the day

- 497 Random Point in Non-overlapping Rectangles [Medium]
  - 223 Rectangle Area [Medium]
    - 84 Largest Rectangle in Histogram [Hard]
    - 531 Lonely Pixel I [Medium]
      - 533 Lonely Pixel II [Medium]
  - 391 Perfect Rectangle [Hard]
  - 85 Maximal Rectangle [Hard]
    - 221 Maximal Square [Medium]

#### Steps by steps

 - [1. From 497 Random Point in Non-overlapping Rectangles [Medium] to 223 Rectangle Area [Medium]](#1-from-497-random-point-in-non-overlapping-rectangles-medium-to-223-rectangle-area-medium)

 - [2. From 223 Rectangle Area [Medium] to 84 Largest Rectangle in Histogram [Hard]](#2-from-223-rectangle-area-medium-to-84-largest-rectangle-in-histogram-hard)

 - [3. From 223 Rectangle Area [Medium] to 531 Lonely Pixel I [Medium]](#3-from-223-rectangle-area-medium-to-531-lonely-pixel-i-medium)

 - [4. From 531 Lonely Pixel I [Medium] to 533 Lonely Pixel II [Medium]](#4-from-531-lonely-pixel-i-medium-to-533-lonely-pixel-ii-medium)

 - [5. From 497 Random Point in Non-overlapping Rectangles [Medium] to 391 Perfect Rectangle [Hard]](#5-from-497-random-point-in-non-overlapping-rectangles-medium-to-391-perfect-rectangle-hard)

 - [6. From 497 Random Point in Non-overlapping Rectangles [Medium] to 85 Maximal Rectangle [Hard]](#6-from-497-random-point-in-non-overlapping-rectangles-medium-to-85-maximal-rectangle-hard)

 - [7. From 85 Maximal Rectangle [Hard] to 221 Maximal Square [Medium]](#7-from-85-maximal-rectangle-hard-to-221-maximal-square-medium)

#### Summary


- 391 Perfect Rectangle : Given a list of rectangles, determine if they form a perfect rectangle.
- 497 Random Point in Non-overlapping Rectangles : The essence of the problem is to randomly and uniformly pick an integer point in the space covered by the rectangles.
- 223 Rectangle Area : Compute the area covered by two rectangles in a 2D plane.
- 85 Maximal Rectangle : The essence of this problem is to find the largest rectangle in a binary matrix by using dynamic programming and a stack.
- 84 Largest Rectangle in Histogram : The essence of this problem is to find the maximum area of rectangles in a histogram.
- 221 Maximal Square : The essence of this problem is to find the largest square containing only 1's in a binary matrix.
- 531 Lonely Pixel I : Counting the number of black pixels that are lonely in a picture
- 533 Lonely Pixel II : Count the number of black lonely pixels in a picture.
> Similarity Diameter of these problems: 0.7958


---
# 1. From 497 Random Point in Non-overlapping Rectangles [Medium] to 223 Rectangle Area [Medium]
> Similarity Distance: 0.4323

### >> 497 Random Point in Non-overlapping Rectangles [Medium]
Given a list of non-overlapping axis-aligned rectangles rects, write a function pick which randomly and uniformily picks an integer point in the space covered by the rectangles.
##### Sample input:
[[1,1,5,5]]
##### Sample output:
[[4,1],[4,1],[3,3],[3,3],[3,3]]

##### Questions to ask to clarify requirements:
What is the range of the coordinates of the points? Can the rectangles have negative coordinates?

##### Optimal Python solution:
```python
class Solution:
    def __init__(self, rects: List[List[int]]):
        self.rects = rects
        self.weights = []
        self.total_area = 0
        for rect in rects:
            area = (rect[2] - rect[0] + 1) * (rect[3] - rect[1] + 1)
            self.total_area += area
            self.weights.append(self.total_area)

    def pick(self) -> List[int]:
        rand_area = random.randint(1, self.total_area)
        left, right = 0, len(self.weights) - 1
        while left < right:
            mid = (left + right) // 2
            if self.weights[mid] < rand_area:
                left = mid + 1
            else:
                right = mid
        rect = self.rects[left]
        x = random.randint(rect[0], rect[2])
        y = random.randint(rect[1], rect[3])
        return [x, y]
```
##### Time complexity:
O(logN) for pick()
##### Space complexity:
O(N)
##### Notes:
1. Calculate the total area covered by all the rectangles
2. Generate a random number between 1 and the total area
3. Use binary search to find the rectangle that corresponds to the random number
4. Generate a random point within the chosen rectangle
Use binary search to find the rectangle that corresponds to the random number.
The tricky part is to use binary search to find the rectangle that corresponds to the random number.
Avoid generating a random point within each rectangle and then checking if it is covered by any of the rectangles.
    
### >> 223 Rectangle Area [Medium]
Given the coordinates of two rectilinear rectangles in a 2D plane, return the total area covered by the two rectangles.
##### Sample input:
[-3, 0, 3, 4, 0, -1, 9, 2]
##### Sample output:
45

##### Questions to ask to clarify requirements:

- Can the rectangles be overlapping?
- Can the rectangles have negative coordinates?
- Can the rectangles have zero area?

##### Optimal Python solution:
```python
class Solution:
    def computeArea(self, A: int, B: int, C: int, D: int, E: int, F: int, G: int, H: int) -> int:
        area1 = (C - A) * (D - B)
        area2 = (G - E) * (H - F)
        overlap_width = min(C, G) - max(A, E)
        overlap_height = min(D, H) - max(B, F)
        overlap_area = max(overlap_width, 0) * max(overlap_height, 0)
        return area1 + area2 - overlap_area
```
##### Time complexity:
O(1)
##### Space complexity:
O(1)
##### Notes:

- Compute the area of each rectangle separately
- Compute the overlap area by finding the intersection of the rectangles
- Subtract the overlap area from the total area

- Use the min and max functions to find the intersection of the rectangles.
- Handle the case where the rectangles do not overlap separately.

- Handling the case where the rectangles do not overlap

- Calculating the area of the rectangles separately and then subtracting the overlap area
    
### >> Comparison: 497 Random Point in Non-overlapping Rectangles [Medium] *VS* 223 Rectangle Area [Medium]
> Similarity distance: 0.4323
##### Similarities

- Both questions involve rectangles and their areas.
- Both questions require generating random points within rectangles.
##### Differences

- Question 497 involves non-overlapping rectangles, while question 223 does not specify overlapping.
- Question 497 requires generating random points uniformly within the given rectangles, while question 223 does not involve random point generation.
- Question 497 has a constraint on the number of rectangles, while question 223 does not have such a constraint.
##### New Insights in 223 Rectangle Area [Medium]

- Question 497 requires implementing a weighted random selection algorithm to generate points uniformly within the rectangles.
- Question 223 may require calculating the intersection area of two rectangles.


---
# 2. From 223 Rectangle Area [Medium] to 84 Largest Rectangle in Histogram [Hard]
> Similarity Distance: 0.4500

### >> Reminder: 223 Rectangle Area [Medium]
Given the coordinates of two rectilinear rectangles in a 2D plane, return the total area covered by the two rectangles.
##### Optimal Python solution:
```python
class Solution:
    def computeArea(self, A: int, B: int, C: int, D: int, E: int, F: int, G: int, H: int) -> int:
        area1 = (C - A) * (D - B)
        area2 = (G - E) * (H - F)
        overlap_width = min(C, G) - max(A, E)
        overlap_height = min(D, H) - max(B, F)
        overlap_area = max(overlap_width, 0) * max(overlap_height, 0)
        return area1 + area2 - overlap_area
```
Compute the area covered by two rectangles in a 2D plane.
    
### >> 84 Largest Rectangle in Histogram [Hard]
Given n non-negative integers representing the histogram's bar height where the width of each bar is 1, find the area of the largest rectangle in the histogram.
##### Sample input:
[2,1,5,6,2,3]
##### Sample output:
10

##### Questions to ask to clarify requirements:
Can the histogram contain negative integers? Can the histogram be empty?

##### Optimal Python solution:
```python
class Solution:
    def largestRectangleArea(self, heights: List[int]) -> int:
        stack = [-1]
        max_area = 0
        for i in range(len(heights)):
            while stack[-1] != -1 and heights[stack[-1]] >= heights[i]:
                h = heights[stack.pop()]
                w = i - stack[-1] - 1
                max_area = max(max_area, h * w)
            stack.append(i)
        while stack[-1] != -1:
            h = heights[stack.pop()]
            w = len(heights) - stack[-1] - 1
            max_area = max(max_area, h * w)
        return max_area
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use a stack to keep track of the indices of the bars
2. Iterate through the histogram
3. If the current bar is shorter than the bar at the top of the stack, calculate the area of the rectangle formed by the bar at the top of the stack and the previous bar
4. Keep track of the maximum area
5. Return the maximum area
Make sure to handle edge cases such as an empty histogram.
None
None
    
### >> Comparison: 223 Rectangle Area [Medium] *VS* 84 Largest Rectangle in Histogram [Hard]
> Similarity distance: 0.4500
##### Similarities

- Both questions involve calculating the area of rectangles.
- Both questions require understanding the concept of overlapping rectangles.
##### Differences

- Question 223 involves finding the area of a rectangle formed by the intersection of two rectangles.
- Question 84 involves finding the largest rectangle that can be formed in a histogram.
##### New Insights in 84 Largest Rectangle in Histogram [Hard]

- Question 223 introduces the concept of overlapping rectangles and requires finding the area of the intersection.
- Question 84 introduces the concept of finding the largest rectangle in a histogram using stack data structure.


---
# 3. From 223 Rectangle Area [Medium] to 531 Lonely Pixel I [Medium]
> Similarity Distance: 0.5908

### >> Reminder: 223 Rectangle Area [Medium]
Given the coordinates of two rectilinear rectangles in a 2D plane, return the total area covered by the two rectangles.
##### Optimal Python solution:
```python
class Solution:
    def computeArea(self, A: int, B: int, C: int, D: int, E: int, F: int, G: int, H: int) -> int:
        area1 = (C - A) * (D - B)
        area2 = (G - E) * (H - F)
        overlap_width = min(C, G) - max(A, E)
        overlap_height = min(D, H) - max(B, F)
        overlap_area = max(overlap_width, 0) * max(overlap_height, 0)
        return area1 + area2 - overlap_area
```
Compute the area covered by two rectangles in a 2D plane.
    
### >> 531 Lonely Pixel I [Medium]
Given a picture consisting of black and white pixels, find the number of black lonely pixels.
##### Sample input:

- [['W', 'W', 'B'],
-  ['W', 'B', 'W'],
-  ['B', 'W', 'W']]
##### Sample output:
3

##### Questions to ask to clarify requirements:

- What is the maximum size of the picture?
- Can the picture contain other characters besides 'B' and 'W'?
- Should the solution be case-sensitive?

##### Optimal Python solution:
```python

- def findLonelyPixel(picture):
-     rows = len(picture)
-     cols = len(picture[0])
-     row_count = [0] * rows
-     col_count = [0] * cols
-     for i in range(rows):
-         for j in range(cols):
-             if picture[i][j] == 'B':
-                 row_count[i] += 1
-                 col_count[j] += 1
-     count = 0
-     for i in range(rows):
-         for j in range(cols):
-             if picture[i][j] == 'B' and row_count[i] == 1 and col_count[j] == 1:
-                 count += 1
-     return count
- 
- picture = [['W', 'W', 'B'],
-            ['W', 'B', 'W'],
-            ['B', 'W', 'W']]
- print(findLonelyPixel(picture))
```
##### Time complexity:
O(m * n)
##### Space complexity:
O(m + n)
##### Notes:

- Count the number of black pixels in each row and column
- Count the number of black pixels that are lonely

- Use arrays to count occurrences
- Optimize the solution by avoiding unnecessary iterations

- The picture can be represented as a matrix
- Use two arrays to count the number of black pixels in each row and column

- Using a brute force approach to count the number of black pixels
    
### >> Comparison: 223 Rectangle Area [Medium] *VS* 531 Lonely Pixel I [Medium]
> Similarity distance: 0.5908
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve manipulating a grid or matrix.
- Both questions require understanding and manipulating the dimensions of rectangles or pixels.
- Both questions involve counting or calculating areas.
##### Differences

- Question 223 involves calculating the area of overlapping rectangles, while question 531 involves finding the number of lonely pixels in a grid.
- Question 223 requires understanding and manipulating rectangles, while question 531 focuses on individual pixels.
- Question 223 involves finding the area of rectangles, while question 531 involves counting pixels.
- Question 223 requires considering overlapping rectangles, while question 531 focuses on isolated pixels.
##### New Insights in 531 Lonely Pixel I [Medium]

- Question 223 introduces the concept of overlapping rectangles and requires finding the area of the overlap.
- Question 531 introduces the concept of lonely pixels and requires identifying and counting them in a grid.
- Both questions provide opportunities to practice problem-solving skills related to grids and counting.


---
# 4. From 531 Lonely Pixel I [Medium] to 533 Lonely Pixel II [Medium]
> Similarity Distance: 0.2126

### >> Reminder: 531 Lonely Pixel I [Medium]
Given a picture consisting of black and white pixels, find the number of black lonely pixels.
##### Optimal Python solution:
```python

- def findLonelyPixel(picture):
-     rows = len(picture)
-     cols = len(picture[0])
-     row_count = [0] * rows
-     col_count = [0] * cols
-     for i in range(rows):
-         for j in range(cols):
-             if picture[i][j] == 'B':
-                 row_count[i] += 1
-                 col_count[j] += 1
-     count = 0
-     for i in range(rows):
-         for j in range(cols):
-             if picture[i][j] == 'B' and row_count[i] == 1 and col_count[j] == 1:
-                 count += 1
-     return count
- 
- picture = [['W', 'W', 'B'],
-            ['W', 'B', 'W'],
-            ['B', 'W', 'W']]
- print(findLonelyPixel(picture))
```
Counting the number of black pixels that are lonely in a picture
    
### >> 533 Lonely Pixel II [Medium]
Given a picture consisting of black and white pixels, find the number of black lonely pixels.
##### Sample input:

- [["W","B","W","B","B","W"],["W","B","W","B","B","W"],["W","B","W","B","B","W"],["W","W","B","W","B","W"]]
##### Sample output:

- 6

##### Questions to ask to clarify requirements:

- What is the definition of a lonely pixel?
- Can the picture contain other colors besides black and white?
- Can the picture be empty?

##### Optimal Python solution:
```python

- def findBlackPixel(picture, N):
-     rows = collections.defaultdict(int)
-     cols = collections.defaultdict(int)
-     for i in range(N):
-         for j in range(N):
-             if picture[i][j] == 'B':
-                 rows[i] += 1
-                 cols[j] += 1
-     count = 0
-     for i in range(N):
-         for j in range(N):
-             if picture[i][j] == 'B' and rows[i] == cols[j] == N:
-                 count += 1
-     return count
- 
- picture = [['W','B','W','B','B','W'],['W','B','W','B','B','W'],['W','B','W','B','B','W'],['W','W','B','W','B','W']]
- N = 4
- print(findBlackPixel(picture, N))
```
##### Time complexity:
O(N^2)
##### Space complexity:
O(N)
##### Notes:

- Count the number of black pixels in each row and column
- Check if the black pixel is lonely by comparing the counts with N

- Use dictionaries to count the number of black pixels in each row and column.
- Iterate through the picture to check if each black pixel is lonely.

- The black pixels must be in the same row and column to be considered lonely

- Counting the black pixels individually for each row and column
    
### >> Comparison: 531 Lonely Pixel I [Medium] *VS* 533 Lonely Pixel II [Medium]
> Similarity distance: 0.2126
##### Similarities

- Both questions are related to finding lonely pixels in a binary image.
##### Differences

- Lonely Pixel I focuses on finding the number of lonely black pixels in the image.
- Lonely Pixel II focuses on finding the number of lonely black pixels in each row.
##### New Insights in 533 Lonely Pixel II [Medium]

- Lonely Pixel I: The lonely black pixels are those that are the only black pixel in their respective row and column.
- Lonely Pixel II: The lonely black pixels are those that are the only black pixel in their respective row and column, and there are exactly 'N' black pixels in the same column.


---
# 5. From 497 Random Point in Non-overlapping Rectangles [Medium] to 391 Perfect Rectangle [Hard]
> Similarity Distance: 0.4609

### >> Reminder: 497 Random Point in Non-overlapping Rectangles [Medium]
Given a list of non-overlapping axis-aligned rectangles rects, write a function pick which randomly and uniformily picks an integer point in the space covered by the rectangles.
##### Optimal Python solution:
```python
class Solution:
    def __init__(self, rects: List[List[int]]):
        self.rects = rects
        self.weights = []
        self.total_area = 0
        for rect in rects:
            area = (rect[2] - rect[0] + 1) * (rect[3] - rect[1] + 1)
            self.total_area += area
            self.weights.append(self.total_area)

    def pick(self) -> List[int]:
        rand_area = random.randint(1, self.total_area)
        left, right = 0, len(self.weights) - 1
        while left < right:
            mid = (left + right) // 2
            if self.weights[mid] < rand_area:
                left = mid + 1
            else:
                right = mid
        rect = self.rects[left]
        x = random.randint(rect[0], rect[2])
        y = random.randint(rect[1], rect[3])
        return [x, y]
```
The essence of the problem is to randomly and uniformly pick an integer point in the space covered by the rectangles.
    
### >> 391 Perfect Rectangle [Hard]
Given N axis-aligned rectangles where N > 0, determine if they all together form an exact cover of a rectangular region.
##### Sample input:

- [[1,1,3,3],[3,1,4,2],[3,2,4,4],[1,3,2,4],[2,3,3,4]]
##### Sample output:

- true

##### Questions to ask to clarify requirements:

- Can the rectangles overlap with each other?
- Can the rectangles be rotated?
- Can the rectangles have negative coordinates?

##### Optimal Python solution:
```python

- class Solution:
-     def isRectangleCover(self, rectangles: List[List[int]]) -> bool:
-         corners = set()
-         area = 0
-         for rect in rectangles:
-             x1, y1, x2, y2 = rect
-             area += (x2 - x1) * (y2 - y1)
-             corners ^= {(x1, y1), (x1, y2), (x2, y1), (x2, y2)}
-         if len(corners) != 4:
-             return False
-         corners = sorted(corners)
-         return area == (corners[-1][0] - corners[0][0]) * (corners[-1][1] - corners[0][1])
```
##### Time complexity:
O(n log n)
##### Space complexity:
O(n)
##### Notes:

- The rectangles must form a perfect rectangle
- The area of the perfect rectangle must be equal to the sum of the areas of the individual rectangles
- The corners of the perfect rectangle must be the corners of the individual rectangles

- Use a hash set to efficiently check for duplicate corners.
- Sort the corners to easily calculate the area of the perfect rectangle.

- Handling overlapping rectangles
- Handling rotated rectangles
- Handling negative coordinates

- Using brute force to check all possible combinations of rectangles
    
### >> Comparison: 497 Random Point in Non-overlapping Rectangles [Medium] *VS* 391 Perfect Rectangle [Hard]
> Similarity distance: 0.4609
##### Similarities

- Both questions involve rectangles and points within those rectangles.
- Both questions require calculating the area of rectangles.
- Both questions involve randomization.
##### Differences

- Question 497 involves generating random points within non-overlapping rectangles, while question 391 involves determining if a set of rectangles can form a perfect rectangle.
- Question 497 is rated as Medium difficulty, while question 391 is rated as Hard difficulty.
- Question 497 requires implementing a randomization algorithm, while question 391 requires checking the validity of a set of rectangles.
##### New Insights in 391 Perfect Rectangle [Hard]

- Question 497 introduces the concept of generating random points within non-overlapping rectangles.
- Question 391 introduces the concept of determining if a set of rectangles can form a perfect rectangle.


---
# 6. From 497 Random Point in Non-overlapping Rectangles [Medium] to 85 Maximal Rectangle [Hard]
> Similarity Distance: 0.5244

### >> Reminder: 497 Random Point in Non-overlapping Rectangles [Medium]
Given a list of non-overlapping axis-aligned rectangles rects, write a function pick which randomly and uniformily picks an integer point in the space covered by the rectangles.
##### Optimal Python solution:
```python
class Solution:
    def __init__(self, rects: List[List[int]]):
        self.rects = rects
        self.weights = []
        self.total_area = 0
        for rect in rects:
            area = (rect[2] - rect[0] + 1) * (rect[3] - rect[1] + 1)
            self.total_area += area
            self.weights.append(self.total_area)

    def pick(self) -> List[int]:
        rand_area = random.randint(1, self.total_area)
        left, right = 0, len(self.weights) - 1
        while left < right:
            mid = (left + right) // 2
            if self.weights[mid] < rand_area:
                left = mid + 1
            else:
                right = mid
        rect = self.rects[left]
        x = random.randint(rect[0], rect[2])
        y = random.randint(rect[1], rect[3])
        return [x, y]
```
The essence of the problem is to randomly and uniformly pick an integer point in the space covered by the rectangles.
    
### >> 85 Maximal Rectangle [Hard]
Given a 2D binary matrix filled with 0's and 1's, find the largest rectangle containing only 1's and return its area.
##### Sample input:

- [["1","0","1","0","0"],["1","0","1","1","1"],["1","1","1","1","1"],["1","0","0","1","0"]]
##### Sample output:

- 6

##### Questions to ask to clarify requirements:

- What is the maximum size of the matrix?
- Can the matrix be empty?
- Can the matrix contain characters other than '0' and '1'?
- Should the rectangle be a square or can it have different width and height?

##### Optimal Python solution:
```python

- def maximalRectangle(matrix):
    if not matrix:
        return 0
    m, n = len(matrix), len(matrix[0])
    left = [0] * n
    right = [n] * n
    height = [0] * n
    max_area = 0
    for i in range(m):
        cur_left, cur_right = 0, n
        for j in range(n):
            if matrix[i][j] == '1':
                height[j] += 1
                left[j] = max(left[j], cur_left)
            else:
                height[j] = 0
                left[j] = 0
                cur_left = j + 1
        for j in range(n - 1, -1, -1):
            if matrix[i][j] == '1':
                right[j] = min(right[j], cur_right)
                max_area = max(max_area, height[j] * (right[j] - left[j]))
            else:
                right[j] = n
                cur_right = j
    return max_area

matrix = [["1","0","1","0","0"],["1","0","1","1","1"],["1","1","1","1","1"],["1","0","0","1","0"]]
print(maximalRectangle(matrix))
```
##### Time complexity:
O(m * n)
##### Space complexity:
O(n)
##### Notes:

- Use dynamic programming to calculate the height, left, and right arrays
- Use a stack to keep track of the left and right boundaries of the rectangles
- Calculate the area of each rectangle and update the maximum area

- Use a stack to keep track of the left and right boundaries of the rectangles.
- Calculate the area of each rectangle and update the maximum area.
- Handle edge cases and optimize the solution for large matrices.

- Calculating the left and right boundaries of the rectangles
- Updating the maximum area

- Brute force approach
- Nested loops
    
### >> Comparison: 497 Random Point in Non-overlapping Rectangles [Medium] *VS* 85 Maximal Rectangle [Hard]
> Similarity distance: 0.5244
##### Similarities

- Both questions involve rectangles and points within those rectangles.
- Both questions require finding random points within the given rectangles.
##### Differences

- Question 497 involves non-overlapping rectangles, while question 85 does not have this constraint.
- Question 497 is classified as medium difficulty, while question 85 is classified as hard difficulty.
- Question 497 requires generating random points, while question 85 requires finding the maximal rectangle.
- Question 497 has a straightforward solution using random number generation, while question 85 requires a more complex algorithm.
##### New Insights in 85 Maximal Rectangle [Hard]

- Question 497 introduces the concept of generating random points within non-overlapping rectangles.
- Question 85 introduces the concept of finding the maximal rectangle within a matrix.


---
# 7. From 85 Maximal Rectangle [Hard] to 221 Maximal Square [Medium]
> Similarity Distance: 0.3415

### >> Reminder: 85 Maximal Rectangle [Hard]
Given a 2D binary matrix filled with 0's and 1's, find the largest rectangle containing only 1's and return its area.
##### Optimal Python solution:
```python

- def maximalRectangle(matrix):
    if not matrix:
        return 0
    m, n = len(matrix), len(matrix[0])
    left = [0] * n
    right = [n] * n
    height = [0] * n
    max_area = 0
    for i in range(m):
        cur_left, cur_right = 0, n
        for j in range(n):
            if matrix[i][j] == '1':
                height[j] += 1
                left[j] = max(left[j], cur_left)
            else:
                height[j] = 0
                left[j] = 0
                cur_left = j + 1
        for j in range(n - 1, -1, -1):
            if matrix[i][j] == '1':
                right[j] = min(right[j], cur_right)
                max_area = max(max_area, height[j] * (right[j] - left[j]))
            else:
                right[j] = n
                cur_right = j
    return max_area

matrix = [["1","0","1","0","0"],["1","0","1","1","1"],["1","1","1","1","1"],["1","0","0","1","0"]]
print(maximalRectangle(matrix))
```
The essence of this problem is to find the largest rectangle in a binary matrix by using dynamic programming and a stack.
    
### >> 221 Maximal Square [Medium]
Given an m x n binary matrix filled with 0's and 1's, find the largest square containing only 1's and return its area.
##### Sample input:

- [["1","0","1","0","0"],["1","0","1","1","1"],["1","1","1","1","1"],["1","0","0","1","0"]]
##### Sample output:

- 4

##### Questions to ask to clarify requirements:

- What is the maximum size of the matrix?
- Can the matrix be empty?
- Can the matrix contain characters other than '0' and '1'?

##### Optimal Python solution:
```python

- def maximalSquare(matrix):
    if not matrix:
        return 0
    m, n = len(matrix), len(matrix[0])
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    max_len = 0
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if matrix[i - 1][j - 1] == '1':
                dp[i][j] = min(dp[i - 1][j], dp[i][j - 1], dp[i - 1][j - 1]) + 1
                max_len = max(max_len, dp[i][j])
    return max_len * max_len
- matrix = [["1","0","1","0","0"],["1","0","1","1","1"],["1","1","1","1","1"],["1","0","0","1","0"]]
print(maximalSquare(matrix))
```
##### Time complexity:
O(m*n)
##### Space complexity:
O(m*n)
##### Notes:

- Use dynamic programming to solve the problem
- Create a 2D array to store the maximum square size at each position
- Iterate through the matrix and update the maximum square size
- Return the area of the largest square

- Break down the problem into smaller subproblems.
- Use a 2D array to store intermediate results.
- Optimize the solution by avoiding unnecessary calculations.

- Finding the minimum value among three adjacent cells

- Brute force approach
    
### >> Comparison: 85 Maximal Rectangle [Hard] *VS* 221 Maximal Square [Medium]
> Similarity distance: 0.3415
##### Similarities

- Both questions involve finding the largest rectangle/square in a matrix.
- Both questions have a dynamic programming solution approach.
- Both questions have a time complexity of O(m*n), where m is the number of rows and n is the number of columns in the matrix.
##### Differences

- Question 85 (Maximal Rectangle) finds the largest rectangle, while question 221 (Maximal Square) finds the largest square.
- Question 85 allows rectangles to be formed by connecting adjacent 1s vertically or horizontally, while question 221 only allows squares to be formed by connecting adjacent 1s vertically or horizontally.
- Question 85 requires calculating the area of the largest rectangle, while question 221 requires calculating the side length of the largest square.
##### New Insights in 221 Maximal Square [Medium]

- Question 85 can be solved using the largest rectangle in histogram approach, where the problem is reduced to finding the largest rectangle in each row of the matrix.
- Question 221 can be solved using dynamic programming, where the problem is reduced to finding the largest square ending at each cell of the matrix.

