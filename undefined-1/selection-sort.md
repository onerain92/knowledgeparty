# 선택정렬\( Selection Sort \)

## 선택정렬이란? 

* 다음과 같은 순서를 반복하며 정렬하는 알고리즘
  * 주어진 데이터 중 최솟값을 찾는다.
  * 해당 최솟값을 데이터 맨 앞에 위치한 값과 교체한다.
  * 맨 앞의 위치를 뺀 나머지 데이터를 동일한 방법으로 반복한다.

![https://ko.wikipedia.org/wiki/%EC%84%A0%ED%83%9D\_%EC%A0%95%EB%A0%AC](../.gitbook/assets/selection.gif)



## 구현

1. for i in range\(len\(data\) - 1\) 로 반복
2. min\_index = i 로 놓고
3. for j in range\(i + 1, len\(data\)\) 반복
   1. 반복문 내부에서 data\[min\_index\] &gt; data\[j\] 이면,
      1. min\_index = j
4. data\[i\], data\[min\_index\] = data\[min\_index\], data\[i\] 로 자리바

```text
import random


def selection_sort(arr):
    length = len(arr)

    for i in range(length - 1):
        min_index = i
        for j in range(i + 1, length):
            if arr[min_index] > arr[j]:
                min_index = j

        arr[i], arr[min_index] = arr[min_index], arr[i]

    return arr


random_arr = random.sample(range(100), 50)
print(selection_sort(random_arr))
```



## 알고리즘 분석

* 반복문이 두개 O\(n^2\)
  * 실제로 상세하게 계산하면, n\*\(n-1\) / 2



