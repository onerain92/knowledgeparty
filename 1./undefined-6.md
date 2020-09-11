---
description: >-
  문제 난이도: 중 / 문제 유형 : 해시, 집합, 그래프 / 풀이 시간 : 50분 /
  https://www.acmicpc.net/problem/4195
---

# 친구 네트워크

## 1. 문제 풀이 핵심 아이디어

* 해시를 활용한 Union-Find 알고리즘을 이용해 문제를 풀 수 있다.
* Python에서는 dictionary 자료형을 해시처럼 사용할 수 있다.

```text
parent = dict()
number = dict()

def find(friend):
    if friend == parent[friend]:
        return friend
    else:
        new_parent = find(parent[friend])
        parent[friend] = new_parent

        return new_parent


def union(friend1, friend2):
    friend1_parent = find(friend1)
    friend2_parent = find(friend2)

    if friend1_parent != friend2_parent:
        parent[friend2_parent] = friend1_parent
        number[friend1_parent] += number[friend2_parent]

def solution(friends_relationship):
    for friend1, friend2 in friends_relationship:
        if friend1 not in parent:
            parent[friend1] = friend1
            number[friend1] = 1

        if friend2 not in parent:
            parent[friend2] = friend2
            number[friend2] = 1

        union(friend1, friend2)
        print(number[find(friend1)])


print(solution([('Fred', 'Barney'), ('Barney', 'Betty'), ('Betty', 'Wilma')]))
```

```text
parent2 = dict()
number2 = dict()

def find2(x):
    if x == parent2[x]:
        return x
    else:
        p = find2(parent2[x])
        parent2[x] = p

        return p


def union2(x, y):
    x = find2(x)
    y = find2(y)

    if x != y:
        parent2[y] = x
        number2[x] += number2[y]


def solution2():
    test_case = int(input())

    for _ in range(test_case):
        f = int(input())

        for _ in range(f):
            x, y = input().split(' ')

            if x not in parent2:
                parent2[x] = x
                number2[x] = 1

            if y not in parent2:
                parent2[y] = y
                number2[y] = 1

            union2(x, y)
            print(number2[find2(x)])


solution2()
```



