# DFS / BFS

## DFS \( Depth First Search \)

* _**'깊이 우선 탐색'**_ 이라고도 부르며, _**그래프에서 깊은 부분을 우선적으로 탐색**_하는 알고리즘이다.
* DFS는 **스택 자료구조**를 이용하며 구체적인 동작 과정은 다음과 같다.
  * 탐색 시작 노드를 스택에 삽입하고 방문 처리를 한다.
  * 스택의 최상단 노드에 방문하지 않은 인접 노드가 있으면 그 인접 노드를 스택에 넣고 방문 처리를 한다. 방문하지 않은 인접 노드가 없으면 스택에서 최상단 노드를 꺼낸다.
  * 위의 과정을 더 이상 수행할 수 없을 때까지 반복한다.
* 일반적으로 인접한 노드 중에서 방문하지 않은 노드가 여러 개 있으면 번호가 낮은 순서부터 처리한다.

{% hint style="info" %}
'방문 처리'는 스택에 한 번 삽입되어 처리된 노드가 다시 삽입되지 않게 체크하는 것을 의미한다. 방문 처리를 함으로써 각 노드를 한 번씩만 처리할 수 있다.
{% endhint %}



## BFS\( Breath First Search \)

* _**'너비 우선 탐색'**_ 이라는 의미를 가지며 _**가까운 노드부터 탐색**_하는 알고리즘이다.
* BFS는 **큐 자료구조**를 이용하는 것이 정석이다. 인접한 노드를 반복적으로 큐에 넣도록 알고리즘을 작성하면 자연스럽게 먼저 들어온 것이 먼저 나가게 되어, 가까운 노드부터 탐색을 진행하게 된다.
* BFS의 정확한 동작 방식은 다음과 같다.
  * 탐색 시작 노드를 큐에 삽입하고 방문 처리를 한다.
  * 큐에서 노드를 꺼내 해당 노드의 인접 노드 중에서 방문하지 않은 노드를 모두 큐에 삽입하고 방문 처리를 한다.
  * 위의 과정을 더 이상 수행할 수 없을때까지 반복한다.
* 일반적으로 인접한 노드 중에서 방문하지 않은 노드가 여러 개 있으면 번호가 낮은 노드부터 큐에 삽입한다.



