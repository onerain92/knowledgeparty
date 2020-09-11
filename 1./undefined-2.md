---
description: >-
  문제 난이도: 하 / 문제 유형 : 스택, 그리디 / 풀이 시간 : 30분 /
  https://www.acmicpc.net/problem/1874
---

# 스택 수열

## 문제 풀이 핵심 아이디어

1. 스택에 원소를 삽입할 때는, 단순히 특정 수에 도달할 때까지 삽입하면 된다.
2. 스택에서 원소를 연달아 빼낼 때 내림차순을 유지할 수 있는지 확인한다.

```text
def solution(n, numbers):
    numbers = list(map(int, numbers))
    stack = []
    result = []
    numbers_index = 0

    for i in range(n):
        stack.append(i + 1)
        result.append('+')

        while stack and stack[-1] == numbers[numbers_index]:
            stack.pop()
            numbers_index += 1
            result.append('-')

    return '\n'.join(result) if not stack else 'NO'


print(solution(8, '43687521'))
```



