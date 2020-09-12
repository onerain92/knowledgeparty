---
description: >-
  문제 난이도: 하 / 문제 유형 : 힙, 자료구조 / 풀이 시간 : 20분/
  https://www.acmicpc.net/problem/1927
---

# 최소 힙

## 문제 풀이 핵심 아이디어

* 최소 힙의 기본적인 기능을 구현합니다.
* 파이썬에서 heapq 라이브러리를 이용하면 간단히 힙을 구현할 수 있습니다.

```text
import heapq

n = int(input())
array = []
result = []

for _ in range(n):
    value = int(input())

    if value == 0:
        if array:
            result.append(heapq.heappop(array))
        else:
            result.append(0)
    else:
        heapq.heappush(array, value)

for data in result:
    print(data)
```

