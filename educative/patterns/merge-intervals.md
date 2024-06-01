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

### Insert interval

``` python
from collections import deque

class Solution:
    def insert(self, intervals: List[List[int]], newInterval: List[int]) -> List[List[int]]:
        if not intervals:
            return [newInterval]
        
        intervals.append(newInterval)

        intervals = sorted(intervals, key=lambda x: x[0])
            
        results = deque()

        for curr in intervals:
            if not results:
                results.append(curr)
            else:
                top = results[-1]
                if curr[0] > top[1]:
                    results.append(curr)
                elif top[0] > curr[1]:
                    results.appendleft(curr)
                else:
                    if top[0] > curr[0]:
                        top[0] = curr[0]
                    if curr[1] > top[1]:
                        top[1] = curr[1]

        return list(results)
```

### Intersections of intervals

```python
class Solution:
    def intervalIntersection(self, firstList: List[List[int]], secondList: List[List[int]]) -> List[List[int]]:
        i, j = 0, 0
        
        results = []        
        while i < len(firstList) and j < len(secondList):
            first = firstList[i]
            second = secondList[j]

            l = max(first[0], second[0])
            r = min(first[1], second[1])

            if l <= r:
                results.append([l, r])
            
            
            if first[1] < second[1]:
                i += 1
            else:
                j += 1


        return results
```

### Employee Free Time 