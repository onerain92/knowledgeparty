---
description: LIFO ( Last-In-First-Out )
---

# 스택 \( STACK \)

## 1. 스택이란?

* 스택은 LIFO\(Last-In-First-Out\) 또는 FILO\(First-In-Last-Out\) 데이터 관리 방식을 따름
  * LIFO : 마지막에 넣은 데이터를 가장 먼저 추출하는 데이터 관리 정책
  * FILO : 처음에 넣은 데이터를 가장 마지막에 추출하는 데이터 관리 정책
* 대표적인 스택의 활용
  * 컴퓨터 내부의 프로세스 구조의 함수 동작 방식
* 주요 기능
  * push\(\) : 데이터를 스택에 넣기
  * pop\(\) : 데이터를 스택에서 꺼내기

![Stack](.gitbook/assets/stack%20%281%29.png)



## 2. 구조

* 데이터를 제한적으로 접근할 수 있는 구조
  * 한쪽 끝에서만 자료를 넣거나 뺄 수 있는 구조
* 가장 나중에 쌓은 데이터를 가장 먼저 뺄 수 있는 데이터 구조



## 3. 장단점

#### 장점

* 구조가 단순해서 구현이 쉽다.
* 데이터 저장 / 읽기 속도가 빠르다.

#### 단점 

* 데이터 최대 갯수를 미리 정해야 한다.
  * 파이썬의 경우 재귀 함수는 1000번까지만 호출 가능하다.
* 저장 공간의 낭비가 발생할 수 있다.
  * 미리 최대 갯수만큼 저장 공간을 확보해야 함.
* 스택은 단순하고 빠른 성능을 위해 사용되므로, 보통 배열 구조를 활용해서 구현하는 것이 일반적이다.



## 4. Stack \( Python \)

```text
data_stack = list()

data_stack.append(1) // [1]
data_stack.append(2) // [1, 2]

data_stack.pop() // 2
```



## 5. 연습

```text
stack_list = list()

def push(data):
    stack_list.append(data)

def pop():
    data = stack_list[-1]
    del stack_list[-1]
    return data
    
for index in range(10):
    push(index)
    
pop() // 9
```



