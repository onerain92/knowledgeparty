---
description: '문제 난이도: 중 / 문제 유형 : 이진탐색 / 풀이 시간 : 40분 / https://www.acmicpc.net/problem/2110'
---

# 공유기 설치

## 문제 풀이 핵심 아이디어

* 집의 갯수 N은 최대 200,000개이며, 집의 좌표 X는 최대 1,000,000,000 입니다.
* 이진 탐색을 이용하여 O\( N \* log X \)에 문제를 해결할 수 있습니다.
* 가장 인접한 두 공유기 사이의 최대 Gap을 이진 탐색으로 찾습니다.

```text
def solution(locations, N):
    answer = 0
    locations.sort()
    lower = locations[1] - locations[0]
    upper = locations[-1] - locations[0]

    while lower <= upper:
        mid = (lower + upper) // 2
        value = locations[0]
        count = 1

        for i in range(1, len(locations)):
            if value + mid <= locations[i]:
                count += 1
                value = locations[i]

        if count >= N:
            lower = mid + 1
            answer = mid
        else:
            upper = mid - 1

    return answer

print(solution([1, 2, 8, 4, 9], 3))
```



