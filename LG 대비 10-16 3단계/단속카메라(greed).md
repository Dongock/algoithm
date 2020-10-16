## 단속카메라(greed)

```
def solution(routes):
    enter, exit, N = 0, 1, len(routes)
    answer = 0
    check = [0]*N
    routes.sort(key=lambda x:x[1])
    camera = -30001
    for i in range(N):
        if check[i] != 0 :
            continue
        answer += 1
        camera = routes[i][exit]
        for j in range(i,N):
            if routes[j][enter] <= camera <= routes[j][exit]:
                check[j] = 1
                
    
    return answer
```

- 후 난 왜이렇게 못풀까;; 2단계는 쉽던데
- 암튼 각설하고 일단 routes에서 배열들의 뒷부분, 나가는 것으로 정렬을 했다. 그래야 순서대로 확인이 가능하니까
- 그래서 첫번째 나갔을때 그 친구가 겹치는 애들이 있으면 거기에 카메라를 설치하고 체크처리해줬다
- 그렇게 예외를 거니까 쉽게 해결
- 그리드는 결국 다검사를 하긴해야한다 어떻게보면