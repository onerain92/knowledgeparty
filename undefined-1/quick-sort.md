# 퀵 정렬\( Quick Sort \)

## 1. 퀵 정렬\( Quick sort \)이란?

* 정렬 알고리즘의 꽃
* 기준점\( pivot \)을 정해서, 기준점보다 작은 데이터는 왼쪽, 큰 데이터는 오르쪽으로 모으는 함수를 작성한다.
* 각 왼쪽, 오른쪽은 재귀용법을 사용해서 다시 동일 함수를 호출하여 위 작업을 반복한다.
* 함수는 왼쪽 + 기준점 + 오른쪽을 리턴한다.



## 2. 연습

* 리스트 슬라이싱을 이용해서 세 개로 짤라서 각 리스트 변수에 넣고 출력해보자.

```text

```



## 3. 알고리즘 구현

* quicksort 함수 만들기
  * 만약 리스트 갯수가 한 개이면 해당 리스트 리턴
  * 그렇지 않으면, 리스트 맨 챂의 데이터를 기준점\( pivot \)으로 놓기
  * left, right 리스트 변수를 만들고,
  * 맨 앞의 데이터를 뺀 나머지 데이터를 기준점과 비교\( pivot \)
    * 기준점보다 작으면 left.append\( 데이터 \)
    * 기준점보다 크면 right.append\( 데이터 \)
  * return quicksort\(left\) + pivot + quicksort\(right\) 로 재귀 호출

{% hint style="info" %}
리스트로 만들어서 리턴하기 : return quicksort\(left\) + \[ pivot \] + quicksort\(right\)
{% endhint %}



```text
def qsort(data):
    if len(data) <= 1:
        return data
        
    left, right = list(), list()
    pivot = data[0]
    
    for index in range(1, len(data)):
        if pivot > data[index]:
            left.append(data[index])
        else:
            right.append(data[index])
            
    return qsort(left) + [ pivot ] + qsort(right)
```

```text
# List Comprehension 활

def qsort(data):
    if len(data) <= 1:
        return data
        
    left, right = list(), list()
    pivot = data[0]
    
    left = [ item for item in data[1:] if pivot > item ]
    right = [ item for item in data[1:] if pivot <= item ]
            
    return qsort(left) + [ pivot ] + qsort(right)
```



## 4. 알고리즘 분석

* 병합정렬과 유사, 시간 복잡도는 O\( n log n 
  * 단, 최악의 경우
    * 맨 처음 pivot이 가장 크거나, 가장 작으면
    * 모든 데이터를 비교하는 상황이 생김.
    * O\(n^2\)









