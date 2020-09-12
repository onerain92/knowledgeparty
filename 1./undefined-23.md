---
description: >-
  문제 난이도: 중 / 문제 유형 : 힙, 위상 정렬 / 풀이 시간 : 40분/
  https://www.acmicpc.net/problem/1766
---

# 문제집

## 문제 풀이 핵심 아이디어

* 전형적인 위상 정렬 문제이다.
* 위상 정렬은 순서가 정해져 있는 작업을 차례로 수행해야 할 때, 순서를 결정해주는 알고리즘이다.
* 위상 정렬의 시간 복잡도는 O\( V + E \)로 해결할 수 있다.

```text
import heapq

n, m = map(int, input().split())
array = [[] for i in range(n + 1)]
indegree = [0] * (n + 1)

heap = []
result = []

for _ in range(m):
    x, y = map(int, input().split())
    array[x].append(y)
    indegree[y] += 1

for i in range(1, n + 1):
    if indegree[i] == 0:
        heapq.heappush(heap, i)

while heap:
    data = heapq.heappop(heap)
    result.append(data)

    for y in array[data]:
        indegree[y] -= 1

        if indegree[y] == 0:
            heapq.heappush(heap, y)

for i in result:
    print(i, end = '')
```



