---
description: '문제 난이도: 하 / 문제 풀이 시간 : 20분 / 시간 제한 : 1초 / 메모리 제한 : 128MB'
---

# 3. 왕실의 나이트

## 문제 설명

행복 왕국의 왕실 정원은 체스판과 같은 8 x 8 좌표 평면이다. 왕실 정원의 특정한 한 칸에 나이트가 서 있다. 나이트는 매우 충성스러운 신하로서 매일 무술을 연마한다. 나이트는 말을 타고 있기 때문에 이동을 할 때는 L자 형태로만 이동할 수 있으며 정원 밖으로는 나갈 수 없다. 특정한 위치에서 다음과 같은 2가지 경우로 이동할 수 있다.

1. 수평으로 두 칸 이동한 뒤에 수직으로 한 칸 이동하기.
2. 수직으로 두 칸 이동한 뒤에 수평으로 한 칸 이동하기.

8 x 8 좌표 평면상에서 나이트의 위치가 주어졌을 때 나이트가 이동할 수 있는 경우의 수를 출력하는 프로그램을 작성하시오. 이 때 왕실의 정원에서 행 위치를 표현할 때는 1부터 8로 표현하며, 열 위치를 표현할 때는 a부터 h로 표현한다.

예를 들어 만약 나이트가 a1에 있을 때 이동할 수 있는 경우의 수는 다음 2가지이다. a1의 위치는 좌표 평면에서 구석의 위치에 해당하며 나이트는 정원의 밖으로는 나갈 수 없기 때문이다.

1. 오른쪽으로 두 칸 이동 후 아래로 한 칸 이동하기\( c2 \)
2. 아래로 두 칸 이동 후 오른쪽으로 한 칸 이동하기\( b3 \)

또 다른 예로 나이트가 c2에 위치해 있다면 나이트가 이동할 수 있는 경우의 수는 6가지이다.

#### 입력 조건

* 첫째 줄에 8 x 8 좌표 평면상에서 현재 나이트가 위치한 곳의 좌표를 나타내는 두 문자로 구성된 문자열이 입력된다. 입력 문자는 a1처럼 열과 행으로 이뤄진다.

#### 출력 조건

* 첫째 줄에 나이트가 이동할 수 있는 경우의 수를 출력하시오.

#### 입력 예시

a1

#### 출력 예시

2



## 문제 해설

나이트가 이동할 수 있는 경로를 하나씩 확인하여 이동하면 된다. 다만, 8 x 8 좌표 평면을 벗어나지 않도록 꼼꼼하게 검사하는 과정이 필요하다. 나이트는 2가지 경로로 움직일 수 있다고 했다.

1. 수평으로 두 칸 이동한 뒤에 수직으로 한 칸 이동하기.
2. 수직으로 두 칸 이동한 뒤에 수평으로 한 칸 이동하기.

나이트의 이동 경로를 DIRECTIONS 변수에 넣는다면, 이 2가지 규칙에 따라 DIRECTIONS = \[\(-2, -1\), \(-2, 1\), \(-1, -2\), \(-1, 2\), \(2, -1\) ,\(2, 1\) ,\(1, -2\) ,\(1, 2\)\]로 값을 대입할 수 있다. 현재 위치를 기준으로 아래쪽과 오른쪽은 양수의 값을, 위쪽과 왼쪽은 음수의 값을 대입한 결과이다. 이제 나이트의 현재 위치가 주어지면 현재 위치에서 이동 경로를 더한 다음, 8 x 8 좌표 평면에 있는지 반목문으로 확인하여 처리할 수 있다.



## 답안

### 내가 푼 답안

```text
def solution(location):
    DIRECTIONS = [(-2, -1), (-2, 1), (-1, -2), (-1, 2), (2, -1) ,(2, 1) ,(1, -2) ,(1, 2)]
    x, y = int(ord(location[0])) - int(ord('a')) + 1, int(location[1])
    count = 0

    for direction in DIRECTIONS:
        dx, dy = direction
        nx, ny = x + dx, y + dy

        if vaild_coordinate(nx, ny):
            count += 1

    return count


def vaild_coordinate(x, y):
    return 1 <= x < 9 and 1<= y < 9

print(solution("c2"))
```



### 다른 답안

```text
input_data = input()

row = int(input_data[1])
column = int(ord(input_data[0])) - int(ord('a')) + 1

steps = [(-2, -1), (-2, 1), (-1, -2), (-1, 2), (2, -1) ,(2, 1) ,(1, -2) ,(1, 2)]

result = 0
for step in steps:
    next_row = row + step[0]
    next_column = column + step[1]
    
    if next_row >= 1 and next_row <= 8 and next_column >= 1 and next_column <= 8:
        result+=1

 print(result) 
```





