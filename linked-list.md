---
description: 연결 리스트라고도 함.
---

# 링크드 리스트 \( Linked List \)

## 1. 구조

* 연결 리스트라고도 함.
* 배열은 순차적으로 연결된 공간에 데이터를 나열하는 데이터 구조.
* 링크드 리스트는 떨어진 곳에 존재하는 데이터를 화살표로 연결해서 관리하는 데이터 구조.

{% hint style="info" %}
C 언어에서는 주요한 데이터 구조이지만, 파이썬은 리스트 타입이 링크드 리스트의 기능을 모두 지원.
{% endhint %}

* 링크드 리스트 기본 구조와 용어
  * 노드 \( Node \) :  데이터 저장 단위\(데이터 값, 포인터\)로 구성.
  * 포인터 \( Pointer \) : 각 노드 안에서, 다음이나 이전의 노드와의 연결 정보를 가지고 있는 공간.

![Linked List](.gitbook/assets/linkedlist.png)



## 2. 간단한 링크드 리스트 

#### Node 구현 \( Python \)

* 파이썬에선 보통 링크드 리스트 구현시, 파이썬 클래스를 활용한다.

```text
class Node:
    def __init__(self, data, next = None):
        self.data = data
        self.next = next
```

#### Node와 Node 연결하기 \( 포인터 활용 \)

```text
node1 = Node(1)
node2 = Node(2)

node1.next = node2
head = node1
```

#### 링크드 리스트로 데이터 추가하기

```text
class Node:
    def __init__(self, data, next = None):
        self.data = data
        self.next = next
        
def add(data):
    node = head
    
    while node.next:
        node = node.next
        
    node.next = Node(data)
```

#### 링크드 리스트 데이터 출력하기 \( 검색하 \)

```text
node = head

while node.next:
    print(node.data)
    node = node.next

print(node.data)
```



## 3. 장단점

### 장점

* 미리 데이터 공간을 할당하지 않아도 된다.
  * 배열은 미리 데이터 공간을 할당 해야한다.

### 단점

* 연결을 위한 별도 데이터 공간이 필요하므로 저장공간 효율이 높지 않다.
* 연결 정보를 찾는 시간이 필요하므로 접근 속도가 느리다.
* 중간 데이터 삭제시 앞뒤 데이터의 연결을 재구성해야하는 부가적인 작업이 필요하다.



## 4. 링크드 리스트의 복잡한 기능1\( 링크드 리스트 데이터 사이에 데이터 추가 \)

* 링크드 리스트는 유지 관리에 부가적인 구현이 필요함.

```text
class Node:
    def __init__(self, data, next = None):
        self.data = data
        self.next = next
        
node = head    
node3 = Node(1.5)
search = True

while search:
    if node.data == 1:
        search = False
    else:
        node = node.next

node_next = node.next
node.next = node3
node3.next = node_next
```



## 5. 객체지향 프로그래밍으로 링크드 리스트 구현하기\( Python \)

```text
class Node:
    def __init__(self, data, next = None):
        self.data = data
        self.next = next

class NodeManagement:
    def __init__(self, data):
        self.head = Node(data)

    def add(self, data):
        if self.head == '':
            self.head = Node(data)
        else:
            node = self.head
            while node.next:
                node = node.next
            
            node.next = Node(data)
        
    def description(self):
        node = self.head
        
        while node:
            print(node.data)
            node = node.next    
```

```text
linkedlist1 = NodeManagement(0)
linkdelist1.description() // 0

for data in range(1, 10):
    linkedlist1.add(data)
print(linkedlist1.description()) // 0, 1, 2, 3, 4, 5, 6, 7, 8, 9
```



## 6. 링크드 리스트의 복잡한 기능2\( 특정 노드를 삭제 \)

```text
class Node:
    def __init__(self, data, next = None):
        self.data = data
        self.next = next

class NodeManagement:
    def __init__(self, data):
        self.head = Node(data)

    def add(self, data):
        if self.head == '':
            self.head = Node(data)
        else:
            node = self.head
            while node.next:
                node = node.next
            
            node.next = Node(data)
        
    def description(self):
        node = self.head
        
        while node:
            print(node.data)
            node = node.next
    
    def delete(self, data):
        if self.head == '':
            print("해당 값을 가진 노드가 없습니다.")
            return
        
        if self.head == data:
            temp = self.head
            self.head = self.head.next
            del temp
        else:
            node = self.head
            while node.next:
                if node.next.data == data:
                    temp = node.next
                    node.next = node.next.next
                    del temp
                else:
                    node = node.next
```



## 7. 다양한 링크드 리스트 구조

* 더블 링크드 리스트\( Doubly linked list \) 기본 구조
  * 이중 연결 리스트라고도 한다.
  * 장점: 양방향으로 연결되어 있어서 노드 탐색이 양쪽으로 모두 가능하다.

```text

```



