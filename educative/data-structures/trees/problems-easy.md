## Tree problems

### Find minimum in a binary tree

<details><summary>Solution</summary>

```python
def find_min(root):
    if root is None:
        return None
        
    current = root
    while current.leftChild is not None:
        current = current.leftChild

    # Replace this placeholder return statement with your code
    return current.val
```

</details>

### Search binary search tree in a iterative way

<details><summary>Solution</summary>

```python
def iterativeSearch(root, key):
     
    # Traverse until root reaches 
    # to dead end 
    while root != None:
         
        # pass right subtree as new tree 
        if key > root.data: 
            root = root.right
 
        # pass left subtree as new tree
        elif key < root.data:
            root = root.left 
        else:
            return True # if the key is found return 1 
    return False
```

</details>

### Check if binary tree is a valid BST

<details><summary>Solution</summary>

```python
    def checkBST(self, root, min_val, max_val):
        if root is None:
            return True
        
        if root.data > max_val or root.data < min_val:
            return False
        
        return self.checkBST(root.left, min_val, root.data - 1) and self.checkBST(root.right, root.data + 1, max_val)

    
    #Function to check whether a Binary Tree is BST or not.
    def isBST(self, root):
        min_val = -sys.maxsize - 1
        max_val = sys.maxsize
        #code here
        return self.checkBST(root, min_val, max_val)
```

</details>

### Convert a binary tree to a BST

<details><summary>Solution</summary>

- Perform in-order traversal and 

```python
    def binaryTreeToBST(self, root):
        tree_data = []
        self.get_data(root, tree_data)
        tree_data.sort()
        tree_data.reverse()
        self.update_tree(root, tree_data)
        
    
    def update_tree(self, root, tree_data):
        if root is None:
            return
        self.update_tree(root.left, tree_data)
        root.data = tree_data.pop()
        self.update_tree(root.right, tree_data)
        

    def get_data(self, root, tree_data):
        if root is None:
            return
        self.get_data(root.left, tree_data)
        tree_data.append(root.data)
        self.get_data(root.right, tree_data)
```

</details>

### Find the node with minimum value in a Binary Search Tree


<details><summary>Solution</summary>

- Run the in-order traversal and return the first value 

```python
def minValue(self, root):
    if root is None:
        return 0
        
    ##Your code here
    curr = root
    while curr is not None:
        min_val = curr.data
        curr = curr.left
        
    return min_val
```
</details>

### Check if an array represents Inorder of Binary Search tree or not

<details><summary>Solution</summary>

The idea is to use the fact that the inorder traversal of Binary Search Tree is sorted. So, just check if given array is sorted or not. 

</details>

### How to determine if a binary tree is height-balanced?

<details><summary>Solution</summary>

```python
def height(self, root):
    if root is None:
        return 0
    return 1 + max(self.height(root.left), self.height(root.right))
            
def isBalanced(self,root):
    if root is None:
        return True
    
    lh = self.height(root.left)
    rh = self.height(root.right)
    
    return abs(lh - rh) <= 1 and self.isBalanced(root.left) and self.isBalanced(root.right)
```

</details>

### Convert sorted array to BST

<details><summary>Solution</summary>

```python
def sortedArrayToBST(arr):
    if not arr:
        return None
 
    # find middle index
    mid = (len(arr)) // 2
 
    # make the middle element the root
    root = Node(arr[mid])
 
    # left subtree of root has all
    # values <arr[mid]
    root.left = sortedArrayToBST(arr[:mid])
 
    # right subtree of root has all
    # values >arr[mid]
    root.right = sortedArrayToBST(arr[mid+1:])
    return root
```
</details>
