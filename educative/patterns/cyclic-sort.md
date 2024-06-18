## Cyclic Sort

### Missing Number

```python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        i = 0
        len_nums = len(nums)
        while i < len_nums:
            val = nums[i]
            if val < len_nums and val != i:
                nums[i], nums[val] = nums[val], nums[i]
            else:
                i += 1

        for i, x in enumerate(nums):
            if i != x:
                return i

        return len(nums)
```

### First missing positive number

```python
class Solution:
    def firstMissingPositive(self, nums: List[int]) -> int:
        i = 0
        while i < len(nums):
            correct_spot = nums[i] - 1
            if 0 <= correct_spot < len(nums) and nums[i] != nums[correct_spot]:
                nums[i], nums[correct_spot] = nums[correct_spot], nums[i]
            else:
                i += 1

        for i in range(len(nums)):
            if i + 1 != nums[i]:
                return i + 1
        return len(nums) + 1
```

