# 그래프\( Graph \)

## 1. 그래프\( Graph \)란?

* 그래프는 실제 세계의 현상이나 사물을 정점\( Vertex \) 또는 노드\( Node \)와 간선\( Edge \)로 표현하기 위해 사용.

#### 집에서 회사로 가는 경로를 그래프로 표현한 예

![https://www.fun-coding.org](../.gitbook/assets/graph.png)



## 2. 관련 용어

* 노드\( Node \) : 위치를 말하며 정점\( Vertex \)라고도 함.
* 간선\( Edge \) : 위치간의 관계를 표시한 선으로 노드를 연결한 선이라고 보면 됨.\( link 또는 branch 라고도 함 \)
* 인접 정점\( Adjacent Vertex \) : 간선으로 직접 연결된 정점\( 또는 노드 \)
* 참고 용어
  * 정점의 차수\( Degree \) : 무방향 그래프에서 하나의 정점에 인접한 정점의 수.
  * 진입 차수\( In-Degree \) : 방향 그래프에서 외부에서 오는 간선의 수.
  * 진출 차수\( Out-Degree \) : 방향 그래프에서 외부로 향하는 간선의 수.
  * 경로 길이\( Path Length \) : 경로를 구성하기 위해 사용된 간선의 수.
  * 단순 경로\( Simple Path \) : 처음 정점과 끝 정점을 제외하고 중복된 정접이 없는 경로.
  * 사이클\( Cycle \) : 단순 경로의 시작 정점과 종료 정점이 동일한 경우.



## 3. 종

#### 무방향 그래프\( Undirected Graph \)

* 방향이 없는 그래프.
* 간선을 통해 노드는 양방향으로 갈 수 있다.
* 보통 노드 A, B가 연결되어 있을 경우, \( A, B \) 또는 \( B, A \)로 표

![https://www.fun-coding.org](../.gitbook/assets/undirectedgraph.png)



#### 방향 그래프\( Directed Graph \)

* 간선에 방향이 있는 그래프
* 보통 노드 A, B가 A -&gt; B로 가는 간선으로 연결되어 있을 경우, &lt;A, B&gt;로 표기. \( &lt;B, A&gt;는 B -&gt; A로 가는 간선이 있는 경우이므로 &lt;A, B&gt;와 다름. \) 

![https://www.fun-coding.org](../.gitbook/assets/directedgraph.png)



#### 가중치 그래프\( Weighted Graph \) 또는 네트워크\( Network \)

* 간선에 비용 또는 가중치가 할당된 그래프

![https://www.fun-coding.org](../.gitbook/assets/weightedgraph.png)



#### 연결 그래프\( Connected Graph \)와 비연결 그래프\( Disconnected Graph \)

* 연결 그래프\( Connected Graph \)
  * 무방향 그래프에 있는 모든 노드에 대해 항상 경로가 존재하는 경우. 
* 비연결 그래프\( Disconnected Graph \)
  * 무방향 그래프에서 특정 노드에 대해 경로가 존재하지 않는 경우.

![https://www.fun-coding.org](../.gitbook/assets/disconnectedgraph.png)



#### 사이클\( Cycle \)과 비순환 그래프\( Acyclic Graph \)

* 사이클\( Cycle \)
  * 단순 경로의 시작 노드와 종료 노드가 동일한 경우. 
* 비순환 그래프\( Acyclic Graph \)
  * 사이클이 없는 그래

![https://www.fun-coding.org](../.gitbook/assets/acyclicgraph.png)



#### 완전 그래프\( Complete Graph \)

* 그래프의 모든 노드가 서로 연결되어 있는 그래프

![https://www.fun-coding.org](../.gitbook/assets/completegraph.png)



## 3. 그래프와 트리의 차이

* 트리는 그래프 중에 속한 특별한 종류라고 볼 수 있다.

|  | 그래프 | 트리 |
| :--- | :--- | :--- |
| 정 | 노드와 노드를 연결하는 간선으로 표현되는 자료 구 | 그래프의 한 종류, 방향성이 있는 비순환 그래 |
| 방향성 | 방향 그래프, 무방향 그래프 둘 다 존재함. | 방향 그래프만 존재함. |
| 사이클 | 사이클 가능, 순환 및 비순환 그래프 모두 존재함. | 비순환 그래프로 사이클이 존재하지 않음 |
| 루트 노드 | 루트 노드 존재하지 않음 | 루트 노드 존재함 |
| 부모 / 자식 관 | 부모 / 자식 개념이 존재하지 않음 | 부모 / 자식 관계가 존재함 |







