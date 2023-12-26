
# Leetcode Intensive Tutorial Day 30 
> [Difficulty Score: 18]

> [Version: 20231225_200427]

## Courses overview of the day

- 125 Valid Palindrome [Easy]
  - 8 String to Integer (atoi) [Medium]
    - 415 Add Strings [Easy]
      - 67 Add Binary [Easy]
        - 171 Excel Sheet Column Number [Easy]
          - 168 Excel Sheet Column Title [Easy]
        - 65 Valid Number [Hard]
      - 233 Number of Digit One [Hard]
  - 9 Palindrome Number [Easy]
    - 393 UTF-8 Validation [Medium]

#### Steps by steps

 - [1. From 125 Valid Palindrome [Easy] to 8 String to Integer (atoi) [Medium]](#1-from-125-valid-palindrome-easy-to-8-string-to-integer-atoi-medium)

 - [2. From 8 String to Integer (atoi) [Medium] to 415 Add Strings [Easy]](#2-from-8-string-to-integer-atoi-medium-to-415-add-strings-easy)

 - [3. From 415 Add Strings [Easy] to 67 Add Binary [Easy]](#3-from-415-add-strings-easy-to-67-add-binary-easy)

 - [4. From 67 Add Binary [Easy] to 171 Excel Sheet Column Number [Easy]](#4-from-67-add-binary-easy-to-171-excel-sheet-column-number-easy)

 - [5. From 171 Excel Sheet Column Number [Easy] to 168 Excel Sheet Column Title [Easy]](#5-from-171-excel-sheet-column-number-easy-to-168-excel-sheet-column-title-easy)

 - [6. From 67 Add Binary [Easy] to 65 Valid Number [Hard]](#6-from-67-add-binary-easy-to-65-valid-number-hard)

 - [7. From 415 Add Strings [Easy] to 233 Number of Digit One [Hard]](#7-from-415-add-strings-easy-to-233-number-of-digit-one-hard)

 - [8. From 125 Valid Palindrome [Easy] to 9 Palindrome Number [Easy]](#8-from-125-valid-palindrome-easy-to-9-palindrome-number-easy)

 - [9. From 9 Palindrome Number [Easy] to 393 UTF-8 Validation [Medium]](#9-from-9-palindrome-number-easy-to-393-utf-8-validation-medium)

#### Summary


- 125 Valid Palindrome : Check if a string is a palindrome by ignoring non-alphanumeric characters and cases.
- 233 Number of Digit One : Count the number of '1' digits in all numbers from 1 to n.
- 9 Palindrome Number : Check if an integer is a palindrome by comparing it with its reverse.
- 8 String to Integer (atoi) : Convert a string to an integer and handle edge cases.
- 171 Excel Sheet Column Number : Convert characters to numbers and sum them up.
- 168 Excel Sheet Column Title : Given a positive integer, convert it to its corresponding column title in an Excel sheet.
- 65 Valid Number : The essence of this problem is to determine if a given string can be interpreted as a decimal number.
- 67 Add Binary : Adding binary strings by converting them to integers and then back to binary.
- 393 UTF-8 Validation : Validating UTF-8 encoding using bit manipulation.
- 415 Add Strings : Perform addition digit by digit and handle the carry-over correctly.
> Similarity Diameter of these problems: 0.6479


---
# 1. From 125 Valid Palindrome [Easy] to 8 String to Integer (atoi) [Medium]
> Similarity Distance: 0.4522

### >> 125 Valid Palindrome [Easy]
Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.
##### Sample input:
"A man, a plan, a canal: Panama"
##### Sample output:
true

##### Questions to ask to clarify requirements:
Should the solution consider only alphanumeric characters? Should it be case-insensitive?

##### Optimal Python solution:
```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = ''.join(e for e in s if e.isalnum()).lower()
        return s == s[::-1]
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Remove non-alphanumeric characters and convert to lowercase
2. Check if the string is equal to its reverse
Use built-in string methods to remove non-alphanumeric characters and convert to lowercase.
Handling non-alphanumeric characters and case-insensitivity
Using extra space
    
### >> 8 String to Integer (atoi) [Medium]
Implement atoi which converts a string to an integer.
##### Sample input:
"42"
"   -42"
"4193 with words"
"words and 987"
"-91283472332"
##### Sample output:
42
-42
4193
0
-2147483648

##### Questions to ask to clarify requirements:
What should be the output if the string does not represent a valid integer?

##### Optimal Python solution:
```python
class Solution:
    def myAtoi(self, s: str) -> int:
        s = s.strip()
        if not s:
            return 0
        sign = -1 if s[0] == '-' else 1
        if s[0] in ['-', '+']:
            s = s[1:]
        result = 0
        for char in s:
            if not char.isdigit():
                break
            result = result * 10 + int(char)
        result = sign * result
        result = max(min(result, 2**31 - 1), -2**31)
        return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Convert the string to an integer.
2. Handle leading whitespace characters.
3. Handle the sign of the integer.
4. Handle invalid characters in the string.
5. Handle integer overflow.
Use the ord() function to get the ASCII value of a character.
Handling leading whitespace characters and invalid characters in the string.
Using built-in functions like int() or str.isdigit().
    
### >> Comparison: 125 Valid Palindrome [Easy] *VS* 8 String to Integer (atoi) [Medium]
> Similarity distance: 0.4522
##### Similarities

- Both questions involve string manipulation.
- Both questions require checking for certain conditions in the given string.
##### Differences

- Question 125 is about checking if a string is a valid palindrome, while question 8 is about converting a string to an integer.
- Question 125 requires ignoring non-alphanumeric characters and considering case-insensitivity, while question 8 requires handling leading whitespace and sign characters.
- Question 125 can be solved by comparing characters from both ends of the string, while question 8 requires parsing and converting the string to an integer.
- Question 125 has a time complexity of O(n), where n is the length of the string, while question 8 has a time complexity of O(n), where n is the number of characters that can be converted to an integer.
##### New Insights in 8 String to Integer (atoi) [Medium]

- Question 125: To check if a string is a valid palindrome, we can use two pointers starting from both ends of the string and compare characters while ignoring non-alphanumeric characters and considering case-insensitivity.
- Question 8: To convert a string to an integer, we can iterate through the string, handling leading whitespace, sign characters, and converting the remaining characters to an integer using the ASCII values.


---
# 2. From 8 String to Integer (atoi) [Medium] to 415 Add Strings [Easy]
> Similarity Distance: 0.4106

### >> Reminder: 8 String to Integer (atoi) [Medium]
Implement atoi which converts a string to an integer.
##### Optimal Python solution:
```python
class Solution:
    def myAtoi(self, s: str) -> int:
        s = s.strip()
        if not s:
            return 0
        sign = -1 if s[0] == '-' else 1
        if s[0] in ['-', '+']:
            s = s[1:]
        result = 0
        for char in s:
            if not char.isdigit():
                break
            result = result * 10 + int(char)
        result = sign * result
        result = max(min(result, 2**31 - 1), -2**31)
        return result
```
Convert a string to an integer and handle edge cases.
    
### >> 415 Add Strings [Easy]
Given two non-negative integers, num1 and num2 represented as string, return the sum of num1 and num2.
##### Sample input:
"11"
"123"
##### Sample output:
"134"

##### Questions to ask to clarify requirements:
Are the input strings always non-negative integers? Can the input strings be empty?

##### Optimal Python solution:
```python
def addStrings(num1: str, num2: str) -> str:
    res = []
    carry = 0
    p1, p2 = len(num1) - 1, len(num2) - 1
    while p1 >= 0 or p2 >= 0:
        x1 = ord(num1[p1]) - ord('0') if p1 >= 0 else 0
        x2 = ord(num2[p2]) - ord('0') if p2 >= 0 else 0
        value = (x1 + x2 + carry) % 10
        carry = (x1 + x2 + carry) // 10
        res.append(str(value))
        p1 -= 1
        p2 -= 1
    if carry:
        res.append(str(carry))
    return ''.join(res[::-1])
```
##### Time complexity:
O(max(n, m))
##### Space complexity:
O(max(n, m))
##### Notes:
1. Convert the strings to integers and perform addition digit by digit.
2. Use a carry variable to keep track of the carry-over.
3. Append the result to a list and convert it back to a string.
Use ord() to convert characters to integers, and chr() to convert integers to characters.
Handling the carry-over correctly.
Converting the strings to integers directly without considering the carry-over.
    
### >> Comparison: 8 String to Integer (atoi) [Medium] *VS* 415 Add Strings [Easy]
> Similarity distance: 0.4106
##### Similarities

- Both questions involve manipulating strings.
- Both questions require converting strings to integers.
- Both questions have a specific format for the input strings.
##### Differences

- String to Integer (atoi) involves converting a string to an integer based on a set of rules, while Add Strings involves adding two strings as if they were numbers.
- String to Integer (atoi) has more complex rules for converting the string to an integer, while Add Strings simply requires adding the two strings digit by digit.
- String to Integer (atoi) has a wider range of possible inputs, including negative numbers and leading/trailing whitespace, while Add Strings assumes the input strings are non-negative integers.
- String to Integer (atoi) returns an integer as the result, while Add Strings returns a string as the result.
##### New Insights in 415 Add Strings [Easy]

- String to Integer (atoi) requires handling edge cases such as leading/trailing whitespace, sign symbols, and overflow/underflow of the resulting integer.
- Add Strings requires handling the carry-over when adding digits, and converting the resulting sum to a string.


---
# 3. From 415 Add Strings [Easy] to 67 Add Binary [Easy]
> Similarity Distance: 0.3088

### >> Reminder: 415 Add Strings [Easy]
Given two non-negative integers, num1 and num2 represented as string, return the sum of num1 and num2.
##### Optimal Python solution:
```python
def addStrings(num1: str, num2: str) -> str:
    res = []
    carry = 0
    p1, p2 = len(num1) - 1, len(num2) - 1
    while p1 >= 0 or p2 >= 0:
        x1 = ord(num1[p1]) - ord('0') if p1 >= 0 else 0
        x2 = ord(num2[p2]) - ord('0') if p2 >= 0 else 0
        value = (x1 + x2 + carry) % 10
        carry = (x1 + x2 + carry) // 10
        res.append(str(value))
        p1 -= 1
        p2 -= 1
    if carry:
        res.append(str(carry))
    return ''.join(res[::-1])
```
Perform addition digit by digit and handle the carry-over correctly.
    
### >> 67 Add Binary [Easy]
Given two binary strings, return their sum (also a binary string).
##### Sample input:
"11", "1"
##### Sample output:
"100"

##### Questions to ask to clarify requirements:
Are the input strings always valid binary strings? Can the input strings be empty?

##### Optimal Python solution:
```python
def addBinary(a: str, b: str) -> str:
    return bin(int(a, 2) + int(b, 2))[2:]
```
##### Time complexity:
O(max(n, m))
##### Space complexity:
O(max(n, m))
##### Notes:
1. Convert the binary strings to integers using int(a, 2) and int(b, 2).
2. Add the integers.
3. Convert the sum back to a binary string using bin(sum)[2:].
Use the built-in functions int(a, 2) and bin(sum)[2:] to convert between binary strings and integers.
Handling the carry when adding the binary digits.
Converting the binary strings to decimal and then adding them.
    
### >> Comparison: 415 Add Strings [Easy] *VS* 67 Add Binary [Easy]
> Similarity distance: 0.3088
##### Similarities

- Both questions involve adding two strings
- Both questions have a binary addition operation
##### Differences

- 415 Add Strings deals with adding decimal numbers represented as strings
- 67 Add Binary deals with adding binary numbers represented as strings
- 415 Add Strings allows for numbers of any length
- 67 Add Binary assumes the input strings are of equal length
- 415 Add Strings requires carrying over when the sum of digits exceeds 9
- 67 Add Binary requires carrying over when the sum of digits exceeds 1
##### New Insights in 67 Add Binary [Easy]

- 415 Add Strings can handle numbers of any length, making it more versatile
- 67 Add Binary is limited to binary numbers of equal length
- Both questions require carrying over when the sum of digits exceeds a certain value


---
# 4. From 67 Add Binary [Easy] to 171 Excel Sheet Column Number [Easy]
> Similarity Distance: 0.3754

### >> Reminder: 67 Add Binary [Easy]
Given two binary strings, return their sum (also a binary string).
##### Optimal Python solution:
```python
def addBinary(a: str, b: str) -> str:
    return bin(int(a, 2) + int(b, 2))[2:]
```
Adding binary strings by converting them to integers and then back to binary.
    
### >> 171 Excel Sheet Column Number [Easy]
Given a column title as appear in an Excel sheet, return its corresponding column number.
##### Sample input:
"A"
"AB"
"ZY"
"FXSHRXW"
##### Sample output:
1
28
701
2147483647

##### Questions to ask to clarify requirements:
What is the maximum length of the column title? Can the column title be empty?

##### Optimal Python solution:
```python
class Solution:
    def titleToNumber(self, columnTitle: str) -> int:
        result = 0
        for i in range(len(columnTitle)):
            result = result * 26 + ord(columnTitle[i]) - ord('A') + 1
        return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
Convert each character to its corresponding value and sum them up.
Use the ord() function to get the ASCII value of a character.
None
None
    
### >> Comparison: 67 Add Binary [Easy] *VS* 171 Excel Sheet Column Number [Easy]
> Similarity distance: 0.3754
##### Similarities

- Both questions are classified as 'Easy' level.
- Both questions involve string manipulation.
- Both questions require converting between different representations of numbers.
##### Differences

- Question 67 involves adding two binary numbers, while question 171 involves converting an Excel column title to a corresponding number.
- Question 67 deals with binary representation, while question 171 deals with alphabetic representation.
- Question 67 requires handling carry-over during addition, while question 171 requires multiplying the column letters by powers of 26.
##### New Insights in 171 Excel Sheet Column Number [Easy]

- Question 67 teaches us how to perform addition on binary numbers.
- Question 171 teaches us how to convert Excel column titles to numbers.
- Both questions provide practice in manipulating strings and converting between different number representations.


---
# 5. From 171 Excel Sheet Column Number [Easy] to 168 Excel Sheet Column Title [Easy]
> Similarity Distance: 0.4608

### >> Reminder: 171 Excel Sheet Column Number [Easy]
Given a column title as appear in an Excel sheet, return its corresponding column number.
##### Optimal Python solution:
```python
class Solution:
    def titleToNumber(self, columnTitle: str) -> int:
        result = 0
        for i in range(len(columnTitle)):
            result = result * 26 + ord(columnTitle[i]) - ord('A') + 1
        return result
```
Convert characters to numbers and sum them up.
    
### >> 168 Excel Sheet Column Title [Easy]
Given a positive integer, return its corresponding column title as appear in an Excel sheet.

For example:

    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB
    ...

Example 1:

Input: 1
Output: "A"

Example 2:

Input: 28
Output: "AB"

Example 3:

Input: 701
Output: "ZY"
##### Sample input:
1
##### Sample output:
"A"

##### Questions to ask to clarify requirements:
What is the maximum value of n? Can n be zero or negative?

##### Optimal Python solution:
```python
def convertToTitle(n):
    result = ''
    while n > 0:
        n -= 1
        result = chr(n % 26 + ord('A')) + result
        n //= 26
    return result
```
##### Time complexity:
O(log(n))
##### Space complexity:
O(log(n))
##### Notes:
1. Convert the number to a string representation of its corresponding column title.
2. Use the ASCII values of characters to determine the column title.
1. Remember to subtract 1 from the number before converting the remainder to a character.
2. Be careful with the indices, as they are not zero-based.
None
None
    
### >> Comparison: 171 Excel Sheet Column Number [Easy] *VS* 168 Excel Sheet Column Title [Easy]
> Similarity distance: 0.4608
##### Similarities

- Both questions are related to Excel sheet column representation.
- Both questions are categorized as 'Easy' level difficulty.
##### Differences

- 171 Excel Sheet Column Number: Given a column title as appear in an Excel sheet, return its corresponding column number.
- 168 Excel Sheet Column Title: Given a positive integer, return its corresponding column title as appear in an Excel sheet.
##### New Insights in 168 Excel Sheet Column Title [Easy]

- 171 Excel Sheet Column Number: The column number is calculated by multiplying the corresponding digit value with 26 raised to the power of its position.
- 168 Excel Sheet Column Title: The column title is constructed by repeatedly dividing the number by 26 and mapping the remainder to the corresponding character.


---
# 6. From 67 Add Binary [Easy] to 65 Valid Number [Hard]
> Similarity Distance: 0.5202

### >> Reminder: 67 Add Binary [Easy]
Given two binary strings, return their sum (also a binary string).
##### Optimal Python solution:
```python
def addBinary(a: str, b: str) -> str:
    return bin(int(a, 2) + int(b, 2))[2:]
```
Adding binary strings by converting them to integers and then back to binary.
    
### >> 65 Valid Number [Hard]
Validate if a given string can be interpreted as a decimal number.
##### Sample input:
"0"
##### Sample output:
true

##### Questions to ask to clarify requirements:
What are the valid formats for a decimal number? Can the number have leading or trailing spaces? Can it have a sign (+/-)? Can it have exponential notation?

##### Optimal Python solution:
```python
class Solution:
    def isNumber(self, s: str) -> bool:
        try:
            float(s)
            return True
        except:
            return False
```
##### Time complexity:
O(1)
##### Space complexity:
O(1)
##### Notes:
Use the built-in float() function to parse the string as a float. If an exception is raised, return False.
Make sure to handle all the edge cases correctly, such as leading or trailing spaces, signs, and exponential notation.
Handling all the edge cases correctly.
Using regular expressions or manual parsing.
    
### >> Comparison: 67 Add Binary [Easy] *VS* 65 Valid Number [Hard]
> Similarity distance: 0.5202
##### Similarities

- Both questions involve manipulating and comparing binary numbers.
- Both questions require string manipulation and handling edge cases.
##### Differences

- Question 67 (Add Binary) focuses on adding two binary numbers and returning the sum as a binary string.
- Question 65 (Valid Number) focuses on determining if a given string represents a valid number according to the specified rules.
- Question 67 has an easier difficulty level (Easy) compared to Question 65 (Hard).
- Question 67 has a simpler problem statement and solution approach compared to Question 65.
##### New Insights in 65 Valid Number [Hard]

- Question 67 teaches us how to perform addition of binary numbers using string manipulation and carry handling.
- Question 65 teaches us how to validate a string representation of a number by considering various rules and edge cases.


---
# 7. From 415 Add Strings [Easy] to 233 Number of Digit One [Hard]
> Similarity Distance: 0.3605

### >> Reminder: 415 Add Strings [Easy]
Given two non-negative integers, num1 and num2 represented as string, return the sum of num1 and num2.
##### Optimal Python solution:
```python
def addStrings(num1: str, num2: str) -> str:
    res = []
    carry = 0
    p1, p2 = len(num1) - 1, len(num2) - 1
    while p1 >= 0 or p2 >= 0:
        x1 = ord(num1[p1]) - ord('0') if p1 >= 0 else 0
        x2 = ord(num2[p2]) - ord('0') if p2 >= 0 else 0
        value = (x1 + x2 + carry) % 10
        carry = (x1 + x2 + carry) // 10
        res.append(str(value))
        p1 -= 1
        p2 -= 1
    if carry:
        res.append(str(carry))
    return ''.join(res[::-1])
```
Perform addition digit by digit and handle the carry-over correctly.
    
### >> 233 Number of Digit One [Hard]
Given an integer n, count the total number of digit 1 appearing in all non-negative integers less than or equal to n.
##### Sample input:
13

##### Sample output:
6


##### Questions to ask to clarify requirements:
What is the maximum value of n? Can n be negative?

##### Optimal Python solution:
```python
class Solution:
    def countDigitOne(self, n: int) -> int:
        count = 0
        for i in range(1, n+1):
            count += str(i).count('1')
        return count

```
##### Time complexity:
O(n log n)
##### Space complexity:
O(1)
##### Notes:
1. Iterate through all numbers from 1 to n
2. Convert each number to a string and count the number of '1' digits
3. Return the total count
Use the count() method to count the number of occurrences of a specific character in a string.
The time complexity of the optimal solution is O(n log n), which is not efficient for large values of n.
Avoid brute force solution that counts the number of '1' digits for each number individually.
    
### >> Comparison: 415 Add Strings [Easy] *VS* 233 Number of Digit One [Hard]
> Similarity distance: 0.3605
##### Similarities

- Both questions involve manipulating strings and performing arithmetic operations.
- Both questions require counting or calculating the occurrence of certain digits.
- Both questions have a time complexity of O(n), where n is the length of the input strings or numbers.
##### Differences

- 415 Add Strings is an easy level question, while 233 Number of Digit One is a hard level question.
- 415 Add Strings involves adding two non-negative integers represented as strings, while 233 Number of Digit One involves counting the number of digit 1's in a range of numbers.
- 415 Add Strings requires converting the strings to integers and performing addition, while 233 Number of Digit One requires counting the occurrence of digit 1 in each number within a range.
- 415 Add Strings has a straightforward solution using a carry variable and string concatenation, while 233 Number of Digit One requires a more complex mathematical approach using digit positions and counting formulas.
##### New Insights in 233 Number of Digit One [Hard]

- From 415 Add Strings, we can learn how to convert strings to integers and perform arithmetic operations on them.
- From 233 Number of Digit One, we can learn how to count the occurrence of a specific digit in a range of numbers using mathematical formulas.


---
# 8. From 125 Valid Palindrome [Easy] to 9 Palindrome Number [Easy]
> Similarity Distance: 0.4553

### >> Reminder: 125 Valid Palindrome [Easy]
Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.
##### Optimal Python solution:
```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = ''.join(e for e in s if e.isalnum()).lower()
        return s == s[::-1]
```
Check if a string is a palindrome by ignoring non-alphanumeric characters and cases.
    
### >> 9 Palindrome Number [Easy]
Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward.
##### Sample input:
121
##### Sample output:
true

##### Questions to ask to clarify requirements:
Can the input be negative?

##### Optimal Python solution:
```python
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x < 0:
            return False
        else:
            return str(x) == str(x)[::-1]
```
##### Time complexity:
O(log n)
##### Space complexity:
O(1)
##### Notes:
1. Negative numbers are not palindromes
2. Convert the integer to a string and compare it with its reverse
3. Time complexity: O(log n)
Use the slicing operator [::-1] to reverse a string.
Negative numbers are not palindromes
Converting the integer to a string and comparing it with its reverse
    
### >> Comparison: 125 Valid Palindrome [Easy] *VS* 9 Palindrome Number [Easy]
> Similarity distance: 0.4553
##### Similarities

- Both questions are related to palindromes.
- Both questions are classified as easy difficulty level.
##### Differences

- Question 125 (Valid Palindrome) checks if a given string is a valid palindrome, considering alphanumeric characters only.
- Question 9 (Palindrome Number) checks if a given integer is a palindrome.
##### New Insights in 9 Palindrome Number [Easy]

- Question 125 requires handling strings and checking alphanumeric characters.
- Question 9 requires handling integers and checking for palindromic properties.


---
# 9. From 9 Palindrome Number [Easy] to 393 UTF-8 Validation [Medium]
> Similarity Distance: 0.5899

### >> Reminder: 9 Palindrome Number [Easy]
Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward.
##### Optimal Python solution:
```python
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x < 0:
            return False
        else:
            return str(x) == str(x)[::-1]
```
Check if an integer is a palindrome by comparing it with its reverse.
    
### >> 393 UTF-8 Validation [Medium]
Given an integer array data representing the data, return whether it is a valid UTF-8 encoding.
##### Sample input:
[197, 130, 1]
##### Sample output:
true

##### Questions to ask to clarify requirements:

- What is the maximum length of the input array?
- Can the input array be empty?

##### Optimal Python solution:
```python
def validUtf8(data):
    num_bytes = 0
    for num in data:
        if num_bytes == 0:
            if (num >> 5) == 0b110:
                num_bytes = 1
            elif (num >> 4) == 0b1110:
                num_bytes = 2
            elif (num >> 3) == 0b11110:
                num_bytes = 3
            elif (num >> 7):
                return False
        else:
            if (num >> 6) != 0b10:
                return False
            num_bytes -= 1
    return num_bytes == 0
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Use bit manipulation to check the number of bytes in each UTF-8 character.
- Handle different byte lengths separately.
- Return False if the byte sequence is invalid.

- Understand the UTF-8 encoding rules.
- Use bit manipulation to extract information from binary numbers.

- Handling the different byte lengths of UTF-8 characters.
- Checking the validity of the byte sequence.

- Using built-in functions or libraries.
    
### >> Comparison: 9 Palindrome Number [Easy] *VS* 393 UTF-8 Validation [Medium]
> Similarity distance: 0.5899
##### Similarities

- Both questions involve checking for a specific pattern or property in a given input.
- Both questions require manipulating and analyzing the input in some way.
- Both questions have a specific set of rules or conditions that need to be satisfied.
##### Differences

- Palindrome Number checks if a given integer is a palindrome, while UTF-8 Validation checks if a given array of integers represents a valid UTF-8 encoding.
- Palindrome Number involves comparing digits in a number, while UTF-8 Validation involves bitwise operations and bit manipulation.
- Palindrome Number has a time complexity of O(log10(n)), while UTF-8 Validation has a time complexity of O(n).
##### New Insights in 393 UTF-8 Validation [Medium]

- Palindrome Number: Understanding how to reverse an integer and compare it with the original.
- UTF-8 Validation: Understanding the bitwise operations and bit manipulation required to validate UTF-8 encoding.

