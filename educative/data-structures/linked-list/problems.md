## Linked List
### Find the middle of the linked list

<details><summary>Solution</summary>

```python
def find_mid(lst):
    # Replace this placeholder return statement with your code
    sp = lst.head
    fp = lst.head

    while fp is not None and fp.next_element is not None:
        sp = sp.next_element
        fp = fp.next_element.next_element
    
    middle = sp
```
</details>

### Return the nth node from the end

<details><summary>Solution</summary>

- Use two pointers and increment first pointer n times
- start second pointer until end is reached

</details>

