---
description: '문제 난이도: 하 / 시간 제한 : 1초 / 메모리 제한 : 128MB'
---

# 숫자 카드 게임

## 문제 설명

숫자 카드 게임은 여러 개의 숫자 카드 중에서 가장 높은 숫자가 쓰인 카드 한 장을 뽑는 게임이다. 단, 게임의 룰을 지키며 카드를 뽑아야 하고 룰은 다음과 같다.

1. 숫자가 쓰인 카드들이 N x M 형태로 놓여 있다. 이 때 N은 행의 개수를 의미하며, M은 열의 개수를 의미한다.
2. 먼저 뽑고자 하는 카드가 포함되어 있는 행을 선택한다.
3. 그다음 선택된 행에 포함된 카드들 중 가장 숫자가 낮은 카드를 뽑아야 한다.
4. 따라서 처음에 카드를 골라낼 행을 선택할 때, 이후에 해당 행에서 가장 숫자가 낮은 카드를 뽑을 것을 고려하여 최종적으로 가장 높은 숫자의 카드를 뽑을 수 있도록 전략을 세워야 한다.

예를 들어, 3 x 3 형태로 카드들이 다음과 같이 놓여 있다고 가정하자.

3 1 2  
4 1 4  
2 2 2

여기서 카드를 골라낼 행을 고를 때 첫 번째 혹은 두 번째 행을 선택하는 경우, 최종적으로 뽑는 카드는 1이다. 하지만 세 번째 행을 선택하는 경우 최종적으로 뽑는 카드는 2이다. 따라서 이 예제에서는 세 번쨰 행을 선택하여 숫자 2가 쓰여진 카드를 뽑는 것이 정답이다.

카 N x M 형태로 놓여 있을 때, 게임의 룰에 맞게 카드를 뽑는 프로그램을 만드시오.

#### 입력 조건

* 첫째 줄에 숫자 카드들이 놓인 행의 개수 N과 열의 개수 M이 공백을 기준으로 하여 각각 자연수로 주어진. \( 1 &lt;= N, M &lt;= 100 \)
* 둘째 줄부터 N개의 줄에 걸쳐 각 카드에 적힌 숫자가 주어진다. 각 숫자는 1 이상 10,000 이하의 자연수이다. 

#### 출력 조건

* 첫째 줄에 게임의 룰에 맞게 선택한 카드에 적힌 숫자를 출력한다. 

#### 입력 예시

3 3  
3 1 2  
4 1 4  
2 2 2  


#### 출력 예시

2



## 문제 해설

**그리디 알고리즘 유형**의 문제는 문제 해결을 위한 아이디어를 떠올렸다면 정답을 찾을 수 있다. 이 문제를 푸는 아이디어는 바로 _**'각 행마다 가장 작은 수를 찾은 뒤에 그 수 중에서 가장 큰 수'**_ 를 찾는 것이다. 이 문제는 문제 설명이 길어서 지문 이해에 시간이 많이 소요될 수 있지만, 문제의 아이디어를 떠올리는 것은 쉬운 문제에 속한다.

입력 조건에서 입력으로 들어오는 수는 모두 10,000 이하이므로 단순히 배열에서 가장 작은 수를 찾는 기본 문법을 이용하여 각 행에서 가장 작은 수를 찾은 다음 그 수 중에서 가장 큰 수를 찾는 방식으로 문제를 해결할 수 있다.

이 문제를 해결하기 위해서는 리스트에서 가장 작은 원소를 찾아주는 min\(\) 함수를 이용할 수 있거나, 2중 반복문 구조를 이용할 수 있어야 한다.



## 답안

### 내가 푼 답안

```text
def solution(n, m, cards):
    row_min = 0
    max_value = 0

    for card in cards:
        row_min = min(card)

        if max_value < row_min:
            max_value = row_min

    return max_value


print(solution(3, 3, [[3, 1, 2], [4, 1, 4], [2, 2, 2]]))
print(solution(2, 4, [[7, 3, 1, 8], [3, 3, 3, 4]]))
```



### 다른 답안1

```text
n, m = map(int, input().split())

result = 0

for i in range(n):
    data = list(map(int, input().split()))
    min_value = min(data)
    result = max(result, min_value)

print(result)
```



### 다른 답안2

```text
n, m = map(int, input().split())

result = 0

for i in range(n):
    data = list(map(int, input().split()))
    min_value = 100001
    
    for a in data:
        min_value = min(min_value, a)
        
    result = max(result, min_value)

print(result)
```


