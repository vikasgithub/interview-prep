## Graph Algorithms

### Bread First Search

<details><summary>Solution</summary>

```python
# Function to perform Breadth First Search on a graph
# represented using adjacency list
def bfs(adjList, startNode, visited):
    # Create a queue for BFS
    q = deque()

    # Mark the current node as visited and enqueue it
    visited[startNode] = True
    q.append(startNode)

    # Iterate over the queue
    while q:
        # Dequeue a vertex from queue and print it
        currentNode = q.popleft()
        print(currentNode, end=" ")

        # Get all adjacent vertices of the dequeued vertex
        # If an adjacent has not been visited, then mark it visited and enqueue it
        for neighbor in adjList[currentNode]:
            if not visited[neighbor]:
                visited[neighbor] = True
                q.append(neighbor)
```

</details>

### Breadth First Traversal ( BFS ) on a 2D array

<details><summary>Solution</summary>

```python
# Direction vectors
dRow = [ -1, 0, 1, 0]
dCol = [ 0, 1, 0, -1]
 
# Function to check if a cell
# is be visited or not
def isValid(vis, row, col):
   
    # If cell lies out of bounds
    if (row < 0 or col < 0 or row >= 4 or col >= 4):
        return False
 
    # If cell is already visited
    if (vis[row][col]):
        return False
 
    # Otherwise
    return True
 
# Function to perform the BFS traversal
def BFS(grid, vis, row, col):
   
    # Stores indices of the matrix cells
    q = queue()
 
    # Mark the starting cell as visited
    # and push it into the queue
    q.append(( row, col ))
    vis[row][col] = True
 
    # Iterate while the queue
    # is not empty
    while (len(q) > 0):
        cell = q.popleft()
        x = cell[0]
        y = cell[1]
        print(grid[x][y], end = " ")
 
 
        # Go to the adjacent cells
        for i in range(4):
            adjx = x + dRow[i]
            adjy = y + dCol[i]
            if (isValid(vis, adjx, adjy)):
                q.append((adjx, adjy))
                vis[adjx][adjy] = True
```

</details>

### Depth First Traversal

<details><summary>Solution</summary>

```python
# A function used by DFS
def DFSUtil(self, v, visited):

    # Mark the current node as visited
    # and print it
    visited.add(v)
    print(v, end=' ')

    # Recur for all the vertices
    # adjacent to this vertex
    for neighbour in self.graph[v]:
        if neighbour not in visited:
            self.DFSUtil(neighbour, visited)

    
# The function to do DFS traversal. It uses
# recursive DFSUtil()
def DFS(self, v):

    # Create a set to store visited vertices
    visited = set()

    # Call the recursive helper function
    # to print DFS traversal
    self.DFSUtil(v, visited)
```

</details>

### Iterative Depth First Traversal 

<details><summary>Solution</summary>

```python
def DFS(self,s):            # prints all vertices in DFS manner from a given source.
                            # Initially mark all vertices as not visited 
    visited = [False for i in range(self.V)] 

    # Create a stack for DFS 
    stack = []

    # Push the current source node. 
    stack.append(s) 

    while (len(stack)): 
        # Pop a vertex from stack and print it 
        s = stack.pop()

        # Stack may contain same vertex twice. So 
        # we need to print the popped item only 
        # if it is not visited. 
        if (not visited[s]): 
            print(s,end=' ')
            visited[s] = True

        # Get all adjacent vertices of the popped vertex s 
        # If a adjacent has not been visited, then push it 
        # to the stack. 
        for node in self.adj[s]: 
            if (not visited[node]): 
                stack.append(node) 
```

</details>

### Detect Cycle in an undirected graph

<details><summary>Solution</summary>

```python
    def isCyclicUtil(self, v, visited, parent):
 
        # Mark the current node as visited
        visited[v] = True
 
        # Recur for all the vertices
        # adjacent to this vertex
        for i in self.graph[v]:
 
            # If the node is not
            # visited then recurse on it
            if visited[i] == False:
                if(self.isCyclicUtil(i, visited, v)):
                    return True
            # If an adjacent vertex is
            # visited and not parent
            # of current vertex,
            # then there is a cycle
            elif parent != i:
                return True
 
        return False
 
    # Returns true if the graph
    # contains a cycle, else false.
 
    def isCyclic(self):
 
        # Mark all the vertices
        # as not visited
        visited = [False]*(self.V)
 
        # Call the recursive helper
        # function to detect cycle in different
        # DFS trees
        for i in range(self.V):
 
            # Don't recur for u if it
            # is already visited
            if visited[i] == False:
                if(self.isCyclicUtil
                   (i, visited, -1)) == True:
                    return True
 
        return False
```

</details>

### Detect Cycle in a directed graph

<details><summary>Solution</summary>

```python
def isCyclicUtil(self, v, visited, recStack):
    # Mark current node as visited and
    # adds to recursion stack
    visited[v] = True
    recStack[v] = True

    # Recur for all neighbours
    # if any neighbour is visited and in
    # recStack then graph is cyclic
    for neighbour in self.graph[v]:
        if visited[neighbour] == False:
            if self.isCyclicUtil(neighbour, visited, recStack) == True:
                return True
        elif recStack[neighbour] == True:
            return True

    # The node needs to be popped from
    # recursion stack before function ends
    recStack[v] = False
    return False

# Returns true if graph is cyclic else false
def isCyclic(self):
    visited = [False] * (self.V + 1)
    recStack = [False] * (self.V + 1)
    for node in range(self.V):
        if visited[node] == False:
            if self.isCyclicUtil(node, visited, recStack) == True:
                return True
    return False
```

</details>

### Print pre and post visit times for a node

<details><summary>Solution</summary>

```python
# Variable to keep track of time 
time = 1
 
# Function to perform DFS starting 
# from node u 
def dfs(u, aList, pre, post, vis):
     
    global time
     
    # Storing the pre number whenever 
    # the node comes into recursion stack 
    pre[u] = time
 
    # Increment time 
    time += 1
     
    vis[u] = 1
     
    for v in aList[u]:
        if (vis[v] == 0):
            dfs(v, aList, pre, post, vis)
             
    # Storing the post number whenever 
    # the node goes out of recursion stack 
    post[u] = time
    time += 1
```

</details>