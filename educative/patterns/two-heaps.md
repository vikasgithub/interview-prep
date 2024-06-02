## Two Heaps

### Maximize Capital
```python
class Solution:
    def findMaximizedCapital(self, k: int, w: int, profits: List[int], capital: List[int]) -> int:
        current_capital = w
        capital_min_heap = []
        profit_max_heap = []

        for i in range(len(capital)):
            heappush(capital_min_heap, (capital[i], i))

        while k > 0:
            while capital_min_heap and capital_min_heap[0][0] <= w:
                c, i = heappop(capital_min_heap)
                heappush(profit_max_heap, -profits[i])

            if not profit_max_heap:
                break

            p = -heappop(profit_max_heap)
            current_capital = current_capital + p
            w = current_capital
            k -= 1

        return current_capital
```

### Sliding Window Median

```java
public class Solution {
    public static void main(String[] args) {
        double[] vals = new Solution().medianSlidingWindow(new int[]{1, 4, 2, 3}, 4);
        System.out.println(Arrays.toString(vals));

    }

    public double[] medianSlidingWindow(int[] nums, int k) {
        PriorityQueue<Integer> minHeap = new PriorityQueue<>();
        PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());
        ArrayList<Double> results = new ArrayList<>();
        for (int i = 0; i < nums.length; i++) {
            if (i >= k) {
                removeValue(nums, k, i, minHeap, maxHeap);
            }

            addValue(maxHeap, minHeap, nums[i]);
            getMedian(minHeap, maxHeap, results, k);
        }

        double[] vals = new double[results.size()];
        int i = 0;
        for (Double val : results) {
            vals[i] = val;
            i++;
        }
        return vals;
    }

    private static void addValue(PriorityQueue<Integer> maxHeap, PriorityQueue<Integer> minHeap, int nums) {
        int value = nums;
        if (maxHeap.isEmpty() || maxHeap.peek() >= value) {
            maxHeap.offer(value);
        } else {
            minHeap.offer(value);
        }

        rebalance(maxHeap, minHeap);
    }

    private static void rebalance(PriorityQueue<Integer> maxHeap, PriorityQueue<Integer> minHeap) {
        while (maxHeap.size() - minHeap.size() > 1) {
            minHeap.offer(maxHeap.poll());
        }

        while (minHeap.size() - maxHeap.size() > 1) {
            maxHeap.offer(minHeap.poll());
        }
    }

    private static void removeValue(int[] nums, int k, int i, PriorityQueue<Integer> minHeap, PriorityQueue<Integer> maxHeap) {
        int e = nums[i - k];
        if (!minHeap.remove(e)) {
            maxHeap.remove(e);
        }
        rebalance(maxHeap, minHeap);
    }

    private static void getMedian(PriorityQueue<Integer> minHeap, PriorityQueue<Integer> maxHeap, ArrayList<Double> results, int k) {
        if (minHeap.size() + maxHeap.size() < k) {
            return;
        }
        if (minHeap.size() > maxHeap.size()) {
            results.add(Double.valueOf(minHeap.peek()));
        } else if (maxHeap.size() > minHeap.size()) {
            results.add(Double.valueOf(maxHeap.peek()));
        } else {
            double val = (minHeap.peek() / 2.0) + (maxHeap.peek() / 2.0);
            results.add(val);
        }
    }
}
```

### Schedule tasks on minimum machines
