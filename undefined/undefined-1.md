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

1. 사용자로부터 주민등록번호를 입력받아 출생 연도를 출력하기.  
    e.g.\) 184638 - 1746283 를 입력받으면 18을 출력하면 됨.

```text
personalId = "184638 - 1746283"

print(personalId[0:2])
```

2. 사용자로부터 주민등록번호를 입력받아 뒷자리 맨 앞의 숫자를 출력하기.  
    e.g.\) 주민등록번호 뒷자리의 맨 앞자리는 성별을 나타냄.  
             184638 - 1746283 를 입력받으면 1을 출력하면 됨.  
             1은 남성을 의미, 2는 여성의 의미, 현재는 3과 4를 사용함.

```text
personalId = "184638 - 1746283"

print(personalId[9])
```

3. 사용자로부터 주민등록번호를 입력받아 성별을 '남성' 또는 '여성'으로 출력하기.

```text
personalId = "184638 - 1746283"

if personalId[9] == "1":
    print("남성")
elif personalId[9] == "2":
    print("여")
else:
    print("잘못된 주민등록번호입니다.")
```

## 문자열

1. 다음 문자열에서 ...을 제거하기.  
    e.g.\) mystr = "a man goes into the room..."  
        =&gt;  "a man goes into the room"

```text
mystr = "a man goes into the room..."

print(mystr.strip("."))
```

2. 주식 종목을 나타내는 종목코드에서 공백과 줄바꿈 기호가 포함되어 있다. 공백과 줄바꿈 기호를 제거하고 종목코드만 추출하기.

```text
code = "             000660\n       "

print(code.strip(" \n"))
```

3. 다음 문자열에서 'Python' 문자열의 빈도수를 출력하기.

```text
desc = "Python is an interpreted high-level programming language for general-purpose programming. Created by Guido van Rossum and first released in 1991, Python has a design philosophy that emphasizes code readability, notably using significant whitespace."

print(desc.count("Python")) // 2
```

4. 다음 문자열에서 'p' 문자열의 빈도수를 출력하기.

```text
desc = "Python is an interpreted high-level programming language for general-purpose programming. Created by Guido van Rossum and first released in 1991, Python has a design philosophy that emphasizes code readability, notably using significant whitespace."
countDesc = desc.dount("p")

print(countDesc) // 9
```

5. letters라는 변수에 들어있는 문자열에서 두 번째와 네 번째 문자를 출력하기.

```text
letters = "python"

print(letters[1], letters[3]) // y, h
```

6. letters 라는 변수에 사용자로부터 문자열을 입력받아서 문자 n 이 들어있는지를 출력하기.  
    \( n 이 들어 있으면 0, 안들어있으면 -1을 출력하라\)

```text
letters = input()

if letters.find("n") >= 0:
    print("0");
else:
    print("-1")
```

7. letters 라는 변수에 사용자로부터 문자열을 입력받아서 문자 n 이 들어있는지를 출력하기.  
    n 이 들어 있으면 'n 이 들어있습니다.', 안들어있으면 'n 이 안들어있습니다.' 를 출력하기.

```text
letters = input()

if letters.find("n") >= 0:
    print("n이 있습니다.");
else:
    print("n이 습니다.")
```

8. 주민등록번호의 뒷 자리 7자리 중 두번째부터 세번째는 출생 지역 코드입니다.  
    다음 표를 참조하여 사용자로부터 주민 등록 번호를 입력 받은 후 출생지를 출력하세요.

| 지역 코드 | 출생 지역 |
| :--- | :--- |
| 00 ~ 08 | 서울 |
| 09 ~ 12 | 부산 |

```text
personalId = input()
regionCode = int(personalId[8:10])

if regionCode >= 0 and regionCode <= 8:
    print("서울");
elif regionCode >= 9 and regionCode <= 12:
    print("부산");
```

9. letters 라는 변수에 Dave,David,Andy 가 들어있다. 해당 변수값을 , 를 기준으로 분리해서 출력하기.  
    e.g.\) \['Dave', 'David', 'Andy'\]

```text
letters = "Dave, David, Andy"

print(letters.split(","))
```

10. 다음과 같은 파일 이름\(확장자 포함\)에서 확장자를 제거한 파일 이름만 출력하.

```text
filename = "exerciese01.docx"
filenameList = filename.split(".")

print(filenameList[0])
```

