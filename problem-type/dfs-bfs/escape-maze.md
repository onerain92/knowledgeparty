---
description: '문제 난이도: 중하 / 문제 풀이 시간 : 30분 / 시간 제한 : 1초 / 메모리 제한 : 128MB'
---

# 미로 탈출

## 문제 설명

이모는 N x M 크기의 직사각형 형태의 미로에 갇혀 있다. 미로에는 여러 마리의 괴물이 있어 이를 피해 탈출해야 한다. 이모의 위치는 \( 1, 1 \)이고 미로의 출구는 \( N, M \)의 위치에 존재하며 한 번에 한 칸씩 이동할 수 있다. 이때 괴물이 있는 부분은 0으로, 괴물이 없는 부분은 1로 표시되어 있다. 미로는 반드시 탈출할 수 있는 형태로 제시된다. 이때 이모가 탈출하기 위해 움직여야 하는 최소 칸의 개수를 구하시오. 칸을 셀 때는 시작 칸과 마지막 칸을 모두 포함해서 계산한다.

#### 입력 조건

* 첫째 줄에 두 정수 N, M\( 4 &lt;= N, M &lt;= 200 \)이 주어집니다. 다음 N개의 줄에는 각각 M개의 정수\( 0 혹은 1 \)로 미로의 정보가 주어진다. 각각의 수들은 공백 없이 붙어서 입력으로 제시된다. 또한 시작 칸과 마지막 칸은 항상 1이다.

#### 출력 조건

* 첫째 줄에 최소 이동 칸의 개수를 출력한다.

#### 입력 예시

5 6  
101010  
111111  
000001  
111111  
111111

#### 출력 예시

10



## 문제 해설

이 문제는 BFS를 이용했을 때 매우 효과적으로 해결할 수 있다. 그러므로 \( 1, 1 \) 지점에서부터 BFS를 수행하여 모든 노드의 값을 거리 정보로 넣으면 된다. 특정한 노드를 방문하면 그 이전 노드의 거리에 1을 더한 값을 리스트에 넣는다.



## 답안

### 내가 푼 답안

```text
from collections import deque

def valid_coord(n, m, x, y):
    return 0 <= x < n and 0 <= y < m

def solution(n, m, maze):
    visited = [[False] * m for _ in range(n)]
    visited[0][0] = True
    queue = deque([(0, 0)])
    DIRECTIONS = [(-1, 0), (1, 0), (0, -1), (0, 1)]

    while queue:
        print(queue)
        current_x, current_y = queue.popleft()

        for direction in DIRECTIONS:
            nx, ny = current_x + direction[0], current_y + direction[1]

            if valid_coord(n, m, nx, ny) and maze[nx][ny] == 1 and not visited[nx][ny]:
                queue.append((nx, ny))
                maze[nx][ny] = maze[current_x][current_y] + 1
                visited[nx][ny] = True

    return maze[n -1][m -1]


print(solution(5, 6, [[1, 0, 1, 0, 1, 0], [1, 1, 1, 1, 1, 1], [
      0, 0, 0, 0, 0, 1], [1, 1, 1, 1, 1, 1], [1, 1, 1, 1, 1, 1]]))
print(solution(3, 3, [[1, 1, 0], [0, 1, 0], [0, 1, 1]]))
```



### 다른 답안

```text
from collections import deque

n, m = map(int, input().split())
graph = []
for i in range(n):
    graph.append(list(map(int, input().split())))

dx = [-1, 1, 0, 0]
dy = [0, 0, -1, 1]


def bfs(x, y):
    queue = deque()
    queue.append((x, y))

    while queue:
        x, y = queue.popleft()

        for i in range(4):
            nx = x + dx[i]
            ny = y + dy[i]

            if nx < 0 or ny < 0 or nx >= n or ny >= m:
                continue

            if graph[nx][ny] == 0:
                continue

            if graph[nx][ny] == 1:
                graph[nx][ny] = graph[x][y] + 1
                queue.append((nx, ny))

    return graph[n - 1][m - 1]


print(bfs(0, 0))
```



