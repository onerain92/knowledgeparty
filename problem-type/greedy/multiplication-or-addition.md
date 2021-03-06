---
description: '문제 난이도: 하 / 문제 풀이 시간 : 30분 / 시간 제한 : 1초 / 메모리 제한 : 128MB / 기출 : Facebook 인터뷰'
---

# 6. 곱하기 혹은 더하기

## 문제 설명

각 자리가 숫자\( 0부터 9 \)로만 이루어진 문자열 S가 주어졌을 때, 왼쪽부터 오른쪽으로 하나씩 모든 숫자를 확인하며 숫자 사이에 'x' 혹은 '+' 연산자를 넣어 결과적으로 만들어질 수 있는 가장 큰 수를 구하는 프로그램을 작성하세요. 단, + 보다 x를 먼저 계산하는 일반적인 방식과는 달리, 모든 연산은 왼쪽에서부터 순서대로 이루어진다고 가정합니다.

예를 들어 02984라는 문자열이 주어지면, 만들어질 수 있는 가장 큰 수는 \(\(\(\( 0 + 2 \) x 9 \) x 8 \) \* 4 \) = 576 입니다.



#### 입력 조건

* 첫째 줄에 여러 개의 숫자로 구성된 하나의 문자열 S가 주어집니다. \( 1 &lt;= S의 길이 &lt;= 20 \)

#### 출력 조건

* 첫째 줄에 만들어질 수 있는 가장 큰 수를 출력합니다. 

#### 입력 예시

02984

#### 출력 예시

567



## 문제 해설

일반적으로 특정한 두 수에 대하여 연산을 수행할 때, 대부분 '+'보다는 'x'가 더 값을 크게 만든다. 하지만 두 수 중에서 하나라도 '0' 혹은 '1'인 경우, 곱하기보다는 더하기를 수행하는 것이 효율적이다. 예를 들어 1과 2가 있을 때, 1 + 2 = 3이고, 1 x 2 = 2이다.

다시 말해 두 수에 대하여 연산을 수행할 때, 두 수 중에서 하나라도 1 이하인 경우에는 더하며, 두 수가 모두 2 이상인 경우에는 곱하면 된다.

이러한 원리를 이용하면 쉽게 문제를 해결할 수 있다. 현재까지의 계산 결과를 result에 담은 상태로, 매 숫자에 대하여 연산을 수행하면 된다. 그래서 result가 1 이하이거나, 현재 처리하고 있는 숫자가 1 이하라면 더하기 연산을 수행하고, 그렇지 않은 경우 곱하기 연산을 수행하면 항상 최적의 결과를 얻을 수 있다.



## 답안

### 내가 푼 답안

```text
def solution(s):
    result = 0

    for letter in s:
        if result <= 1 or int(letter) <= 1:
            result += int(letter)
        else:
            result *= int(letter)

    return result


print(solution('02984'))
print(solution('567')
```



