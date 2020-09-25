# 이진탐색

## 범위를 반씩 좁혀가는 탐색

* 배열 내부의 데이터가 정렬되어 있어야만 사용할 수 있는 알고리즘
* 탐색 범위를 절반씩 좁혀가며 데이터를 탐색한다.
* 이진탐색은 위치를 나타내는 변수 3개를 사용하는데 탐색하고자 하는 범위의 **시작점**, **끝점** 그리고 **중간점**이다.
* **찾으려는 데이터와 중간점 위치에 있는 데이터를 반복적으로 비교**해서 원하는 데이터를 찾는다.
* 이진 탐색은 한 번 확인할 때마다 확인하는 원소의 개수가 절반씩 줄어든다는 점에서 시간 복잡도가 O\( log N \)이다.
* 이진 탐색을 구현하는 방법에는 2가지 있으며, 하나는 재귀 함수를 이용하는 방법이고, 다른 하나는 단순하게 반복문을 이용하는 방법이다.
* 이진 탐색 문제는 입력 데이터가 많거나, 탐색 범위가 매우 넓은 편이다. 예를 들어 데이터의 개수가 1,000만 개를 넘어가거나 탐색 범위의 크기가 1,000억 이상이라면 이진 탐색 알고리즘을 의심해보자.
* 그런데 이렇게 입력 데이터의 개수가 많은 문제에 input\(\) 함수를 사용하면 동작 속도가 느려서 시간 초과로 오답 판정을 받을 수 있다. 이처럼 입력 데이터가 많은 문제는 sys 라이브러리의 readline\(\) 함수를 이용하면 시간 초과를 피할 수 있다.

```text
import sys
# 하나의 문자열 데이터 입력받기
input_data = sys.stdin.readline().rstrip()

# 입력받은 문자열 그대로 출력
print(input_data)
```



### 재귀 함수로 구현한 이진 탐색

```text
def recursive_binary_search(array, target, start, end):
    if start > end:
        return None

    mid = (start + end) // 2
    if array[mid] == target:
        return mid
    elif array[mid] > target:
        return binary_search(array, target, start, mid - 1)
    else:
        return binary_search(array, target, mid + 1, end)
        
        
n, target = list(map(int, input().split()))
array = list(map(int, input().split()))

result = loop_binary_search(array, target, 0, n - 1)
if result == None:
    print('원소가 존재하지 않습니다.')
else:
    print(result + 1)
```



### 반복문으로 구현한 이진 탐색

```text
def loop_binary_search(array, target, start, end):
    while start <= end:
        mid = (start + end) // 2

        if array[mid] == target:
            return mid
        elif array[mid] > target:
            end = mid - 1
        else:
            start = mid + 1

    return None
    

n, target = list(map(int, input().split()))
array = list(map(int, input().split()))

result = loop_binary_search(array, target, 0, n - 1)
if result == None:
    print('원소가 존재하지 않습니다.')
else:
    print(result + 1)
```



