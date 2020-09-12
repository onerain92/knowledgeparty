---
description: '문제 난이도: 중 / 문제 유형 : 정렬 / 풀이 시간 : 25분 / https://www.acmicpc.net/problem/11004'
---

# K 번째 수

## 문제 풀이 핵심 아이디어

* 데이터의 갯수가 최대 5,000,000개입니다.
* 시간 복잡도 O\( N log N \)의 정렬 알고리즘을 이용해야 합니다.
* 고급 정렬 알고리즘\( 병합 / 퀵/ 힙 정렬 등 \)을 이용하여 문제를 해결할 수 있습니다.
* 혹은 파이썬의 기본 정렬 라이브러리를 이용하여 문제를 풀 수 있습니다.

```text
def merge_sort(array):
    if len(array) <= 1:
        return array

    mid = len(array) // 2
    left = merge_sort(array[:mid])
    right = merge_sort(array[mid:])

    i, j, k = 0, 0, 0
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            array[k] = left[i]
            i += 1
        else:
            array[k] = right[j]
            j += 1
        k += 1

    if i == len(left):
        while j < len(right):
          array[k] = right[j]
          j += 1
          k += 1
    elif j == len(right):
        while i < len(left):
            array[k] = left[i]
            i += 1
            k += 1

    return array


n, k = map(int, input().split(' '))
array = []

for _ in range(n):
    array.append(int(input()))

array = merge_sort(array)

for data in array:
    print(data)
```

```text
n, k = map(int, input().split(' '))
array = list(map(int, input().split()))

array = sorted(array)

print(array[k - 1])
```

