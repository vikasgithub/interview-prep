## BackTracking

### House Robber III

```python
class Solution:
    def rob(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0

        return max(self.robHelper(root))

    def robHelper(self, root):
        if not root:
            return 0, 0

        (wl, wol) = self.robHelper(root.left)
        (wr, wor) = self.robHelper(root.right)

        return root.val + wol + wor, max(wl, wol) + max(wr, wor)
```

### Restore IP Address

```python
class Solution:
    def restoreIpAddresses(self, s: str) -> List[str]:
        solutions = []

        self.backtrack(1, 0, s, solutions, [])
        return solutions

    def backtrack(self, addr_part, start, ip, solutions, curr_solution):
        if addr_part == 4 and len(ip) - start > 3:
            return
        if addr_part > 4:
            solutions.append(".".join(curr_solution))
            return

        curr_part = ""
        end = start + 3 if start + 3 < len(ip) else len(ip)
        for s in ip[start:end]:
            curr_part += s
            valid = self.is_valid(addr_part, curr_part, start, end, ip)
            curr_solution.append(curr_part)
            if valid:
                self.backtrack(addr_part + 1, start + len(curr_part), ip, solutions, curr_solution)
            curr_solution.pop()


    def is_valid(self, addr_part, curr_part, start, end, ip):
        if len(curr_part) > 1 and curr_part.startswith("0"):
            return False
        if addr_part == 4 and len(curr_part) < (end - start):
            return False
        if addr_part == 4 and len(curr_part) > 3:
            return False
        if int(curr_part) > 255:
            return False

        return True

        return True

```

### Flood fill

```python
class Solution:
    def floodFill(self, image: List[List[int]], sr: int, sc: int, color: int) -> List[List[int]]:
        if not image:
            return []

        coords = [(1, 0), (0, 1), (-1, 0), (0, -1)]
        visited = [[False] * len(image[0]) for i in range(len(image))]

        src_color = image[sr][sc]
        self.dfs(image, sr, sc, src_color, color, visited, coords)
        return image

    def dfs(self, image, sr, sc, src_color, color, visited, coords):
        if not visited[sr][sc]:
            visited[sr][sc] = True
            image[sr][sc] = color
            for c in coords:
                new_sr = sr + c[0]
                new_sc = sc + c[1]
                if self.is_valid(new_sr, new_sc, visited) and image[new_sr][new_sc] == src_color:
                    self.dfs(image, new_sr, new_sc, src_color, color, visited, coords)

    def is_valid(self, new_sr, new_sc, visited):
        if new_sr < 0 or new_sr >= len(visited):
            return False
        if new_sc < 0 or new_sc >= len(visited[0]):
            return False

        return not visited[new_sr][new_sc]
```