# 이진 탐색\( Binary Search \)

## 1. 이진 탐색\( Binary Search \)이란?

* 탐색할 자료를 둘로 나누어 해당 데이터가 있을만한 곳을 탐색하는 방법이다.



## 2. 이진 탐색의 이해

#### 순차 탐색과 비교하며 이해하

![https://blog.penjee.com/binary-vs-linear-search-animated-gifs](../.gitbook/assets/binary-and-linear-search-animations.gif)



#### 분할 정복 알고리즘과 이진 탐색

* 분할 정복 알고리즘\( Divide and Conquer \)
  * Divide : 문제를 하나 또는 둘 이상으로 나눈다.
  * Conquer : 나눠진 문제가 충분히 작고, 해결이 가능하다면 해결하고, 그렇지 않다면 다시 나눈다. 
* 이진 탐색
  * Divide : 리스트를 두 개의 서브 리스트로 나눈다.
  * Conquer
    * 검색할 숫자\( search \) &gt; 중간 값 이면, 뒷 부분의 서브 리스트에서 검색할 숫자를 찾는다.
    * 검색할 숫자\( search \) &lt; 중간 값 이면,  부분의 서브 리스트에서 검색할 숫자를 찾는다.



## 3. 구현

* 이진 탐색은 데이터가 정렬되있는 상태에서 진행한다.
* 데이터가 \[2, 3, 8, 12, 20\] 일 때,
  * binary\_search\(data\_list, find\_data\) 함수를 만들고
  * find \_data는 찾는 숫자
  * data\_list는 데이터 리스트
  * data\_list의 중간값을 find\_data와 비교해서
    * find\_data &lt; data\_list의 중간 값 이면
      * 맨 앞부터 data\_list의 중간까지에서 다시 find\_data 찾기
    * data\_list &lt; find\_data 이면
      * data\_list의 중간부터 맨 끝까지에서 find\_data 찾기
    * 그렇지 않다면, data\_list의 중간값은 find\_dat인 경우로 return data\_list 중간위치



```text
import random

def binary_search(data, search):
    if len(data) == 1 and search == data[0]:
        return True
    
    if len(data) == 1 and search != data[0]:
        return False
    
    if len(data) == 0:
        return False
    
    medium = len(data) // 2

    if search == data[medium]:
        return True
    else:
        if search > data[medium]:
            return binary_search(data[medium:], search)
        else:
            return binary_search(data[:medium], search)
        

data_list = random.sample(range(100), 10)
data_list.sort()
binary_search(data_list, 10)
```



## 4.알고리즘 분석

* n개의 리스트를 매번 2로 나누어 1이 될 때까지 비교연산을 k회 진행한다.
  * n x 1/2 x 1/2 x 1/2 x ... = 1
  * n x 1/2^k = 1
  * n = 2^k = log2 n = log2 2^k
  * log2 n = k
  * Big-O 표기법으로는 k + 1이 결국 최종 시간 복잡도이다. \(1이 되었을 때도, 비교연산을 한 번 수행\)
    * 결국 O\(log2 n + 1\) 이고, 2와 1, 상수는 삭제되므로 O\(log n\)



