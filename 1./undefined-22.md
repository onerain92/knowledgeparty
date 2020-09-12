---
description: >-
  문제 난이도: 하 / 문제 유형 : 힙, 자료구조, 그리디 / 풀이 시간 : 20분/
  https://www.acmicpc.net/problem/1715
---

# 카드 정렬하기

## 문제 풀이 핵심 아이디어

* 가장 크기가 작은 숫자 카드 묶음들을 먼저 합쳤을 때, 비교 횟수가 가장 적다.

```text
import heapq

n = int(input())
heap = []
answer = 0

for _ in range(n):
    data = int(input())
    heapq.heappush(heap, data)

while len(heap) != 1:
    data1 = heapq.heappop(heap)
    data2 = heapq.heappop(heap)
    sum_data = data1 + data2
    answer += sum_data
    heapq.heappush(heap, sum_data)

print(answer)
```



