## 백트래킹

##### N과 M

```python
# 재귀 + sorted이용
def solve(ans, N, M):
    if M == 0:
        string = ' '.join(map(str,sorted(ans)))
        if string not in all:
            all.append(string)
    for i in range(0, N):
        if visited[i] == False:
            ans.append(i+1)
            visited[i] = True
            solve(ans, N, M-1)
            visited[i] = False
            ans.pop()

N, M = map(int,input().split())
visited=[False]*N
ans, all = [], []
(solve(ans, N, M))
for i in all:
    print(i)


# 인덱스 넘기기
# 재귀를 이용
def solve(ans,idx, N, M):
    if M == 0:
        string = ' '.join(map(str,sorted(ans)))
        if string not in all:
            all.append(string)
    for i in range(idx, N):
        if visited[i] == False:
            ans.append(i+1)
            visited[i] = True
            solve(ans,idx+1, N, M-1)
            visited[i] = False
            ans.pop()

N, M = map(int,input().split())
visited=[False]*N
ans, all = [], []
(solve(ans,0, N, M))
for i in all:
    print(i)
```

