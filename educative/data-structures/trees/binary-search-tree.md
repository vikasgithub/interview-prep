## Binary Search Tree

### Search Binary Search Tree

<details><summary>Solution</summary>

```python
# Utility function to search a key in a BST
def search(root, key):
    # Base Cases: root is null or key is present at root
    if root is None or root.key == key:
        return root

    # Key is greater than root's key
    if root.key < key:
        return search(root.right, key)

    # Key is smaller than root's key
    return search(root.left, key)
```
</details>

### Insert into a Binary Search Tree

<details><summary>Solution</summary>

```python
# Function to insert a new node with
# given key in BST
def insert(node, key):
    # If the tree is empty, return a new node
    if node is None:
        return Node(key)

    # Otherwise, recur down the tree
    if key < node.key:
        node.left = insert(node.left, key)
    elif key > node.key:
        node.right = insert(node.right, key)

    # Return the node pointer
    return node
```
</details>

### Deletion in a binary search tree

<details><summary>Solution</summary>

- Node is a leaf node: Assign node to null
- Node has one child: Replace the value of the node with's child value
- Node has two children
    - Find the min value in the right sub-tree
    - set the matched node value as the min value
    - delete the node with min value

```python
# Given a binary search tree and a key, this function deletes the key and returns the new root
    def deleteNode(self, root, key):
        # Base case
        if root is None:
            return root

        # If the key to be deleted is smaller than the root's key, then it lies in the left subtree
        if key < root.key:
            root.left = self.deleteNode(root.left, key)
        # If the key to be deleted is greater than the root's key, then it lies in the right subtree
        elif key > root.key:
            root.right = self.deleteNode(root.right, key)
        # If key is same as root's key, then this is the node to be deleted
        else:
            # Node with only one child or no child
            if root.left is None:
                return root.right
            elif root.right is None:
                return root.left

            # Node with two children: Get the inorder successor (smallest in the right subtree)
            root.key = self.minValue(root.right)

            # Delete the inorder successor
            root.right = self.deleteNode(root.right, root.key)

        return root

    def minValue(self, root):
        minv = root.key
        while root.left:
            minv = root.left.key
            root = root.left
        return minv

```

</details>

### BST traversals

#### Pre-Order traversal
- Visit node -> left subtree -> right subtree 

#### In-Order traversal
- Visit left subtree -> node -> right subtree 
- Gives the values of the nodes in the sorted order.
- To get the decreasing order, visit in right subtree -> node -> left subtree

```python
def printInorder(root):
    if root:
        # Traverse left subtree
        printInorder(root.left)
         
        # Visit node
        print(root.data,end=" ")
         
        # Traverse right subtree
        printInorder(root.right)
```

#### Post-Order traversal
- Visit left subtree -> right subtree -> node

