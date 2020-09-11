---
description: '문제 난이도: 하 / 문제 유형 : 정렬 / 풀이 시간 : 15분 / https://www.acmicpc.net/problem/2750'
---

# 수 정렬하기

## 1. 문제 풀이 핵심 아이디어

* 데이터의 갯수가 1,000개 이하이므로 기본적인 정렬 알고리즘으로 해결할 수 있다.

```text
import random

# 버블 정렬
def solution(numbers):
    for i in range(len(numbers) - 1):
        is_swap = False

        for j in range(len(numbers) - 1 - i):
            if numbers[j] > numbers[j + 1]:
                numbers[j], numbers[j + 1] = numbers[j + 1], numbers[j]
                is_swap = True

        if is_swap == False:
            break

    return numbers


random_numbers = random.sample(range(100), 10)
print(solution(random_numbers))
```

