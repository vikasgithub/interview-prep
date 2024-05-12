## Easy problems

### Merge two sorted arrays
<details><summary>Solution</summary>

```python
def merge_lists(lst1, lst2):
    result = []
    i, j = 0, 0
    
    while i < len(lst1) and j < len(lst2):
        if lst1[i] <= lst2[j]:
            result.append(lst1[i])
            i += 1
        else:
            result.append(lst2[j])
            j += 1
    
    while i < len(lst1):
        result.append(lst1[i])
        i += 1

        
    while j < len(lst2):
        result.append(lst2[j])
        j += 1

    return result
```
</details>

### Find two numbers that add upto "k"
<details><summary>Solution 1</summary>

```python
def find_sum(arr, k):
    negative_map = {}
    for i, j in enumerate(arr):
        negative_map[j] = i
    
    print(negative_map)
    result = []
    for i, j in enumerate(arr):
        diff = k - j
        if diff in negative_map and negative_map[diff] != i:
            result.append(j)
            result.append(diff)
            break

    return result
```
</details>

<details><summary>Solution 2</summary>

```python
def find_sum(arr, k):
    arr.sort()

    i, j = 0, len(arr) - 1

    result = []
    while i < j:
        s = arr[i] + arr[j]
        if s == k:
            result.append(arr[i])
            result.append(arr[j])
            break
        elif s > k:
            j -= 1
        else:
            i += 1

    return result    
```
</details>

### First Non-Repeating Integer in a List
Given a list, find the first integer which is unique in the list

<details><summary>Solution 1</summary>

Using Counter
```python

```

```python
from collections import Counter
def find_first_unique(lst):
    c = Counter(lst)
    for e, cnt  in c.items():
        if cnt == 1:
            return e
    # Replace this placeholder return statement with your code
    return 0
```
</details>