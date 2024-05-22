### Backtracking

### Subsets

```python
    class Solution:
        def subsets(self, a):
            #code here
            subsets = []
            current_solution = []
            self.subsets_helper(a, 0, subsets, current_solution)
            return subsets

        def subsets_helper(self, a, start, subsets, current_solution):
            if start == len(a):
                subsets.add(current_solution)
                return

            self.subsets_helper(a, start + 1, subsets, current_solution + [a[start]])
            self.subsets_helper(a, start + 1, subsets, current_solution)
```

### Permutations

```python
class Solution:
    def find_permutation(self, S):
        # Code here
        solutions = set()
        self.find_helper(S, solutions, "")
        return list(solutions)

    def find_helper(self, S, solutions, curr_str):
        if len(S) == 0:
            solutions.add(curr_str)
            return

        for i, c in enumerate(S):
            rest_string = S[0:i] + S[i + 1:]
            self.find_helper(rest_string, solutions, curr_str + c)
```

### N Queens

```python
class Solution:
    def nQueen(self, n):
        # code here
        board = [[False] * n for i in range(n)]
        solutions = []
        self.nQueenHelper(n, 0, board, solutions, [])
        results = []
        for sol in solutions:
            result = []
            for i in sol:
                print(f" i = {i}")
                result.append("".join(["Q" if j == i else "." for j in range(n)]))
            results.append(result)
        return results

    def nQueenHelper(self, n, row, board, solutions, curr_solution):
        if row == n:
            solutions.append(curr_solution)
            return

        for i in range(n):
            if self.is_safe(board, row, i):
                if row == 0:
                    curr_solution = []

                curr_solution.append(i)
                board[row][i] = True
                # self.print_board(board)
                self.nQueenHelper(n, row + 1, board, solutions, curr_solution)
                board[row][i] = False

    def is_safe(self, board, row, col):
        # print(f"checking safe for {row} and {col}")
        if row > 0:
            for i in range(col):
                if board[row][i]:
                    return False

            for i in range(row):
                if board[i][col]:
                    return False

            # upper left column
            temprow = row - 1
            tempcol = col - 1
            while temprow >= 0 and tempcol >= 0:
                if board[temprow][tempcol]:
                    return False
                temprow = temprow - 1
                tempcol = tempcol - 1

            temprow = row - 1
            tempcol = col + 1
            while temprow >= 0 and tempcol < len(board):
                if board[temprow][tempcol]:
                    return False
                temprow = temprow - 1
                tempcol = tempcol + 1

        return True

    def print_board(self, board):
        print("===============")
        for i in range(len(board)):
            row = []
            for j in range(len(board[0])):
                if board[i][j]:
                    row.append("1")
                else:
                    row.append("0")
            print(" ".join(row))
        print("===============")

#{
# Driver Code Starts
#Initial Template for Python 3

print(Solution().nQueen(4))
```