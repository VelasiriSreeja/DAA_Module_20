# EX 2A BACKTRACKING - RAT IN MAZE PROBLEM
## DATE:29.04.25
## AIM:
To implement the Rat in a Maze problem using backtracking and find all possible paths from the start to the destination in a given maze.


## Algorithm
```
1. If maze[0][0] == 0 or maze[N-1][N-1] == 0, return "No path".
2. Create a recursive function solve(x, y, path):
   a. If x == N-1 and y == N-1:
      - Add path to result list.
      - Return.
   b. Mark (x, y) as visited.
   c. For each direction (D, L, R, U):
      - Compute next cell (nx, ny).
      - If (nx, ny) is within bounds, not visited, and maze[nx][ny] == 1:
         - Call solve(nx, ny, path + direction).
   d. Unmark (x, y) as visited (backtrack).

3. Initialize visited[N][N] as false.
4. Call solve(0, 0, "").
5. Return all paths found.
```
## Program:
```
/*
Program to implement Rat in a Maze.
Developed by: sreeja.v
Register Number: 212222230169
*/
N = 4
 
def printSolution( sol ):
     
    for i in sol:
        for j in i:
            print(str(j) + " ", end ="")
        print("")
 

def isSafe( maze, x, y ):
     
    if x >= 0 and x < N and y >= 0 and y < N and maze[x][y] == 1:
        return True
     
    return False
 

def solveMaze( maze ):
     
    # Creating a 4 * 4 2-D list
    sol = [ [ 0 for j in range(4) ] for i in range(4) ]
     
    if solveMazeUtil(maze, 0, 0, sol) == False:
        print("Solution doesn't exist");
        return False
     
    printSolution(sol)
    return True
     

def solveMazeUtil(maze, x, y, sol):
    if x == N-1 and y == N-1:
        sol[x][y]=1
        return True
    if isSafe(maze,x,y)==True:
        sol[x][y]=1
        if solveMazeUtil(maze,x+1,y,sol):
            return True
        if solveMazeUtil(maze,x,y+1,sol):
            return True
        sol[x][y]=0
        return False
    return False
 


if __name__ == "__main__":
    # Initialising the maze
    maze = [ [1, 0, 0, 0],
             [1, 1, 0, 1],
             [0, 1, 0, 0],
             [1, 1, 1, 1] ]
              
    solveMaze(maze)


```

## Output:
![Screenshot 2025-04-29 135608](https://github.com/user-attachments/assets/49adb04d-767c-48b3-b515-28052653e501)



## Result:
The Rat in a Maze program executed successfully, and a valid path from the start to the destination was found and display.
