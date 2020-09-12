---
description: '문제 난이도: 하 / 문제 유형 : 탐색 / 풀이 시간 : 20분 / https://www.acmicpc.net/problem/1568'
---

# 새

## 문제 풀이 핵심 아이디어

* N이 최대 1,000,000,000 입니다,
* K가 반복적으로 증가하므로, 날아가는 새의 마리 수는 빠르게 증가합니다.
* 따라서 문제에서 요구하는대로 단순히 구현하여 정답 처리를 받을 수 있습니다.

```text
def solution(birds):
    count = 0
    number_of_bird = 1

    while birds != 0:
        if number_of_bird >= birds:
            number_of_bird = 1
        birds -= number_of_bird
        number_of_bird += 1
        count += 1

    return count


print(solution(14))
```

