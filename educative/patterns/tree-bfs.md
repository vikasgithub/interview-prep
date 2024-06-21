## Tree Breadth First Search

### Level Order Traversal of Binary Tree
```python
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root:
            return []

        q = deque()
        q.appendleft(root)

        result = []
        while q:
            curr_len = len(q)

            curr_level = []
            while curr_len > 0:
                curr = q.pop()
                curr_level.append(curr.val)
                if curr.left:
                    q.appendleft(curr.left)
                if curr.right:
                    q.appendleft(curr.right)
                curr_len -= 1

            result.append(curr_level)

        return result
```

### Binary Tree Zigzag Level Order Traversal

```python
class Solution:
    def zigzagLevelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root:
            return []

        q = deque()
        q.appendleft(root)

        result = []
        reverse = True
        while q:
            curr_len = len(q)

            curr_level = []
            while curr_len > 0:
                if reverse:
                    curr = q.pop()
                    curr_level.append(curr.val)
                    if curr.left:
                        q.appendleft(curr.left)
                    if curr.right:
                        q.appendleft(curr.right)
                else:
                    curr = q.popleft()
                    curr_level.append(curr.val)
                    if curr.right:
                        q.append(curr.right)
                    if curr.left:
                        q.append(curr.left)

                curr_len -= 1

            reverse = not reverse
            result.append(curr_level)

        return result
```

### Symmetric Tree

```py
def is_symmetric(root):
  queue = []
  queue.append(root.left)
  queue.append(root.right)

  while queue:
    left = queue.pop(0)
    right = queue.pop(0)

    if not left and not right:
      continue

    if not left or not right:
      return False

    if left.data != right.data:
      return False

    queue.append(left.left)
    queue.append(right.right)
    queue.append(left.right)
    queue.append(right.left)
  
  return True
```
