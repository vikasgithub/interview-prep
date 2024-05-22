## Heap Problems

### Is Binary Tree a Heap

```python
class Solution:
    #Your Function Should return True/False
    def isHeap(self, root):
        #Code Here
        heap_size = self.count_nodes(root)
        return self.is_complete(root, 0, heap_size) and self.meets_heap_property(root, heap_size)
        
    
    def is_complete(self, root, index, heap_size):
        if root is None:
            return True
            
        if index >= heap_size:
            return False
            
        return self.is_complete(root.left, 2 * index + 1, heap_size) and self.is_complete(root.right, 2 * index + 2, heap_size)
        
    
    def meets_heap_property(self, root, heap_size):
        if root is None:
            return True
            
        if root.left is not None and root.data < root.left.data:
            return False
            
        if root.right is not None and root.data < root.right.data:
            return False
        
        return self.meets_heap_property(root.left, heap_size) and self.meets_heap_property(root.right, heap_size)
        
    
    def count_nodes(self, root):
        if root is None:
            return 0
        
        return 1 + self.count_nodes(root.left) + self.count_nodes(root.right)
```