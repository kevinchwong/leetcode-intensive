
# Leetcode Intensive Tutorial Day 59 
> [Difficulty Score: 28]

> [Version: 20231226_040350]

> [Including this day, you had studied : 510 leetcode problems]


## Courses overview of the day

- 121 Best Time to Buy and Sell Stock [Easy]
  - 122 Best Time to Buy and Sell Stock II [Easy]
  - 123 Best Time to Buy and Sell Stock III [Hard]
    - 188 Best Time to Buy and Sell Stock IV [Hard]
      - 309 Best Time to Buy and Sell Stock with Cooldown [Medium]
    - 322 Coin Change [Medium]
      - 198 House Robber [Medium]
        - 213 House Robber II [Medium]
          - 337 House Robber III [Medium]
        - 465 Optimal Account Balancing [Hard]
      - 312 Burst Balloons [Hard]

#### Step by step

 - [1. From 121 Best Time to Buy and Sell Stock [Easy] to 122 Best Time to Buy and Sell Stock II [Easy]](#1-from-121-best-time-to-buy-and-sell-stock-easy-to-122-best-time-to-buy-and-sell-stock-ii-easy))

 - [2. From 121 Best Time to Buy and Sell Stock [Easy] to 123 Best Time to Buy and Sell Stock III [Hard]](#2-from-121-best-time-to-buy-and-sell-stock-easy-to-123-best-time-to-buy-and-sell-stock-iii-hard))

 - [3. From 123 Best Time to Buy and Sell Stock III [Hard] to 188 Best Time to Buy and Sell Stock IV [Hard]](#3-from-123-best-time-to-buy-and-sell-stock-iii-hard-to-188-best-time-to-buy-and-sell-stock-iv-hard))

 - [4. From 188 Best Time to Buy and Sell Stock IV [Hard] to 309 Best Time to Buy and Sell Stock with Cooldown [Medium]](#4-from-188-best-time-to-buy-and-sell-stock-iv-hard-to-309-best-time-to-buy-and-sell-stock-with-cooldown-medium))

 - [5. From 123 Best Time to Buy and Sell Stock III [Hard] to 322 Coin Change [Medium]](#5-from-123-best-time-to-buy-and-sell-stock-iii-hard-to-322-coin-change-medium))

 - [6. From 322 Coin Change [Medium] to 198 House Robber [Medium]](#6-from-322-coin-change-medium-to-198-house-robber-medium))

 - [7. From 198 House Robber [Medium] to 213 House Robber II [Medium]](#7-from-198-house-robber-medium-to-213-house-robber-ii-medium))

 - [8. From 213 House Robber II [Medium] to 337 House Robber III [Medium]](#8-from-213-house-robber-ii-medium-to-337-house-robber-iii-medium))

 - [9. From 198 House Robber [Medium] to 465 Optimal Account Balancing [Hard]](#9-from-198-house-robber-medium-to-465-optimal-account-balancing-hard))

 - [10. From 322 Coin Change [Medium] to 312 Burst Balloons [Hard]](#10-from-322-coin-change-medium-to-312-burst-balloons-hard))

    

#### Summary


- 188 Best Time to Buy and Sell Stock IV : The essence of this problem is to find the maximum profit by buying and selling stocks, with a limit on the number of transactions.
- 123 Best Time to Buy and Sell Stock III : Dynamic programming approach to track the minimum buy price and maximum sell price for each transaction.
- 213 House Robber II : The essence of this problem is to find the maximum amount of money that can be robbed from a circular arrangement of houses.
- 465 Optimal Account Balancing : The essence of this problem is to find the minimum number of transactions required to settle the debt between a group of people.
- 121 Best Time to Buy and Sell Stock : Maximize profit by buying at the lowest price and selling at the highest price.
- 337 House Robber III : The essence of this problem is to find the maximum amount of money the thief can rob from a binary tree without alerting the police.
- 322 Coin Change : The essence of this problem is to find the fewest number of coins needed to make up a given amount of money.
- 309 Best Time to Buy and Sell Stock with Cooldown : The essence of the problem is to find the maximum profit by buying and selling stocks with the cooldown restriction.
- 122 Best Time to Buy and Sell Stock II : Maximize profit by buying at the lowest price and selling at the highest price, and adding the difference between consecutive prices if the price is increasing.
- 312 Burst Balloons : Find the maximum coins collected by bursting balloons.
- 198 House Robber : Use dynamic programming to calculate the maximum amount of money that can be robbed.
> Similarity Diameter of these problems: 0.7626


---
# 1. From 121 Best Time to Buy and Sell Stock [Easy] to 122 Best Time to Buy and Sell Stock II [Easy]
> Similarity Distance: 0.3446

### >> 121 Best Time to Buy and Sell Stock [Easy]
You are given an array prices where prices[i] is the price of a given stock on the ith day. You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock. Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.
##### Sample input:
[7,1,5,3,6,4]
##### Sample output:
5

##### Questions to ask to clarify requirements:

- Can I only buy and sell once?
- Can I buy and sell on the same day?
- Can I buy and sell on consecutive days?

##### Optimal Python solution:
```python
def maxProfit(prices):
    min_price = float('inf')
    max_profit = 0
    for price in prices:
        min_price = min(min_price, price)
        max_profit = max(max_profit, price - min_price)
    return max_profit
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Keep track of the minimum price seen so far
- Calculate the profit by subtracting the minimum price from the current price
- Update the maximum profit if a higher profit is found

- Use a variable to keep track of the minimum price
- Use a variable to keep track of the maximum profit

- Finding the minimum price
- Updating the maximum profit

- Brute force approach of checking all possible buy and sell combinations
    
### >> 122 Best Time to Buy and Sell Stock II [Easy]
You are given an array prices where prices[i] is the price of a given stock on the ith day. Find the maximum profit you can achieve. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times).
##### Sample input:
[7,1,5,3,6,4]
##### Sample output:
7

##### Questions to ask to clarify requirements:

- Can I only buy and sell once?
- Can I buy and sell on the same day?
- Can I buy and sell on consecutive days?

##### Optimal Python solution:
```python
def maxProfit(prices):
    max_profit = 0
    for i in range(1, len(prices)):
        if prices[i] > prices[i-1]:
            max_profit += prices[i] - prices[i-1]
    return max_profit
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Add the difference between consecutive prices to the maximum profit if the price is increasing

- Use a variable to keep track of the maximum profit

- Identifying the increasing prices

- Brute force approach of checking all possible buy and sell combinations
    
### >> Comparison: 121 Best Time to Buy and Sell Stock [Easy] *VS* 122 Best Time to Buy and Sell Stock II [Easy]
> Similarity distance: 0.3446
##### Similarities

- Both questions are related to buying and selling stocks.
- Both questions have an array of stock prices as input.
- Both questions require finding the maximum profit that can be obtained from buying and selling stocks.
##### Differences

- In question 121, only one transaction is allowed, i.e., buying one stock and selling it.
- In question 122, multiple transactions are allowed, i.e., buying and selling stocks multiple times.
- Question 121 focuses on finding the maximum profit for a single transaction.
- Question 122 focuses on finding the maximum profit by making multiple transactions.
##### New Insights in 122 Best Time to Buy and Sell Stock II [Easy]

- Question 121 can be solved using a simple one-pass algorithm.
- Question 122 can be solved using a greedy algorithm.
- Both questions provide insights into different approaches for maximizing profit in stock trading.


---
# 2. From 121 Best Time to Buy and Sell Stock [Easy] to 123 Best Time to Buy and Sell Stock III [Hard]
> Similarity Distance: 0.4014

### >> Reminder: 121 Best Time to Buy and Sell Stock [Easy]
You are given an array prices where prices[i] is the price of a given stock on the ith day. You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock. Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.
##### Optimal Python solution:
```python
def maxProfit(prices):
    min_price = float('inf')
    max_profit = 0
    for price in prices:
        min_price = min(min_price, price)
        max_profit = max(max_profit, price - min_price)
    return max_profit
```
Maximize profit by buying at the lowest price and selling at the highest price.
    
### >> 123 Best Time to Buy and Sell Stock III [Hard]
Given an array prices where prices[i] is the price of a given stock on the ith day, return the maximum profit you can achieve. You may complete at most two transactions.
##### Sample input:
[3,3,5,0,0,3,1,4]
##### Sample output:
6

##### Questions to ask to clarify requirements:
Can the same stock be bought and sold multiple times on the same day?

##### Optimal Python solution:
```python
def maxProfit(prices):
    buy1, buy2 = float('inf'), float('inf')
    sell1, sell2 = 0, 0
    for price in prices:
        buy1 = min(buy1, price)
        sell1 = max(sell1, price - buy1)
        buy2 = min(buy2, price - sell1)
        sell2 = max(sell2, price - buy2)
    return sell2
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:

- Use dynamic programming to track the minimum buy price and maximum sell price for each transaction
- Use two arrays to track the maximum profit for one transaction and two transactions

- Start with a brute force approach and optimize it using dynamic programming.
- Think about the information you need to track for each transaction.

- Tracking the minimum buy price and maximum sell price for each transaction

- Brute force approach of trying all possible combinations of buying and selling
    
### >> Comparison: 121 Best Time to Buy and Sell Stock [Easy] *VS* 123 Best Time to Buy and Sell Stock III [Hard]
> Similarity distance: 0.4014
##### Similarities

- Both questions are related to buying and selling stocks to maximize profit.
- Both questions involve finding the best time to buy and sell stocks.
##### Differences

- Question 121 is classified as Easy, while question 123 is classified as Hard.
- Question 121 allows only one transaction (buy and sell), while question 123 allows at most two transactions.
- Question 121 requires finding the maximum profit, while question 123 requires finding the maximum profit with at most two transactions.
- Question 121 can be solved using a simple one-pass algorithm, while question 123 requires a more complex dynamic programming approach.
##### New Insights in 123 Best Time to Buy and Sell Stock III [Hard]

- Question 123 introduces the concept of multiple transactions and the need to consider the impact of previous transactions on future ones.
- Question 123 challenges the understanding of dynamic programming and the ability to optimize the solution for multiple transactions.


---
# 3. From 123 Best Time to Buy and Sell Stock III [Hard] to 188 Best Time to Buy and Sell Stock IV [Hard]
> Similarity Distance: 0.4317

### >> Reminder: 123 Best Time to Buy and Sell Stock III [Hard]
Given an array prices where prices[i] is the price of a given stock on the ith day, return the maximum profit you can achieve. You may complete at most two transactions.
##### Optimal Python solution:
```python
def maxProfit(prices):
    buy1, buy2 = float('inf'), float('inf')
    sell1, sell2 = 0, 0
    for price in prices:
        buy1 = min(buy1, price)
        sell1 = max(sell1, price - buy1)
        buy2 = min(buy2, price - sell1)
        sell2 = max(sell2, price - buy2)
    return sell2
```
Dynamic programming approach to track the minimum buy price and maximum sell price for each transaction.
    
### >> 188 Best Time to Buy and Sell Stock IV [Hard]
You are given an integer array prices where prices[i] is the price of a given stock on the ith day. Design an algorithm to find the maximum profit. You may complete at most k transactions. Note: You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).
##### Sample input:
[2,4,1], 2
##### Sample output:
2

##### Questions to ask to clarify requirements:
1. Can the prices array be empty? 2. Can the number of transactions be zero? 3. Can the prices be negative?

##### Optimal Python solution:
```python
class Solution:
    def maxProfit(self, k: int, prices: List[int]) -> int:
        if k >= len(prices) // 2:
            return self.maxProfitUnlimited(prices)
        dp = [[0] * len(prices) for _ in range(k + 1)]
        for i in range(1, k + 1):
            maxDiff = -prices[0]
            for j in range(1, len(prices)):
                dp[i][j] = max(dp[i][j - 1], prices[j] + maxDiff)
                maxDiff = max(maxDiff, dp[i - 1][j] - prices[j])
        return dp[k][len(prices) - 1]

    def maxProfitUnlimited(self, prices: List[int]) -> int:
        maxProfit = 0
        for i in range(1, len(prices)):
            if prices[i] > prices[i - 1]:
                maxProfit += prices[i] - prices[i - 1]
        return maxProfit
```
##### Time complexity:
O(k * n)
##### Space complexity:
O(k * n)
##### Notes:
1. Use dynamic programming to solve the problem. 2. If k is greater than or equal to half the length of the prices array, use a different approach. 3. Keep track of the maximum difference between the current price and the previous prices.
1. Break down the problem into subproblems and use dynamic programming to solve them. 2. Optimize the solution by using a different approach when k is large. 3. Keep track of the maximum difference between the current price and the previous prices.
None
None
    
### >> Comparison: 123 Best Time to Buy and Sell Stock III [Hard] *VS* 188 Best Time to Buy and Sell Stock IV [Hard]
> Similarity distance: 0.4317
##### Similarities

- Both questions are related to buying and selling stocks.
- Both questions have a constraint on the number of transactions allowed.
- Both questions have a similar goal of maximizing profit.
##### Differences

- Question 123 allows at most two transactions, while question 188 allows at most k transactions.
- Question 123 has a fixed number of transactions, while question 188 allows a variable number of transactions.
- Question 123 requires the transactions to be non-overlapping, while question 188 allows overlapping transactions.
- Question 123 has a time complexity of O(n), while question 188 has a time complexity of O(nk).
##### New Insights in 188 Best Time to Buy and Sell Stock IV [Hard]

- Question 188 introduces the concept of dynamic programming with multiple states.
- Question 188 requires a more advanced approach to solve compared to question 123.


---
# 4. From 188 Best Time to Buy and Sell Stock IV [Hard] to 309 Best Time to Buy and Sell Stock with Cooldown [Medium]
> Similarity Distance: 0.4150

### >> Reminder: 188 Best Time to Buy and Sell Stock IV [Hard]
You are given an integer array prices where prices[i] is the price of a given stock on the ith day. Design an algorithm to find the maximum profit. You may complete at most k transactions. Note: You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).
##### Optimal Python solution:
```python
class Solution:
    def maxProfit(self, k: int, prices: List[int]) -> int:
        if k >= len(prices) // 2:
            return self.maxProfitUnlimited(prices)
        dp = [[0] * len(prices) for _ in range(k + 1)]
        for i in range(1, k + 1):
            maxDiff = -prices[0]
            for j in range(1, len(prices)):
                dp[i][j] = max(dp[i][j - 1], prices[j] + maxDiff)
                maxDiff = max(maxDiff, dp[i - 1][j] - prices[j])
        return dp[k][len(prices) - 1]

    def maxProfitUnlimited(self, prices: List[int]) -> int:
        maxProfit = 0
        for i in range(1, len(prices)):
            if prices[i] > prices[i - 1]:
                maxProfit += prices[i] - prices[i - 1]
        return maxProfit
```
The essence of this problem is to find the maximum profit by buying and selling stocks, with a limit on the number of transactions.
    
### >> 309 Best Time to Buy and Sell Stock with Cooldown [Medium]
You are given an array prices where prices[i] is the price of a given stock on the ith day. Find the maximum profit you can achieve. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times) with the following restrictions: After you sell your stock, you cannot buy stock on the next day (i.e., cooldown one day).
##### Sample input:
[1,2,3,0,2]
##### Sample output:
3

##### Questions to ask to clarify requirements:

- Can I buy and sell stock on the same day?
- Can I buy and sell stock multiple times on the same day?
- What is the maximum number of transactions allowed?

##### Optimal Python solution:
```python
def maxProfit(prices):
    if not prices:
        return 0
    n = len(prices)
    dp = [[0] * 3 for _ in range(n)]
    dp[0][0] = -prices[0]
    for i in range(1, n):
        dp[i][0] = max(dp[i-1][0], dp[i-1][2] - prices[i])
        dp[i][1] = dp[i-1][0] + prices[i]
        dp[i][2] = max(dp[i-1][1], dp[i-1][2])
    return max(dp[n-1][1], dp[n-1][2])
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- Use dynamic programming to solve the problem.
- Maintain three states: holding stock, not holding stock with cooldown, not holding stock without cooldown.
- Update the states based on the previous states and current price.

- Break down the problem into smaller subproblems.
- Think about the states and transitions between states.
- Consider edge cases such as empty input or negative prices.

- The cooldown restriction makes the problem more challenging.
- Consider the case where the cooldown is longer than one day.

- Avoid brute force approach with multiple buy and sell operations.
- Avoid using recursion for dynamic programming solution.
    
### >> Comparison: 188 Best Time to Buy and Sell Stock IV [Hard] *VS* 309 Best Time to Buy and Sell Stock with Cooldown [Medium]
> Similarity distance: 0.4150
##### Similarities

- Both questions are related to buying and selling stocks.
- Both questions involve maximizing profit.
- Both questions have a constraint on the number of transactions allowed.
##### Differences

- Question 188 allows unlimited transactions, while question 309 has a cooldown period after each transaction.
- Question 188 is classified as hard, while question 309 is classified as medium.
- Question 188 allows the same stock to be bought and sold multiple times, while question 309 does not.
##### New Insights in 309 Best Time to Buy and Sell Stock with Cooldown [Medium]

- Question 188 requires finding the maximum profit with at most k transactions, where k can be any non-negative integer.
- Question 309 introduces a cooldown period, where after selling a stock, you cannot buy another stock on the next day.


---
# 5. From 123 Best Time to Buy and Sell Stock III [Hard] to 322 Coin Change [Medium]
> Similarity Distance: 0.4590

### >> Reminder: 123 Best Time to Buy and Sell Stock III [Hard]
Given an array prices where prices[i] is the price of a given stock on the ith day, return the maximum profit you can achieve. You may complete at most two transactions.
##### Optimal Python solution:
```python
def maxProfit(prices):
    buy1, buy2 = float('inf'), float('inf')
    sell1, sell2 = 0, 0
    for price in prices:
        buy1 = min(buy1, price)
        sell1 = max(sell1, price - buy1)
        buy2 = min(buy2, price - sell1)
        sell2 = max(sell2, price - buy2)
    return sell2
```
Dynamic programming approach to track the minimum buy price and maximum sell price for each transaction.
    
### >> 322 Coin Change [Medium]
You are given coins of different denominations and a total amount of money amount. Write a function to compute the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.
##### Sample input:
[1, 2, 5]
11
##### Sample output:
3

##### Questions to ask to clarify requirements:

- Can the denominations of coins be negative?
- Can the amount of money be negative?
- Can the denominations of coins be floating point numbers?

##### Optimal Python solution:
```python
def coinChange(self, coins: List[int], amount: int) -> int:
    dp = [float('inf')] * (amount + 1)
    dp[0] = 0
    for coin in coins:
        for i in range(coin, amount + 1):
            dp[i] = min(dp[i], dp[i - coin] + 1)
    return dp[amount] if dp[amount] != float('inf') else -1
```
##### Time complexity:
O(amount * n)
##### Space complexity:
O(amount)
##### Notes:

- Use dynamic programming to solve the problem.
- Initialize a list dp with length amount + 1 and set all values to infinity.
- Set dp[0] to 0.
- Iterate over the coins and for each coin, iterate over the range from coin to amount + 1.
- Update dp[i] to the minimum of dp[i] and dp[i - coin] + 1.
- Return dp[amount] if it is not infinity, otherwise return -1.

- Initialize a list dp with length amount + 1 and set all values to infinity.
- Set dp[0] to 0.
- Iterate over the coins and for each coin, iterate over the range from coin to amount + 1.
- Update dp[i] to the minimum of dp[i] and dp[i - coin] + 1.
- Return dp[amount] if it is not infinity, otherwise return -1.

- The problem can be solved using dynamic programming.
- The minimum number of coins needed to make up the amount can be found by iterating over the coins and updating the dp array.

- Avoid using brute force approach to try all possible combinations of coins.
- Avoid using recursion to solve the problem.
    
### >> Comparison: 123 Best Time to Buy and Sell Stock III [Hard] *VS* 322 Coin Change [Medium]
> Similarity distance: 0.4590
##### Similarities

- Both questions are related to financial transactions.
- Both questions involve making optimal decisions to maximize profit or minimize cost.
- Both questions require dynamic programming techniques to solve efficiently.
##### Differences

- Question 123 involves buying and selling stocks to maximize profit, while question 322 involves finding the minimum number of coins needed to make a certain amount of change.
- Question 123 allows at most two transactions, while question 322 has no limit on the number of coin changes.
- Question 123 is classified as a hard-level problem, while question 322 is classified as a medium-level problem.
##### New Insights in 322 Coin Change [Medium]

- From question 123, we can learn how to optimize stock trading strategies by considering multiple transactions.
- From question 322, we can learn how to solve the coin change problem using dynamic programming, which can be applied to other similar optimization problems.


---
# 6. From 322 Coin Change [Medium] to 198 House Robber [Medium]
> Similarity Distance: 0.3888

### >> Reminder: 322 Coin Change [Medium]
You are given coins of different denominations and a total amount of money amount. Write a function to compute the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.
##### Optimal Python solution:
```python
def coinChange(self, coins: List[int], amount: int) -> int:
    dp = [float('inf')] * (amount + 1)
    dp[0] = 0
    for coin in coins:
        for i in range(coin, amount + 1):
            dp[i] = min(dp[i], dp[i - coin] + 1)
    return dp[amount] if dp[amount] != float('inf') else -1
```
The essence of this problem is to find the fewest number of coins needed to make up a given amount of money.
    
### >> 198 House Robber [Medium]
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security systems connected and it will automatically contact the police if two adjacent houses were broken into on the same night. Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.
##### Sample input:
Input: 

[1,2,3,1]

Output: 

4

Explanation: 

Rob house 1 (money = 1) and then rob house 3 (money = 3).
Total amount you can rob = 1 + 3 = 4.
##### Sample output:
Explanation: 

Rob house 1 (money = 1) and then rob house 3 (money = 3).
Total amount you can rob = 1 + 3 = 4.

##### Questions to ask to clarify requirements:
None

##### Optimal Python solution:
```python
def rob(nums):
    if not nums:
        return 0
    if len(nums) == 1:
        return nums[0]
    dp = [0] * len(nums)
    dp[0] = nums[0]
    dp[1] = max(nums[0], nums[1])
    for i in range(2, len(nums)):
        dp[i] = max(dp[i-1], dp[i-2] + nums[i])
    return dp[-1]
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:
None
None
None
None
    
### >> Comparison: 322 Coin Change [Medium] *VS* 198 House Robber [Medium]
> Similarity distance: 0.3888
##### Similarities

- Both questions are classified as medium difficulty.
- Both questions involve dynamic programming.
- Both questions require finding the maximum or minimum value.
- Both questions involve making decisions based on previous subproblems.
##### Differences

- 322 Coin Change involves finding the minimum number of coins needed to make a certain amount of money.
- 198 House Robber involves finding the maximum amount of money that can be robbed without alerting the police.
- 322 Coin Change has an unlimited supply of each coin denomination.
- 198 House Robber has a constraint that adjacent houses cannot be robbed.
##### New Insights in 198 House Robber [Medium]

- From 322 Coin Change, we can learn how to use dynamic programming to solve the minimum coin change problem.
- From 198 House Robber, we can learn how to use dynamic programming to solve the maximum amount of money that can be robbed problem.
- We can learn how to make decisions based on previous subproblems to optimize the solution.


---
# 7. From 198 House Robber [Medium] to 213 House Robber II [Medium]
> Similarity Distance: 0.3738

### >> Reminder: 198 House Robber [Medium]
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security systems connected and it will automatically contact the police if two adjacent houses were broken into on the same night. Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.
##### Optimal Python solution:
```python
def rob(nums):
    if not nums:
        return 0
    if len(nums) == 1:
        return nums[0]
    dp = [0] * len(nums)
    dp[0] = nums[0]
    dp[1] = max(nums[0], nums[1])
    for i in range(2, len(nums)):
        dp[i] = max(dp[i-1], dp[i-2] + nums[i])
    return dp[-1]
```
Use dynamic programming to calculate the maximum amount of money that can be robbed.
    
### >> 213 House Robber II [Medium]
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed. All houses at this place are arranged in a circle. That means the first house is the neighbor of the last one. Meanwhile, adjacent houses have a security system connected, and it will automatically contact the police if two adjacent houses were broken into on the same night. Given a list of non-negative integers nums representing the amount of money of each house, return the maximum amount of money you can rob tonight without alerting the police.
##### Sample input:
[2,3,2]
##### Sample output:
3

##### Questions to ask to clarify requirements:
Can I assume that the list of houses will always have at least one house? Can I assume that the list of houses will always have at most 100 houses? Can I assume that the amount of money in each house will always be a non-negative integer? Can I assume that the amount of money in each house will always be at most 10000?

##### Optimal Python solution:
```python
def rob(nums):
    if len(nums) == 1:
        return nums[0]
    return max(rob_helper(nums[:-1]), rob_helper(nums[1:]))


def rob_helper(nums):
    prev1 = 0
    prev2 = 0
    for num in nums:
        temp = prev1
        prev1 = max(prev2 + num, prev1)
        prev2 = temp
    return prev1
```
##### Time complexity:
O(n)
##### Space complexity:
O(1)
##### Notes:
The problem can be divided into two subproblems: rob houses from 0 to n-2 and rob houses from 1 to n-1. Use dynamic programming to solve each subproblem. The maximum amount of money that can be robbed is the maximum of the two subproblems.
Use dynamic programming to solve the problem. Break down the problem into smaller subproblems. Use variables to store intermediate results.
Handling the circular arrangement of houses. Choosing the correct subproblem to solve.
Using recursion to solve the problem. Using brute force to try all possible combinations.
    
### >> Comparison: 198 House Robber [Medium] *VS* 213 House Robber II [Medium]
> Similarity distance: 0.3738
##### Similarities

- Both questions are related to the problem of robbing houses.
- Both questions involve a sequence of houses, each containing a certain amount of money.
- Both questions require finding the maximum amount of money that can be robbed without robbing adjacent houses.
##### Differences

- In question 198, the houses are arranged in a straight line, while in question 213, the houses are arranged in a circle.
- In question 198, the robber cannot rob adjacent houses, while in question 213, the robber cannot rob the first and last houses simultaneously.
- In question 198, the robber can start from any house, while in question 213, the robber can only start from the first or second house.
##### New Insights in 213 House Robber II [Medium]

- Question 198 can be solved using dynamic programming by considering two cases: robbing the current house or not robbing the current house.
- Question 213 can be solved by breaking it down into two subproblems: robbing houses from the first to the second-to-last house, and robbing houses from the second to the last house.


---
# 8. From 213 House Robber II [Medium] to 337 House Robber III [Medium]
> Similarity Distance: 0.5016

### >> Reminder: 213 House Robber II [Medium]
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed. All houses at this place are arranged in a circle. That means the first house is the neighbor of the last one. Meanwhile, adjacent houses have a security system connected, and it will automatically contact the police if two adjacent houses were broken into on the same night. Given a list of non-negative integers nums representing the amount of money of each house, return the maximum amount of money you can rob tonight without alerting the police.
##### Optimal Python solution:
```python
def rob(nums):
    if len(nums) == 1:
        return nums[0]
    return max(rob_helper(nums[:-1]), rob_helper(nums[1:]))


def rob_helper(nums):
    prev1 = 0
    prev2 = 0
    for num in nums:
        temp = prev1
        prev1 = max(prev2 + num, prev1)
        prev2 = temp
    return prev1
```
The essence of this problem is to find the maximum amount of money that can be robbed from a circular arrangement of houses.
    
### >> 337 House Robber III [Medium]
The thief has found himself a new place for his thievery again. There is only one entrance to this area, called the "root." Besides the root, each house has one and only one parent house. After a tour, the smart thief realized that "all houses in this place forms a binary tree". It will automatically contact the police if two directly-linked houses were broken into on the same night.

Determine the maximum amount of money the thief can rob tonight without alerting the police.
##### Sample input:

- 3,2,3,null,3,null,1
##### Sample output:

- 7

##### Questions to ask to clarify requirements:

- Can the thief rob the root node?
- Can the thief rob adjacent houses?
- What is the maximum amount of money the thief can rob?

##### Optimal Python solution:
```python

- class Solution:
-     def rob(self, root: TreeNode) -> int:
-         def dfs(node):
-             if not node:
-                 return 0, 0
-             left, right = dfs(node.left), dfs(node.right)
-             rob = node.val + left[1] + right[1]
-             not_rob = max(left) + max(right)
-             return rob, not_rob
-         return max(dfs(root))
```
##### Time complexity:
O(n)
##### Space complexity:
O(n)
##### Notes:

- The maximum amount of money the thief can rob is the maximum of the amount robbed from the root node and the amount robbed from its children.
- The amount robbed from a node is the sum of the node's value and the amounts robbed from its grandchildren.
- The amount not robbed from a node is the maximum of the amounts robbed from its children.

- Use a recursive function to calculate the maximum amount of money the thief can rob from a binary tree.
- Use a tuple to store the maximum amount of money robbed and the maximum amount of money not robbed.
- Use dynamic programming techniques to optimize the solution.

- The solution uses a recursive function to calculate the maximum amount of money the thief can rob.
- The function returns a tuple containing the maximum amount of money robbed and the maximum amount of money not robbed.

- Avoid using a brute force approach to calculate the maximum amount of money the thief can rob.
- Avoid using a global variable to store the maximum amount of money robbed.
    
### >> Comparison: 213 House Robber II [Medium] *VS* 337 House Robber III [Medium]
> Similarity distance: 0.5016
##### Similarities

- Both questions are related to the problem of robbing houses.
- Both questions have a similar dynamic programming approach.
- Both questions involve making decisions on whether to rob adjacent houses.
##### Differences

- Question 213 involves a circular street of houses, while question 337 involves a binary tree structure.
- Question 213 allows robbing the first and last houses together, while question 337 does not have this constraint.
- Question 213 has a linear time complexity, while question 337 has a time complexity of O(n^2).
##### New Insights in 337 House Robber III [Medium]

- Question 213 requires considering two scenarios: robbing the first house and not robbing the first house.
- Question 337 introduces the concept of considering the grandchildren of a node in the binary tree.


---
# 9. From 198 House Robber [Medium] to 465 Optimal Account Balancing [Hard]
> Similarity Distance: 0.4499

### >> Reminder: 198 House Robber [Medium]
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security systems connected and it will automatically contact the police if two adjacent houses were broken into on the same night. Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.
##### Optimal Python solution:
```python
def rob(nums):
    if not nums:
        return 0
    if len(nums) == 1:
        return nums[0]
    dp = [0] * len(nums)
    dp[0] = nums[0]
    dp[1] = max(nums[0], nums[1])
    for i in range(2, len(nums)):
        dp[i] = max(dp[i-1], dp[i-2] + nums[i])
    return dp[-1]
```
Use dynamic programming to calculate the maximum amount of money that can be robbed.
    
### >> 465 Optimal Account Balancing [Hard]
A group of friends went on holiday and sometimes lent each other money. For example, Alice paid for Bill's lunch for $10. Then later Chris gave Alice $5 for a taxi ride. We can model each transaction as a tuple (x, y, z) which means person x gave person y $z. Assuming Alice, Bill, and Chris are person 0, 1, and 2 respectively (0, 1, 2 are the person's ID), the transactions can be represented as [[0, 1, 10], [2, 0, 5]]. Given a list of transactions between a group of people, return the minimum number of transactions required to settle the debt.
##### Sample input:
[[0,1,10], [2,0,5]]
##### Sample output:
2

##### Questions to ask to clarify requirements:

- Can there be multiple transactions between the same pair of people?
- Can there be cycles in the transactions?
- Can the transactions be in any order?

##### Optimal Python solution:
```python
def minTransfers(transactions):
    balances = defaultdict(int)
    for x, y, z in transactions:
        balances[x] -= z
        balances[y] += z
    debts = list(balances.values())
    return settle(debts, 0)


def settle(debts, start):
    while start < len(debts) and debts[start] == 0:
        start += 1
    if start == len(debts):
        return 0
    min_transfers = float('inf')
    for i in range(start + 1, len(debts)):
        if debts[i] * debts[start] < 0:
            debts[i] += debts[start]
            min_transfers = min(min_transfers, 1 + settle(debts, start + 1))
            debts[i] -= debts[start]
    return min_transfers
```
##### Time complexity:
O(2^n)
##### Space complexity:
O(n)
##### Notes:

- Use a dictionary to keep track of the balances for each person
- Convert the dictionary values to a list of debts
- Use backtracking to settle the debts

- Use a dictionary to keep track of the balances for each person
- Convert the dictionary values to a list of debts
- Use backtracking to settle the debts

- The problem can be solved using backtracking and dynamic programming

- Avoid using a brute force approach to check all possible combinations of transactions
    
### >> Comparison: 198 House Robber [Medium] *VS* 465 Optimal Account Balancing [Hard]
> Similarity distance: 0.4499
##### Similarities

- Both questions involve optimizing a sequence of actions to maximize a certain value.
- Both questions require dynamic programming techniques to solve efficiently.
##### Differences

- House Robber involves finding the maximum amount of money that can be robbed from a row of houses, where adjacent houses cannot be robbed consecutively.
- Optimal Account Balancing involves settling debts among a group of people, where each person owes or is owed a certain amount of money.
##### New Insights in 465 Optimal Account Balancing [Hard]

- House Robber: The key insight is to use dynamic programming to keep track of the maximum amount of money that can be robbed at each house.
- Optimal Account Balancing: The key insight is to convert the problem into a graph where nodes represent people and edges represent debts, and then use backtracking to find the minimum number of transactions needed to settle all debts.


---
# 10. From 322 Coin Change [Medium] to 312 Burst Balloons [Hard]
> Similarity Distance: 0.4295

### >> Reminder: 322 Coin Change [Medium]
You are given coins of different denominations and a total amount of money amount. Write a function to compute the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.
##### Optimal Python solution:
```python
def coinChange(self, coins: List[int], amount: int) -> int:
    dp = [float('inf')] * (amount + 1)
    dp[0] = 0
    for coin in coins:
        for i in range(coin, amount + 1):
            dp[i] = min(dp[i], dp[i - coin] + 1)
    return dp[amount] if dp[amount] != float('inf') else -1
```
The essence of this problem is to find the fewest number of coins needed to make up a given amount of money.
    
### >> 312 Burst Balloons [Hard]
Given n balloons, indexed from 0 to n-1. Each balloon is painted with a number on it represented by an array nums. You are asked to burst all the balloons. If you burst the ith balloon, you will get nums[left] * nums[i] * nums[right] coins. Here left and right are adjacent indices of i. After the burst, the left and right then becomes adjacent. Find the maximum coins you can collect by bursting the balloons wisely.
##### Sample input:

- [3,1,5,8]
##### Sample output:
167

##### Questions to ask to clarify requirements:

- Can the balloons have negative numbers?
- Can the balloons have duplicate numbers?

##### Optimal Python solution:
```python

- def maxCoins(nums):
-     nums = [1] + nums + [1]
-     n = len(nums)
-     dp = [[0] * n for _ in range(n)]
-     for length in range(2, n):
-         for left in range(n - length):
-             right = left + length
-             for k in range(left + 1, right):
-                 dp[left][right] = max(dp[left][right], nums[left] * nums[k] * nums[right] + dp[left][k] + dp[k][right])
-     return dp[0][n - 1]
```
##### Time complexity:
O(n^3)
##### Space complexity:
O(n^2)
##### Notes:

- Bursting a balloon affects adjacent balloons.
- The order of bursting affects the coins collected.
- Use dynamic programming to find the maximum coins.

- Break down the problem into subproblems.
- Use dynamic programming to solve the subproblems efficiently.

- Finding the optimal order of bursting balloons.
- Handling the boundaries of the balloons.

- Bursting balloons in a random order.
- Iterating over all possible orders of bursting balloons.
    
### >> Comparison: 322 Coin Change [Medium] *VS* 312 Burst Balloons [Hard]
> Similarity distance: 0.4295
##### Similarities

- Both questions involve finding the minimum number of operations to achieve a certain goal.
- Both questions require dynamic programming to solve efficiently.
##### Differences

- Coin Change involves finding the minimum number of coins needed to make a certain amount of money, while Burst Balloons involves finding the maximum number of coins that can be obtained by bursting balloons.
- Coin Change allows unlimited use of each coin, while Burst Balloons requires balloons to be burst in a specific order.
- Coin Change has a linear time complexity solution using dynamic programming, while Burst Balloons has a more complex time complexity.
##### New Insights in 312 Burst Balloons [Hard]

- Coin Change can be solved using a bottom-up dynamic programming approach, where the minimum number of coins for each amount is calculated iteratively.
- Burst Balloons can be solved using a divide and conquer approach, where the problem is divided into subproblems and the solutions are combined.

