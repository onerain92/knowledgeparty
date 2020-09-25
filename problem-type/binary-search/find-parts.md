---
description: '문제 난이도: 중하 / 문제 풀이 시간 : 30분 / 시간 제한 : 1초 / 메모리 제한 : 128MB'
---

# 부품 찾기

## 문제 설명

명원이네 전자 매장에는 부품이 N개 있다. 각 부품은 정수 형태의 고유한 번호가 있다. 어느 날 손님이 M개 종류의 부품을 대량으로 구매하겠다며 당일 날 견적서를 요청했다. 명원이는 때를 놓치지 않고 손님이 문의한 부품 M개 종류를 모두 확인해서 견적서를 작성해야 한다. 이때 가게 안에 부품이 모두 있는지 확인하는 프로그램을 작성해보자.

예를 들어 가게의 부품이 총 5개일 때 부품 번호가 다음과 같다고 하자.

N = 5  
\[ 8, 3, 7, 9, 2 \]

손님은 총 3개의 부품이 있는지 확인 요청했는데 부품 번호는 다음과 같다.

M = 3  
\[ 5, 7, 9 \]

이때 손님이 요청한 부품 번호의 순서대로 부품을 확인해 부품이 있으면 yes, 없으면 no를 출력한다. 구분은 공백으로 한다.



#### 입력 조건

* 첫째 줄에 정수 N이 주어진다. \( 1 &lt;= N &lt;= 1,000,000 \)
* 둘째 줄에는 공백으로 구분하여 N개의 정수가 주어진다. 이때 정수는 1보다 크고 1,000,000 이하이다.
* 셋째 줄에는 정수 M이 주어진다. \( 1 &lt;= M &lt;= 100,000 \)
* 넷째 줄에는 공백으로 구분하여 M개의 정수가 주어진다. 이때 정수는 1보다 크고 10억 이하이다.

#### 출력 조건

* 첫째 줄에 공백으로 구분하여 각 부품이 존재하면 yes를, 없으면 no를 출력한다.

#### 입력 예시

5  
8 3 7 9 2  
3  
5 7 9

#### 출력 예시

no yes yes



## 문제 해설

이 문제는 여러 방법으로 해결할 수 있다. 여기서는 가장 먼저 이진 탐색 알고리즘으로 풀이할 텐데, 이처럼 다량의 데이터 검색은 이진 탐색 알고리즘을 이용해 효과적으로 처리할 수 있다.

먼저 매장 내 N개의 부품을 번호를 기준으로 정렬하자. 그 이후에 M개의 찾고자 하는 부품이 각각 매장에 존재하는지 검사하면 된다. 이때 매장의 부품들은 정렬이 되어 있기 때문에 이진 탐색을 수행해  찾을 수 있다.

따라서 이렇게 문제를 풀면, 부품을 찾는 과정에서 최악의 경우 시간 복잡도 O\( M x log N \)의 연산이 필요하므로 최대 약 200만 번의 연산이 이루어진다고 분석할 수 있다. 오히려 N개의 부품을 정렬하기 위해서 요구되는 시간 복잡도 O\( N x log N \)이 이론적으로 최대 약 2,000만으로 더욱더 많은 연산이 필요한 것을 알 수 있다. 결과적으로 이진 탐색을 사용하는 문제 풀이 방법의 경우 시간 복잡도는 O\( \(M + N\) x log N \)이다.



## 답안

### 내가 푼 답안

```text
def binary_search(shop_parts, parts, start, end):
    while start <= end:
        mid = (start + end) // 2

        if shop_parts[mid] == parts:
            return 'yes'
        elif shop_parts[mid] > parts:
            end = mid - 1
        else:
            start = mid + 1

    return 'no'


def solution(shop_parts, guest_parts):
    result = []
    shop_parts.sort()

    for parts in guest_parts:
        start = 0
        end = len(shop_parts) - 1
        result.append(binary_search(shop_parts, parts, start, end))

    return ' '.join(result)


print(solution([8, 3, 7, 9, 2], [5, 7, 9]))
```



### 다른 답안1

```text
# 계수 정렬을 이용한 풀이

n = int(input())
array = [0] * 1000000

for i in input().split():
    array[int(i)] = 1

m = int(input())
x = list(map(int, input().split()))

for i in x:
    if array[i] == 1:
        print('yes', end=' ')
    else:
        print('no', end=' ')
```



### 다른 답안2

```text
# set을 이용한 풀이

n = int(input())
array = set(map(int, input().split()))

m = int(input())
x = list(map(int, input().split()))

for i in x:
    if i in array:
        print('yes', end=' ')
    else:
        print('no', end=' ')
```



