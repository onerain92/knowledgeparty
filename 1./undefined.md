---
description: >-
  문제 난이도: 하 / 문제 유형 : 배열, 구현 / 풀이 시간 : 15분 /
  https://www.acmicpc.net/problem/2920
---

# 음계

```text
def solution(scales):
    scales = list(map(int, input().split(' ')))

    asc = True
    desc = True

    for i in range(1, len(scales)):
        if scales[i] < scales[i - 1]:
            asc = False
        elif scales[i] > scales[i - 1]:
            desc = False

    if asc:
        return 'ascending'
    elif desc:
        return 'descending'
    else:
        return 'mixed'


print(solution('12345678'))
```



