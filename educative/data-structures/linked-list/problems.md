## Linked List
### Find the middle of the linked list
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

### Return the nth node from the end
- Use two pointers and increment first pointer n times
- start second pointer until end is reached

