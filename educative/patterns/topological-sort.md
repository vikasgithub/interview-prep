## Topological Sort

### Topological Sort (using BFS)

```py
class Graph:
    def __init__(self, vertices):
        # Number of vertices
        self.V = vertices  
        # Dictionary to store adjacency lists
        self.adj = defaultdict(list)  

    def addEdge(self, u, v):
        # Function to add an edge to the graph
        self.adj[u].append(v)

    def topologicalSort(self):
        # Function to perform Topological Sort
        # Create a list to store in-degree of all vertices
        in_degree = [0] * self.V

        # Traverse adjacency lists to fill in_degree of vertices
        for i in range(self.V):
            for j in self.adj[i]:
                in_degree[j] += 1

        # Create a queue and enqueue all vertices with in-degree 0
        q = []
        for i in range(self.V):
            if in_degree[i] == 0:
                q.append(i)

        # Initialize count of visited vertices
        count = 0

        # Create a list to store topological order
        top_order = []

        # One by one dequeue vertices from queue and enqueue
        # adjacent vertices if in-degree of adjacent becomes 0
        while q:
            # Extract front of queue (or perform dequeue)
            # and add it to topological order
            u = q.pop(0)
            top_order.append(u)

            # Iterate through all its neighbouring nodes
            # of dequeued node u and decrease their in-degree
            # by 1
            for node in self.adj[u]:
                # If in-degree becomes zero, add it to queue
                in_degree[node] -= 1
                if in_degree[node] == 0:
                    q.append(node)

            count += 1

        # Check if there was a cycle
        if count != self.V:
            print("Graph contains cycle")
            return

        # Print topological order
        print("Topological Sort:", top_order)
```

### Topological Sort (using DFS)

```python
def topologicalSortUtil(v, adj, visited, stack):
    # Mark the current node as visited
    visited[v] = True

    # Recur for all adjacent vertices
    for i in adj[v]:
        if not visited[i]:
            topologicalSortUtil(i, adj, visited, stack)

    # Push current vertex to stack which stores the result
    stack.append(v)


# Function to perform Topological Sort
def topologicalSort(adj, V):
    # Stack to store the result
    stack = []

    visited = [False] * V

    # Call the recursive helper function to store
    # Topological Sort starting from all vertices one by
    # one
    for i in range(V):
        if not visited[i]:
            topologicalSortUtil(i, adj, visited, stack)

    # Print contents of stack
    print("Topological sorting of the graph:", end=" ")
    while stack:
```

### Course Schedule

- Using BFS

```py
class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        adj_list = [[] for i in range(numCourses)]

        for cl in prerequisites:
            c = cl[0]
            dep = cl[1]
            adj_list[dep].append(c)

        in_degree = [0] * numCourses

        for i in range(numCourses):
            for v in adj_list[i]:
                in_degree[v] = in_degree[v] + 1

        d = deque()

        for i in range(numCourses):
            if in_degree[i] == 0:
                d.appendleft(i)

        count = 0
        top_sort = []
        while d:
            v = d.pop()
            top_sort.append(v)

            for n in adj_list[v]:
                in_degree[n] = in_degree[n] - 1
                if in_degree[n] == 0:
                    d.appendleft(n)

            count += 1

        if count != numCourses:
            return False

        return True
```

- Using DFS

```py
class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        adj_list = [[] for i in range(numCourses)]

        for cl in prerequisites:
            c = cl[0]
            dep = cl[1]
            adj_list[dep].append(c)

        in_degree = [0] * numCourses

        for i in range(numCourses):
            for v in adj_list[i]:
                in_degree[v] = in_degree[v] + 1

        d = deque()

        for i in range(numCourses):
            if in_degree[i] == 0:
                d.appendleft(i)

        count = 0
        top_sort = []
        while d:
            v = d.pop()
            top_sort.append(v)

            for n in adj_list[v]:
                in_degree[n] = in_degree[n] - 1
                if in_degree[n] == 0:
                    d.appendleft(n)

            count += 1

        if count != numCourses:
            return False

        return True
```
