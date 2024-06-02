### In place reversal of linked list

## Reverse a linked list

<details><summary>Solution</summary>

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        curr = head
        prev = None
        while curr is not None:
            nxt = curr.next
            curr.next = prev
            prev = curr
            curr = nxt

        return prev
```
</details>

## Reverse nodes in k-groups

<details><summary>Solution</summary>

```python
class Solution:
    def reverseKGroup(self, head: Optional[ListNode], k: int) -> Optional[ListNode]:
        dummy = ListNode(0)
        dummy.next = head

        before = dummy
        first = head
        curr = head

        i = 1

        # Before reversal
        # Before -> First -> N -> N -> Last -> After
        # Before -> Last -> N -> N -> First -> After
        # Next reversal
        # Before -> First
        while curr is not None:
            if i % k == 0:
                after = curr.next
                self.reverseBetween(before, first, after)
                before = first
                first = after
                curr = after
            else:
                curr = curr.next
            i += 1

        return dummy.next

    def reverseBetween(self, before, first, after):
        prev = None
        curr = first
        while curr != after:
            nxt = curr.next
            curr.next = prev
            prev = curr
            curr = nxt

        before.next = prev
        first.next = after
```

</details>

### Reverse Linked list between two given nodes

<details><summary>Solution</summary>

```python
class Solution:
    def reverseBetween(self, head: Optional[ListNode], left: int, right: int) -> Optional[ListNode]:
        dummy = ListNode(0)
        dummy.next = head

        before = dummy

        i = 1
        first = None
        curr = head
        while curr is not None:
            if i < left:
                before = curr
            elif i == left:
                first = curr
            elif i == right:
                self.reverse(before, curr, first)
                break

            curr = curr.next
            i += 1

        return dummy.next

    def reverse(self, before, curr, first):
        after = curr.next
        temp = first
        prev = None
        while temp != after:
            nxt = temp.next
            temp.next = prev
            prev = temp
            temp = nxt
        before.next = prev
        first.next = after        
```

</details>

### Reorder List

<details><summary>Solution</summary>

```python
class Solution:
    def reorderList(self, head: Optional[ListNode]) -> None:
        dummy = ListNode(0, head)
        slow = fast = head

        while fast is not None and fast.next is not None:
            slow = slow.next
            fast = fast.next.next

        middle = slow
        reverse_head = self.reverse(middle.next)
        middle.next = None

        first = head
        second = reverse_head
        while first is not None and second is not None:
            temp1 = first.next
            temp2 = second.next
            first.next = second
            second.next = temp1
            first = temp1
            second = temp2

        return dummy.next


    def reverse(self, head):
        prev = None
        curr = head
        while curr is not None:
            nxt = curr.next
            curr.next = prev
            prev = curr
            curr = nxt

        return prev
```

</details>

### Swap Nodes

<details><summary>Solution</summary>

```python
class Solution:
    def swapNodes(self, head: Optional[ListNode], k: int) -> Optional[ListNode]:
        dummy = ListNode(0, head)
        first = head
        second = head
        curr = head
        i = 1

        while curr is not None:
            if i == k:
                first = curr
            elif i > k:
                second = second.next
            curr = curr.next
            i += 1

        first_val = first.val
        second_val = second.val
        second.val = first_val
        first.val = second_val

        return dummy.next
```

</details>

### Reverse nodes in even length groups

<details><summary>Solution</summary>

```python
class Solution:
    def reverseEvenLengthGroups(self, head: Optional[ListNode]) -> Optional[ListNode]:
        dummy = ListNode(0, head)

        curr = head
        before = dummy
        first = head
        k = 1
        i = 1
        while curr is not None:
            if i == k:
                after = curr.next
                if k % 2 == 0:
                    self.reverse(before, first, after)
                    before = first
                else:
                    before = curr
                curr = after
                first = after
                k += 1
                i = 1
            else:
                i += 1
                curr = curr.next

        if i > 1 and i % 2 == 1:
            self.reverse(before, first, None)

        return dummy.next

    def reverse(self, before, first, after):
        prev = None
        curr = first

        while curr is not None and curr != after:
            nxt = curr.next
            curr.next = prev
            prev = curr
            curr = nxt

        before.next = prev
        first.next = after
```

</details>

### Reverse in pairs

<details><summary>Solution</summary>

```python
class Solution:
    def swapPairs(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if not head or not head.next:
            return head

        dummy = ListNode(0, head)
        before = dummy
        first = head

        while first is not None and first.next is not None:
            second = first.next
            nxt2 = second.next
            second.next = first
            first.next = nxt2
            before.next = second
            before = first
            first = nxt2

        return dummy.next
```

</details>