## 2xN 타일링

```
def solution(n):
    a,b=1,1
    for i in range(n):
        a,b=b,a+b
    return a%1000000007
```

- 재귀로 풀려했는데 오류가 났다
- 다른 풀이를 보다보니 피보나치 수열을 따름. 이유는 모르겠다