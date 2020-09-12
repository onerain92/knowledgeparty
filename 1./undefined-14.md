---
description: '문제 난이도: 하 / 문제 유형 : 탐색 / 풀이 시간 : 20분 / https://www.acmicpc.net/problem/1302'
---

# 베스트셀러

## 문제 풀이 핵심 아이디어

* 가장 많이 등장한 문자열을 출력하는 문제와 동일합니다.
* 등장 횟수를 계산할 때는 파이썬의 Dictionary 자료형을 이용하면 효과적입니다.

```text
n = int(input())
books = {}

for _ in range(n):
    book = input()

    if book not in books:
        books[book] = 1
    else:
        books[book] += 1

target = max(books.values())
array = []

for book, number in books.items():
    if number == target:
        array.append(book)

print(sorted(array)[0])
```



