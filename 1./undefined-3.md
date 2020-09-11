---
description: >-
  문제 난이도: 하 / 문제 유형 : 큐, 구현, 그리디 / 풀이 시간 : 30분 /
  https://www.acmicpc.net/problem/1966
---

# 프린터 큐

## 문제 풀이 핵심 아이디어

1. 데이터의 개수\( N &lt;= 100 \)가 많지 않으므로, 단순히 문제에서 요구하는 대로 구현합니다.
2. 현재 리스트에서 가장 큰 수가 앞에 올 때까지 회전시킨 뒤에 추출합니다.
3. 가장 큰 수가 M이면서 가장 앞에 있을 때 프로그램을 종료합니다.

```text
def solution():
    test_case = int(input())

    for _ in range(test_case):
        number_of_doc, target_doc = list(map(int, input().split(' ')))
        queue = list(map(int, input().split(' ')))
        queue = [(idx, priority) for idx, priority in enumerate(queue)]
        count = 0

        while queue:
            highest_priority = max(queue, key=lambda x: x[1])[1]
            current_idx, current_priority = queue.pop(0)
            if highest_priority == current_priority:
                count += 1
                if current_idx == target_doc:
                    print(count)
                    break
            else:
                queue.append((current_idx, current_priority))
```

```text
def solution2():
    test_case = int(input())

    for _ in range(test_case):
        n, m = list(map(int, input().split(' ')))
        queue = list(map(int, input().split(' ')))
        queue = [(i, idx) for idx, i in enumerate(queue)]

        count = 0
        while True:
            if queue[0][0] == max(queue, key=lambda x: x[0])[0]:
                count += 1

                if queue[0][1] == m:
                    print(count)
                    break
                else:
                    queue.pop(0)
            else:
                queue.append(queue.pop(0))
```



