---
description: >-
  문제 난이도: 하 / 문제 유형 : 배열, 완전 탐색 / 풀이 시간 : 20분 /
  https://www.acmicpc.net/problem/2798
---

# 블랙잭

```text
import itertools

def solution(card_num, max_num, cards):
    all_cases = itertools.combinations(cards, 3)
    max_sum = 0

    for case in all_cases:
        case_sum = sum(case)
        if case_sum <= max_num and case_sum > max_sum:
            max_sum = case_sum

    return max_sum

print(solution(5, 21, [5, 6, 7, 8, 9]))
```



