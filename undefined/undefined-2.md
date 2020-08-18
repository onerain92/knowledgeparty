# 반복문

## 반복문

1. 1 ~ 10까지의 숫자에 대해 모두 더한 값을 출력하는 프로그램을 for 문을 사용하여 작성하.

```text
total = 0

for num in range(1, 11):
    total += num

print("Total: ", total) // 55
```

2. 사용자로부터 2 ~ 9 사이의 숫자를 입력 받은 후, 해당 숫자에 대한 구구단을 출력하기.

```text
digit = int(input())

for num in range(1, 10):
    print(digit, "X", num, "=", digit * num)
```

3. 사용자로부터 , 로 구분된 여러 이름을 입력받아서, 한 줄에 하나씩 이름을 출력하기.

* 사용자 입력: Dave,David,Andy,Arthor
* 출력 예: Dave David Andy Arthor

```text
strings = input()

for string in strings.split(","):
    print(string)
```

4. 사용자로부터 \[이름1\],\[이름2\],\[이름3\] 과 같은 형식으로 데이터를 입력받아서, 한 줄에 하나씩 이름을 출력하기.

* 사용자 입력: \[Dave\],\[David\],\[Andy\],\[Arthor\]
* 출력 예: Dave David Andy Arthor

```text
strings = input()

for string in strings.split(","):
    print(string.strip("[]"))
```

5. 1부터 30까지의 숫자 중 3의 배수만 출력하기.

```text
for num in range(1, 31):
    if num % 3 == 0:
        print(num)
```

6. 1부터 100까지 숫자를 모두 더한 값을 출력하세요. 단, while 구문을 사용해서 작성하세요.

```text
total = 0
count = 1

while count < 101:
    total += count
    count++
    
print(total)
```

7. 사용자로부터 4자리의 숫자로 구성된 데이터를 입력받아서 비밀번호와 같으면 '비밀번호가 맞습니다.'를 출력하고 종료하세요. 비밀번호와 다르면 '비밀번호가 틀렸습니다.'를 출력하고 다시 사용자로부터 데이터를 입력받으세요. 비밀번호는 4312 입니다.

```text
password = "4312"
data = str()

while data != password:
    data = input()
    
    if data == password:
        print("비밀번호가 맞씁니다.")
        break
    else:
        print("비밀번호가 틀렸습니다.")
```

8. 다음 리스트 변수에서 음수 데이터를 삭제하고, 양수만 가진 리스트 변수로 만들고, 해당 변수를 출력하세요.

```text
num_list = [0, -11, 31, 22, -11, 33, -44, -55]
num_list2 = list()

for index, num in enumerate(num_list):
    if num >= 0:
        num_list2.append(num)
        
print(num_list2)
```

9. 다음 리스트에 있는 데이터의 길이를 한 라인에 하나씩 출력하세요.

```text
list_data = ["fun-coding", "Dave", "Linux", "Python", "javascript", "front-end", "back-end", "dataengineering"]

for data in list_data:
    print(data + "\"" + "'s length is ", len(data))
```

10. 다음 리스트에 있는 숫자를 역 방향으로 출력하세요. 단, 리스트에 있는 숫자들은 한 라인에 하나씩 출력하세요.

```text
data = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
data.reverse()

for item in data:
    print(data)
```

11. 다음과 같이 파일 이름\(확장자 포함\) 저장하고 있는 리스트가 있을 때 확장자를 제거하고 파일 이름만 출력하세요.

```text
filelist = ['exercise01.docx', 'exercise02.docx', 'exercise03.docx', 'exercise04.docx', 'exercise05.docx']

for item in filelist:
    print(item.split(".")[0])
```

12. 파일 이름이 다음과 같은 리스트에 저장되어 있을 때 확장자가 .txt 인 파일에 대한 리스트를 출력하기.

```text
filelist = ['exercise01.docx', 'exercise02.csv', 'exercise03.txt', 'exercise04.hwp']

for item in filelist:    
    if item.split(".")[1] == "txt":
        print(item)
```

13. prices 변수에 입력된 값을 원 화로 바꿔서 계산하세요.

* 환율은 다음과 같음

  | 통화단위 | 원화 환율 |
  | :--- | :--- |
  | 달러 | 1112 |

출력:  
111200 원

```text
prices = '100 달러'
price = prices.split()

print(int(price[0]) * 1112, "원")
```

14. 사용자로부터 달러 또는 위안 금액을 입력받은 후 이를 원으로 바꿔서 계산하세요.

* 사용자는 100 달러, 100 위안 과 같이 금액과 통화명 사이에 공백을 넣어 입력합니다.
  * 각 통화별 환율은 다음과 같습니다.

    | 통화단위 | 원화 환율 |
    | :--- | :--- |
    | 달러 | 1112 |
    | 위안 | 171 |

출력:  
111200 원

```text
prices = input()
price = prices.split()

if price[1] == "달러":
    print(int(price[0]) * 1112, "원")
elif price[1] == "위안":
    print(int(price[0]) * 171, "")
```

## 딕셔너리

1. 다음 통화별 환율을 통화단위와 원화 환율을 가진 딕셔너리로 만들고 사용자로부터 달러, 엔, 또는 위안 금액을 입력받은 후 이를 원으로 바꿔서 계산하세요.

   * 사용자는 100 달러, 100 위안 과 같이 금액과 통화명 사이에 공백을 넣어 입력하기로 합니다.

   | 통화단위 | 원화 환율 |
   | :--- | :--- |
   | 달러 | 1112 |
   | 위안 | 171 |
   | 엔 | 1010 |

```text
exchange = {"달러": 1112, "위안": 171, "엔": 1010}
prices = input()
price = prices.split()

if price[1] == "달러" or price[1] == "위안" or price[1] == "":
    print(int(price[0]) * exchange[price[1]], "원")
```

## 이중 반복문

1. 구구단을 2단부터 9단까지 다음과 같이 출력하세요

```text
2 X 1 = 2
2 X 2 = 4
2 X 3 = 6
2 X 4 = 8
2 X 5 = 10
2 X 6 = 12
2 X 7 = 14
2 X 8 = 16
2 X 9 = 18
3 X 1 = 3
3 X 2 = 6
.
.
.
9 X 7 = 63
9 X 8 = 72
9 X 9 = 81
```

```text
for i in range(2, 10):
    for j in range(1, 10):
        print(i, "X", j, "=", i * j)
```

2. 구구단을 2단부터 9단까지 출력하되, 계산 값이 짝수인 경우에만 출력하세요

* 예: 3 X 3 = 9 에서 9는 홀수이므로 출력하지 않는다.
* 예: 2 X 4 = 8 에서 8은 짝수이므로 출력한다.

```text
for i in range(2, 10):
    for j in range(1, 10):
        if (i * j) % 2 == 0:
            print(i, "X", j, "=", i * j)
```

3. 아파트 동호수를 다음과 같은 두 리스트 변수를 활용해서 출력하세요.

* 단, 각 동과 동 사이에는 구분이 되도록 한 라인씩 띄워서 출력하세요

```text
dongs = ["6209동", "6208동", "6207동"]
hos = ["101호", "102호", "103호", "104호"]
```

```text
for dong in dongs:
    for ho in hos:
        print(dong, ho)
```

