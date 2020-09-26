---
description: '문제 난이도: 중 / 문제 풀이 시간 : 20분 / 시간 제한 : 2초 / 메모리 제한 : 128MB'
---

# 팀 결성

## 문제 설명

학교에서 학생들에게 0번부터 N번까지의 번호를 부여했다. 처음에는 모든 학생이 서로 다른 팀으로 구분되어, 총 N + 1개의 팀이 존재한다. 이때 선생님은 '팀 합치기' 연산과 '같은 팀 여부 확인' 연산을 사용할 수 있다.

1. '팀 합치기' 연산은 두 팀을 합치는 연산이다.
2. '같은 팀 여부 확인' 연산은 특정한 두 학생이 같은 팀에 속하는지를 확인하는 연산이다.

선생님이 M개의 연산을 수행할 수 있을 때, '같은 팀 여부 확인' 연산에 대한 연산 결과를 출력하는 프로그램을 작성하시오.



#### 입력 조건

* 첫째 줄에 N, M이 주어진다. M은 입력으로 주어지는 연산의 개수이다.
* 다음 M개의 줄에는 각각의 연산이 주어진다.
* '팀 합치기' 연산은 0 a b 형태로 주어진다. 이는 a번 학생이 속한 팀과 b번 학생이 속한 팀을 합친다는 의미이다.
* '같은 팀 여부 확인' 연산은 1 a b 형태로 주어진다. 이는 a번 학생과 b번 학생이 같은 팀에 속해 있는지를 확인하는 연산이다.
* a와 b는 N 이하의 양의 정수이다.

#### 출력 조건

* '같은 팀 여부 확인' 연산에 대하여 한 줄에 하나씩 YES 혹은 NO로 결과를 출력한다.

#### 입력 예시

7 8  
0 1 3  
1 1 7  
0 7 6  
1 7 1  
0 3 7  
0 4 2  
0 1 1  
1 1 1

#### 출력 예시

NO  
NO  
YES

## 문제 해설

전형적인 서로소 집합 알고리즘 문제로 N과 M의 범위가 모두 100,000 이상이다. 범위가 100,000 이상이니 경로 압축 방식의 서로소 집합 자료구조를 이용하여 시간 복잡도를 개선해야 한다.

## 답안

### 내가 푼 답안

```text
def find_parent(parent, x):
    if parent[x] != x:
        return find_parent(parent, parent[x])
    return parent[x]


def union(parent, a, b):
    a = find_parent(parent, a)
    b = find_parent(parent, b)

    if a < b:
        parent[b] = a
    else:
        parent[a] = b


def solution(n, teams):
    parent = [0] * (n + 1)

    for i in range(n + 1):
        parent[i] = i

    print(parent)

    for team in teams:
        operation, team1, team2 = team
        if operation == 0:
            union(parent, team1, team2)
        elif operation == 1:
            if find_parent(parent, team1) == find_parent(parent, team2):
                print('YES')
            else:
                print('NO')

    print("후: ", parent)


print(solution(7, [[0, 1, 3], [1, 1, 7], [0, 7, 6], [1, 7, 1], [0, 3, 7], [0, 4, 2], [0, 1, 1], [1, 1, 1]]))
```



