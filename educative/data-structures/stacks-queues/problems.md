## Queues and Stacks
### Find binary representation of n numbers

<details><summary>Solution</summary>

```python
def find_bin(n):
    d = deque()
    d.appendleft('1')
    result = []
    for i in range(n):
        v = d.pop()
        result.append(v)
        d.appendleft(v + '0')
        d.appendleft(v + '1')

    return result
``` 
</details>

###  Reverse First k Elements of Queue

<details><summary>Solution</summary>

- Use deque and appendleft to reverse k elements

</details>

### Sort values in a stack

<details><summary>Solution</summary>

```python
def sort_stack(stack):
    if not stack.is_empty():
        value = stack.pop()
        sort_stack(stack)
        insert_value(stack, value)
    return stack

def insert_value(stack, value):
    if stack.is_empty() or value < stack.peek():
        stack.push(value)
    else:
        temp = stack.pop()
        insert_value(stack, value)
        stack.push(temp)
```

</details>

### Next greater element using a stack

<details><summary>Solution</summary>

```python
def next_greater_element(lst):
    result = deque()
    
    stack = MyStack()

    for i, j in enumerate(lst[::-1]):
        while not stack.is_empty() and j >= stack.peek():
            stack.pop()
        if stack.is_empty():
            result.appendleft(-1)
        else:
            result.appendleft(stack.peek())
            
        stack.push(j)

    return list(result)
```

</details>