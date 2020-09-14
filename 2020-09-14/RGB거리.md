## DP

##### RGB거리

```PYTHON
N = int(input())
maps = [list(map(int,input().split())) for _ in range(N)]
for i in range(1,N):
    maps[i][0] = min(maps[i-1][1], maps[i-1][2]) + maps[i][0]
    maps[i][1] = min(maps[i-1][0], maps[i-1][2]) + maps[i][1]
    maps[i][2] = min(maps[i-1][0], maps[i-1][1]) + maps[i][2]
print(min(maps[N-1][0], maps[N-1][1], maps[N-1][2]))
```

