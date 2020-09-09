# 순차 탐색\( Sequential Search \)

## 1. 순차 탐색\( Sequential Search \)이란?

* 탐색은 여러 데이터 중에서 원하는 데이터를 찾아내는 것을 의미한다.
* 데이터가 담겨있는 리스트를 앞에서부터 하나씩 비교해서 원하는 데이터를 찾는 방법이다.



#### 예제1

* 임의 리스트가 다음과 같이 rand\_data\_list로 있을 때, 원하는 데이터의 위치를 리턴하는 순차탐색 알고리즘 작성.

```text
from random import *

def sequential(data_list, search_data):
    for index in range(len(data_list)):
        if data_list[index] == search_data:
            return index
    return -1

rand_data_list = list()
for num in range(10):
    rand_data_list.append(randint(1, 100))
    
print(sequential(rand_data_list, 10))
```



## 2. 알고리즘 분석

* 최악의 경우 리스트 길이가 n일 때, n번 비교해야하므로
  * O\(N\)



