# EX 2C BACKTRACKING- SUBSET SUM PROBLEM
## DATE:29.04.25
## AIM:
To demonstrate that the sum of the subset of a given set is equal to the given sum.


## Algorithm
```
1. Define a recursive function `isSubsetSum(arr, n, sum)`:
   a. If sum == 0:
      - Return True (empty subset or sum 0 is possible).
   b. If n == 0 (no elements left in the set):
      - Return False (no subset can sum to the target).
   c. If arr[n-1] > sum:
      - Skip the current element and recursively call `isSubsetSum(arr, n-1, sum)`.
   d. Else:
      - Return True if either:
        - Include arr[n-1] and call `isSubsetSum(arr, n-1, sum-arr[n-1])`.
        - Exclude arr[n-1] and call `isSubsetSum(arr, n-1, sum)`.

2. Initialize the function call `isSubsetSum(arr, len(arr), sum)`.

3. Return the result (True if a subset sum is found, False otherwise).
 ```  

## Program:
```
/*
Program to implement Subset sum problem.
Developed by: sreeja.v
Register Number: 212222230169 
*/
def SubsetSum(a,i,sum,target,n):
    if i==n:
        return sum==target
    if SubsetSum(a,i+1,sum+a[i],target,n):
        return True
    if SubsetSum(a,i+1,sum,target,n): 
        return True
    return False

a=[]
size=int(input())
for i in range(size):
    x=int(input())
    a.append(x)

target=int(input())
n=len(a)
if(SubsetSum(a,0,0,target,n)==True):
    for i in range(size):
        print(a[i])
    print("True,subset found")
else:
    for i in range(size):
        print(a[i])
    print("False,subset not found")


```

## Output:
![Screenshot 2025-04-29 140058](https://github.com/user-attachments/assets/729efbc2-7b19-49cd-8b38-2248549eb079)



## Result:
The Subset Sum program executed successfully, and the result was determined based on whether a subset matching the target sum was found or not.
