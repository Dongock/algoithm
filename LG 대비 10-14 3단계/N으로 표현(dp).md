## N으로 표현(dp)

```
def solution(N, number):
    num_set = [set() for _ in range(8)]
    for i,x in enumerate(num_set,1):
        x.add(int(str(N) * i))
    if number in num_set[0]:
        return 1
    for i in range(1,8):
        for j in range(i):
            for cal1 in num_set[j]:
                for cal2 in num_set[i-j-1]:
                    num_set[i].add(cal1+cal2)
                    num_set[i].add(cal1-cal2)
                    num_set[i].add(cal1*cal2)
                    if cal2 != 0:
                        num_set[i].add(cal1//cal2)
                    elif cal1 != 0:
                        num_set[i].add(cal2//cal1)
        # if i == 6:
        #     print(num_set[i])
        if number in num_set[i] :
            answer = i+1
            break
    else:
        answer = -1
    return answer
```

- N, NN 이런식으로 개수가 늘어나니까
- set으로 중복을 없애고 개수별로 나올 수 있는 것을 다 때려박는다
- 문제는 양쪽을 서로 나누는 걸 고려못했던 것..

