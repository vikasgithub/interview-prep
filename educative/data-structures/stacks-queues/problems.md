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

### 
