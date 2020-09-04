# 삽입 정렬\( Insertion Sort \)

## 삽입 정렬이란?

* 삽입 정렬은 두 번째 인덱스부터 시작한다.
* 해당 인덱스\( key 값 \) 앞에 있는 데이터\(B\)부터 비교해서 key값이 더 작으면 B값을 뒤 인덱스로 복사한다.
* 이를 key 값이 더 큰 데이터를 만날때까지 반복하고 큰 데이터를 만난 위치 바로 뒤에 key 값을 이동시킨다.

![https://ko.wikipedia.org/wiki/%EC%82%BD%EC%9E%85\_%EC%A0%95%EB%A0%AC](../.gitbook/assets/insertion.gif)



## 구현

1. for i in range\(len\(data\)\) 로 반복
2. key = data\[i\]
3. for j in range\(i, 0, -1\) 반복
   1. 내부 반복문 안에서 data\[i\] &lt; data\[j - 1\] 이면,
      1. data\[j - 1\], data\[j\] = data\[j\], data\[j - 1\]

```text
import random

def insertion_sort(arr):
    for i in range(len(arr) - 1):
        for j in range(i + 1, 0, -1):
            if arr[j] < arr[j - 1]:
                arr[j - 1], arr[j] = arr[j], arr[j - 1]
            else:
                break
                
    return arr

random_arr = random.sample(range(100), 50)
print(selection_sort(random_arr))
```





## 알고리즘 분석

* 반복문이 두개 -&gt; O\(n^2\)
  * 최악의 경우, n \* \(n - 1\) / 2
* 완전 정렬이 되어 있는 상태라면 최선은 O\(N\)



