
# Leetcode Intensive Tutorial Day 54 
> [Difficulty Score: 25]

> [Version: 20231225_200427]

## Courses overview of the day

- 20 Valid Parentheses [Easy]
  - 32 Longest Valid Parentheses [Hard]
    - 301 Remove Invalid Parentheses [Hard]
  - 224 Basic Calculator [Hard]
    - 439 Ternary Expression Parser [Medium]
    - 227 Basic Calculator II [Medium]
    - 166 Fraction to Recurring Decimal [Medium]
      - 592 Fraction Addition and Subtraction [Medium]
  - 591 Tag Validator [Hard]

#### Steps by steps

 - [1. From 20 Valid Parentheses [Easy] to 32 Longest Valid Parentheses [Hard]](#1-from-20-valid-parentheses-easy-to-32-longest-valid-parentheses-hard)

 - [2. From 32 Longest Valid Parentheses [Hard] to 301 Remove Invalid Parentheses [Hard]](#2-from-32-longest-valid-parentheses-hard-to-301-remove-invalid-parentheses-hard)

 - [3. From 20 Valid Parentheses [Easy] to 224 Basic Calculator [Hard]](#3-from-20-valid-parentheses-easy-to-224-basic-calculator-hard)

 - [4. From 224 Basic Calculator [Hard] to 439 Ternary Expression Parser [Medium]](#4-from-224-basic-calculator-hard-to-439-ternary-expression-parser-medium)

 - [5. From 224 Basic Calculator [Hard] to 227 Basic Calculator II [Medium]](#5-from-224-basic-calculator-hard-to-227-basic-calculator-ii-medium)

 - [6. From 224 Basic Calculator [Hard] to 166 Fraction to Recurring Decimal [Medium]](#6-from-224-basic-calculator-hard-to-166-fraction-to-recurring-decimal-medium)

 - [7. From 166 Fraction to Recurring Decimal [Medium] to 592 Fraction Addition and Subtraction [Medium]](#7-from-166-fraction-to-recurring-decimal-medium-to-592-fraction-addition-and-subtraction-medium)

 - [8. From 20 Valid Parentheses [Easy] to 591 Tag Validator [Hard]](#8-from-20-valid-parentheses-easy-to-591-tag-validator-hard)

#### Summary


- 224 Basic Calculator : Implement a basic calculator to evaluate a simple expression string.
- 301 Remove Invalid Parentheses : The essence of the problem is to find the minimum number of invalid parentheses to remove in order to make the input string valid.
- 166 Fraction to Recurring Decimal : Converting a fraction to a decimal and handling repeating fractional parts.
- 227 Basic Calculator II : Implement a basic calculator to evaluate a simple expression string using a stack.
- 32 Longest Valid Parentheses : The essence of the problem is to find the length of the longest valid parentheses substring in a given string.
- 439 Ternary Expression Parser : Evaluate a ternary expression using a stack.
- 20 Valid Parentheses : Checking if a string of parentheses is valid by matching opening and closing parentheses.
- 591 Tag Validator : The essence of this problem is to validate a code snippet by checking the validity of its tags.
- 592 Fraction Addition and Subtraction : The essence of this problem is to add and subtract fractions and return the result as an irreducible fraction.
> Similarity Diameter of these problems: 0.7096


---
# 1. From 20 Valid Parentheses [Easy] to 32 Longest Valid Parentheses [Hard]
> Similarity Distance: 0.3737

### >> 20 Valid Parentheses [Easy]
Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.
##### Sample input:
s = "()[]{}"
##### Sample output:
True

##### Questions to ask to clarify requirements:
Can the input string contain other characters besides parentheses? Can the parentheses be nested?

##### Optimal Python solution:
```python
def isValid(s):
    stack = []
    mapping = {')': '(', ']': '[', '}': '{'}
    for char in s:
        if char in mapping:
            if not stack or stack.pop() != mapping[char]:
                return False
        else:
            stack.append(char)
    return not stack
```
##### Time complexity:
O(N)
##### Space complexity:
O(N)
##### Notes:
Use a stack to keep track of the opening parentheses. When encountering a closing parentheses, check if it matches the top of the stack.
Use a dictionary to map closing parentheses to their corresponding opening parentheses for efficient lookup.
Handling the case where the stack is empty when encountering a closing parentheses.
Using a list as a stack without checking if it is empty before popping.
    
### >> 32 Longest Valid Parentheses [Hard]
Given a string containing just the characters '(' and ')', find the length of the longest valid (well-formed) parentheses substring.
##### Sample input:
"(()"
##### Sample output:
2

##### Questions to ask to clarify requirements:

- What is the definition of a valid parentheses substring?
- Can the input string contain characters other than '(' and ')'?

##### Optimal Python solution:
```python
def longestValidParentheses(s):
    stack = [-1]
    max_length = 0
    for i in range(len(s)):
        if s[i] == '(': stack.append(i)
        else:
            stack.pop()
            if not stack:
                stack.append(i)
            else:
                max_length = max(max_length, i - stack[-1])
    return max_length
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- A valid parentheses substring is a substring that can be balanced by adding parentheses.
- The solution uses a stack to keep track of the indices of opening parentheses.
- The maximum length of a valid parentheses substring is the difference between the current index and the index at the top of the stack.

- Use a stack to keep track of the indices of opening parentheses.
- Use the difference between the current index and the index at the top of the stack to calculate the length of valid parentheses substrings.

- Using a stack to keep track of the indices of opening parentheses allows us to calculate the length of valid parentheses substrings.
- The stack is initialized with -1 to handle the case where the first character is a closing parenthesis.

- Avoid using nested loops.
- Avoid using regular expressions.
    
### >> Comparison: 20 Valid Parentheses [Easy] *VS* 32 Longest Valid Parentheses [Hard]
> Similarity distance: 0.3737
##### Similarities

- Both questions involve checking the validity of parentheses in a given string.
##### Differences

- 20 Valid Parentheses [Easy] requires checking if all parentheses in the string are properly closed and nested.
- 32 Longest Valid Parentheses [Hard] requires finding the length of the longest valid substring of parentheses in the given string.
##### New Insights in 32 Longest Valid Parentheses [Hard]

- 20 Valid Parentheses [Easy] can be solved using a stack data structure.
- 32 Longest Valid Parentheses [Hard] can be solved using dynamic programming.


---
# 2. From 32 Longest Valid Parentheses [Hard] to 301 Remove Invalid Parentheses [Hard]
> Similarity Distance: 0.4711

### >> Reminder: 32 Longest Valid Parentheses [Hard]
Given a string containing just the characters '(' and ')', find the length of the longest valid (well-formed) parentheses substring.
##### Optimal Python solution:
```python
def longestValidParentheses(s):
    stack = [-1]
    max_length = 0
    for i in range(len(s)):
        if s[i] == '(': stack.append(i)
        else:
            stack.pop()
            if not stack:
                stack.append(i)
            else:
                max_length = max(max_length, i - stack[-1])
    return max_length
```
The essence of the problem is to find the length of the longest valid parentheses substring in a given string.
    
### >> 301 Remove Invalid Parentheses [Hard]
Given a string s that contains parentheses and letters, remove the minimum number of invalid parentheses to make the input string valid.
##### Sample input:
"()())()"
##### Sample output:
["(())()","()()()"]

##### Questions to ask to clarify requirements:

- What is the maximum length of the input string?
- Can the input string contain other characters besides parentheses and letters?

##### Optimal Python solution:
```python
class Solution:
    def removeInvalidParentheses(self, s: str) -> List[str]:
        def is_valid(s):
            count = 0
            for char in s:
                if char == '(': count += 1
                elif char == ')': count -= 1
                if count < 0: return False
            return count == 0
        level = {s}
        while True:
            valid = list(filter(is_valid, level))
            if valid: return valid
            level = {s[:i] + s[i+1:] for s in level for i in range(len(s))}
    }
```
##### Time complexity:
O(2^N * N)
##### Space complexity:
O(2^N * N)
##### Notes:

- Use BFS to generate all possible combinations of removing parentheses
- Check if a string is valid by counting the number of opening and closing parentheses

- Use a set to store the intermediate results in order to avoid duplicates

- How to efficiently generate all possible combinations of removing parentheses?

- Using a brute force approach to generate all possible combinations of removing parentheses
    
### >> Comparison: 32 Longest Valid Parentheses [Hard] *VS* 301 Remove Invalid Parentheses [Hard]
> Similarity distance: 0.4711
##### Similarities

- Both questions involve parentheses
- Both questions are classified as Hard difficulty
##### Differences

- Question 32 focuses on finding the length of the longest valid parentheses substring
- Question 301 focuses on removing the minimum number of invalid parentheses to make the input string valid
##### New Insights in 301 Remove Invalid Parentheses [Hard]

- Question 32: The solution can be optimized using a stack or dynamic programming
- Question 301: The solution can be optimized using backtracking and pruning techniques


---
# 3. From 20 Valid Parentheses [Easy] to 224 Basic Calculator [Hard]
> Similarity Distance: 0.3845

### >> Reminder: 20 Valid Parentheses [Easy]
Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.
##### Optimal Python solution:
```python
def isValid(s):
    stack = []
    mapping = {')': '(', ']': '[', '}': '{'}
    for char in s:
        if char in mapping:
            if not stack or stack.pop() != mapping[char]:
                return False
        else:
            stack.append(char)
    return not stack
```
Checking if a string of parentheses is valid by matching opening and closing parentheses.
    
### >> 224 Basic Calculator [Hard]
Implement a basic calculator to evaluate a simple expression string.
##### Sample input:
"1 + 1"
##### Sample output:
2

##### Questions to ask to clarify requirements:

- What operators are supported in the expression?
- Can the expression contain parentheses?
- Can the expression contain negative numbers?

##### Optimal Python solution:
```python
class Solution:
    def calculate(self, s: str) -> int:
        stack = []
        operand = 0
        result = 0
        sign = 1
        for char in s:
            if char.isdigit():
                operand = operand * 10 + int(char)
            elif char == '+':
                result += sign * operand
                operand = 0
                sign = 1
            elif char == '-':
                result += sign * operand
                operand = 0
                sign = -1
            elif char == '(': # push the result and sign onto the stack, start a new calculation
                stack.append(result)
                stack.append(sign)
                result = 0
                sign = 1
            elif char == ')': # complete the current calculation and pop the result and sign from the stack
                result += sign * operand
                operand = 0
                result *= stack.pop()
                result += stack.pop()
        return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- Use a stack to keep track of the operands and operators
- Evaluate the expression using the stack
- Handle parentheses by pushing the result and sign onto the stack

- Use a stack to keep track of the operands and operators.
- Handle parentheses by pushing the result and sign onto the stack.

- Handling nested parentheses
- Handling negative numbers

- Evaluating the expression using a recursive approach
    
### >> Comparison: 20 Valid Parentheses [Easy] *VS* 224 Basic Calculator [Hard]
> Similarity distance: 0.3845
##### Similarities

- Both questions involve processing mathematical expressions.
- Both questions require handling parentheses.
- Both questions involve evaluating the expressions.
##### Differences

- 20 Valid Parentheses is an easy level question, while 224 Basic Calculator is a hard level question.
- 20 Valid Parentheses focuses on checking the validity of parentheses, while 224 Basic Calculator focuses on evaluating the expression.
- 20 Valid Parentheses only involves parentheses, while 224 Basic Calculator involves other mathematical operators as well.
- 20 Valid Parentheses can be solved using a stack data structure, while 224 Basic Calculator requires more complex parsing and evaluation.
##### New Insights in 224 Basic Calculator [Hard]

- In 20 Valid Parentheses, we can use a stack to keep track of the opening parentheses and check if the closing parentheses match the top of the stack.
- In 224 Basic Calculator, we can use a stack to keep track of the operators and operands while evaluating the expression.


---
# 4. From 224 Basic Calculator [Hard] to 439 Ternary Expression Parser [Medium]
> Similarity Distance: 0.3971

### >> Reminder: 224 Basic Calculator [Hard]
Implement a basic calculator to evaluate a simple expression string.
##### Optimal Python solution:
```python
class Solution:
    def calculate(self, s: str) -> int:
        stack = []
        operand = 0
        result = 0
        sign = 1
        for char in s:
            if char.isdigit():
                operand = operand * 10 + int(char)
            elif char == '+':
                result += sign * operand
                operand = 0
                sign = 1
            elif char == '-':
                result += sign * operand
                operand = 0
                sign = -1
            elif char == '(': # push the result and sign onto the stack, start a new calculation
                stack.append(result)
                stack.append(sign)
                result = 0
                sign = 1
            elif char == ')': # complete the current calculation and pop the result and sign from the stack
                result += sign * operand
                operand = 0
                result *= stack.pop()
                result += stack.pop()
        return result
```
Implement a basic calculator to evaluate a simple expression string.
    
### >> 439 Ternary Expression Parser [Medium]
Given a string representing a ternary expression, calculate the result of the expression. You can assume the given expression is always valid.
##### Sample input:
"T?2:3"
##### Sample output:
2

##### Questions to ask to clarify requirements:
What is the maximum length of the expression? Can the expression contain spaces?

##### Optimal Python solution:
```python
def parseTernary(expression):
    stack = []
    for char in expression[::-1]:
        if stack and stack[-1] == '?':
            stack.pop()
            first = stack.pop()
            stack.pop()
            second = stack.pop()
            if char == 'T':
                stack.append(first)
            else:
                stack.append(second)
        else:
            stack.append(char)
    return stack[0]
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use a stack to evaluate the expression from right to left.
2. When encountering a '?', pop the top 3 elements from the stack and push the appropriate value back.
3. Return the final element in the stack.
Make sure to handle the case when the expression is invalid.
None
None
    
### >> Comparison: 224 Basic Calculator [Hard] *VS* 439 Ternary Expression Parser [Medium]
> Similarity distance: 0.3971
##### Similarities

- Both questions involve parsing and evaluating mathematical expressions.
- Both questions require handling parentheses in the expressions.
- Both questions involve arithmetic operations such as addition, subtraction, and multiplication.
##### Differences

- 224 Basic Calculator: The expression is given in string format and can contain spaces.
- 439 Ternary Expression Parser: The expression is given in a ternary format with conditional operators.
- 224 Basic Calculator: The expression can contain both positive and negative numbers.
- 439 Ternary Expression Parser: The expression can contain nested ternary expressions.
##### New Insights in 439 Ternary Expression Parser [Medium]

- 224 Basic Calculator: Implementing a stack-based algorithm to handle parentheses and operators.
- 439 Ternary Expression Parser: Implementing a recursive algorithm to evaluate the ternary expression.


---
# 5. From 224 Basic Calculator [Hard] to 227 Basic Calculator II [Medium]
> Similarity Distance: 0.4147

### >> Reminder: 224 Basic Calculator [Hard]
Implement a basic calculator to evaluate a simple expression string.
##### Optimal Python solution:
```python
class Solution:
    def calculate(self, s: str) -> int:
        stack = []
        operand = 0
        result = 0
        sign = 1
        for char in s:
            if char.isdigit():
                operand = operand * 10 + int(char)
            elif char == '+':
                result += sign * operand
                operand = 0
                sign = 1
            elif char == '-':
                result += sign * operand
                operand = 0
                sign = -1
            elif char == '(': # push the result and sign onto the stack, start a new calculation
                stack.append(result)
                stack.append(sign)
                result = 0
                sign = 1
            elif char == ')': # complete the current calculation and pop the result and sign from the stack
                result += sign * operand
                operand = 0
                result *= stack.pop()
                result += stack.pop()
        return result
```
Implement a basic calculator to evaluate a simple expression string.
    
### >> 227 Basic Calculator II [Medium]
Implement a basic calculator to evaluate a simple expression string.
##### Sample input:
"3+2*2"
##### Sample output:
7

##### Questions to ask to clarify requirements:
What are the possible operators in the expression? Can the expression contain parentheses?

##### Optimal Python solution:
```python
class Solution:
    def calculate(self, s: str) -> int:
        stack = []
        num = 0
        sign = '+'
        for i in range(len(s)):
            if s[i].isdigit():
                num = num * 10 + int(s[i])
            if (not s[i].isdigit() and not s[i].isspace()) or i == len(s) - 1:
                if sign == '+':
                    stack.append(num)
                elif sign == '-':
                    stack.append(-num)
                elif sign == '*':
                    stack.append(stack.pop() * num)
                else:
                    stack.append(int(stack.pop() / num))
                sign = s[i]
                num = 0
        return sum(stack)
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use a stack to store the numbers
2. Iterate through the expression string
3. Handle each character based on its type (digit, operator, or space)
4. Perform the corresponding operation and update the stack
5. Return the sum of the numbers in the stack
1. Use a stack to store intermediate results
2. Handle each character based on its type
3. Update the stack based on the current character
4. Return the final result
Handling division when the result is a decimal
Using eval() function
    
### >> Comparison: 224 Basic Calculator [Hard] *VS* 227 Basic Calculator II [Medium]
> Similarity distance: 0.4147
##### Similarities

- Both questions are related to basic calculator operations.
- Both questions require evaluating arithmetic expressions.
- Both questions involve mathematical calculations.
##### Differences

- Question 224 is classified as 'Hard' while question 227 is classified as 'Medium'.
- Question 224 allows the use of parentheses in the expression, while question 227 does not.
- Question 224 supports both positive and negative numbers, while question 227 only supports positive numbers.
- Question 224 evaluates the expression with operator precedence, while question 227 evaluates the expression without operator precedence.
##### New Insights in 227 Basic Calculator II [Medium]

- Question 224 requires implementing a recursive algorithm to handle parentheses.
- Question 227 requires implementing a stack-based algorithm to evaluate the expression.


---
# 6. From 224 Basic Calculator [Hard] to 166 Fraction to Recurring Decimal [Medium]
> Similarity Distance: 0.4577

### >> Reminder: 224 Basic Calculator [Hard]
Implement a basic calculator to evaluate a simple expression string.
##### Optimal Python solution:
```python
class Solution:
    def calculate(self, s: str) -> int:
        stack = []
        operand = 0
        result = 0
        sign = 1
        for char in s:
            if char.isdigit():
                operand = operand * 10 + int(char)
            elif char == '+':
                result += sign * operand
                operand = 0
                sign = 1
            elif char == '-':
                result += sign * operand
                operand = 0
                sign = -1
            elif char == '(': # push the result and sign onto the stack, start a new calculation
                stack.append(result)
                stack.append(sign)
                result = 0
                sign = 1
            elif char == ')': # complete the current calculation and pop the result and sign from the stack
                result += sign * operand
                operand = 0
                result *= stack.pop()
                result += stack.pop()
        return result
```
Implement a basic calculator to evaluate a simple expression string.
    
### >> 166 Fraction to Recurring Decimal [Medium]
Given two integers representing the numerator and denominator of a fraction, return the fraction in string format.
If the fractional part is repeating, enclose the repeating part in parentheses.
##### Sample input:
1
2
##### Sample output:
"0.5"

##### Questions to ask to clarify requirements:
What is the range of the numerator and denominator? Can the numerator and denominator be negative?

##### Optimal Python solution:
```python
class Solution:
    def fractionToDecimal(self, numerator: int, denominator: int) -> str:
        if numerator % denominator == 0:
            return str(numerator // denominator)
        res = []
        if (numerator < 0) != (denominator < 0):
            res.append('-')
        numerator, denominator = abs(numerator), abs(denominator)
        res.append(str(numerator // denominator) + '.')
        numerator %= denominator
        hashmap = {}
        while numerator != 0:
            if numerator in hashmap:
                res.insert(hashmap[numerator], '(')
                res.append(')')
                break
            hashmap[numerator] = len(res)
            numerator *= 10
            res.append(str(numerator // denominator))
            numerator %= denominator
        return ''.join(res)
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Divide the numerator by the denominator to get the integer part.
2. Append the decimal point.
3. Keep track of the remainder and the position of each remainder in the result.
4. If a remainder repeats, enclose the repeating part in parentheses.
Use a hashmap to keep track of the remainders and their positions.
Handling negative numbers and non-repeating fractional parts.
Using floating-point arithmetic.
    
### >> Comparison: 224 Basic Calculator [Hard] *VS* 166 Fraction to Recurring Decimal [Medium]
> Similarity distance: 0.4577
##### Similarities

- Both questions involve mathematical calculations.
- Both questions require handling of arithmetic operations.
- Both questions involve parsing and evaluating expressions.
##### Differences

- Question 224 involves evaluating a basic arithmetic expression with addition, subtraction, and parentheses.
- Question 166 involves converting a fraction into a decimal representation, with recurring decimals if necessary.
- Question 224 is classified as hard difficulty, while question 166 is classified as medium difficulty.
##### New Insights in 166 Fraction to Recurring Decimal [Medium]

- Question 224 requires implementing a stack-based algorithm to handle parentheses and operator precedence.
- Question 166 requires understanding the concept of recurring decimals and implementing a division-based algorithm.


---
# 7. From 166 Fraction to Recurring Decimal [Medium] to 592 Fraction Addition and Subtraction [Medium]
> Similarity Distance: 0.4657

### >> Reminder: 166 Fraction to Recurring Decimal [Medium]
Given two integers representing the numerator and denominator of a fraction, return the fraction in string format.
If the fractional part is repeating, enclose the repeating part in parentheses.
##### Optimal Python solution:
```python
class Solution:
    def fractionToDecimal(self, numerator: int, denominator: int) -> str:
        if numerator % denominator == 0:
            return str(numerator // denominator)
        res = []
        if (numerator < 0) != (denominator < 0):
            res.append('-')
        numerator, denominator = abs(numerator), abs(denominator)
        res.append(str(numerator // denominator) + '.')
        numerator %= denominator
        hashmap = {}
        while numerator != 0:
            if numerator in hashmap:
                res.insert(hashmap[numerator], '(')
                res.append(')')
                break
            hashmap[numerator] = len(res)
            numerator *= 10
            res.append(str(numerator // denominator))
            numerator %= denominator
        return ''.join(res)
```
Converting a fraction to a decimal and handling repeating fractional parts.
    
### >> 592 Fraction Addition and Subtraction [Medium]
Given a string representing an expression of fraction addition and subtraction, you need to return the calculation result in string format. The final result should be irreducible fraction. If your final result is an integer, say 2, you need to change it to the format of fraction that has denominator 1. So in this case, 2 should be converted to 2/1.
##### Sample input:
"-1/2+1/2"
##### Sample output:
"0/1"

##### Questions to ask to clarify requirements:
What is an irreducible fraction? How should the final result be formatted?

##### Optimal Python solution:
```python
class Solution:
    def fractionAddition(self, expression: str) -> str:
        def gcd(a, b):
            while b:
                a, b = b, a % b
            return a

        def lcm(a, b):
            return a * b // gcd(a, b)

        def add(a, b):
            x, y = a.split('/')
            p, q = b.split('/')
            lcm_val = lcm(int(y), int(q))
            num = int(x) * (lcm_val // int(y)) + int(p) * (lcm_val // int(q))
            g = gcd(num, lcm_val)
            return str(num // g) + '/' + str(lcm_val // g)

        fractions = expression.replace('+', ' +').replace('-', ' -').split()
        result = '0/1'
        for fraction in fractions:
            result = add(result, fraction)
        return result
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
1. Use the greatest common divisor (gcd) to find the common denominator.
2. Use the least common multiple (lcm) to find the common denominator.
3. Use string manipulation to split the expression into fractions.
4. Use a loop to iterate through the fractions and add them.
5. Return the final result as an irreducible fraction.
Use string manipulation to split the expression into fractions. Use the gcd and lcm functions to find the common denominator.
Finding the gcd and lcm of two numbers.
Using floating point arithmetic.
    
### >> Comparison: 166 Fraction to Recurring Decimal [Medium] *VS* 592 Fraction Addition and Subtraction [Medium]
> Similarity distance: 0.4657
##### Similarities

- Both questions involve fractions and decimal representation.
- Both questions require converting fractions to decimal.
- Both questions have a medium difficulty level.
##### Differences

- Question 166 focuses on converting fractions to recurring decimals.
- Question 592 involves addition and subtraction of fractions.
- Question 166 requires handling recurring decimals, while question 592 does not.
- Question 592 involves performing arithmetic operations on fractions.
##### New Insights in 592 Fraction Addition and Subtraction [Medium]

- Question 166 teaches us how to convert fractions to recurring decimals.
- Question 592 teaches us how to perform addition and subtraction on fractions.
- Both questions provide insights into handling fractions in different contexts.


---
# 8. From 20 Valid Parentheses [Easy] to 591 Tag Validator [Hard]
> Similarity Distance: 0.5020

### >> Reminder: 20 Valid Parentheses [Easy]
Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.
##### Optimal Python solution:
```python
def isValid(s):
    stack = []
    mapping = {')': '(', ']': '[', '}': '{'}
    for char in s:
        if char in mapping:
            if not stack or stack.pop() != mapping[char]:
                return False
        else:
            stack.append(char)
    return not stack
```
Checking if a string of parentheses is valid by matching opening and closing parentheses.
    
### >> 591 Tag Validator [Hard]
Given a string representing a code snippet, you need to implement a tag validator to parse the code and return whether it is valid. A code snippet is valid if all the following rules hold:

1. The code must be wrapped in a valid closed tag. Otherwise, the code is invalid.
2. A closed tag (not necessarily valid) has exactly the following format : <TAG_NAME>TAG_CONTENT</TAG_NAME>. Among them, <TAG_NAME> is the start tag, and </TAG_NAME> is the end tag. The TAG_NAME in start and end tags should be the same. A closed tag is valid if and only if the TAG_NAME and TAG_CONTENT are valid.
3. A valid TAG_NAME only contain upper-case letters, and has length in range [1,9]. Otherwise, the TAG_NAME is invalid.
4. A valid TAG_CONTENT may contain other valid closed tags, cdata and any characters (see note1) EXCEPT unmatched <, unmatched start and end tag, and unmatched or closed tags with invalid TAG_NAME. Otherwise, the TAG_CONTENT is invalid.
5. A start tag is unmatched if no end tag exists with the same TAG_NAME, and vice versa. However, you also need to consider the issue of unbalanced when tags are nested.
6. A < is unmatched if you cannot find a subsequent >. And vice versa.
7. A start tag is unmatched if no end tag exists with the same TAG_NAME, and vice versa. However, you also need to consider the issue of unbalanced when tags are nested.
8. A < is unmatched if you cannot find a subsequent >. And vice versa.
9. If the TAG_NAME is invalid, output Invalid.
10. If the TAG_NAME is valid, but TAG_CONTENT is invalid, output Invalid.
11. If the TAG_NAME and TAG_CONTENT are valid, output Valid.
##### Sample input:
"<DIV>This is the first line <![CDATA[<div>]]></DIV>"
##### Sample output:
"Valid"

##### Questions to ask to clarify requirements:
What is a valid closed tag? What is a valid TAG_NAME? What is a valid TAG_CONTENT?

##### Optimal Python solution:
```python
class Solution:
    def isValid(self, code: str) -> bool:
        stack = []
        i = 0
        while i < len(code):
            if i > 0 and not stack:
                return False
            if code[i:i+9] == "<![CDATA[":
                j = i + 9
                i = code.find("]]>", j)
                if i < 0:
                    return False
                i += 3
            elif code[i:i+2] == "</":
                j = i + 2
                i = code.find(">", j)
                if i < 0 or i == j or i - j > 9:
                    return False
                for k in range(j, i):
                    if not code[k].isupper():
                        return False
                if not stack or stack[-1] != code[j:i]:
                    return False
                stack.pop()
                i += 1
            elif code[i] == "<":
                j = i + 1
                i = code.find(">", j)
                if i < 0 or i == j or i - j > 9:
                    return False
                for k in range(j, i):
                    if not code[k].isupper():
                        return False
                stack.append(code[j:i])
                i += 1
            else:
                i += 1
        return not stack
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
1. Use a stack to keep track of the opening tags.
2. Use a loop to iterate through the code snippet.
3. Check for CDATA sections and skip them.
4. Check for opening and closing tags and validate them.
5. Return whether the code snippet is valid or not.
Use a stack to keep track of opening tags. Use string manipulation to iterate through the code snippet.
Handling nested tags and CDATA sections.
Using regular expressions.
    
### >> Comparison: 20 Valid Parentheses [Easy] *VS* 591 Tag Validator [Hard]
> Similarity distance: 0.5020
##### Similarities

- Both questions involve checking the validity of a string based on certain rules.
- Both questions require the use of stack data structure.
- Both questions have a time complexity of O(n).
##### Differences

- 20 Valid Parentheses: Checks the validity of parentheses only.
- 591 Tag Validator: Checks the validity of HTML-like tags and content.
- 20 Valid Parentheses: Uses a stack to keep track of opening parentheses.
- 591 Tag Validator: Uses a stack to keep track of opening tags.
- 20 Valid Parentheses: Only checks for balanced parentheses.
- 591 Tag Validator: Checks for balanced tags and valid content within tags.
##### New Insights in 591 Tag Validator [Hard]

- 20 Valid Parentheses: Can be solved using a stack to keep track of opening parentheses and checking for matching closing parentheses.
- 591 Tag Validator: Requires a more complex approach to handle nested tags and validate the content within tags.

