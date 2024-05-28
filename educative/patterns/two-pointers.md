## Two Pointers

### Sum of 3 values

<details><summary>Solution</summary>

```python
def find_sum_of_three(nums, target):
    nums.sort()

    for i, n in enumerate(nums):
        if find_sum_of_two(nums, i + 1, target - n):
            return True

    return False


def find_sum_of_two(nums, start, target):
    end = len(nums) - 1

    while start < end:
        sum = nums[start] + nums[end]
        if sum == target:
            return True
        elif sum > target:
            end -= 1
        else:
            start += 1
    return False
```

</details>

### Sort Colors

Given an array, colors, which contains a combination of the following three elements: 0, 1, 2
Sort the array in place so that the elements of the same color are adjacent, with the colors in the order of red, white, and blue. To improve your problem-solving skills, do not utilize the built-in sort function.

<details><summary>Solution</summary>

```python
def sort_colors(colors):
    start, current, end = 0, 0, len(colors) - 1
    
    while current <= end:
        if colors[current] == 0:
            colors[start], colors[current] = colors[current], colors[start]
            
            current += 1
            start += 1

        elif colors[current] == 1:
            current += 1
        else:
            if colors[current] == 2:
                colors[current], colors[end] = colors[end], colors[current]

            end -= 1
```

</details>

