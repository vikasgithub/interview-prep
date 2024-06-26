## What to track

### Group Anagrams
```py
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        if not strs:
            return [[""]]

        counters = {}
        for str in strs:
            c = [0] * 26
            for s in str:
                index = ord(s) - ord('a')
                c[index] += 1
            t = tuple(c)
            if t in counters:
                counters[t].append(str)
            else:
                counters[t] = [str]

        return [v for k, v in counters.items()]
```

### Maximum Frequency Stack

```py

```