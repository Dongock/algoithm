## BFS

##### 보급로

```python
for case in range(1,int(input())+1):
    di = [1,0,-1,0]
    dj = [0,1,0,-1]
    N = int(input())
    maps = [list(map(int,input())) for _ in range(N)]
    road = [[10000000]*N for i in range(N)]
    queue = [(0,0)]
    road[0][0] = maps[0][0]
    while queue:
        a,b = queue.pop()
        for k in range(4):
            ni = a+di[k]
            nj = b+dj[k]
            if ni>=0 and ni<N and nj>=0 and nj<N:
                if road[ni][nj] > road[a][b] + maps[ni][nj]:
                    queue.append((ni,nj))
                    road[ni][nj] = road[a][b] + maps[a][b]
    print('#{} {}'.format(case,road[N-1][N-1]))
```



