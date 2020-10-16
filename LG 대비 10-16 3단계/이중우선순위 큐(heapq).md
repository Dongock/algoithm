## 이중우선순위 큐(heapq)

- 후 heap은 감 잡았다 달달하다

```
import heapq
def solution(operations):
    answer = []
    heap = []
    for i in operations:
        if i[0] == "I":
            num = int(i[2:])
            heapq.heappush(heap,num)
            print(heap,'i')
        else:
            heapq.heapify(heap) 
            if len(heap) > 0:
                if int(i[2:]) > 0:
                    heap.pop()
                elif int(i[2:]) < 0:
                    heap.pop(0)
        if len(heap) == 0:
            answer = [0,0]
        else:
            answer = [max(heap),min(heap)]
    return answer
```

- 다른건 쉬웠다 파이썬은 minheap이니
- maxheap하는 방법으로(-num,num)넣으면 된단다 참신 ;;
- heap에 넣은 애들 꺼내는 방법을 알아냇다 이거외우기

```
heapq.heapify(heap) 이게 heap 꺼내는 방법이다
```

