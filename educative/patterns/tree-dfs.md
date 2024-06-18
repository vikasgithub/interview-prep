## Tree DFS

### Flatten Binary Tree to Linked List

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def flatten(self, root: Optional[TreeNode]) -> None:
        """
        Do not return anything, modify root in-place instead.
        """
        if not root:
            return None

        self.dfs(root)

    def dfs(self, root: Optional[TreeNode]) -> TreeNode:

        tail_left = None
        if root.left:
            tail_left = self.dfs(root.left)

        tail_right = None
        if root.right:
            tail_right = self.dfs(root.right)

        if root.left:
            tail_left.right = root.right
            root.right = root.left
            root.left = None

        return tail_right or tail_left or root
```

### Diameter of a binary tree

```python
class Solution:
    def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0

        diameter = 0
        if root.left:
            diameter = 1 + self.height(root.left)

        if root.right:
            diameter += 1 + self.height(root.right)

        return diameter

    def height(self, root):
        if not root:
            return 0

        if not root.left and not root.right:
            return 0

        return 1 + max(self.height(root.left), self.height(root.right))
```

### Invert Binary Tree

```python
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if not root:
            return None
        temp = root.right
        root.right = root.left
        root.left = temp

        if root.left:
            self.invertTree(root.left)
        if root.right:
            self.invertTree(root.right)
```

### Binary tree maximum path sum
```python
class Solution:
    def maxPathSum(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0

        left_sum = self.maxPathSum(root.left)
        right_sum = self.maxPathSum(root.right)

        return max(root.val, root.val + left_sum + right_sum,  root.val + right_sum,  root.val + left_sum)
```

###  Convert Sorted Array to Binary Search Tree

```python
class Solution:
    def sortedArrayToBST(self, nums: List[int]) -> Optional[TreeNode]:
        if not nums:
            return None

        mid = (len(nums)) // 2
        root = TreeNode(nums[mid])
        root.left = self.sortedArrayToBST(nums[0:mid])
        root.right = self.sortedArrayToBST(nums[mid+1:len(nums)])

        return root
```

### Build Binary Tree from Preorder and Inorder Traversal

```python
class Solution:

    def __init__(self):
        self.preIndex = 0

    def buildTree(self, preorder: List[int], inorder: List[int]) -> Optional[TreeNode]:
        return self.buildTreeHelper(preorder, inorder, 0, len(preorder))

    def buildTreeHelper(self, preorder: List[int], inorder: List[int], start, end) -> Optional[TreeNode]:

        if start > end or self.preIndex == len(preorder):
            return None

        root = TreeNode(preorder[self.preIndex])
        self.preIndex += 1
        if start == end:
            return root

        inorder_pos = inorder.index(root.val, start, end + 1)
        root.left = self.buildTreeHelper(preorder, inorder, start, inorder_pos - 1)
        root.right = self.buildTreeHelper(preorder, inorder, inorder_pos + 1, end)

        return root        
```

### Build the right side of the tree
```python
class Solution:

    def __init__(self):
        self.curr_length = 0

    def rightSideView(self, root: Optional[TreeNode]) -> List[int]:
        items = []
        self.rightSideViewHelper(root, items, 0)
        return items

    def rightSideViewHelper(self, root: Optional[TreeNode], items, level):
        if not root:
            return

        if self.curr_length <= level:
            items.append(root.val)
            self.curr_length += 1

        if root.right:
            self.rightSideViewHelper(root.right, items, level + 1)

        if root.left:
            self.rightSideViewHelper(root.left, items, level + 1)
```

### Lowest common ancestor of a binary tree

```python

class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        if not root:
            return None

        if root.val == p.val or root.val == q.val:
            return root

        left = self.lowestCommonAncestor(root.left, p, q)
        right = self.lowestCommonAncestor(root.right, p, q)

        if left and right:
            return root

        return left or right
```

### Is Valid BST

```python
class Solution:
    def isValidBST(self, root: Optional[TreeNode]) -> bool:
        return self.isValidBSTHelper(root, -math.inf, math.inf)

    def isValidBSTHelper(self, root, min, max):
        if root is None:
            return True

        return min < root.val < max and self.isValidBSTHelper(root.left, min, root.val) and self.isValidBSTHelper(root.right, root.val, max)
```

### Maximum Depth of binary tree

```python
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0

        return 1 + max(self.maxDepth(root.left), self.maxDepth(root.right))
```



