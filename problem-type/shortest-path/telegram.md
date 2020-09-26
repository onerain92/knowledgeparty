---
description: '문제 난이도: 상 / 문제 풀이 시간 : 60분 / 시간 제한 : 1초 / 메모리 제한 : 128MB'
---

# 전보

## 문제 설명

어떤 나라에는 N개의 도시가 있다. 그리고 각 도시는 보내고자 하는 메시지가 있는 경우, 다른 도시로 전보를 보내서 다른 도시로 해당 메시지를 전송할 수 있다. 하지만 X라는 도시에서 Y라는 도시로 전보를 보내고자 한다면, 도시 X에서 Y로 향하는 통로가 설치되어 있어햐 한다. 예를 들어 X에서 Y로 향하는 통로는 있지만, Y에서 X로 향하는 통로가 없다면 Y는 X로 메시지를 보낼 수 없다. 또한 통로를 거쳐 메시지를 보낼 때는 일정 시간이 소요된다.

어느 날 C라는 도시에서 위급 상황이 발생했다. 그래서 최대한 많은 도시로 메시지를 보내고자 한다. 메시지는 도시 C에서 출발하여 각 도시 사이에 설치된 통로를 거쳐, 최대한 많이 퍼져나갈 것이다. 각 도시의 번호와 통로가 설치되어 있는 정보가 주어졌을 때, 도시 C에서 보낸 메시지를 받게 되는 도시의 개수는 총 몇 개이며 도시들이 모두 메시지를 받는 데까지 걸리는 시간은 얼마인지 계산하는 프로그램을 작성하시오.  


#### 입력 조건

* 첫째 줄에 도시의 개수 N, 통로의 개수 M, 메시지를 보내고자 하는 도시 C가 주어진다. \( 1 &lt;= N &lt;= 30,000, 1 &lt;= M &lt;= 200,000, 1 &lt;= C &lt;= N \)
* 둘째 줄부터 M + 1번째 줄에 걸쳐서 통로에 대한 정보 X, Y, Z가 주어진다. 이는 특정 도시 X에서 다른 특정 도시 Y로 이어지는 통로가 있으며, 메시지가 전달되는 시간이 Z라는 의미이다. \( 1 &lt;= X, Y &lt;= N, 1 &lt;= Z &lt;= 1,000 \)

#### 출력 조건

* 첫째 줄에 도시 C에서 보낸 메시지를 받는 도시의 총 개수와 총 걸리는 시간을 공백으로 구분하여 출력한다.

#### 입력 예시

3 2 1  
1 2 4  
1 3 2

#### 출력 예시

2 4



## 문제 해설

이 문제를 들여다보면 한 도시에서 다른 도시까지의 최단 거리 문제로 치환할 수 있으므로 다익스트라 알고리즘을 이용해서 풀 수 있다. 또한 N과 M의 범위가 충분히 크기 때문에, 우선순위 큐를 이용하여 다익스트라 알고리즘을 작성해야 한다.



## 답안

### 내가 푼 답안

```text
import heapq

def solution(n, start, routes):
    INF = int(1e9)
    graph = [[] for i in range(n + 1)]
    distance = [INF] * (n + 1)

    for route in routes:
        start_city, end_city, time = route
        graph[start_city].append((end_city, time))

    queue = []
    heapq.heappush(queue, (0, start))
    distance[start] = 0
    while queue:
        dist, now = heapq.heappop(queue)

        if distance[now] < dist:
            continue

        for i in graph[now]:
            cost = dist + i[1]

            if cost < distance[i[0]]:
                distance[i[0]] = cost
                heapq.heappush(queue, (cost, i[0]))

    count = 0
    max_distance = 0
    for d in distance:
        if d != INF:
            count += 1
            max_distance = max(max_distance, d)

    return (count - 1, max_distance)


print(solution(3, 1, [[1, 2, 4], [1, 3, 2]]))
```



