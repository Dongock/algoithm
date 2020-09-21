## 백트래킹

##### 근본의 N-queen(반복해보기)

```python
# N - queen 반복학습
def qa(x):
    for i in range(x):
        if row[x] == row[i] or abs(row[x] - row[i]) == x-i:
            return False
    return True

def check(i):
    global ans

    if i == N:
        ans += 1

    else:
        for j in range(N):
            row[i] = j
            if qa(i):
                check(i+1)

N = int(input())
ans = 0
row = [0] * N
check(0)
print(ans)
```

