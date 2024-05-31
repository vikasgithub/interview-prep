## Merge Intervals

### Merge Intervals

```python
from collections import deque

class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        if not intervals:
            return []

        results = deque()
        intervals = sorted(intervals, key=lambda x: x[0])

        results.append(intervals[0])

        for i in range(1, len(intervals)):
            top = results[-1]
            curr = intervals[i]
            if curr[0] > top[1]:
                results.append(curr)
            else:
                l = min(curr[0], top[0])
                r = max(curr[1], top[1])
                top[0] = l
                top[1] = r

        return list(results)
```
