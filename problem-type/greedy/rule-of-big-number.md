---
description: '문제 난이도: 하 / 문제 풀이 시간 : 30분 / 시간 제한 : 1초 / 메모리 제한 : 128MB'
---

# 2. 큰 수의 법칙

## 문제 설명

다양한 수로 이루어진 배열이 있을 때 주어진 수들을 M번 더하여 가장 큰 수를 만드는 법칙이다. 단, 배열의 특정한 인덱스\( 번호 \)에 해당하는 수가 연속해서 K번을 초과하여 더해질 수 없는 것이 이 법칙의 특징이다. 예를 들어, 순서대로 2, 4, 5, 4, 6으로 이루어진 배열이 있을 때 M이 8이고, K가 3이라고 가정하자. 이 경우 특정한 인덱스의 수가 연속해서 세 번까지만 더해질 수 있으므로 큰 수의 법칙에 따른 결과는 6 + 6 + 6 + 5 + 6 + 6 + 6 + 5인 46이다.

단, 서로 다른 인덱스에 해당하는 수가 같은 경우에도 서로 다른 것으로 간주한다. 예를 들어 순서대로 3, 4, 3, 4, 3으로 이루어진 배열이 있을 때 M이 7이고, K가 2라고 가정하자. 이 경우 두 번째 원소에 해당하는 4와 네 번째 원소에 해당하는 4를 번갈아 두 번씩 더하는 것이 가능하다. 결과적으로 4 + 4 + 4 + 4 + 4 + 4 + 4인 28이 도출된다.

배열의 크기 N, 숫자가 더해지는 횟수 M, 그리고 K가 주어질 때 큰 수의 법칙에 따른 결과를 출력하시오.

#### 입력 조건

* 첫째 줄에 N\( 2 &lt;= N &lt;= 1,000 \), M\( 1 &lt;= M &lt;= 10,000 \), K\(  1 &lt;= K &lt;= 10,000 \)의 자연수가 주어지며, 각 자연수는 공백으로 구분한다.
* 둘째 줄에 N개의 자연수가 주어진다. 각 자연수는 공백으로 구분한다. 단, 각각의 자연수는 1이상 10,000 이하의 수로 주어진다.
* 입력으로 주어지는 K는 항상 M보다 작거나 같다.

#### 출력 조건

* 첫째 줄에 큰 수의 법칙에 따라 더해진 답을 출력한다.

#### 입력 예시

5 8 3  
2 4 5 4 6

#### 출력 예시

46



### 문제해설

이 문제를 해결하기 위해 입력값 중에서 가장 큰 수와 두 번째로 큰 수만 저장하면 된다. 연속으로 더할 수 있는 횟수는 최대 K번이므로 _**'가장 큰 수를 K번 더하고 두 번째로 큰 수를 한 번 더하는 연산'**_ 을 반복하면 된다.



### 내가 푼 답안

```text
def solution(N, M, K, arr):
    arr.sort(reverse=True)
    first_value = arr[0]
    second_value = arr[1]
    result = 0

    while True:
        for i in range(K):
            if M == 0:
                break
            result += first_value
            M -= 1

        if M == 0:
            break;

        result += second_value
        M -= 1

    return result


print(solution(5, 8, 3, [2, 4, 5, 4, 6]))
```



### 다른 답안

```text
def solution(N, M, K, arr):
    arr.sort()
    first_value = arr[N - 1]
    second_value = arr[N - 2]

    count = int(m / (k + 1)) * k
    count += m % (k + 1)
    
    result = 0
    result += count * first_value
    result += ( m - count ) * second_value

    return result


print(solution(5, 8, 3, [2, 4, 5, 4, 6]))
```



