---
description: '자료의 선입선출, FIFO( First-In-First-Out )을 보장하는 자료구조입니다.'
---

# 큐 \( QUEUE \)

## 큐 구조

* 가장  저 넣은 데이터를 가장 먼저 꺼낼 수 있는 구조
  * 음식점에서 가장 먼저 줄을 선 사람이 제일 먼저 음식점에 입장하는 것과 동일
  * FIFO\(First-In-First-Out\) 또는 LILO\(Last-In-Last-Out\) 방식으로 스택과 꺼내는 순서가 반

![Queue](.gitbook/assets/queue.png)



## 알아둘 용어

* Enqueue : 큐에 데이터를 넣는 기능
* Dequeue : 큐에서 데이터를 빼는 기능



## Queue \( Python \)

* queue 라이브러리 활용해서 큐 자료 구조 사용 가능.
* queue 라이브러리에는 다양한 큐 구조로 Queue\(\), LifoQueue\(\), Priority Queue 제공.
* 프로그램을 작성할 때 프로그램에 따라 적합한 자료구조를 사용하자.
  * Queue : 가장 일반적인 큐 자료구조.
  * LifoQueue\(\) : 나중에 입력된 데이터가 먼저 출력되는 구조 \( 스택 구조 \).
  * PriorityQueue\(\) : 데이터마다 우선순위를 넣어서, 우선순위가 높은 순으로 데이터 출력.
  * 일반적인 큐 외에 다양한 정책이 적용된 큐들이 있음.

### Queue\(\)로 큐 만들기 \( 가장 일반적인 큐, FIFO \)

```text
import queue

data_queue = queue.Queue()
data_queue.put(3)
data_queue.put(2)
data_queue.qsize() // 2
data_queue.get() // 3
```

### LifoQueue\(\)로 큐 만들기

```text
import queue

data_queue = queue.LifoQueue()
data_queue.put(1)
data_queue.put(2)
data_queue.qsize() // 2
data_queue.get() // 2
```

### PriorityQueue\(\)로 큐 만들기

```text
import queue

data_queue = queue.PriorityQueue()
data_queue.put((2, 5)) // (우선순위, 데이)
data_queue.put(1, 10)
data_queue.qsize() // 2
data_queue.get() // (1, 10)
```



## 어디에 큐가 많이 쓰일까?

* 멀티태스킹을 위한 프로세스 스케쥴링 방식을 구현하기 위해 많이 사용됨.
* 큐의 경우에는 장단점 보다는 \(특별히 언급되는 장단점이 없음\), 큐의 활용 예로 프로세스 스케쥴링 방식을 함게 이해해두는 것이 좋음. 

## 연습

1. 리스트 변수로 큐를 다루는 enqueue, dequeue 기능 구현해보기

```text
queue_list = list()

def enqueue(data):
    queue_list.append(data)   

def dequeue(data):
    data = queue_list[0]
    del queue_list[0]
    return data
    
for index in range(10):
    enqueue(index)
```



