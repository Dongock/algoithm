## DFS, BFS

###### 문제 설명

n개의 음이 아닌 정수가 있습니다. 이 수를 적절히 더하거나 빼서 타겟 넘버를 만들려고 합니다. 예를 들어 [1, 1, 1, 1, 1]로 숫자 3을 만들려면 다음 다섯 방법을 쓸 수 있습니다.

```
-1+1+1+1+1 = 3
+1-1+1+1+1 = 3
+1+1-1+1+1 = 3
+1+1+1-1+1 = 3
+1+1+1+1-1 = 3
```

사용할 수 있는 숫자가 담긴 배열 numbers, 타겟 넘버 target이 매개변수로 주어질 때 숫자를 적절히 더하고 빼서 타겟 넘버를 만드는 방법의 수를 return 하도록 solution 함수를 작성해주세요.

##### 제한사항

- 주어지는 숫자의 개수는 2개 이상 20개 이하입니다.
- 각 숫자는 1 이상 50 이하인 자연수입니다.
- 타겟 넘버는 1 이상 1000 이하인 자연수입니다.

##### 입출력 예

| numbers         | target | return |
| --------------- | ------ | ------ |
| [1, 1, 1, 1, 1] | 3      | 5      |

##### 입출력 예 설명

문제에 나온 예와 같습니다.

```python
num = 0
def dfs(numbers,i,cal,target):
    global num
    if i == len(numbers):
        if cal == target:
            num += 1
        return
    dfs(numbers,i+1,cal+numbers[i],target)
    numbers[i] *= -1
    dfs(numbers,i+1,cal+numbers[i],target)

def solution(numbers, target):
    global num
    answer = 0
    cal = 0
    dfs(numbers,0,cal,target)
    return num
```

![image-20201014010301831](C:\Users\multicampus\Desktop\first\알고\algoithm\2020-10-14\image-20201014010301831.png)

`느낀점` : 이건 다른사람의 추천을 받은 풀이인데 재귀는 진짜... 어렵고 아름답다. dfs로 global써서 풀고 좀 뿌듯했는데 이거 보고 그저 감탄...

![image-20201014010513840](C:\Users\multicampus\Desktop\first\알고\algoithm\2020-10-14\image-20201014010513840.png)

`느낀점`: 이건 조금 더 깔끔하게 풀었다. 나의 경우는 재귀 값을 더하는거에서 자꾸 오류가 나서 글로벌로 처리했는데 그냥 1로 내보내버리면 좀 편하네

![image-20201014010646309](C:\Users\multicampus\Desktop\first\알고\algoithm\2020-10-14\image-20201014010646309.png)

`느낀점` : 위에꺼까지 보고 아 더 다른 풀이 없겠지했는데 이거 보고 이렇게도 할 수 있구나를 생각하게 된다. 알고리즘의 세계는 넓고 험난하다