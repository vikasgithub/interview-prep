## Sorting Algorithms

### Selection Sort
- In every iteration, find the minimum element and place it in the beginning

```python
def selectionSort(self, arr,n):
    #code here
    for i in range(n):
        min_index = i
        for j in range(i, n):
            if arr[j] < arr[min_index]:
                min_index = j
        
        arr[i], arr[min_index] = arr[min_index], arr[i] 
```

### Bubble Sort
```python
def bubbleSort(arr):
    n = len(arr)
    
    # Traverse through all array elements
    for i in range(n):
        swapped = False

        # Last i elements are already in place
        for j in range(0, n-i-1):

            # Traverse the array from 0 to n-i-1
            # Swap if the element found is greater
            # than the next element
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
                swapped = True
        if (swapped == False):
            break
```

### Insertion Sort

```python
    #code here
    for i in range(1, len(arr)):

        key = arr[i]

        # Move elements of arr[0..i-1], that are
        # greater than key, to one position ahead
        # of their current position
        j = i-1
        while j >= 0 and key < arr[j] :
                arr[j + 1] = arr[j]
                j -= 1
        arr[j + 1] = key
```

### Merge Sort

```python

class Solution:
    def merge(self,arr, l, m, r): 
        # code here
        left = arr[l:m+1]
        right = arr[m+1:r + 1]
        i, j = 0, 0
        while i < len(left) and j < len(right):
            if left[i] <= right[j]:
                arr[l] = left[i]
                i += 1
            elif left[i] >= right[j]:
                arr[l] = right[j]
                j += 1
            l += 1
    
        while i < len(left):
            arr[l] = left[i]
            i += 1
            l += 1
    
        while j < len(right):
            arr[l] = right[j]
            j += 1
            l += 1
            
        
    def mergeSort(self,arr, l, r):
        # code here
        if l >= r:
            return

        m = l + (r - l) // 2
        self.mergeSort(arr, l, m)
        self.mergeSort(arr, m+1, r)
        self.merge(arr, l, m, r)
```


### Quicksort

```python
class Solution:
    #Function to sort a list using quick sort algorithm.
    def quickSort(self,arr,low,high):
        # code here
        if (low >= 0 and low < len(arr)) and (high >= 0 and high < len(arr)) and low < high:
            pivot = self.partition(arr, low, high)
            self.quickSort(arr, low, pivot - 1)
            self.quickSort(arr, pivot + 1, high)
    
    def partition(self,arr,low,high):
        # code here
        pivot = arr[low]
        
        i = low
        j = high
        
        while i < j:
            while i < len(arr) and arr[i] <= pivot:
                i += 1
                
            while j >= 0 and arr[j] > pivot:
                j -= 1
                
            if i < j:
                arr[i], arr[j] = arr[j], arr[i]
        
        arr[low], arr[j] = arr[j], arr[low]
        
        return j    
            
```