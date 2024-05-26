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