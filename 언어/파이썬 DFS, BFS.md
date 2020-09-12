## 잡기술
```python
import sys
sys.setrecursionlimit(10**6)

graph = { 1: [2,3,4,5], 2: [3,4], 3: [], 4: [1], 5:[8], 8: []}
matrx = [[1,0,0,0,1,0], [1,1,1,1,1,0], [0,1,0,0,1,1], [1,1,0,0,0,1], [1,0,1,1,1,1], [1,1,1,0,0,1]]

# graph가 dictionary이고 return으로 
def DFS_g(startp, visited = []):
    visited.append(startp)
    for w in graph[startp]:
        if not w in visited:
            visited = DFS_g(w)
    return visited


def BFS_g(start):
    discovered = [start]
    queue_ = [start]
    while queue_:
        temp = queue_.pop(0)
        for w in graph[temp]:
            if not w in discovered:
                discovered.append(w)
                queue_.append(w)
    return discovered


def DFS_m(startp, visited, step):
    direction = [(0,1),(0,-1),(1,0),(-1,0)]
    visited[startp[0]][startp[1]] = step
    for t, tt in direction:
        if (0 <= startp[0] + t < len(matrx)) and (0 <= startp[1] + tt < len(matrx[0])): 
            if (matrx[startp[0]+t][startp[1]+tt] == 1) and (visited[startp[0]+t][startp[1]+tt] == 0):
                DFS_m([startp[0]+t, startp[1]+tt], visited, step+1)
    return visited



# print(list(DFS_g(1)))
# print(list(BFS_g(1)))
viss = [[0 for i in range(6)] for ii in range(6)]
print(list(DFS_m([0,0],viss , 1)))

for w in DFS_m([0,0],viss , 1):
    for ww in w:
        print(ww, end =" ")
    print()
```
