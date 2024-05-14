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

<details><summary>Solution</summary>

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

### Find the second max from a list
<details><summary>Solution</summary>

```python
def find_second_maximum(lst):
   if (len(lst) < 2):
       return

   # initialize the two to infinity
   max_no = second_max_no = float('-inf')
   
   for i in range(len(lst)):
       # update the max_no if max_no value found
       if (lst[i] > max_no):
           second_max_no = max_no
           max_no = lst[i]
       # check if it is the second_max_no and not equal to max_no
       elif (lst[i] > second_max_no and lst[i] != max_no):
           second_max_no = lst[i]
   
   if (second_max_no == float('-inf')):
       return
   else:
       return second_max_no
```
</details>

### Right rotate list
Given a list, can you rotate its elements by one index from right to left

<details><summary>Solution</summary>

Using python slicing
```python 
def right_rotate(lst, k):
    if len(lst) == 0:
        k = 0
    else:
        k = k % len(lst)
    
    return lst[-k:] + lst[:-k]
```
</details>

### Rearrange positive and negative values
Given a list, can you rearrange its elements in such a way that the negative elements appear at one end and positive elements appear at the other
```python
[10,-1,20,4,5,-9,-6] # input
[-1,-9,-6,10,20,4,5] # output
```

<details><summary>Solution</summary>

```python
def rearrange(lst):
    i, j = 0, 0

    while i < len(lst):
        if lst[i] < 0:
            while j < len(lst) and lst[j] < 0:
                j += 1
            if j < len(lst):
                lst[i], lst[j] = lst[j], lst[i]
        i += 1
 
    # Replace this placeholder return statement with your code
    return lst

# another solution
def rearrange(lst):
    i, j = 0, 0

    while i < j:
        while lst[i] < 0:
            i += 1
        while lst[j] > 0:
            j -= 1
        if i >= j:
            break
        else:
            lst[i], lst[j] = lst[j], lst[i] 
            i += 1
            j -= 1
    # Replace this placeholder return statement with your code
    return lst
```
</details>

###  Maximum Sum Sublist
Given an array, find the contiguous sublist with the largest sum.

<details><summary>Solution</summary>

```python
def find_max_sum_sublist(lst):
    max_sum, curr_max = lst[0], lst[0]

    for i in range(1, len(lst)):
        curr_max = max(curr_max + lst[i], lst[i])
        max_sum = max(curr_max, max_sum)
    return max_sum
```
</details>

### Product of array except self

<details><summary>Solution</summary>

- Create left and right array
- left array contains product for items to the left
- right array contains product for items to the right
- multiply left and right array to get the final product

</details>