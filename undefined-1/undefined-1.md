# 버블 정렬\( Bubble Sort \)

## 버블 정렬이란?

* 두 인접한 데이터를 비교해서 앞에 있는 데이터가 뒤에 있는 데이터보다 크면 자리를 바꾸는 정렬 알고리즘.

![https://en.wikipedia.org/wiki/Bubble\_sort](../.gitbook/assets/bubble.gif)



## 구현

* 특이점 찾아보기
  * n개의 리스트가 있는 경우 최대 n - 1번의 로직을 적용한다.
  * 로직을 1번 적용할 때마다 가장 큰 숫자가 뒤에서부터 1개씩 결정된다.
  * 로직이 경우에 따라 일찍 끝날 수도 있다. 따라서 로직을 적용할 때 한 번도 데이터가 교환된 적이 없다면 이미 정렬된 상태이므로 더 이상 로직을 반복 적용할 필요가 없다.



```text
import random

def bubble_sort(arr):
    length = len(arr) - 1

    for i in range(length):
        swap = False
        for j in range(length - i):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
                swap = True
        
        if swap == False:
            break

    return arr
    

random_arr = random.sample(range(100), 50)
bubble_sort(random_arr)
```



## 알고리즘 분석

* 데이터의 길이 N
* 반복문이 두 개 -&gt; O\(n^2\)
  * 최악의 경우, n\*\(n - 1\) / 2 
* 완전 정렬이 되어 있는 상태라면 최선은 O\(N\)



