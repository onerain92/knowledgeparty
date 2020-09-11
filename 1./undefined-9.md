---
description: '문제 난이도: 하 / 문제 유형 : 정렬 / 풀이 시간 : 15분 / https://www.acmicpc.net/problem/10814'
---

# 나이순 정렬

## 1. 문제 풀이 핵심 아이디어

* \( 나이, 이름 \)의 정보를 입력 받은 뒤에 나이를 기준으로 정렬합니다.
* 파이썬의 기본 정렬 라이브러리를 이용하면 됩니다.
* 나이가 동일한 경우, 먼저 입력된 이름 순서를 따르도록 key 속성을 설정해야 합니다.

```text
def solution(members):
    members.sort(key=lambda x: x[0])

    return members


print(solution([(21, 'Junkyu'), (21, 'Dohyun'), (20, 'Sunyoung')]))
```



