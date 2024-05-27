## Sliding Window

### Find Repeated Sequence

```python
def find_repeated_sequences(s, k):
    start = 0
    sequences = {}

    while start <= len(s) - k:
        end = start + k
        curr_seq = s[start:start+k]
        curr_seq_count = sequences.get(curr_seq, 0) + 1
        sequences[curr_seq] = curr_seq_count
        start += 1

    return [k for k,v in sequences.items() if v > 1]
```

### Find maximum in a sliding window

<details><summary>Solution</summary>

```python
class Solution:
    def maxSlidingWindow(self, nums: List[int], w: int) -> List[int]:
        result = []
        
        dq = deque()
        for i in range(w):
            while dq and nums[dq[-1]] <= nums[i]:
                dq.pop()
            dq.append(i)
        result.append(nums[dq[0]])
        
        end = w
        start = 1
        while end < len(nums):
            while dq and dq[0] < start:
                dq.popleft()

            while dq and nums[dq[-1]] <= nums[end]:
                dq.pop()

            dq.append(end)
            result.append(nums[dq[0]])
            end += 1
            start += 1

        return result
```

</details>

### Length of longest substring without repeating character

<details><summary>Solution</summary>

```python
    def lengthOfLongestSubstring(self, input_str: str) -> int:
        index_map = {}

        longest = 0
        start = 0
        end = 0
        while end < len(input_str):
            curr_char = input_str[end]
            if curr_char in index_map:
                curr_char_index = index_map[curr_char]
                if curr_char_index >= start:
                    start = curr_char_index + 1

            index_map[curr_char] = end
            window = end - start + 1
            if window > longest:
                longest = window
            end += 1

        return longest
```

</details>

### Longest repeating string replacement

<details><summary>Solution</summary>

```python
def longest_repeating_character_replacement(s, k):
    string_length = len(s)
    length_of_max_substring = 0
    start = 0
    char_freq = {}
    most_freq_char = 0

    for end in range(string_length):
        if s[end] not in char_freq:
            char_freq[s[end]] = 1
        else:
            char_freq[s[end]] += 1

        most_freq_char = max(most_freq_char, char_freq[s[end]])

        if end - start + 1 - most_freq_char > k:
            char_freq[s[start]] -= 1
            start += 1
        
        length_of_max_substring = max(end - start + 1, length_of_max_substring)
        
    return length_of_max_substring
```

</details>

### Minimum subarray sun

<details><summary>Solution</summary>

```python
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        # Replace this placeholder return statement with your code
        start = 0
        end = 0

        min_len = len(nums) + 1
        sum = 0
        while end < len(nums):
            sum += nums[end]

            while sum >= target:
                min_len = min(min_len, end - start + 1)
                sum -= nums[start]
                start += 1
                
            end += 1
            
        if min_len > len(nums):
            return 0
        return min_len
```

</details>

### Best time to buy or sell stock

<details><summary>Solution</summary>

```python
def max_profit(prices):

    # Replace this placeholder return statement with your code
    max_profit = 0

    min_price = prices[0]

    for p in prices:
        min_price = min(min_price, p)
        max_profit = max(max_profit, p - min_price)

    return max_profit
```

</details>
