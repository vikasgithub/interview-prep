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

### Find the transitive closure of a Graph

<details><summary>Solution</summary>

```python
def transitiveClosure(self, N, graph):
    # code here
    tran_clo = [[0] * N for i in range(N)]
    adj_list = [[] * N for i in range(N)]
    for i in range(N):
        for j in range(N):
            if graph[i][j] == 1:
                adj_list[i].append(j)

    for i in range(N):
        visited = [False] * N
        visited_list = []
        self.dfs_util(adj_list, i, visited, tran_clo, visited_list)
        for j in visited_list:
            tran_clo[i][j] = 1

    return tran_clo

def dfs_util(self, adj_list, source, visited, tran_clo, visited_list):
    visited[source] = True
    visited_list.append(source)
    for i in adj_list[source]:
        if not visited[i]:
            self.dfs_util(adj_list, i, visited, tran_clo, visited_list)
```

</details>

### Find the number of islands

<details><summary>Solution</summary>

```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        row = [0, 1, 0,  -1]
        col = [1, 0,  -1, 0]

        islands = 0

        visited = [[False] * len(grid[0]) for i in range(len(grid))]
        for i in range(len(grid)):
            for j in range(len(grid[0])):
                if not visited[i][j] and grid[i][j] == "1":
                    self.dfs(grid, i, j, visited, row, col)
                    islands += 1

        return islands
    
    def dfs(self, grid, i, j, visited, row, col):
        visited[i][j] = True

        for k in range(len(row)):
            x = i + row[k]
            y = j + col[k]
            if self.is_safe(x, y, visited, grid):
                self.dfs(grid, x, y, visited, row, col)

    def is_safe(self, x, y, visited, grid):
        return x >= 0 and x < len(grid) and y >= 0 and y < len(grid[0]) and not visited[x][y] and grid[x][y] == "1"
```

</details>

### Detect cycle in an undirected graph

<details><summary>Solution</summary>

```python

class Solution:
    #Function to detect cycle in an undirected graph.
	def isCycle(self, V: int, adj: List[List[int]]) -> bool:
		visited = [False] * V
		
		for i in range(len(adj)):
		    if not visited[i]:
		        if self.dfs(i, -1, adj, visited):
    		        return True
		            
		return False
		
    def dfs(self, node, parent, adj, visited):
        visited[node] = True
        
        for nbr in adj[node]:
            if not visited[nbr]:
                if self.dfs(nbr, node, adj, visited):
                    return True
            # If an adjacent vertex is
            # visited and not parent
            # of current vertex,
            # then there is a cycle
            elif nbr != parent:
                return True
                
        return False

```

</details>

### Detect cycle in a directed graph

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

### Pre-requisite tasks

<details><summary>Solution</summary>

```python
```

</details>