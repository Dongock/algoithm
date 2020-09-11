## DFS BFS

##### DFS BFS

```PYTHON
def dfs(v):
    visited[v] = 1
    print(v, end=' ')
    for i in range(1, N+1):
        if(visited[i] == 0 and maps[v][i] == 1):
            dfs(i)

def bfs(v):
    queue = [v]
    visited[v] = 0
    while queue:
        v = queue.pop(0)
        print(v, end=" ")
        for i in range(1,N+1):
            if(visited[i]==1 and maps[v][i]==1):
                queue.append(i)
                visited[i] = 0

N, M, V = map(int,input().split())
maps = [[0]*(N+1) for _ in  range(N+1)]
for i in range(M):
    a, b = map(int,input().split())
    maps[a][b] = maps[b][a] = 1
visited = [0] * (N+1)

dfs(V)
print()
bfs(V)
```

