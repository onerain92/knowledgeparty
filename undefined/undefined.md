# 입출력, 형변환

## 출력

1. "Hello World!" 출력하기.

```text
print("Hello World");
```

2. "I don't like a C langauge." 출력하기.

```text
print("I don't like a C language.");
print('I dont\'t like a C language.');
```

3. print 함수를 이용해 3.1415 출력하기. \( 단, 소수점 아래는 첫 째자리까지만 표시 \)

```text
print('The answer is %0.1f' % 3.1415);
```

## 형변환

1. 문자열 '1980'을 정수형으로 변환하고, 정수 1080을 문자열 '1080'으로 변환하.

```text
string = '1980'
print(type(string)) // str
string = int(string)
print(type(string)) // int

num = 1080;
print(type(num)) // int
num = str(num);
print(type(num)) // str
```

## 연산

1. 숫자 3, 6을 변수에 할당하고 두 변수를 더한 값, 뺀 값, 곱한 값, 나눈 값을 출력하기.

```text
num1 = 3
num2 = 6
print(num1 + num2) // 9
print(num2 - num1) // 3
print(num1 * num2) // 18
print(num2 / num1) // 2

num3 = '1'
num 4 = '2'
print(num1 + num2) // '12'
```

2. 밑이 5이고 지수가 2인 거듭제곱 구하기.

```text
print(5**2) // 25
```

3. 사용자로부터 2개의 숫자를 입력받은 후 2개의 숫자를 더한 값, 뺀 값, 곱한 값, 나눈 값, 몫, 나머지를 각각 출력하기.

```text
num1 = input()
num1 = int(num1)
num2 = input()
num2 = int(num2)

print(num1 + num2)
print(num1 - num2)
print(num1 * num2)
print(num1 / num2)
print(num1 // num2)
print(num1 % num2)
```

