## List
```python
example_list = [3.14159, 'apple', 23]  # Create a list of elements
empty_list = []  # Create an empty list
sequence_list = list(range(10))  # Create a list of first 10 whole numbers
print(example_list)
print(empty_list)
print(sequence_list)

a_list = [2, 'Educative', 'A']
another_list = [a_list, 'Python', foo, ['yet another list']]
```

### Important functions
```python
list = [1, 3, 5, 'seven']
list.append(9) # append to the end of list
list.insert(0, 2) # insert at index zero
list.remove(0) # remove item with value zero from the list
list.pop(2) # removes item with index 2 from the list
list.pop() # removes the last item from the list
list.reverse() # reverses the list
```

### Slicing
```python
list[start:end]
list = list(range(10)) # 0, 1, 2, 3, 4, 5, 6, 7, 8, 9
list[0:4] # 0, 1, 2, 3
list[start:] # means all numbers greater than start uptil the range
list[:end] # means all numbers less than end uptil the range
list[:] # means all numbers within the range
```
### stepped indexing
```python
list[start:stop:step]
list[0:9:2] # 0, 2, 4, 8
list[9:0:-2] # 9, 7, 5, 3, 1
```
### Initializing list elements
```python
arr[start:end] = [list, of, new, values]
x = list(range(5))
print(x)  # 0, 1, 2, 3, 4
x[1:4] = [45, 21, 83]
print(x) # 0, 45, 21, 83, 4
```
### Deleting elements from a list
```python
list = list(range(10)) # 0, 1, 2, 3, 4, 5, 6, 7, 8, 9
del list[::2]
print(list) # 1, 3, 5, 7, 9
``` 
### Negative Indexing
```python
list = list(range(10))
print(list)
print(list[4: -1]) # 4, 5, 6, 7, 8
```
### slicing in strings
```python
my_string = "somehow"
string1 = my_string[:4] # some
string2 = my_string[4:] # how
```
### list as stack
```python
list = [1,2,3]
list.append(4) # 1, 2, 3, 4
list.pop() # 1, 2, 3
```

### Counter
```python
from collections import Counter
c = Counter(['eggs', 'ham'])
c['bacon'] # 0
c['sausage'] = 0
del c['sausage']

# elements
c = Counter(a=4, b=2, c=0, d=-2)
sorted(c.elements())
['a', 'a', 'a', 'a', 'b', 'b']

# most_common([n])
Counter('abracadabra').most_common(3) # [('a', 5), ('b', 2), ('r', 2)]

# subtract
c = Counter(a=4, b=2, c=0, d=-2)
d = Counter(a=1, b=2, c=3, d=4)
c.subtract(d)
c # Counter({'a': 3, 'b': 0, 'c': -3, 'd': -6})

c.total()                       # total of all counts
c.clear()                       # reset all counts
list(c)                         # list unique elements
set(c)                          # convert to a set
dict(c)                         # convert to a regular dictionary
c.items()                       # convert to a list of (elem, cnt) pairs
Counter(dict(list_of_pairs))    # convert from a list of (elem, cnt) pairs
c.most_common()[:-n-1:-1]       # n least common elements
+c                              # remove zero and negative counts
c.keys()                        # all the keys
c.values()                      # all the values
```