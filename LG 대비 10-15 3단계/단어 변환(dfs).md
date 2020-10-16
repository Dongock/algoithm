## 단어 변환(dfs)

- dfs로 풀껄 dp로 푼다고 개고생했다

```
def solution(begin, target, words):
    answer = 0
    stack = [begin]
    visited = [0] * len(words)
    if target not in words:
        return 0
    while stack:
        start = stack.pop()
        if start == target:
            return answer
        for i in range(len(words)):
            cnt = 0
            if visited[i] == 1:
                    continue
            for j in range(len(start)):
                if start[j] != words[i][j]:
                    cnt += 1
            if cnt == 1:
                visited[i] = 1
                stack.append(words[i])    
        answer += 1
    
        
    return answer
```

- 생각없이 cnt를 2일때 스택을 쌓는다는 바보같은 조건을 걸어서 고생했다. 알고보면 한글자만 바꾸는거니 1이 아닐때를 했어야했는데... lg때 이런걸로 시간낭비하면 큰일일 듯