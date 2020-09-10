## 백트래킹

##### N과M

```PYTHON
# 재귀 이용
def solve(ans, N, M):
    if M == 0:
        print(' '.join(map(str,ans)))
    for i in range(0, N):
        if visited[i] == False:
            ans.append(i+1)
            visited[i] = True
            solve(ans, N, M-1)
            visited[i] = False
            ans.pop()

N, M = map(int,input().split())
visited=[False]*N
ans = []
(solve(ans, N, M))

```



