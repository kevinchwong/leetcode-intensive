
# Leetcode Intensive Tutorial Day 6 
> [Difficulty Score: 12]

> [Version: 20231226_040350]

> [Including this day, you had studied : 42 leetcode problems]


## Courses overview of the day

- 190 Reverse Bits [Easy]
  - 7 Reverse Integer [Easy]
  - 371 Sum of Two Integers [Medium]
    - 289 Game of Life [Medium]
    - 29 Divide Two Integers [Medium]
    - 50 Pow(x, n) [Medium]
      - 372 Super Pow [Medium]

#### Step by step

 - [1. From 190 Reverse Bits [Easy] to 7 Reverse Integer [Easy]](#1-from-190-reverse-bits-easy-to-7-reverse-integer-easy))

 - [2. From 190 Reverse Bits [Easy] to 371 Sum of Two Integers [Medium]](#2-from-190-reverse-bits-easy-to-371-sum-of-two-integers-medium))

 - [3. From 371 Sum of Two Integers [Medium] to 289 Game of Life [Medium]](#3-from-371-sum-of-two-integers-medium-to-289-game-of-life-medium))

 - [4. From 371 Sum of Two Integers [Medium] to 29 Divide Two Integers [Medium]](#4-from-371-sum-of-two-integers-medium-to-29-divide-two-integers-medium))

 - [5. From 371 Sum of Two Integers [Medium] to 50 Pow(x, n) [Medium]](#5-from-371-sum-of-two-integers-medium-to-50-powx,-n-medium))

 - [6. From 50 Pow(x, n) [Medium] to 372 Super Pow [Medium]](#6-from-50-powx,-n-medium-to-372-super-pow-medium))

    

#### Summary


- 371 Sum of Two Integers : The essence of this problem is to perform addition using bit manipulation without using the + and - operators.
- 372 Super Pow : The essence of this problem is to calculate a^b % 1337 using modular arithmetic and exponentiation.
- 50 Pow(x, n) : Calculate x raised to the power n using binary exponentiation.
- 190 Reverse Bits : Reverse the bits of a 32 bits unsigned integer.
- 7 Reverse Integer : Reverse the digits of an integer and handle edge cases.
- 29 Divide Two Integers : Perform division without using multiplication, division, and mod operator.
- 289 Game of Life : The essence of this problem is to update the board in-place without using extra space. This can be achieved by using bit manipulation to store the next state of each cell.
> Similarity Diameter of these problems: 0.6051


---
# 1. From 190 Reverse Bits [Easy] to 7 Reverse Integer [Easy]
> Similarity Distance: 0.4619

### >> 190 Reverse Bits [Easy]
Reverse bits of a given 32 bits unsigned integer.
##### Sample input:
43261596
##### Sample output:
964176192

##### Questions to ask to clarify requirements:
What should be the behavior if the input is not a 32 bits unsigned integer?

##### Optimal Python solution:
```python
def reverseBits(n):
    return int(bin(n)[2:].zfill(32)[::-1], 2)
```
##### Time complexity:
O(1)
##### Space complexity:
O(1)
##### Notes:
Convert the integer to binary representation, reverse the string, and convert it back to an integer.
Use built-in functions to convert between binary and integer representations.
Converting the integer to binary representation and reversing the string.
None
    
### >> 7 Reverse Integer [Easy]
Given a 32-bit signed integer, reverse digits of an integer.
##### Sample input:
123
-123
120
##### Sample output:
321
-321
21

##### Questions to ask to clarify requirements:
What should be the output if the reversed integer overflows?

##### Optimal Python solution:
```python
class Solution:
    def reverse(self, x: int) -> int:
        if x < 0:
            x = -int(str(-x)[::-1])
        else:
            x = int(str(x)[::-1])
        if x < -2**31 or x > 2**31 - 1:
            return 0
        return x
```
##### Time complexity:
O(log(x))
##### Space complexity:
O(1)
##### Notes:
1. Reverse the digits of the given integer.
2. Handle the case when the reversed integer overflows.
3. Handle the case when the input is a negative number.
Use the modulo operator to extract the last digit of a number.
Handling the case when the reversed integer overflows.
Using string conversion to reverse the integer.
    
### >> Comparison: 190 Reverse Bits [Easy] *VS* 7 Reverse Integer [Easy]
> Similarity distance: 0.4619
##### Similarities

- Both questions involve reversing the bits or digits of a given number.
- Both questions have an easy difficulty level.
##### Differences

- Question 190 involves reversing the bits of a 32-bit unsigned integer, while question 7 involves reversing the digits of a signed integer.
- Question 190 requires bitwise operations to reverse the bits, while question 7 requires arithmetic operations to reverse the digits.
- Question 190 has a constraint on the input size (32-bit unsigned integer), while question 7 does not have any specific constraint on the input size.
##### New Insights in 7 Reverse Integer [Easy]

- Question 190: Understanding bitwise operations and their applications in reversing bits.
- Question 7: Handling integer overflow and underflow cases while reversing the digits.


---
# 2. From 190 Reverse Bits [Easy] to 371 Sum of Two Integers [Medium]
> Similarity Distance: 0.4638

### >> Reminder: 190 Reverse Bits [Easy]
Reverse bits of a given 32 bits unsigned integer.
##### Optimal Python solution:
```python
def reverseBits(n):
    return int(bin(n)[2:].zfill(32)[::-1], 2)
```
Reverse the bits of a 32 bits unsigned integer.
    
### >> 371 Sum of Two Integers [Medium]
Calculate the sum of two integers without using the + and - operators.
##### Sample input:
1
2
##### Sample output:
3

##### Questions to ask to clarify requirements:
Can the input integers be negative?

##### Optimal Python solution:
```python
class Solution:
    def getSum(self, a: int, b: int) -> int:
        mask = 0xffffffff
        while b & mask:
            carry = (a & b) << 1
            a = a ^ b
            b = carry & mask
        return a if b > mask else a & mask
```
##### Time complexity:
O(1)
##### Space complexity:
O(1)
##### Notes:
1. Use bit manipulation to perform addition
2. Handle negative integers by using a mask
3. Use a while loop to iterate until there is no carry
Understand how bit manipulation works.
Handling negative integers
Using + and - operators
    
### >> Comparison: 190 Reverse Bits [Easy] *VS* 371 Sum of Two Integers [Medium]
> Similarity distance: 0.4638
##### Similarities

- Both questions involve bitwise operations.
- Both questions require manipulating binary representations of numbers.
##### Differences

- 190 Reverse Bits is an Easy level question, while 371 Sum of Two Integers is a Medium level question.
- 190 Reverse Bits involves reversing the bits of a given 32-bit unsigned integer, while 371 Sum of Two Integers involves finding the sum of two integers without using the + or - operators.
- 190 Reverse Bits requires shifting and bitwise operations, while 371 Sum of Two Integers requires bitwise operations and bit manipulation.
- 190 Reverse Bits has a time complexity of O(1), while 371 Sum of Two Integers has a time complexity of O(log n).
##### New Insights in 371 Sum of Two Integers [Medium]

- From 190 Reverse Bits, we can learn how to reverse the bits of a given number using bitwise operations.
- From 371 Sum of Two Integers, we can learn how to perform addition of two integers using bitwise operations and bit manipulation.


---
# 3. From 371 Sum of Two Integers [Medium] to 289 Game of Life [Medium]
> Similarity Distance: 0.4004

### >> Reminder: 371 Sum of Two Integers [Medium]
Calculate the sum of two integers without using the + and - operators.
##### Optimal Python solution:
```python
class Solution:
    def getSum(self, a: int, b: int) -> int:
        mask = 0xffffffff
        while b & mask:
            carry = (a & b) << 1
            a = a ^ b
            b = carry & mask
        return a if b > mask else a & mask
```
The essence of this problem is to perform addition using bit manipulation without using the + and - operators.
    
### >> 289 Game of Life [Medium]
Given a board with m by n cells, each cell has an initial state live (1) or dead (0). Each cell interacts with its eight neighbors (horizontal, vertical, diagonal) using the following four rules:

Any live cell with fewer than two live neighbors dies, as if caused by under-population.
Any live cell with two or three live neighbors lives on to the next generation.
Any live cell with more than three live neighbors dies, as if by over-population.
Any dead cell with exactly three live neighbors becomes a live cell, as if by reproduction.
Write a function to compute the next state (after one update) of the board given its current state.

Follow up:
Could you solve it in-place? Remember that the board needs to be updated at the same time: You cannot update some cells first and then use their updated values to update other cells.
In this question, we represent the board using a 2D array. In principle, the board is infinite, which would cause problems when the active area encroaches the border of the array. How would you address these problems?
##### Sample input:
[[0,1,0],[0,0,1],[1,1,1],[0,0,0]]
##### Sample output:
[[0,0,0],[1,0,1],[0,1,1],[0,1,0]]

##### Questions to ask to clarify requirements:
What is the maximum size of the board? Can we assume the board is always rectangular?

##### Optimal Python solution:
```python
def gameOfLife(board):
    m, n = len(board), len(board[0])
    for i in range(m):
        for j in range(n):
            count = 0
            for I in range(max(i-1, 0), min(i+2, m)):
                for J in range(max(j-1, 0), min(j+2, n)):
                    count += board[I][J] & 1
            if count == 3 or count - board[i][j] == 3:
                board[i][j] |= 2
    for i in range(m):
        for j in range(n):
            board[i][j] >>= 1
```
##### Time complexity:
O(m * n)
##### Space complexity:
O(1)
##### Notes:
1. Use a nested loop to iterate through each cell in the board.
2. Count the number of live neighbors for each cell.
3. Update the cell based on the rules of the game.
4. Use bit manipulation to store the next state of each cell.
5. Shift the bits to get the final state of each cell.
1. Use bit manipulation to store the next state of each cell.
2. Shift the bits to get the final state of each cell.
3. Optimize the counting of live neighbors by only counting the live neighbors of the cells that are currently alive.
The tricky part of this problem is updating the board in-place. We can use bit manipulation to store the next state of each cell without using extra space.
Avoid using extra space to store the next state of each cell.
    
### >> Comparison: 371 Sum of Two Integers [Medium] *VS* 289 Game of Life [Medium]
> Similarity distance: 0.4004
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve manipulating and updating values in an array.
- Both questions require understanding and implementing specific rules or algorithms.
##### Differences

- Question 371 involves adding two integers without using the + or - operators.
- Question 289 involves simulating the Game of Life using specific rules.
- Question 371 focuses on bitwise operations, while question 289 focuses on array manipulation.
- Question 371 requires understanding and implementing the concept of two's complement.
- Question 289 requires understanding and implementing the concept of Conway's Game of Life.
##### New Insights in 289 Game of Life [Medium]

- Question 371 teaches the concept of using bitwise operations to perform arithmetic operations.
- Question 289 introduces the concept of simulating a cellular automaton using specific rules.
- Both questions provide opportunities to improve problem-solving and algorithmic thinking skills.


---
# 4. From 371 Sum of Two Integers [Medium] to 29 Divide Two Integers [Medium]
> Similarity Distance: 0.4453

### >> Reminder: 371 Sum of Two Integers [Medium]
Calculate the sum of two integers without using the + and - operators.
##### Optimal Python solution:
```python
class Solution:
    def getSum(self, a: int, b: int) -> int:
        mask = 0xffffffff
        while b & mask:
            carry = (a & b) << 1
            a = a ^ b
            b = carry & mask
        return a if b > mask else a & mask
```
The essence of this problem is to perform addition using bit manipulation without using the + and - operators.
    
### >> 29 Divide Two Integers [Medium]
Given two integers dividend and divisor, divide two integers without using multiplication, division, and mod operator. Return the quotient after dividing dividend by divisor.
##### Sample input:
10
3
##### Sample output:
3

##### Questions to ask to clarify requirements:
What should be returned if the division overflows? Can we assume the inputs are valid integers? Can we use the built-in division operator?

##### Optimal Python solution:
```python
class Solution:
    def divide(self, dividend: int, divisor: int) -> int:
        if dividend == -2**31 and divisor == -1:
            return 2**31 - 1
        sign = -1 if (dividend < 0) ^ (divisor < 0) else 1
        dividend, divisor = abs(dividend), abs(divisor)
        quotient = 0
        while dividend >= divisor:
            temp, i = divisor, 1
            while dividend >= temp:
                dividend -= temp
                quotient += i
                i <<= 1
                temp <<= 1
        return sign * quotient
```
##### Time complexity:
O(log(dividend/divisor))
##### Space complexity:
O(1)
##### Notes:
1. Use bit manipulation to perform division without using multiplication, division, and mod operator.
2. Handle edge cases such as overflow and minimum possible value of dividend.
3. Use a while loop to subtract the divisor from the dividend until the dividend is less than the divisor.
4. Keep track of the quotient by incrementing a counter variable.
5. Use bit shifting to multiply the divisor by 2 in each iteration.
1. Use bit manipulation to perform division without using multiplication, division, and mod operator.
2. Handle edge cases such as overflow and the minimum possible value of the dividend.
3. Use a while loop to subtract the divisor from the dividend until the dividend is less than the divisor.
4. Keep track of the quotient by incrementing a counter variable.
5. Use bit shifting to multiply the divisor by 2 in each iteration.
Handling edge cases such as overflow and minimum possible value of dividend.
Using multiplication, division, and mod operator.
    
### >> Comparison: 371 Sum of Two Integers [Medium] *VS* 29 Divide Two Integers [Medium]
> Similarity distance: 0.4453
##### Similarities

- Both questions are medium difficulty level.
- Both questions involve mathematical operations.
- Both questions require handling integer inputs and outputs.
- Both questions involve manipulating bits in binary representation.
##### Differences

- 371 Sum of Two Integers requires finding the sum of two integers without using the + or - operators.
- 29 Divide Two Integers requires dividing two integers without using the / or % operators.
- 371 Sum of Two Integers allows both positive and negative integers as inputs.
- 29 Divide Two Integers only allows positive integers as inputs.
- 371 Sum of Two Integers returns the sum of the two integers.
- 29 Divide Two Integers returns the quotient of the two integers.
##### New Insights in 29 Divide Two Integers [Medium]

- In 371 Sum of Two Integers, the bitwise XOR operation can be used to find the sum of two integers without carry.
- In 29 Divide Two Integers, the bitwise shift operation can be used to perform division by powers of 2.


---
# 5. From 371 Sum of Two Integers [Medium] to 50 Pow(x, n) [Medium]
> Similarity Distance: 0.4786

### >> Reminder: 371 Sum of Two Integers [Medium]
Calculate the sum of two integers without using the + and - operators.
##### Optimal Python solution:
```python
class Solution:
    def getSum(self, a: int, b: int) -> int:
        mask = 0xffffffff
        while b & mask:
            carry = (a & b) << 1
            a = a ^ b
            b = carry & mask
        return a if b > mask else a & mask
```
The essence of this problem is to perform addition using bit manipulation without using the + and - operators.
    
### >> 50 Pow(x, n) [Medium]
Implement pow(x, n), which calculates x raised to the power n (i.e., x^n).
##### Sample input:
2.00000, 10
##### Sample output:
1024.00000

##### Questions to ask to clarify requirements:

- Can x be negative?
- Can n be negative?
- Can n be zero?

##### Optimal Python solution:
```python
def myPow(x, n):
    if n == 0:
        return 1
    if n < 0:
        x = 1 / x
        n = -n
    result = 1
    while n > 0:
        if n % 2 == 1:
            result *= x
        x *= x
        n //= 2
    return result
```
##### Time complexity:
O(log n)
##### Space complexity:
O(1)
##### Notes:

- Use binary exponentiation to calculate x^n
- Handle negative values of n by taking the reciprocal of x

- Handle negative values of n by taking the reciprocal of x.
- Handle large values of n by using binary exponentiation.

- Handling negative values of n

- Calculating x^n using a loop with n iterations
    
### >> Comparison: 371 Sum of Two Integers [Medium] *VS* 50 Pow(x, n) [Medium]
> Similarity distance: 0.4786
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve mathematical operations.
- Both questions require implementing a solution using programming.
##### Differences

- Question 371 involves adding two integers, while question 50 involves calculating the power of a number.
- Question 371 requires implementing the addition operation without using the + or - operators, while question 50 requires implementing the power operation.
- Question 371 has a constraint on the input range, while question 50 does not have any specific constraints.
- Question 371 can be solved using bit manipulation, while question 50 can be solved using recursion or iteration.
##### New Insights in 50 Pow(x, n) [Medium]

- Question 371 teaches us how to perform addition using bit manipulation.
- Question 50 teaches us how to calculate the power of a number efficiently using recursion or iteration.


---
# 6. From 50 Pow(x, n) [Medium] to 372 Super Pow [Medium]
> Similarity Distance: 0.3941

### >> Reminder: 50 Pow(x, n) [Medium]
Implement pow(x, n), which calculates x raised to the power n (i.e., x^n).
##### Optimal Python solution:
```python
def myPow(x, n):
    if n == 0:
        return 1
    if n < 0:
        x = 1 / x
        n = -n
    result = 1
    while n > 0:
        if n % 2 == 1:
            result *= x
        x *= x
        n //= 2
    return result
```
Calculate x raised to the power n using binary exponentiation.
    
### >> 372 Super Pow [Medium]
Calculate a^b % 1337 where a is a positive integer and b is an extremely large positive integer given in the form of an array.
##### Sample input:
[2]
[3]
##### Sample output:
8

##### Questions to ask to clarify requirements:
What is the maximum value of b?

##### Optimal Python solution:
```python
class Solution:
    def superPow(self, a: int, b: List[int]) -> int:
        result = 1
        for digit in b:
            result = pow(result, 10, 1337) * pow(a, digit, 1337) % 1337
        return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Use modular arithmetic to calculate a^b % 1337
2. Break down b into its digits
3. Use the pow function to calculate the exponentiation
Understand modular arithmetic and the pow function.
Handling extremely large positive integers
Using the ** operator
    
### >> Comparison: 50 Pow(x, n) [Medium] *VS* 372 Super Pow [Medium]
> Similarity distance: 0.3941
##### Similarities

- Both questions involve calculating the power of a number.
- Both questions require handling large numbers and modular arithmetic.
##### Differences

- Question 50 involves calculating the power of a number with a given exponent.
- Question 372 involves calculating the power of a number with a given array of exponents.
- Question 50 uses a simple iterative approach to calculate the power.
- Question 372 requires using modular arithmetic and Euler's totient function.
- Question 50 has a time complexity of O(n), where n is the exponent.
- Question 372 has a time complexity of O(k), where k is the length of the array of exponents.
##### New Insights in 372 Super Pow [Medium]

- Question 372 introduces the concept of modular arithmetic and its application in calculating powers.
- Question 372 introduces the use of Euler's totient function to optimize the calculation of powers.

