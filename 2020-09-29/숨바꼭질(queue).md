## BFS(queue)

##### 숨바꼭질(이해했음)

```python
from collections import deque

def solve():
    while q:
        cur = q.popleft()
        if cur == K:
            return visited[cur]
        nextPos(cur - 1, cur)
        nextPos(cur + 1, cur)
        nextPos(cur * 2, cur)

def nextPos(start, cur):
    if maxsize > start >= 0 and (visited[start] == 0 or visited[cur] + 1 < visited[start]):
        visited[start] = visited[cur] + 1
        q.append(start)

N, K = int(input())
maxsize = 100001
visited = [0] * 100001
q = deque([N])
print(solve())
```

