## Greedy Algorithms
### Jump Game

<details><summary>Solution</summary>

```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        target = len(nums) - 1

        for i in reversed(range(target)):
            if i + nums[i] >= target:
                target = i

        return target == 0
```

</details>

### Boats to save people

<details><summary>Solution</summary>

```python
def rescue_boats(people, limit):
    
    people.sort()
   
    left = 0
    right = len(people) - 1

    boats = 0  

    while left <= right:
        if people[left] + people[right] <= limit:
            left += 1  
        
        right -= 1
        boats += 1

    return boats
```

</details>

### Gas Stations

<details><summary>Solution</summary>

```python
def gas_station_journey(gas, cost):
   
    if sum(cost) > sum(gas):  
        return -1             

    current_gas, starting_index = 0, 0

    for i in range(len(gas)):  
        current_gas = current_gas + (gas[i] - cost[i])
        
        if current_gas < 0:
            current_gas = 0
            starting_index = i + 1

    return starting_index
```

</details>

### Two city scheduling

<details><summary>Solution</summary>

```python
def two_city_scheduling(costs):
  # Replace this placeholder return statement with your code
  costs = sorted(costs, key=lambda x: x[0] - x[1])
  mid = len(costs) // 2
  return sum([costs[i][0] if i < mid  else costs[i][1] for i in range(len(costs))])
```

</details>

### Mininum number of jumps to reach end

<details><summary>Solution</summary>

```python
def jump_game_two(nums):
    ans = mx = last = 0  # Step 1: Initialize variables
    for i, x in enumerate(nums[:-1]):  # Step 2: Iterate over the array except the last element
        mx = max(mx, i + x)  # Update mx to the farthest reachable index
        if last == i:  # Check if we've reached the max distance from the last jump
            ans += 1  # Increment ans to record the jump
            last = mx  # Update last to the new maximum reachable index
    return ans  # Return the minimum number of jumps required
```

</details>

