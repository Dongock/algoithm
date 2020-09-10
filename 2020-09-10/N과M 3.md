## 백트래킹

##### N과M3

```PYTHON
def solve(n, N, M):
    if n == M:
        print(*res)
    else:
        for i in range(N):
            visited[i] = True
            res[n] = ans[i]
            solve(n+1, N, M)
            visited[i] = False

N, M = map(int,input().split())
ans = range(1,N+1)
res = [0]*M
visited=[False]*N
(solve(0, N, M))

```

