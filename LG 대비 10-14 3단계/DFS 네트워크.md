## DFS 네트워크

```
def solution(n, computers):
    answer = 0
    visited = [0 for _ in range(n)]
    def dfs(i):
        start = [i]
        while start:
            node = start.pop()
            if visited[node] == 0:
                visited[node] = 1
            for i in range(n):
                if computers[node][i] == 1 and visited[i] == 0:
                    start.append(i)
        
    i = 0
    while 0 in visited:
        if visited[i] == 0:
            dfs(i)
            answer += 1
        i += 1
    return answer
```

- 솔직히 이정돈 풀어야되는데 아직 멀었다

- 방문배열을 통해 중복을 없앴다

- 방문배열을 다 돌때까지 반복문을 걸고 DFS를 걸어서

  연결된 노드를 다 돌고 탈출하면 네트워크의 개수에 1을 추가

- 연결된 노드 도는 건 스택을 이용했다

  방문배열 업데이트와 컴퓨터배열이 1일 때 스택에 넣었다