# 변수, 조건문, 리스트, 문자열

## 변수

#### 기본 자료형

* 10, 2.2, 'python'을 각각의 변수에 넣고, 각 데이터 타입을 출력하기.

```text
digit1 = 10
digit2 = 2.2
string1 = 'python'

print(type(digit1))   // int
print(type(digit2))   // float
print(type(string1))  // str
```

* 다음 코드를 실행해보고, \t와 \n의 역할을 설명해보기.

```text
code = '000660\n00000102\t12312312'

print (code)

// Result
000660
00000102    12312312
```

* \t : 수평 탭
* \n : 줄바꿈

## 조건문

1. 사용자로부터 두 개의 숫자를 입력 받은 후 큰 숫자를 화면에 출력하기.

```text
digit1 = input()
digit2 = input()

if int(digit1) > int(digit2):
    print(digit1)
else:
    print(digit2)
```

2. 사용자로부터 입력 받은 숫자가 홀수인지 짝수인지 출력하기.

```text
digit1 = input()
digit1 = int(digit1)

if digit1 % 2 == 0:
    print("짝수")
else:
    print("홀수")
```

3. 사용자로부터 세 개의 숫자를 입력 받은 후 가장 작은 숫자를 출력하기.

```text
digit1 = int(input())
digit2 = int(input())
digit3 = int(input())

if digit1 < digit2:
    min = digit1
else:
    min = digit2
    
if min < digit3:
    print(min)
else:
    print(digit3)
```

4. 사용자로부터 점수를 입력 받은 후 등급을 출력하기 \( A: 100 ~ 81, B: 80 ~ 61, C: 60 ~ 0 \)

```text
score = int(input())

if score < 100 and score >= 81:
    print("A")
elif score < 80 and score >= 61:
    print("B")
else:
    print("C")
```

## 리스트

## 문자열



