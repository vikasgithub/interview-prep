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

### Reverse a linked list

<details><summary>Solution</summary>

```python
class Solution:
    #Function to reverse a linked list.
    def reverseList(self, head):
        if head is None:
            return head
            
        # Code here
        prev = None
        curr = head
        
        while curr is not None:
            next = curr.next
            curr.next = prev
            prev = curr
            curr = next
            
        return prev
```
</details>

### Rotate a linked list

<details><summary>Solution</summary>


```python
class Solution:
    
    #Function to rotate a linked list.
    def rotate(self, head, k):
        # code here
        curr = head
        prev = None
        while k > 0:
            prev = curr
            curr = curr.next
            k -= 1
            
        if curr is None:
            return head
            
        prev.next = None
        new_head = curr
        
        while curr.next is not None:
            curr = curr.next
            
        curr.next = head
        
        return new_head
        
```

</detail>

