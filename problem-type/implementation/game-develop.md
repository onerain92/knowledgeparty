---
description: '문제 난이도: 중 / 문제 풀이 시간 : 40분 / 시간 제한 : 1초 / 메모리 제한 : 128MB'
---

# 4. 게임 개발

## 문제 설명

동동이는 게임 캐릭터가 맵 안에서 움직이는 시스템을 개발 중이다. 캐릭터가 있는 장소는 1 x 1 크기의 정사각형으로 이뤄진 N x M 크기의 직사각형으로, 각각의 칸은 육지 또는 바다이다. 캐릭터는 동서남북 중 한 곳을 바라본다.

맵의 각 칸은 \( A, B \)로 나타낼 수 있고, A는 북쪽으로부터 떨어진 칸의 개수, B는 서쪽으로부터 떨어진 칸의 개수이다. 캐릭터는 상하좌우로 움직일 수 있고, 바다로 되어 있는 공간에는 갈 수 없다. 캐릭터의 움직임을 설정하기 위해 정해 놓은 메뉴얼은 이러하다.

1. 현재 위치에서 현재 방향을 기준으로 왼쪽 방향\( 반시계 방향으로 90도 회전한 방향 \)부터 차례대로 갈 곳을 정한다.
2. 캐릭터의 바로 왼쪽 방향에 아직 가보지 않은 칸이 존재한다면, 왼쪽 방향으로 회전한 다음 왼쪽으로 한 칸을 전진한다. 왼쪽 방향에 가보지 않은 칸이 없다면, 왼쪽 방향으로 회전만 수행하고 1단계로 돌아간다.
3. 만약 네 방향 모두 이미 가본 칸이거나 바다로 되어 있는 칸인 경우에는, 바라보는 방향을 유지한 채로 한 칸 뒤로 가고 1단계로 돌아간다. 단, 이때 뒤쪽 방향이 바다인 칸이라 뒤로 갈 수 없는 경우에는 움직임을 멈춘다.

동동이는 위 과정을 반복적으로 수행하면서 캐릭터의 움직임에 이상이 있는지 테스트하려고 한다. 메뉴얼에 따라 캐릭터를 이동시킨 뒤에, 캐릭터가 방문한 칸의 수를 출력하는 프로그램을 만드시오.

#### 입력 조건

* 첫째 줄에 맵의 세로 크기 N과 가로 크기 M을 공백으로 구분하여 입력한다. \( N &gt;= 3, M &lt;= 50 \)
* 둘째 줄에 게임 캐릭터가 있는 칸의 좌표 \( A, B \)와 바라보는 방향 d가 각각 서로 공백으로 구분하여 주어진다. 방향 d의 값은 다음과 같다.
  * 0 : 북쪽 / 1 : 동쪽 / 2 : 남쪽 / 3 : 서쪽
* 셋째 줄부터 맵이 육지인지 바디인지 입력한다. N개의 줄에 맵의 상태가 북쪽부터 남쪽 순서대로, 각 줄의 데이터는 서쪽부터 동쪽 순서대로 주어진다. 맵의 외곽은 항상 바다로 되어 있다.
  * 0 : 육지 / 1 : 바다
* 처음에 게임 캐릭터가 위치한 칸의 상태는 항상 육지이다.

#### 출력 조건

* 첫째 줄에 이동을 마친 후 캐릭터가 방문한 칸의 수를 출력한다.

#### 입력 예시

4 4         \# 4 x 4 맵 생성  
1 1 0      \# \( 1, 1 \)에 북쪽\( 0 \)을 바라보고 서 있는 캐릭터  
1 1 1 1   \# 첫 줄은 모두 바다  
1 0 0 1   \# 둘째 줄은 바다 / 육지 / 바다  
1 1 0 1   \# 셋째 줄은 바다 / 바다 / 육지 / 바다  
1 1 1 1   \# 넷째 줄은 모두 바

#### 출력 예시

3



## 문제 해설

전형적인 시뮬레이션 문제입니다. 별도의 알고리즘이 필요하기보다는 문제에서 요구하는 내용을 오류 없이 성실하게 구현만할 수 있다면 풀 수 있다는 특징이 있습니다.

일반적으로 방향을 설정해서 이동하는 문제 유형에서는 dx, dy라는 별도의 리스트를 만들어 방향을 정하는 것이 효과적입니다. 

## 답안

### 내가 푼 답안

```text
def solution(N, M, location, MAP):
    visited = [[False] * M for _ in range(N)]

    current_x, current_y, current_direction = location
    visited[current_x][current_y] = True
    dx = [-1, 0, 1, 0]
    dy = [0, 1, 0, -1]

    result = 1
    count = 0

    while True:
        current_direction -= 1

        if current_direction == - 1:
            current_direction = 3

        nx, ny = current_x + dx[current_direction], current_y + dy[current_direction]

        if not visited[nx][ny] and MAP[nx][ny] != 1:
            current_x, current_y = nx, ny
            visited[nx][ny] = True
            result += 1
            count = 0

            continue
        else:
            count += 1

        if count == 4:
            nx, ny = current_x - dx[current_direction], current_y - dx[current_direction]

            if MAP[nx][ny] == 1:
                break

            current_x, current_y = nx, ny
            count = 0

    print(result)


print(solution(4, 4, [1, 1, 0], [[1, 1, 1, 1], [1, 0, 0, 1], [1, 1, 0, 1], [1, 1, 1, 1]]))
```



### 다른 답안

```text
n, m = map(int, input().split())
d = [[0] * m for _ in range(n)]
x, y, direction = map(int, input().split())
d[x][y] = 1

array = []
for i in range(n):
    array.append(list(map(int, input().split())))
    
dx = [-1, 0, 1, 0]
dy = [0, 1, 0, -1]

def turn_left():
    global direction
    direction -= 1
    if direction == -1:
        direction = 3

count = 1
turn_time = 0
while True:
    turn_left()
    nx = x + dx[direction]
    ny = y + dy[direction]
    
    if d[nx][ny] == 0 and array[nx][ny] == 0:
        d[nx][ny] = 1
        x = nx
        y = ny
        count += 1
        turn_time = 0
        continue
    else:
        turn_time += 1
        
    if turn_time == 4:
        nx = x - dx[direction]
        ny = y - dy[direction]
        
        if array[nx][ny] == 0:
            x = nx
            y = ny
        else:
            break
        turn_time = 0

print(count)
```



