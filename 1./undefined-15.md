---
description: '문제 난이도: 하 / 문제 유형 : 탐색 / 풀이 시간 : 20분 / https://www.acmicpc.net/problem/1668'
---

# 트로피 진열

## 문제 풀이 핵심 아이디어

* 선반 위에 올려져 있는 트로피들에 대하여 왼쪽에서, 오른쪽에서 봤을 때 보이는 트로피의 수를 각각 구합니다.
* 트로피의 개수 N이 최대 50이므로 단순히 구현하면 됩니다.

```text
def solution(trophys):
    left = 1
    right = 1

    for i in range(1, len(trophys)):
        if trophys[i] - trophys[i - 1] > 0:
            left += 1
        else:
            right += 1

    return left, right


print(solution([1, 2, 3, 4, 5]))
```

```text
def ascending(trophys):
    now = trophys[0]
    result = 1

    for i in range(1, len(trophys)):
        if now < trophys[i]:
              result += 1
              now = trophys[i]

    return result

def solution2(trophys):
    print(ascending(trophys))
    trophys.reverse()
    print(ascending(trophys))

print(solution2([1, 2, 3, 4, 5]))
```

