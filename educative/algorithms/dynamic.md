## Dynamic Programming

### 0/1 knapsack

<details><summary>Solution</summary>

```python
def find_max_knapsack_profit(capacity, weights, values):
    dp = [[0] * (capacity + 1) for i in range(len(weights) + 1)]

    for i, w in enumerate(weights):
        i = i + 1
        for j in range(1, capacity + 1):
            if w > j:
                dp[i][j] = dp[i - 1][j]
            else:
                dp[i][j] = max(dp[i - 1][j], values[i - 1] + dp[i - 1][j - w])

    print(dp)
    return dp[len(weights)][capacity]
```

</details>

### Coin change problem

<details><summary>Solution</summary>

```python
def calculate_minimum_coins(coins, rem, counter):  
    if rem < 0: 
        return -1
    if rem == 0:
        return 0
    if counter[rem - 1] != float('inf'):
        return counter[rem - 1]
    minimum = float('inf')

    for s in coins: 
        result = calculate_minimum_coins(coins, rem - s, counter)
        if result >= 0 and result < minimum:
            minimum = 1 + result

    counter[rem - 1] =  minimum if minimum !=  float('inf') else  -1 
    return counter[rem - 1]

def coin_change(coins, total): 
    if total < 1:
        return 0
    return calculate_minimum_coins(coins, total, [float('inf')] * total)
```

</details>

### Find tribonacci number

<details><summary>Solution</summary>

```python

def find_tribonacci(n):

    # Replace this placeholder return statement with your code
    nums = [0, 1, 1]
    if n < 3:
        return nums[n]
    num = 0
    for i in range(3, n+1):
        num = sum(nums)
        nums[i%3] = num

    return nums[n%3]

print(find_tribonacci(4))

```

</details>

### Climbing Stairs

<details><summary>Solution 1</summary>

```python
    def climbStairs(self, n: int) -> int:
        dp = [0] * (n+1)
        dp[0] = 1
        for i in range(1, (n+1)):
            if i == 1:
                dp[1] = 1
            else:
                dp[i] = dp[i-1] + dp[i-2]

        return dp[n]
```

</details>

<details><summary>Solution 2</summary>

```python
class Solution:
    def climbStairs(self, n: int) -> int:
        dp = [0] * (n+1)
        self.climbStairsHelper(n, dp)

        return dp[n]

    def climbStairsHelper(self, n: int, dp):
        if n < 0:
            return 0
        if n == 0:
            return 1
        if dp[n] != 0:
            return dp[n]

        dp1 = self.climbStairsHelper(n - 2, dp)
        dp2 = self.climbStairsHelper(n - 1, dp)

        dp[n] = dp1 + dp2

        return dp[n]
```

### Minimum Path Sum (Leetcode 64)

<details><summary>Solution</summary>

```python

def min_cost_path(mat):
    rows = len(mat)
    cols = len(mat[0])
    cost = [[0] * cols for i in range(rows)]
    cost[0][0] = mat[0][0]
    for r in range(0, rows):
        for c in range(0, cols):
            if r == 0 and c == 0:
                cost[0][0] = mat[0][0]
            elif r == 0:
                cost[r][c] = cost[r][c - 1] + mat[r][c]
            elif c == 0:
                cost[r][c] = cost[r-1][c] + mat[r][c]
            else:
                cost[r][c] = min(cost[r-1][c], cost[r][c-1]) + mat[r][c]

    print(cost)
    return cost[rows - 1][cols - 1]

```

</details>