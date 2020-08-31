---
description: 파이썬에서는 자주 사용되는 함수를 내장 함수( Built-in Functions )라는 이름으로 기본적으로 제공한다.
---

# 내장 함수

## 내장 함수 종류

| abs\(\) | dict \(\) | help \(\) | min \(\) | setattr\(\) |
| :--- | :--- | :--- | :--- | :--- |
| all\(\) | dir\(\) | hex\(\) | next\(\) | slice\(\) |
| any\(\) | divmod\(\) | id\(\) | object\(\) | sorted\(\) |
| ascii\(\) | enumerate\(\) | input\(\) | oct\(\) | staticmethod\(\) |
| bin\(\) | eval\(\) | int\(\) | open\(\) | str\(\) |
| bool\(\) | exec\(\) | isinstance\(\) | ord\(\) | sum\(\) |
| bytearray\(\) | filter\(\) | issubclass\(\) | pow\(\) | super\(\) |
| bytes\(\) | float\(\) | iter\(\) | print\(\) | tuple\(\) |
| callable\(\) | format\(\) | len\(\) | property\(\) | type\(\) |
| chr\(\) | frozenset\(\) | list\(\) | range\(\) | vars\(\) |
| classmethod\(\) | getattr\(\) | locals\(\) | repr\(\) | zip\(\) |
| compile\(\) | globals\(\) | map\(\) | reversed\(\) | **import**\(\) |
| complex\(\) | hasattr\(\) | max\(\) | round\(\) |  |
| delattr\(\) | hash\(\) | memoryview\(\) | set\(\) |  |



## Filter

filter란 무엇인가를 걸러낸다는 뜻으로 filter 함수도 동일한 의미를 가진다.

* filter 함수는 첫 번째 인수로 함수 이름을, 두 번째 인수로 그 함수에 차례로 들어갈 반복 가능한 자료형을 받는다.
* 그리고 두 번째 인수인 반복 가능한 자료형 요소가 첫 번째 인수인 함수에 입력되었을 때 반환 값이 참인 것만 묶어서 반환한다.

```text
def positive(l):
    result = []
    
    for i in l:
        if i > 0:
            result.append(i)
    
    return result

print(positive([1, -3, 2, 0, -5, 6])) // [1, 2, 6]
```

위에서 만든 positive 함수는 리스트를 입력값으로 받아 각각의 요소를 판별해서 양수 값만 돌려주는 함수이다.

filter함수를 사용하면 위 코드를 다음과 같이 작성할 수 있다.

```text
def positive(x):
    return x > 0
    
print(list(filter(positive, [1, -3, 2, 0, -5, 6]))) // [1, 2, 6]
```

여기에서는 두 번쨰 인수인 리스트의 요소들이 첫 번째 인수인 positive 함수에 입력되었을 때 반환 값이 참인 것만 묶어서 돌려준다.

위 코드는 lambda를 사용하면 더욱 간편하게 코드를 작성할 수 있다.

```text
list(filter(lambda x: x > 0, [1, -3, 2, 0, -5, 6])) // [1, 2, 6]
```

## ZIP

* **zip\(\*iterable\)**은 동일한 개수로 이루어진 자료형을 묶어주는 역할을 하는 함수이다.

```text
list(zip([1, 2, 3], [4, 5, 6]))
=> [(1, 4), (2, 5), (3, 6)]

list(zip([1, 2, 3], [4, 5, 6], [7, 8, 9]))
=> [(1, 4, 7), (2, 5, 8), (3, 6, 9)]

list(zip("abc", "def"))
=> [('a', 'd'), ('b', 'e'), ('c', 'f')]
```



## ENUMERATE

* '열거하다' 라는 뜻이다.
* 이 함수는 순서가 있는 자료형\( 리스트, 튜플, 문자열 \)을 입력으로 받아 인덱스 값을 포함하는 enumerate 객체를 돌려준다.
* 자료형의 현재 순서\( index \)와 그 값을 쉽게 알 수 있다.

```text
for i, name in enumerate(['body', 'foo', 'bar']):
    print(i, name)
    
# 0, body
# 1, foo
# 2, bar
```



