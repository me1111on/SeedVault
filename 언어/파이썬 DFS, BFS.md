## 잡기술
```python
import sys
sys.setrecursionlimit(10**6)

graph = { 1: [2,3,4,5], 2: [3,4], 3: [], 4: [1], 5:[8], 8: []}
matrx = [[1,0,0,0,1,0], [1,1,1,1,1,0], [0,1,0,0,1,1], [1,1,0,0,0,1], [1,0,1,1,1,1], [1,1,1,0,0,1]]
visited = [[0,0,0,0,0,0], [0,0,0,0,0,0], [0,0,0,0,0,0], [0,0,0,0,0,0], [0,0,0,0,0,0], [0,0,0,0,0,0]]

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


# 지나간 행적을 return
def DFS_m(startp, visited, step):
    #방향에 따라, 더 추가 가능
    direction = [(0,1),(0,-1),(1,0),(-1,0)]
    visited[startp[0]][startp[1]] = step
    
    for t, tt in direction:
        #boundry 검사
        if (0 <= startp[0] + t < len(matrx)) and (0 <= startp[1] + tt < len(matrx[0])): 
            #조건이 맞으면 해당 위치에서 dfs 재귀실행, 조건 변경은 여기서
            if (matrx[startp[0]+t][startp[1]+tt] == 1) and (visited[startp[0]+t][startp[1]+tt] == 0):

                #도착조건은 여기서 확인해야함. 아니면 다른 갈림길에서 또 계속 탐색함. 
                if [startp[0]+t, startp[1]+tt] == [2,4]:
                    visited[startp[0]+t][startp[1]+tt] = step+1
                    return visited
                    break
                DFS_m([startp[0]+t, startp[1]+tt], visited, step+1)
    
    return visited


# 지나간 행적을 return
def BFS_m(startp, visited, step):
    #방향에 따라, 더 추가 가능
    direction = [(0,1),(0,-1),(1,0),(-1,0)]
    
    qu_ = [[startp[0], startp[1], 1]]
    while qu_:
        tp = qu_.pop(0)
        
        #도착확인
        if tp[0] == 2 and tp[1] == 4:
            break
        
        visited[tp[0]][tp[1]] = tp[2]

        for t,tt in direction:
            if (0 <= tp[0] + t < len(matrx)) and (0 <= tp[1] + tt < len(matrx[0])): 
                #조건이 맞으면 해당 위치에서 dfs 재귀실행, 조건 변경은 여기서
                if (matrx[tp[0]+t][tp[1]+tt] == 1) and (visited[tp[0]+t][tp[1]+tt] == 0):
                #if (matrx[tp[0]+t][tp[1]+tt] == 1) and (visited[startp[0]+t][startp[1]+tt] == 0) and (visited[tp[0]+t][tp[1]+tt] < tp[2]):
                    qu_.append([tp[0]+t, tp[1]+tt, tp[2]+1])

    return visited

```
