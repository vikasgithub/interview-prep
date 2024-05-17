## Bread First Search

### Basic Algorithm
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

### Find the level of a given node

<details><summary>Solution</summary>

```python
#Function to find the level of node X.
def nodeLevel(self, V, adj, X):
    # code here
    q = deque()
    level = [0] * V
    visited = [False] * V
    q.append(0)
    
    level = 0
    while q:
        sz = len(q)
        level = level + 1
        while sz > 0:
            sz -= 1
            node = q.popleft()
            visited[node] = True
            
            adj_nodes = adj[node]
            for an in adj_nodes:
                if not visited[an]:
                    if an == X:
                        return level
                    q.append(an)
                
    return -1
```
</details>