## K-Way Merge

```python
class Solution(object):
    def merge(self, nums1, m, nums2, n):
        """
        :type nums1: List[int]
        :type m: int
        :type nums2: List[int]
        :type n: int
        :rtype: None Do not return anything, modify nums1 in-place instead.
        """
        k = len(nums1) - 1
        m -= 1
        n -= 1
        while k >= 0:
            if n < 0:
                break
            if m >= 0 and nums1[m] >= nums2[n]:
                nums1[k] = nums1[m]
                m -= 1
            else:
                nums1[k] = nums2[n]
                n -= 1
            k -= 1
```
### Kth Smallest Number in M Sorted Lists

```python
from heapq import *

def k_smallest_number(lists, k):
    data = []

    n = len(lists)
    for i in range(n):
        heappush(data, (lists[i][0], i, 0))

    if k <= n:
        return data[k]

    i = n
    while data and i < k:
        num, list_index, item_index = heappop(data)
        if item_index < len(lists[list_index]) - 1:
            heappush(data, (lists[list_index][item_index + 1], list_index, item_index + 1))
            i += 1
    
    if data:
        return data[-1][0]
    else:
        return num

```

### Find K Pairs with Smallest Sums
```python
class Solution:
    def kSmallestPairs(self, nums1: List[int], nums2: List[int], k: int) -> List[List[int]]:
        data = []
        result = []
        heappush(data, (nums1[0] + nums2[0], 0, 0))
        already_used = set()
        while len(result) < k:
            s, i, j = heappop(data)
            result.append([nums1[i], nums2[j]])
            if i < len(nums1) - 1:
                key = f"{i+1},{j}"
                if key not in already_used:
                    heappush(data, (nums1[i + 1] + nums2[j], i + 1, j))
                    already_used.add(key)
            if j < len(nums2) - 1:
                key2 = f"{i},{j+1}"
                if key2 not in already_used:
                    heappush(data, (nums1[i] + nums2[j + 1], i, j + 1))
                    already_used.add(key2)

        return result
```

### Merge k-Lists

```python
class CustomNode(ListNode):
    def __init__(self, node:ListNode):
        self.val = node.val
        self.next = node.next
    def __lt__(self,other):
        return self.val < other.val
    def __le__(self,other):
        return self.val <= other.val

class Solution:
    def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        if not lists:
            return None
        data = []
        for i in range(len(lists)):
            if lists[i]:
                heappush(data, (lists[i].val, CustomNode(lists[i])))

        if not data:
            return None
            
        results = []
        while data:
            val, node = heappop(data)
            results.append(val)

            if node.next:
                heappush(data, (node.next.val, CustomNode(node.next)))

        prev = ListNode(results[0])
        head = prev

        for i in range(1, len(results)):
            curr = ListNode(results[i])
            prev.next = curr
            prev = curr

        return head
```

