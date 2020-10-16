## HEAP(디스크 컨트롤러)

- 우선순위큐 할 때 명심할점

```
heapq.heappush를 사용해 우선 순위 큐 또는 힙을 쉽게 생성할 수 있다. 첫번째 인자는 heap 자체인 list이고, 두번째 인자는 튜플인데 튜플의 첫번째 요소는 우선순위 값, 두번째 요소는 데이터를 넣어주면 된다. 함수의 두번째 인자로 튜플이 아닌 일반 값을 넣어주면, 값을 기준으로 heap을 만들어준다. 파이썬이 제공하는 힙은 최소힙(min-heap)이므로 주의하자. 삽입 별 시간 복잡도는 O(log n) 이다.
```

- 이걸명심해서 풀면 풀수있다
- 디스크 컨트롤러의 핵심은 작업시간이 짧은게 먼저와야한다는 것
- 기다리는 시간이 길수록 안좋으니까

```
import heapq #파이썬에서 우선순위큐는 넣으면 튜플의 첫번째 꺼를 우선순위로(min) 자동정렬
def solution(jobs):
    count, last, answer = 0, -1, 0 #카운트는 횟수(while탈출), last는 시작시간인데 처음은 0부터 시작하다보니 -1에서 시작하게 해놓음, answer는 대기시간과 활동시간들의 합
    heap = [] # 우선순위큐에 넣을 heap
    jobs.sort() # 시작시간 별로 정리
    times = jobs[0][0] # 시작시간(0으로 초기화)
    while count < len(jobs): # 카운트세서 작업 개수만큼만
        for s,t in jobs: # 작업에서 시작시간과 작업시간 뺌
            if last < s <= times: # 시작시간이 포함되어야 하는데 0부터 시작하는 경우도 있으면 하나만 껴야되서 last는 0보다 작게, times는 크거나 같게
                heapq.heappush(heap,(t,s)) # 위에설명
        if len(heap) > 0: #이제 우선순위큐에넣었으면 시작
            count += 1 # 우선순위 큐에 들갔으니 카운트 증가
            last = times # 시작시간 업데이트
            term, start = heapq.heappop(heap) #꺼낸애가 작업시간이랑 시작시간
            times += term #작업시간만큼 시간 늘려주고
            answer += (times-start) # 대기시간도 더해야하므로 현재시간에 시작시간 빼줌
        else:
            time += 1 # 만약에 시작시간이 저 범위안에 없으면 범위를 늘려준다
    return answer//len(jobs)
```



