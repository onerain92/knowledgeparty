---
description: '문제 난이도: 하 / 문제 유형 : 정렬 / 풀이 시간 : 15분 / https://www.acmicpc.net/problem/11650'
---

# 좌표 정렬하기

## 1. 문제 풀이 핵심 아이디어

* \( x 좌표, y 좌표 \)를 입력 받은 뒤 x 좌표, y 좌표 순서대로 차례대로 오름차순 정렬합니다.
* 파이썬의 기본 정렬 라이브러리는 기본적으로 튜플의 인덱스 순서대로 오름차순 정렬합니다.
* 따라서 단순히 기본 정렬 라이브러리를 사용하면 됩니다. \( key 속성 설정 없이 \)

```text
def solution(coordinates):
    coordinates.sort()

    return coordinates


print(solution([(3, 4), (1, 1), (1, -1), (2, 2), (3, 3)]))
```

```text
def solution2(coordinates):
    array = []

    for coordinate in coordinates:
        x, y = coordinate
        array.append((x, y))

    array = sorted(array)

    for i in array:
        print(i[0], i[1])


print(solution2([[3, 4], [1, 1], [1, -1], [2, 2], [3, 3]]))
```



