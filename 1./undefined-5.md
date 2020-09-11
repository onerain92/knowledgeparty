---
description: >-
  문제 난이도: 하 / 문제 유형 : 해시, 배열, 구현 / 풀이 시간 : 20분 /
  https://www.acmicpc.net/problem/1920
---

# 수 찾기

## 1. 문제 풀이 핵심 아이디어

* 특정 정수의 등장 여부만을 간단히 체크하면 됩니다.
* Python에서는 dictionary 자료형을 해시처럼 사용할 수 있습니다.
* 본 문제는 set 자료형을 이용해 더욱 간단히 풀 수 있습니다.

```text
def solution(save_data, find_data):
    data_set = set(save_data)
    answer = []

    for data in find_data:
        if data in data_set:
            answer.append(1)
        else:
            answer.append(0)

    return answer


print(solution([4, 1, 5, 2, 3], [1, 3, 7, 9, 5]))
```

```text
def solution2():
    n = int(input())
    data_set = set(map(int, input().split(' ')))
    m = int(input())
    find_data = list(map(int, input().split(' ')))

    for data in find_data:
        if data in data_set:
            print(1)
        else:
            print(0)

solution2()
```

