---
description: >-
  문제 난이도: 하 / 문제 유형 : 정렬, 배열 / 풀이 시간 : 25분 /
  https://www.acmicpc.net/problem/1427
---

# 소트인사이드

## 1. 문제 풀이 핵심 아이디어

* 자릿수를 기준으로 정렬하므로 9 부터 0 까지 차례대로 확인합니다.
* 각 숫자에 대하여 해당 숫자의 개수를 계산하여 출력합니다.

```text
def solution(num):
    num_array = list(num)
    num_array.sort(reverse=True)

    return ''.join(num_array)


print(solution('2143'))
```

```text
def solution2(num):
    for i in range(9, -1, -1):
        for j in num:
            if int(j) == i:
                print(i, end='')

print(solution2('2143'))
```

