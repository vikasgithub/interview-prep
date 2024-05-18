## Graph Problems

### Print adjacency list of a graph

<details><summary>Solution</summary>

```python
def printGraph(self, V : int, edges : List[List[int]]) -> List[List[int]]:
        # code here
        adj_list = [[] for i in range(V)]
        
        for e in edges:
            adj_list[e[0]].append(e[1])
            adj_list[e[1]].append(e[0])
            
        return adj_list
```

</details>

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

### Find if there is a path between two vertices in a directed graph

<details><summary>Solution</summary>

```python
    # Use BFS to check path between s and d
def isReachable(self, s, d):
    # Mark all the vertices as not visited
    visited =[False]*(self.V)

    # Create a queue for BFS
    queue=[]

    # Mark the source node as visited and enqueue it
    queue.append(s)
    visited[s] = True

    while queue:

        #Dequeue a vertex from queue 
        n = queue.pop(0)
            
        # If this adjacent node is the destination node,
        # then return true
        if n == d:
                return True

        #  Else, continue to do BFS
        for i in self.graph[n]:
            if visited[i] == False:
                queue.append(i)
                visited[i] = True
        # If BFS is complete without visited d
    return False
```

</details>


