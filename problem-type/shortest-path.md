# 최단 경로

## 특정 지점까지 가장 빠르게 도달하는 방법을 찾는 알고리즘

* 최단 경로 알고리즘은 말 그대로 가장 짧은 경로를 찾는 알고리즘이다.
* '길 찾기' 문제라고도 불린다.
* 최단 경로 알고리즘은 보통 그래프로 표현하는데 각 지점은 그래프에서 '노드'로 표현되고, 지점 간 연결된 도로는 그래프에서 '간선'으로 표현된다. 또한 실제 코딩 테스트에서는 최단 경로를 모두 출력하는 문제보다는 단순히 최단 거리를 출력하도록 요구하는 문제가 많이 출제된다.
* 기본적으로 다익스트라 알고리즘, 플로이드 워셜 알고리즘, 벨만 포드 알고리즘 등이 있다.



### 간단한 다익스트라 알고리즘

* 처음에 각 노드에 대한 최단 거리를 담는 1차원 리스트를 선언한다.
* 이후에 단계마다 '방문하지 않은 노드 중에서 최단 거리가 가장 짧은 노드를 선택'하기 위해 매 단계마다 1차원 리스트의 모든 원소를 확인\( 순차 탐색 \)한다.
* 간단한 다익스트라 알고리즘은 O\( V^2 \)의 시간 복잡도를 가지며, 다익스트라에 의해서 처음 고안되었다. \( 여기서 V는 노드의 개수를 의미한다. \)
* 왜냐하면 총 O\( V \)번에 걸쳐서 최단 거리가 가장 짧은 노드를 매번 선형 탐색해야 하고, 현재 노드와 연결된 노드를 매번 일일이 확인하기 때문이다.
* 따라서 전체 노드의 개수가 5,000개 이하라면 일반적으로 이 코드로 문제를 풀 수 있을 것이다. 하지만 10,000개를 넘어가는 문제라면 이 코드로는 해결하기 어렵다.

```text
import sys
input = sys.stdin.readline
INF = int(1e9)

# 노드의 개수, 간선의 개수를 입력받기
n, m = map(int, input().split())

# 시작 노드 번호를 입력받기
start = int(input())

# 각 노드에 연결되어 있는 노드에 대한 정보를 담는 리스트를 만들기
graph = [[] for i in range(n + 1)]

# 방문한 적이 있는지 체크하는 목적의 리스트를 만들기
visited = [False] * (n + 1)

# 최단 거리 테이블을 모두 무한으로 초기화
distance = [INF] * (n + 1)

# 모든 간선 정보를 입력받기
for _ in range(m):
    a, b, c = map(int, input().split())
    
    # a번 노드에서 b번 노드로 가는 비용이 c라는 의미
    graph[a].append((b, c))
    
    
# 방문하지 않은 노드 중에서, 가장 최단 거리가 짧은 노드의 번호를 반환
def get_smallest_node():
    min_value = INF
    index = 0 # 가장 최단 거리가 짧은 노드(인덱스)
    for i in range(1, n + 1):
        if distance[i] < min_value and not visited[i]:
            min_value = distance[i]
            index = i
            
    return index
    

def dijkstra(start):
    # 시작 노드에 대해서 초기화
    distance[start] = 0
    visited[start] = True
    for j in graph[start]:
        distance[j[0]] = j[1]
        
    # 시작 노드를 제외한 전체 n - 1개의 노드에 대해 반복
    for i in range(n - 1):
        # 현재 최단 거리가 가장 짧은 노드를 꺼내서, 방문 처리
        now = get_smallest_node()
        visited[now] = True
        
        # 현재 노드와 연결된 다른 노드를 확인
        for j in graph[now]:
            cost = distance[now] + j[1]
            
            # 현재 노드를 거쳐서 다른 노드로 이동하는 거리가 더 짧은 경우
            if cost < distance[j[0]]:
                distance[j[0]] = cost

# 다익스트라 알고리즘 수행
dijkstra(start)

# 모든 노드로 가기 위한 최단 거리를 출력
for i in range(1, n + 1):
    # 도달할 수 없는 경우, 무한(INFINITY)이라고 출력
    if distance[i] == INF:
        print("INFINITY")
    # 도달할 수 있는 경우 거리를 출력
    else:
        print(distance[i])
```



### 개선된 다익스트라 알고리즘

* 최악의 경우에도 시간 복잡도 O\( E log V \)를 보장하여 해결할 수 있다. 여기서 V는 노드의 개수이고, E는 간선의 개수를 의미한다.
* 개선된 다익스트라 알고리즘에서는 힙 자료구조를 사용한다. 힙 자료구조를 사용하게 되면 특정 노드까지의 최단 거리에 대한 정보를 힙에 담아서 처리하므로 출발 노드로부터 가장 거리가 짧은 노드를 더욱 빠르게 찾을 수 있다. 이 과정에서 선형 시간이 아닌 로그 시간이 걸린다.
* '최단 거리가 가장 짧은 노드'를 선택하는 과정을 다익스트라 최단 경로 함수 안에서 우선순위 큐를 이용하는 방식으로 대체할수 있기 때문에 간단한 다익스트라 알고리즘의 get\_smallest\_node\(\) 함수를 작성할 필요가 없다.

```text
import heapq
import sys
input = sys.stdin.readline
INF = int(1e9)

# 노드의 개수, 간선의 개수를 입력받기
n, m = map(int, input().split())

# 시작 노드 번호를 입력받기
start = int(input())

# 각 노드에 연결되어 있는 노드에 대한 정보를 담는 리스트를 만들기
graph = [[] for i in range(n + 1)]

# 최단 거리 테이블을 모두 무한으로 초기화
distance = [INF] * (n + 1)

# 모든 간선 정보를 입력받기
for _ in range(m):
    a, b, c = map(int, input().split())
    
    # a번 노드에서 b번 노드로 가는 비용이 c라는 의미
    graph[a].append((b, c))
    

def dijkstra(start):
    q = []
    
    # 시작 노드로 가기 위한 최단 경로는 0으로 설정하여, 큐에 삽입
    heapq.heappush(q, (0, start))
    distance[start] = 0
    while q:
        # 가장 최단 거리가 짧은 노드에 대한 정보 꺼내기
        dist, now = heapq.heappop(0)
        
        # 현재 노드가 이미 처리된 적이 있는 노드라면 무시
        if distance[now] < dist:
            continue
        
        # 현재 노드와 연결된 다른 인접한 노드들을 확인
        for i in graphp[now]:
            cost = dist + i[1]
            
            # 현재 노드를 거쳐서, 다른 노드로 이동하는 거리가 더 짧은 경우
            if cost < distance[i[0]]:
                distance[i[0]] = cost
                heapq.heappush(q, (cost, i[0]))
    

# 다익스트라 알고리즘 수행
dijkstra(start)

# 모든 노드로 가기 위한 최단 거리를 출력
for i in range(1, n + 1):
    # 도달할 수 없는 경우, 무한(INFINITY)이라고 출력
    if distance[i] == INF:
        print("INFINITY")
    # 도달할 수 있는 경우 거리를 출력
    else:
        print(distance[i])

```



