# EX 2D BACKTRACKING - GRAPH COLORING PROBLEM
## DATE:29.04.25
## AIM:
To solve the Graph Coloring Problem using backtracking, assigning colors to the vertices of a graph such that no two adjacent vertices share the same color while minimizing the number of colors used.
## Algorithm:
```
1. Define a recursive function `graphColoring(graph, V, m, color, v)`:
   a. If v == V (all vertices are colored):
      - Return True (all vertices are successfully colored).
   b. For each color from 1 to m:
      - Check if coloring vertex `v` with color `c` is safe:
        - Ensure no adjacent vertex has the same color.
      - If safe, assign color `c` to vertex `v` and recursively call `graphColoring(graph, V, m, color, v + 1)`.
      - If no valid color assignment is found, backtrack:
        - Unassign color `c` from vertex `v`.

2. Initialize an empty color array `color[]` of size `V`, with all elements initially set to 0 (indicating no color).
3. Call `graphColoring(graph, V, m, color, 0)` to start coloring from the first vertex.
4. Return True if a valid coloring is found, otherwise False.
```
## Program:
```
/*
Program to implement Graph Coloring Problem using backtracking.
Developed by: sreeja.v
Register Number: 212222230169
*/
class Graph:
    def __init__(self,vertices):
        self.V=vertices
        self.graph=[[0 for row in range(vertices)] for column in range(vertices)]
        
    def isSafe(self,v,colour,c):
        for i in range(v):
            if self.graph[v][i]==1 and colour[i]==c:
                return False
        return True
        
    def graphColourUtil(self,m,colour,v):
        if v==self.V:
            return True 
        for i in range(1,m+1):
            if self.isSafe(v,colour,i):
                colour[v]=i
                if self.graphColourUtil(m,colour,v+1):
                    return True
        return False
        
    def graphColouring(self,m):
        colour=[0]*self.V
        if not self.graphColourUtil(m,colour,0):
            print("No solution Exist")
            return False
        print("Solution exist and Following are the assigned colours:")
        
        for c in colour:
            print(c,end=' ')
        print()
        return True

```

## Output:
![Screenshot 2025-04-29 140301](https://github.com/user-attachments/assets/34922abb-fc61-44f8-bf76-93b7c2c4bd6d)



## Result:
The Graph Coloring program executed successfully, and the colors were assigned to the vertices such that no two adjacent vertices share the same color.
