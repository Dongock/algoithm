## 여행경로 (dfs)

```
def solution(tickets):
    routes = {}
    for t in tickets:
        # 출발 공항이 키, value는 갈 수 있는 공항 들어있는 리스트
        routes[t[0]] = routes.get(t[0], [])+[t[1]] 
    for r in routes:
        routes[r].sort(reverse=True)
    print(routes)
    stack = ["ICN"]  # 빈 걸로 초기화할 수도 있지만 무조건 ICN은 넣어서 시작하므로
    path = []  # 가려고 하는 경로 표현
    while len(stack) > 0:  # stack이 다 없어질 때까지
        top = stack[-1]
        # 어떤 공항에서 출발하는 표가 한장도 없다면 또는 있었는데, 다 써버렸다면
        if top not in routes or len(routes[top]) == 0:
            path.append(stack.pop())
        else:
            stack.append(routes[top][-1])  # 역순으로 정렬을 해놨으니, 가장 앞서는
            # -1 직전까지 슬라이스를 해서, 떼어낸다. pop을 적용해도 된다.
            routes[top] = routes[top][:-1]
    return path[::-1]  # 역순- [start,end,step]이므로
```

- 감탄했다.... 나는 정렬해서 푸는데 도저히 중간에끊기는 걸 해결할 수 없었는데.... 이렇게 해결하다니 심지어 역순... 나의 지식의 길은 멀다