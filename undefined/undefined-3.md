# 튜블, 딕셔너리, 집합

## 튜플

1. a, b, c, d, e를 저장하는 튜플을 만들고 첫 번째 튜플값과 마지막 번째 튜플값을 출력하세요.

```text
tuple_data = ("a", "b", "c", "d", "e")

print(type(tuple_data)) // tuple
print(tuple_data[0], tuple_data[4])
```

2. 다음 코드를 작성해서 실행해보고 에러가 나는 이유를 설명하세요.

* 실행코드

  ```text
  tupledata = ('dave', 'fun-coding', 'endless')
  tupledata[0] = 'david'
  ```

* 에러

  ```text
  TypeError                                 Traceback (most recent call last)
  <ipython-input-2-db4a259aad24> in <module>()
        1 tupledata = ('dave', 'fun-coding', 'endless')
  ----> 2 tupledata[0] = 'david'

  TypeError: 'tuple' object does not support item assignment
  ```

  =&gt; 튜플 데이터는 바꿀 수 없기 때문

2. 다음 코드를 읽고, 최종적으로 var1과 var2의 값이 어떤 값이될지 확인해보고, 왜 이렇게 동작하는지 튜플을 기반으로 설명하세요.

* 실행코드

  ```text
  var1, var2 = 1, 2
  var1, var2 = var2, var1
  ```

=&gt; 튜플의 해체할당기능을 통해 바로 바꿔줄 수 있습니다.

3. 다음 코드에서 두 번째 데이터부터 마지막 데이터를 출력하세요

```text
tupledata = ('fun-coding1', 'fun-coding2', 'fun-coding3', 'fun-coding4', 'fun-coding5')

print(tupledata[1:])
```

4. 다음 튜플 데이터를 리스트 데이터로 변환한 후에 'fun-coding4' 데이터를 마지막에 추가하고, 다시 튜플 데이터로 변환하세요.

```text
tupledata = ('fun-coding1', 'fun-coding2', 'fun-coding3')

listdata = list(tupledata)
listdata.append("fun-coding4")
tupledata = tuple(listdata)
```

5. 비어 있는 튜플, 리스트, 딕셔너리 변수를 하나씩 각각 만드세요.

```text
tupledata = tuple()
listdata = list()
dictdata = dict()
```

## 딕셔너리

1. 다음 영어 사전 데이터를 딕셔너리 변수로 만들고, 딕셔너리 변수의 key 값인 영어단어, value 값인 의미 만을 가진 리스트 변수를 각각 만들고, 두 리스트 변수를 출력하세요.

| 영어단어 | 의미 |
| :--- | :--- |
| environment | 환경 |
| company | 회사 |
| government | 정부, 정치 |
| face | 얼굴 |

```text
dictdata = {"environment": "환경", "company": "회", "government": "정", "face": "얼굴"}
dictdata_keys = [data for data in dictdata.keys()]
dictdata_values = [data for data in dictdata.values()]

print(dictdata_keys)
print(dictdata_values)
print(dictdata.keys())
print(dictdata.values())
```

2. 다음 영어 사전 데이터를 딕셔너리 변수로 만들어서 다음과 같이 출력하세요. 단, 반복문을 사용하세요.

| 영어단어 | 의미 |
| :--- | :--- |
| environment | 환경 |
| company | 회사 |
| government | 정부, 정치 |
| face | 얼굴 |

```text
environment : 환경
company : 회사
gonernment : 정부, 정치
face : 얼굴
```

```text
dictdata = {"environment": "환경", "company": "회", "government": "정", "face": "얼굴"}

for data in dictdata.keys():
    print(data, ":" , dictdata[data])
```

3. 다음 영어 사전 데이터를 딕셔너리 변수로 만들고 외움표시가 X 인 영어단어만 출력하세요. 단, key는 영어단어, value는 의미와 외움표시 두 데이터를 넣습니다.

| 영어단어 | 의 | 외움표시 |
| :--- | :---: | :---: |
| environment | 환경 | X |
| company | 회사 | O |
| government | 정부 | X |
| face | 얼굴 | X |

```text
environment : 환경
company : 회사
gonernment : 정부, 정치
face : 얼굴
```

```text
dictdata = {"environment": ["환경", "X"], "company": ["회사", "O"], "government": ["정부", "X"], "face": ["얼굴", "X"]}

for data in dictdata:
    if dictdata[data][1] == "X":
        print(data, ":", dictdata[data][0])
```

4. 다음 영어 사전 데이터를 딕셔너리 변수로 만들고 사용자로부터 영어단어를 입력받으면 해당 영어단어의 외움표시를 O로 수정하고, 외움표시가 X 인 단어만 출력하는 프로그램을 작성하세요. 단, key는 영어단어, value는 의미와 외움표시 두 데이터를 넣습니다.

| 영어단어 | 의 | 외움표시 |
| :--- | :---: | :---: |
| environment | 환경 | X |
| company | 회사 | O |
| government | 정부 | X |
| face | 얼굴 | X |

```text
environment : 환경
company : 회사
gonernment : 정부, 정치
face : 얼굴
```

```text
dictdata = {"environment": ["환경", "X"], "company": ["회사", "O"], "government": ["정부", "X"], "face": ["얼굴", "X"]}

data = input()
dictdata[data][1] = "O"

for data in dictdata:
    if dictdata[data][1] == "X":
        print(data, ":", dictdata[data][0])
```

5. 다음 dict\_all, dict2, dict3 딕셔너리 변수가 있을 때, dict2와 dict3 두 데이터를 dict\_all 딕셔너리 변수에 추가한 후, dict\_all 변수를 출력하세요.

```text
dict_all = {'environment': '환경', 'gonernment':'정부, 정치'}
dict2 = {'company': '회사', 'face':'얼굴'}
dict3 = {'apple': '사과'}

for data in dict2.keys():
    dict_all[data] = dict2[data]

for data in dict3.keys():
    dict_all[data] = dict3[data]
    
print(dict_all)
```

6. 다음 actor\_info 딕셔너리 변수를 만들고, 홈페이지, 배우 이름, 최근 출연 영화 갯수를 다음과 같이 출력하세요

```text
actor_info = {'actor_details': {'생년월일': '1971-03-01',
                   '성별': '남',
                   '직업': '배우',
                   '홈페이지': 'https://www.instagram.com/madongseok'},
 'actor_name': '마동석',
 'actor_rate': 59361,
 'date': '2017-10',
 'movie_list': ['범죄도시', '부라더', '부산행']}
```

```text
print("Actor name: ", actor_info["actor_name"])
print("Homepage: ", actor_info["actor_details"]["홈페이"])
print("movie list: ", actor_info["movie_list"])
```

7. number\_list가 다음과 같은 리스트일 때 중복 숫자를 제거한 리스트를 만들고, 출력하세요

```text
number_list = [5, 1, 2, 2, 3, 3, 4, 5, 5, 6, 7, 8, 9, 9, 10, 10]

number_set = set(number_list)
print(number_set)
```



## 집합 

