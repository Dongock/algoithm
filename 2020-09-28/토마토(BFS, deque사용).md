## BFS

##### 토마토(deque를 사용 외우기)

```python
from collections import deque
M, N = map(int,input().split())
maps = [list(map(int,input().split())) for _ in range(N)]
queue = deque()
di = [1,-1,0,0]
dj = [0,0,1,-1]
for i in range(N):
    for j in range(M):
        if maps[i][j] == 1:
            queue.append((i,j))
while queue:
    a, b = queue.popleft()
    for k in range(4):
        ni = a + di[k]
        nj = b + dj[k]
        if ni >= 0 and ni < N and nj >= 0 and nj < M and maps[ni][nj] == 0:
            maps[ni][nj] = maps[a][b] + 1
            queue.append((ni,nj))
isTrue = False
result = -2
for i in maps:
    for j in i:
        if j == 0:
            isTrue = True
        result = max(result,j)
if isTrue == True:
    print(-1)
elif result == -1:
    print(0)
else:
    print(result-1)
```

