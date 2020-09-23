---
description: '문제 난이도: 하 / 문제 풀이 시간 : 15분 / 시간 제한 : 1초 / 메모리 제한 : 128MB'
---

# 상하좌우

## 문제설명

여행가 A는 N x N 크기의 정사각형 공간 위에 서 있다. 이 공간은 1 x 1 크기의 정사각형으로 나누어져 있다. 가장 왼쪽 위 좌표는 \( 1, 1 \)이며, 가장 오른쪽 아래 좌표는 \( N, N \)에 해당한다. 여행가 A는 상, 하, 좌, 우 방향으로 이동할 수 있으며, 시작 좌표는 항상 \( 1, 1 \)이다. 우리 앞에는 여행가 A가 이동할 계획이 적힌 계획서가 놓여 있다. 계획서에는 하나의 줄에 띄어쓰기를 기준으로 하여 L, R, U, D 중 하나의 문자가 반복적으로 적혀있다. 각 문자의 의미는 다음과 간다.

* L : 왼쪽으로 한 칸 이동
* R : 오른쪽으로 한 칸 이동
* U : 위로 한 칸 이동
* D : 아래로 한 칸 이동

이 때 여행가 A가 N x N 크기의 정사각형 공간을 벗어나는 움직임은 무시된다. 예를 들어 \( 1, 1 \)의 위치에서 L 혹은 U를 만나면 무시된다. 다음은 N = 5인 지도와 계획서이다.

이 경우 6개의 명령\( RRRUDD \)에 따라서 여행가가 움직이게 되는 위치는 순서대로 \( 1, 2 \), \( 1, 3 \), \( 1, 4 \), \( 1, 4 \), \( 2, 4 \), \( 3, 4 \)이므로, 최종적으로 여행가 A가 도착하게 되는 곳의 좌표는 \( 3, 4 \)이다. 다시 말해 3행 4열의 위치에 해당하므로 \( 3, 4 \)라고 적는다. 계획서가 주어졌을 때 여행가 A가 최종적으로 도착할 지점의 좌표를 출력하는 프로그램을 작성하시오.

#### 입력 조건

* 첫째 줄에 공간의 크기를 나타내는 N이 주어진다. \( 1 &lt;= N &lt;= 100 \)
* 둘째 줄에 여행가 A가 이동할 계획서 내용이 주어진다. \( 1 &lt;= 이동 횟수 &lt;= 100 \)

#### 출력 조건

* 첫째 줄에 여행가 A가 최종적으로 도착할 지점의 좌표 \( X, Y \)를 공백으로 구분하여 출력한다.

#### 입력 예시

5  
RRRUDD

#### 출력 예시

3 4



### 문제 해설

이 문제를 요구사항대로 구현하면 연산 횟수는 이동 횟수에 비례하게 된다. 예를 들어 이동 횟수가 N번인 경우 시간 복잡도는 O\( N \)이다. 이러한 문제는 일련의 명령에 따라서 개체를 차례대로 이동시킨다는 점에서 시뮬레이션 유형으로 분류되며 구현이 중요한 대표적인 문제 유형이다.



### 내가 푼 답안

```text
def solution(N, commands):
    DIRECTIONS = {"R": (0, 1), "L": (0, -1), "U": (-1, 0), "D": (1, 0)}
    current_x, current_y = 1, 1

    for command in commands:
        dx, dy = DIRECTIONS[command]
        nx, ny = current_x + dx, current_y + dy

        if valid_coordinate(N, nx, ny):
            current_x, current_y = nx, ny

    return current_x, current_y

def valid_coordinate(N, x, y):
    return 1 <= x <= N and 1 <= y <= N


print(solution(5, ["R", "R", "R", "U", "D", "D"]))
```



### 다른 답안

```text
n = int(input())
x, y = 1, 1
plans = input().split()

dx = [0, 0, -1, 1]
dy = [-1, 1, 0, 0]
move_types = ['L', 'R', 'U', 'D']

for plan in plans:
    for i in range(len(move_types)):
        if plan == move_types[i]:
            nx = x + dx[i]
            ny = y + dy[i]
        
        if nx < 1 or ny < 1 or nx > n or ny > n:
            continue
            
        x, y = nx, ny

print(x, y)
```



