---
description: '문제 난이도: 하 / 문제 유형 : 탐색 / 풀이 시간 : 20분 / https://www.acmicpc.net/problem/1543'
---

# 문서 검색

## 문제 풀이 핵심 아이디어

* 문서의 길이는 최대 2,500이고 단어의 길이는 최대 50입니다.
* 단순히 모든 경우의 수를 계산하여 문제를 해결할 수 있습니다.
* 시간 복잡도 O\( NM \)의 알고리즘으로 해결할 수 있습니다.
* 문서와 단어의 위치를 맞추어서 반복적으로 비교합니다.

```text
def solution(document, word):
    index = 0
    result = 0

    while len(document) - index >= len(word):
        if document[index:index + len(word)] == word:
            result += 1
            index += len(word)
        else:
            index += 1

    return result


print(solution('ababababa', 'aba'))
```

