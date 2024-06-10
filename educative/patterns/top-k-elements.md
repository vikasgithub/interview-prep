## Top K elements

### Kth Largest Element in a Stream

```python
class Solution:

    def __init__(self, k: int, nums: List[int]):
        self.k = k
        self.data = []
        for n in nums:
            self.add(n)
        print(self.data)

    def add(self, val: int) -> int:
        if len(self.data) < self.k:
            heappush(self.data, val)
        elif self.data[0] < val:
            heappop(self.data)
            heappush(self.data, val)

        return self.data[0]
```

### Reorganize string

```python
from collections import Counter, OrderedDict
class Solution:
    def reorganizeString(self, s: str) -> str:
        freq_count = OrderedDict(Counter(s))
        top_chars = []

        for k, v in freq_count.items():
            heappush(top_chars, (-v, k))

        prev = (-1, '')
        result = ""
        while len(top_chars) > 0:
            count, c = heappop(top_chars)
            result += c
            count = -count

            if -prev[0] > 0 and prev[1] != '':
                heappush(top_chars, prev)

            prev = (-(count - 1), c)

        if len(s) != len(result):
            return ""
        return result
```

### K Closest Points to Origin

To recap, the solution to this problem can be divided into the following parts:

Push the first k points to the max-heap.

Calculate and compare the distances of the points list with the distance of the top of the max-heap.

If the point distance is smaller than the max-heap top’s distance, pop the top from the max heap and push the point.

### Top K Frequent Elements

```python
from heapq import heappush, heappop
from typing import List
from collections import Counter

class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        c = dict(Counter(nums))

        data = []
        result = []
        for n, c in c.items():
            if len(data) < k:
                heappush(data, (c, n))
            else:
                if c > data[0][0]:
                    heappop(data)
                    heappush(data, (c, n))

        while len(data):
            result.append(heappop(data)[1])

        return result
```

### Kth largest elements

```python
from heapq import heappush, heappop
from typing import List
from collections import Counter

class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        data = []

        for n in nums:
            if len(data) < k:
                heappush(data, n)
            else:
                if n >= data[0]:
                    heappop(data)
                    heappush(data, n)

        return data[0]
```

