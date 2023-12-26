
# Leetcode Intensive Tutorial Day 7 
> [Difficulty Score: 12]

> [Version: 20231226_040350]

> [Including this day, you had studied : 51 leetcode problems]


## Courses overview of the day

- 504 Base 7 [Easy]
  - 326 Power of Three [Easy]
    - 231 Power of Two [Easy]
      - 556 Next Greater Element III [Medium]
    - 412 Fizz Buzz [Easy]
    - 263 Ugly Number [Easy]
      - 264 Ugly Number II [Medium]
        - 313 Super Ugly Number [Medium]
    - 342 Power of Four [Easy]

#### Step by step

 - [1. From 504 Base 7 [Easy] to 326 Power of Three [Easy]](#1-from-504-base-7-easy-to-326-power-of-three-easy))

 - [2. From 326 Power of Three [Easy] to 231 Power of Two [Easy]](#2-from-326-power-of-three-easy-to-231-power-of-two-easy))

 - [3. From 231 Power of Two [Easy] to 556 Next Greater Element III [Medium]](#3-from-231-power-of-two-easy-to-556-next-greater-element-iii-medium))

 - [4. From 326 Power of Three [Easy] to 412 Fizz Buzz [Easy]](#4-from-326-power-of-three-easy-to-412-fizz-buzz-easy))

 - [5. From 326 Power of Three [Easy] to 263 Ugly Number [Easy]](#5-from-326-power-of-three-easy-to-263-ugly-number-easy))

 - [6. From 263 Ugly Number [Easy] to 264 Ugly Number II [Medium]](#6-from-263-ugly-number-easy-to-264-ugly-number-ii-medium))

 - [7. From 264 Ugly Number II [Medium] to 313 Super Ugly Number [Medium]](#7-from-264-ugly-number-ii-medium-to-313-super-ugly-number-medium))

 - [8. From 326 Power of Three [Easy] to 342 Power of Four [Easy]](#8-from-326-power-of-three-easy-to-342-power-of-four-easy))

    

#### Summary


- 504 Base 7 : The essence of this problem is to convert an integer to its base 7 string representation.
- 326 Power of Three : The solution checks if the input is less than or equal to 0, then divides it by 3 until it is no longer divisible by 3, and finally checks if the result is equal to 1.
- 556 Next Greater Element III : Given a positive integer, find the next greater integer with the same digits.
- 313 Super Ugly Number : The essence of this problem is to generate the nth super ugly number using a dynamic programming approach.
- 342 Power of Four : Check if an integer is a power of four
- 231 Power of Two : Check if a number is a power of two using bitwise operations.
- 263 Ugly Number : Check if a number is an ugly number by dividing it by 2, 3, and 5 until it is no longer divisible by any of them.
- 412 Fizz Buzz : Write a program that outputs the string representation of numbers from 1 to n.
- 264 Ugly Number II : Find the n-th ugly number by generating the ugly numbers in order and keeping track of the indices for multiplying by 2, 3, and 5.
> Similarity Diameter of these problems: 0.6771


---
# 1. From 504 Base 7 [Easy] to 326 Power of Three [Easy]
> Similarity Distance: 0.4489

### >> 504 Base 7 [Easy]
Given an integer, return its base 7 string representation.
##### Sample input:
100
##### Sample output:
"202"

##### Questions to ask to clarify requirements:
What should be the output if the input number is negative?

##### Optimal Python solution:
```python
def convertToBase7(num):
    if num == 0:
        return "0"
    res = ""
    is_negative = num < 0
    num = abs(num)
    while num > 0:
        res = str(num % 7) + res
        num //= 7
    if is_negative:
        res = "-" + res
    return res
```
##### Time complexity:
O(log(n))
##### Space complexity:
O(log(n))
##### Notes:
1. Check if the number is zero, return "0".
2. Initialize an empty string to store the result.
3. Check if the number is negative, set a flag.
4. Take the absolute value of the number.
5. Iterate until the number is greater than zero.
6. Append the remainder of the number divided by 7 to the result string.
7. Divide the number by 7.
8. If the number was negative, prepend a "-" to the result string.
9. Return the result string.
1. Understand the problem statement and the requirements.
2. Check if the number is zero, return "0".
3. Initialize an empty string to store the result.
4. Check if the number is negative, set a flag.
5. Take the absolute value of the number.
6. Iterate until the number is greater than zero.
7. Append the remainder of the number divided by 7 to the result string.
8. Divide the number by 7.
9. If the number was negative, prepend a "-" to the result string.
10. Return the result string.
Handling negative numbers and zero.
Using built-in functions to convert the number to base 7.
    
### >> 326 Power of Three [Easy]
Given an integer n, return true if it is a power of three. Otherwise, return false.
##### Sample input:
27
##### Sample output:
true

##### Questions to ask to clarify requirements:
Can the input be negative? Can the input be zero?

##### Optimal Python solution:
```python
def isPowerOfThree(n):
    if n <= 0:
        return False
    while n % 3 == 0:
        n /= 3
    return n == 1
```
##### Time complexity:
O(log n)
##### Space complexity:
O(1)
##### Notes:
1. Check if the input is less than or equal to 0. If so, return False.
2. Divide the input by 3 until it is no longer divisible by 3.
3. Check if the result is equal to 1. If so, return True.
Use the modulo operator to check divisibility.
Handling negative and zero inputs.
Using recursion to check all possible powers of three.
    
### >> Comparison: 504 Base 7 [Easy] *VS* 326 Power of Three [Easy]
> Similarity distance: 0.4489
##### Similarities

- Both questions are classified as 'Easy' level.
- Both questions involve mathematical operations.
- Both questions require determining a property of a given number.
##### Differences

- 504 Base 7 involves converting a decimal number to base 7, while 326 Power of Three involves determining if a number is a power of three.
- 504 Base 7 requires string manipulation, while 326 Power of Three involves mathematical calculations.
- 504 Base 7 has a time complexity of O(log n), while 326 Power of Three has a time complexity of O(1).
##### New Insights in 326 Power of Three [Easy]

- 504 Base 7 teaches the concept of converting numbers to a different base.
- 326 Power of Three introduces the concept of determining if a number is a power of a specific base.


---
# 2. From 326 Power of Three [Easy] to 231 Power of Two [Easy]
> Similarity Distance: 0.3728

### >> Reminder: 326 Power of Three [Easy]
Given an integer n, return true if it is a power of three. Otherwise, return false.
##### Optimal Python solution:
```python
def isPowerOfThree(n):
    if n <= 0:
        return False
    while n % 3 == 0:
        n /= 3
    return n == 1
```
The solution checks if the input is less than or equal to 0, then divides it by 3 until it is no longer divisible by 3, and finally checks if the result is equal to 1.
    
### >> 231 Power of Two [Easy]
Given an integer n, return true if it is a power of two. Otherwise, return false.
##### Sample input:
1
16
3
4
5
##### Sample output:
true
true
false
true
false

##### Questions to ask to clarify requirements:
What should be the output if n is 0?

##### Optimal Python solution:
```python
class Solution:
    def isPowerOfTwo(self, n: int) -> bool:
        return n > 0 and (n & (n - 1)) == 0
```
##### Time complexity:
O(1)
##### Space complexity:
O(1)
##### Notes:
A number is a power of two if it has only one bit set to 1 in its binary representation.
Use bitwise operations to check if a number is a power of two.
None
None
    
### >> Comparison: 326 Power of Three [Easy] *VS* 231 Power of Two [Easy]
> Similarity distance: 0.3728
##### Similarities

- Both questions are related to powers of numbers.
- Both questions require determining if a given number is a power of a specific number.
##### Differences

- 326 Power of Three: The given number must be a power of 3.
- 231 Power of Two: The given number must be a power of 2.
##### New Insights in 231 Power of Two [Easy]

- 326 Power of Three: The maximum value of the given number is 2^31 - 1.
- 231 Power of Two: The maximum value of the given number is 2^31 - 1.


---
# 3. From 231 Power of Two [Easy] to 556 Next Greater Element III [Medium]
> Similarity Distance: 0.4146

### >> Reminder: 231 Power of Two [Easy]
Given an integer n, return true if it is a power of two. Otherwise, return false.
##### Optimal Python solution:
```python
class Solution:
    def isPowerOfTwo(self, n: int) -> bool:
        return n > 0 and (n & (n - 1)) == 0
```
Check if a number is a power of two using bitwise operations.
    
### >> 556 Next Greater Element III [Medium]
Given a positive integer n, find the smallest integer which has exactly the same digits existing in the integer n and is greater in value than n. If no such positive integer exists, return -1.
##### Sample input:
12
##### Sample output:
21

##### Questions to ask to clarify requirements:

- Can the input be a negative integer?
- What is the maximum value of the input?
- What is the maximum number of digits in the input?

##### Optimal Python solution:
```python

- def nextGreaterElement(self, n: int) -> int:
-     digits = list(str(n))
-     i = len(digits) - 2
-     while i >= 0 and digits[i] >= digits[i+1]:
-         i -= 1
-     if i < 0:
-         return -1
-     j = len(digits) - 1
-     while digits[j] <= digits[i]:
-         j -= 1
-     digits[i], digits[j] = digits[j], digits[i]
-     digits[i+1:] = digits[i+1:][::-1]
-     res = int(''.join(digits))
-     return res if res <= 2**31 - 1 else -1
```
##### Time complexity:
O(d)
##### Space complexity:
O(d)
##### Notes:

- Find the next greater integer with the same digits
- Return -1 if no such integer exists

- Use integer manipulation techniques
- Find patterns in numbers
- Optimize the solution to handle large inputs

- Finding the next greater integer
- Handling edge cases

- Brute force checking all possible integers
- Sorting the digits and checking all possible combinations
    
### >> Comparison: 231 Power of Two [Easy] *VS* 556 Next Greater Element III [Medium]
> Similarity distance: 0.4146
##### Similarities

- Both questions involve manipulating numbers.
- Both questions require some form of iteration or calculation.
- Both questions have a specific input and output format.
##### Differences

- 231 Power of Two: Determines if a given number is a power of two.
- 556 Next Greater Element III: Finds the next greater permutation of a given number.
##### New Insights in 556 Next Greater Element III [Medium]

- 231 Power of Two: The number must have only one bit set to 1 in its binary representation.
- 556 Next Greater Element III: The next greater permutation can be found by rearranging the digits of the given number.


---
# 4. From 326 Power of Three [Easy] to 412 Fizz Buzz [Easy]
> Similarity Distance: 0.3920

### >> Reminder: 326 Power of Three [Easy]
Given an integer n, return true if it is a power of three. Otherwise, return false.
##### Optimal Python solution:
```python
def isPowerOfThree(n):
    if n <= 0:
        return False
    while n % 3 == 0:
        n /= 3
    return n == 1
```
The solution checks if the input is less than or equal to 0, then divides it by 3 until it is no longer divisible by 3, and finally checks if the result is equal to 1.
    
### >> 412 Fizz Buzz [Easy]
Write a program that outputs the string representation of numbers from 1 to n.
##### Sample input:

- 15
##### Sample output:
["1","2","Fizz","4","Buzz","Fizz","7","8","Fizz","Buzz","11","Fizz","13","14","FizzBuzz"]

##### Questions to ask to clarify requirements:

- What is the maximum value of n?

##### Optimal Python solution:
```python

- class Solution:
-     def fizzBuzz(self, n: int) -> List[str]:
-         result = []
-         for i in range(1, n + 1):
-             if i % 3 == 0 and i % 5 == 0:
-                 result.append("FizzBuzz")
-             elif i % 3 == 0:
-                 result.append("Fizz")
-             elif i % 5 == 0:
-                 result.append("Buzz")
-             else:
-                 result.append(str(i))
-         return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Use modulo operator to check if a number is divisible by 3 or 5
- Use if-else statements to determine the string representation of a number

- Use the modulo operator to check if a number is divisible by another number.
- Use if-else statements to determine the string representation of a number.

- Handling the case where n is 0

- Using a loop to iterate from 1 to n
- Using a linear search to check if a number is divisible by 3 or 5
    
### >> Comparison: 326 Power of Three [Easy] *VS* 412 Fizz Buzz [Easy]
> Similarity distance: 0.3920
##### Similarities

- Both questions are classified as 'Easy' level.
- Both questions involve mathematical calculations.
- Both questions require iterating over a range of numbers.
##### Differences

- 326 Power of Three: Checks if a given number is a power of three.
- 412 Fizz Buzz: Generates a list of strings based on given conditions.
- 326 Power of Three: Uses logarithmic calculation to determine if a number is a power of three.
- 412 Fizz Buzz: Uses modulo operation to determine if a number is divisible by 3 or 5.
##### New Insights in 412 Fizz Buzz [Easy]

- 326 Power of Three: Demonstrates the use of logarithmic calculation to solve a problem efficiently.
- 412 Fizz Buzz: Introduces the concept of generating a list of strings based on certain conditions.


---
# 5. From 326 Power of Three [Easy] to 263 Ugly Number [Easy]
> Similarity Distance: 0.4458

### >> Reminder: 326 Power of Three [Easy]
Given an integer n, return true if it is a power of three. Otherwise, return false.
##### Optimal Python solution:
```python
def isPowerOfThree(n):
    if n <= 0:
        return False
    while n % 3 == 0:
        n /= 3
    return n == 1
```
The solution checks if the input is less than or equal to 0, then divides it by 3 until it is no longer divisible by 3, and finally checks if the result is equal to 1.
    
### >> 263 Ugly Number [Easy]
Write a program to check whether a given number is an ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, and/or 5.
##### Sample input:
6
8
14
##### Sample output:
true
true
false

##### Questions to ask to clarify requirements:
What is the range of input numbers? Can the input be negative?

##### Optimal Python solution:
```python
class Solution:
    def isUgly(self, num: int) -> bool:
        if num <= 0:
            return False
        while num % 2 == 0:
            num //= 2
        while num % 3 == 0:
            num //= 3
        while num % 5 == 0:
            num //= 5
        return num == 1
```
##### Time complexity:
O(log n)
##### Space complexity:
O(1)
##### Notes:
Ugly numbers are positive numbers whose prime factors only include 2, 3, and/or 5.

To check if a number is ugly, divide it by 2, 3, and 5 until it is no longer divisible by any of them.

If the resulting number is 1, then the original number is ugly.
Use the modulo operator (%) to check if a number is divisible by another number.
Handling negative numbers
Using recursion
    
### >> Comparison: 326 Power of Three [Easy] *VS* 263 Ugly Number [Easy]
> Similarity distance: 0.4458
##### Similarities

- Both questions are classified as 'Easy' level.
- Both questions involve numbers and require some mathematical calculations.
- Both questions require determining if a given number meets certain criteria.
##### Differences

- 326 Power of Three: The question asks whether a given number is a power of three.
- 263 Ugly Number: The question asks whether a given number is an ugly number, which is a positive number whose prime factors only include 2, 3, and 5.
##### New Insights in 263 Ugly Number [Easy]

- 326 Power of Three: The insight is to use logarithms to check if the number is a power of three.
- 263 Ugly Number: The insight is to divide the number by 2, 3, and 5 repeatedly until it becomes 1 or cannot be divided anymore.


---
# 6. From 263 Ugly Number [Easy] to 264 Ugly Number II [Medium]
> Similarity Distance: 0.3847

### >> Reminder: 263 Ugly Number [Easy]
Write a program to check whether a given number is an ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, and/or 5.
##### Optimal Python solution:
```python
class Solution:
    def isUgly(self, num: int) -> bool:
        if num <= 0:
            return False
        while num % 2 == 0:
            num //= 2
        while num % 3 == 0:
            num //= 3
        while num % 5 == 0:
            num //= 5
        return num == 1
```
Check if a number is an ugly number by dividing it by 2, 3, and 5 until it is no longer divisible by any of them.
    
### >> 264 Ugly Number II [Medium]
Write a program to find the n-th ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, and/or 5.
##### Sample input:
10
##### Sample output:
12

##### Questions to ask to clarify requirements:
What is the range of n? Can n be negative?

##### Optimal Python solution:
```python
class Solution:
    def nthUglyNumber(self, n: int) -> int:
        ugly = [1]
        i2 = i3 = i5 = 0
        while len(ugly) < n:
            next_ugly = min(ugly[i2] * 2, ugly[i3] * 3, ugly[i5] * 5)
            ugly.append(next_ugly)
            if next_ugly == ugly[i2] * 2:
                i2 += 1
            if next_ugly == ugly[i3] * 3:
                i3 += 1
            if next_ugly == ugly[i5] * 5:
                i5 += 1
        return ugly[-1]
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
Ugly numbers are positive numbers whose prime factors only include 2, 3, and/or 5.

To find the n-th ugly number, generate the ugly numbers in order and keep track of the indices for multiplying by 2, 3, and 5.

The next ugly number is the minimum of the current ugly numbers multiplied by 2, 3, and 5.
Use dynamic programming to generate the ugly numbers in order.
None
None
    
### >> Comparison: 263 Ugly Number [Easy] *VS* 264 Ugly Number II [Medium]
> Similarity distance: 0.3847
##### Similarities

- Both questions are related to finding ugly numbers.
- Both questions require determining whether a given number is an ugly number.
##### Differences

- Ugly Number: It asks to determine whether a given number is an ugly number.
- Ugly Number II: It asks to find the n-th ugly number.
- Ugly Number II requires finding the n-th ugly number, while Ugly Number only requires determining whether a given number is an ugly number.
##### New Insights in 264 Ugly Number II [Medium]

- Ugly Number: The prime factors of an ugly number are limited to 2, 3, and 5.
- Ugly Number II: The n-th ugly number can be generated by multiplying the previous ugly numbers by 2, 3, or 5.


---
# 7. From 264 Ugly Number II [Medium] to 313 Super Ugly Number [Medium]
> Similarity Distance: 0.4887

### >> Reminder: 264 Ugly Number II [Medium]
Write a program to find the n-th ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, and/or 5.
##### Optimal Python solution:
```python
class Solution:
    def nthUglyNumber(self, n: int) -> int:
        ugly = [1]
        i2 = i3 = i5 = 0
        while len(ugly) < n:
            next_ugly = min(ugly[i2] * 2, ugly[i3] * 3, ugly[i5] * 5)
            ugly.append(next_ugly)
            if next_ugly == ugly[i2] * 2:
                i2 += 1
            if next_ugly == ugly[i3] * 3:
                i3 += 1
            if next_ugly == ugly[i5] * 5:
                i5 += 1
        return ugly[-1]
```
Find the n-th ugly number by generating the ugly numbers in order and keeping track of the indices for multiplying by 2, 3, and 5.
    
### >> 313 Super Ugly Number [Medium]
Write a program to find the nth super ugly number.

Super ugly numbers are positive numbers whose all prime factors are in the given prime list primes of size k.

Example:

Input: n = 12, primes = [2,7,13,19]
Output: 32 
Explanation: [1,2,4,7,8,13,14,16,19,26,28,32] is the sequence of the first 12
             super ugly numbers given primes = [2,7,13,19] of size 4.
##### Sample input:
12
[2,7,13,19]
##### Sample output:
32

##### Questions to ask to clarify requirements:
What is the range of n? What is the range of primes? Can primes contain duplicates?

##### Optimal Python solution:
```python
class Solution:
    def nthSuperUglyNumber(self, n: int, primes: List[int]) -> int:
        ugly = [1]
        pointers = [0] * len(primes)
        while len(ugly) < n:
            next_ugly = min(ugly[pointers[i]] * primes[i] for i in range(len(primes)))
            ugly.append(next_ugly)
            for i in range(len(primes)):
                if ugly[pointers[i]] * primes[i] == next_ugly:
                    pointers[i] += 1
        return ugly[-1]
```
##### Time complexity:
O(nk)
##### Space complexity:
O(n+k)
##### Notes:
1. Super ugly numbers have all prime factors in the given prime list.
2. Use a list of pointers to keep track of the current index for each prime.
3. Generate the next super ugly number by multiplying the current ugly number at each pointer with its corresponding prime.
4. Append the minimum of the generated numbers to the ugly list.
5. Update the pointers for the primes whose multiples were used to generate the next ugly number.
6. Repeat steps 3-5 until the ugly list has n numbers.
1. Use a list of pointers to keep track of the current index for each prime.
2. Generate the next super ugly number by multiplying the current ugly number at each pointer with its corresponding prime.
3. Append the minimum of the generated numbers to the ugly list.
4. Update the pointers for the primes whose multiples were used to generate the next ugly number.
5. Repeat steps 2-4 until the ugly list has n numbers.
None
None
    
### >> Comparison: 264 Ugly Number II [Medium] *VS* 313 Super Ugly Number [Medium]
> Similarity distance: 0.4887
##### Similarities

- Both questions are related to finding ugly numbers.
- Both questions require finding the nth ugly number.
- Both questions have a similar approach to solving the problem.
##### Differences

- 264 Ugly Number II only considers prime factors 2, 3, and 5.
- 313 Super Ugly Number allows any given set of prime factors.
- 313 Super Ugly Number has a more generalized solution.
##### New Insights in 313 Super Ugly Number [Medium]

- The new insight in both questions is the concept of ugly numbers.
- Ugly numbers are positive numbers whose prime factors are limited to a given set.
- Both questions provide an opportunity to learn about dynamic programming.


---
# 8. From 326 Power of Three [Easy] to 342 Power of Four [Easy]
> Similarity Distance: 0.4728

### >> Reminder: 326 Power of Three [Easy]
Given an integer n, return true if it is a power of three. Otherwise, return false.
##### Optimal Python solution:
```python
def isPowerOfThree(n):
    if n <= 0:
        return False
    while n % 3 == 0:
        n /= 3
    return n == 1
```
The solution checks if the input is less than or equal to 0, then divides it by 3 until it is no longer divisible by 3, and finally checks if the result is equal to 1.
    
### >> 342 Power of Four [Easy]
Given an integer n, return true if it is a power of four. Otherwise, return false. An integer n is a power of four, if there exists an integer x such that n == 4^x.
##### Sample input:
16
##### Sample output:
true

##### Questions to ask to clarify requirements:

- Can the input be negative?
- Can the input be zero?

##### Optimal Python solution:
```python
class Solution:
    def isPowerOfFour(self, n: int) -> bool:
        if n <= 0:
            return False
        while n % 4 == 0:
            n //= 4
        return n == 1
```
##### Time complexity:
O(log n)
##### Space complexity:
O(1)
##### Notes:

- Check if n is positive
- Divide n by 4 until it is no longer divisible by 4
- Check if n is equal to 1

- Use the modulo operator to check if a number is divisible by 4
- Use integer division to divide a number by 4

- Handling negative numbers
- Handling zero

- Using recursion to check if n is a power of four
    
### >> Comparison: 326 Power of Three [Easy] *VS* 342 Power of Four [Easy]
> Similarity distance: 0.4728
##### Similarities

- Both questions are about determining if a given number is a power of a specific base.
- Both questions have an easy difficulty level.
##### Differences

- 326 Power of Three is about determining if a given number is a power of three.
- 342 Power of Four is about determining if a given number is a power of four.
- 326 Power of Three has a base of three, while 342 Power of Four has a base of four.
##### New Insights in 342 Power of Four [Easy]

- The new insight we can learn from these questions is how to efficiently check if a number is a power of a specific base.
- We can use logarithms to solve these questions by checking if the logarithm of the number to the base is an integer.

