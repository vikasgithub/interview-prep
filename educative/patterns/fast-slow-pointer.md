## Fast and Slow Pointers

### Happy Number

```python
class Solution:
    def isHappy(self, n: int) -> bool:

        if n == 1:
            return True

        slow = n
        fast = self.sqOfNums(n)

        while slow != fast and slow != 1 and fast != 1:
            slow = self.sqOfNums(slow)
            fast = self.sqOfNums(self.sqOfNums(fast))

        return slow == 1 or fast == 1

    def sqOfNums(self, number: int) -> int:
        total_sum = 0
        while number > 0:
            number, digit = divmod(number, 10)
            total_sum += digit ** 2
        return total_sum
```

### Linked List Cycle

```python
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        slow = head
        fast = head

        while slow is not None and fast is not None and fast.next is not None:
            slow = slow.next
            fast = fast.next.next

            if slow == fast:
                return True

        return False
```

### Middle of the linked list

```python
class Solution:
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:
        slow = head
        fast = head

        while fast is not None and fast.next is not None:
            slow = slow.next
            fast = fast.next.next

        return slow
```

