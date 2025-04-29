# EX 2B BACKTRACKING - NQUEEN PROBLEM
## DATE:29.04.25
## AIM:
To solve the N-Queen problem using backtracking, which places N queens on an N*N chessboard such that no two queens threaten each other.


## Algorithm
```

1. Initialize an empty board of size N x N.

2. Create a recursive function solve(row):
   a. If row == N:
      - Return the current board configuration as a valid solution.
   b. For each column in the current row:
      - Check if placing a queen at (row, col) is safe:
        - Ensure no queen exists in the same column.
        - Ensure no queen exists in the same diagonal (both main and anti-diagonal).
      - If safe, place the queen at (row, col) and recursively call solve(row + 1).
      - If no valid placement is found, backtrack:
        - Remove the queen from (row, col).

3. Initialize an empty board of size N x N.
4. Call solve(0) to start placing queens from the first row.
5. Return all valid board configurations.
```
## Program:
```
/*
Program to implement N-Queen problem using backtracking.
Developed by: srreja.v
Register Number:  212222230169
*/
global N
N = int(input())
 
def printSolution(board):
    for i in range(N):
        for j in range(N):
            print(board[i][j], end = " ")
        print()
 
def isSafe(board, row, col):
 
    # Check this row on left side
    for i in range(col):
        if board[row][i] == 1:
            return False
 
    # Check upper diagonal on left side
    for i, j in zip(range(row, -1, -1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False
 
    # Check lower diagonal on left side
    for i, j in zip(range(row, N, 1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False
 
    return True
 
def solveNQUtil(board, col):
     
    if col>=N:
        return True
    for i in range(N):
        if isSafe(board,i,col):
            board[i][col]=1
            if solveNQUtil(board,col+1)==True:
                return True
            board[i][col]=0
    return False
      
def solveNQ():
    board = [ [0, 0, 0, 0],
              [0, 0, 0, 0],
              [0, 0, 0, 0],
              [0, 0, 0, 0]]
              
    if solveNQUtil(board, 0) == False:
        print ("Solution does not exist")
        return False
 
    printSolution(board)
    return True
 
# Driver Code
solveNQ()

```

## Output:
![Screenshot 2025-04-29 135838](https://github.com/user-attachments/assets/b61db434-8cbe-4322-878b-b17078594eae)



## Result:
The N-Queens program executed successfully, and a valid board configuration was generated.
