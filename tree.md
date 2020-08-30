# 트리 \( Tree \)

## 1. 구조

* 트리\( Tree \) : Node와 Branch를 이용해서 사이클을 이루지 않도록 구성한 데이터 구조
* 실제로 어디에 많이 사용될까?
  * 트리 중 이진 트리\( Binary Tree \) 형태의 구조로 탐색\( 검색 \) 알고리즘 구현을 위해 많이 사용된다.



## 2. 알아둘 용어

* Node : 트리에서 데이터를 저장하는 기본 요소\( 데이터와 다른 연결된 노드에 대한 Branch 정보 포함 \)
* Root Node : 트리 맨 위에 있는 노드.
* Level : 최상위 노드를 Level 0으로 하였을 때, 하위 Branch로 연결된 노드의 깊이를 나타냄.
* Parent Node : 어떤 노드의 상위 레벨에 연결된 노드.
* Childe Node : 어떤 노드의 다음 레벨에 연결된 노드.
* Leaf Node\( Terminal Node \) : Child Node가 하나도 없는 노드.
* Sibling\( Brother Node \) : 동일한 Parent Node를 가진 노드.
* Depth : 트리에서 Node가 가질 수 있는 최대 Level

![Tree](.gitbook/assets/tree.png)



## 3. 이진 트리와 이진 탐색 트리 \( Binary Search Tree \)

* 이진 트리 : 노드의 최대 Branch가 2인 트리.
* 이진 탐색 트리 \( Binary Search Tree, BST \) : 이진 트리에 다음과 같은 추가적인 조건이 있는 트리.
  * 왼쪽 노드는 해당 노드보다 작은 값, 오른쪽 노드는 해당 노드보다 큰 값을 가지고 있어야 한다.

![Binary Search Tree, BST](.gitbook/assets/bst.png)



## 4. 자료 구조 이진 탐색 트리의 장점과 주요 용도

* 주요 용도 : 데이터 검색\( 탐색 \)
* 장점
  * 탐색 속도를 개선할 수 있다.
* 단점
  * 평균 시간 복잡도는 O\(log n\)이지만, 이는 트리가 균형잡혀 있을 때의 평균 시간복잡도이다.
  * 다음 예와 같이 구성되어 있을 경우, 최악의 경우는 링크드 리스트 등과 동일한 성능을 보여준다.\( O\(n\) \)

![BST](.gitbook/assets/right-bst.png)



## 5. 이진 트리와 정렬된 배열간의 탐색 비교

![BST vs Array](.gitbook/assets/binary-search-tree-sorted-array-animation.gif)



## 6. 링크드 리스트를 이용하여 트리 구현해보기

#### 1. 노드 클래스 만들기

```text
class Node:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None
```



#### 2. 이진 탐색 트리에 데이터 넣기

* 이진 탐색 트리 조건에 부합하게 데이터를 넣어야 한다.

```text
class NodeManagement:
    def __init__(self, head):
        self.head = head
        
    def insert(self, value):
        self.current_node = self.head
        
        while True:
            if value < self.current_node.value:
                if self.cuurent_node.left !== None:
                    self.current_node = self.current_node.left
                else:
                    self.current_node.left = Node(value)
                    break
            else:
                if self.cuurent_node.right !== None:
                    self.current_node = self.current_node.right
                else:
                    self.current_node.right = Node(value)
                    break
```



#### 3. 이진 탐색 트리 탐색

```text
class NodeManagement:
    def __init__(self, head):
        self.head = head
        
    def insert(self, value):
        self.current_node = self.head
        
        while True:
            if value < self.current_node.value:
                if self.cuurent_node.left !== None:
                    self.current_node = self.current_node.left
                else:
                    self.current_node.left = Node(value)
                    break
            else:
                if self.cuurent_node.right !== None:
                    self.current_node = self.current_node.right
                else:
                    self.current_node.right = Node(value)
                    break
                    
    def search(self, value):
        self.current_node = self.head
        
        while self.current_node:
            if self.current_node.value == value:
                return True
            elif value < self.current_node.value:
                self.current_node = self.current_node.left
            else:
                self.current_node = self.current_node.right
                
        return False
```



#### 4. 이진 탐색 트리 삭제

* 매우 복잡하므로 경우를 나눠서 이해하는 것이 좋다.



#### 삭제할 Node 탐색

* 삭제할 Node가 없는 경우도 처리해야 한다.
  * 이를 위해 삭제할 Node가 없는 경우는 False를 리턴하고 함수를 종료 시킨다.

```text
def delete(self, value):
    searched = False
    self.current_node = self.head
    self.parent = self.head
    
    while self.current_node:
        if self.current_node.value == value:
            searched = True
            break
        elif value < self.current_node.value:
            self.parent = self.current_node
            self.current_node = self.current_node.left
        else:
            self.parent = self.current_node
            self.current_node = self.current_node.right
            
    if searched == False:
        return False
```



#### Leaf Node 삭제

* Leaf Node : Childe Node가 없는 Node
* 삭제할 Node의 Parent Node가 삭제할 Node를 가리키지 않도록 한다.

```text
# self.current_node가 삭제할 Node, self.prent는 삭제할 Node의 Parent Node인 상태

    if self.current_node.left == None and self.current_node.right == None:
        if value < self.parent.value:
            self.parent.left = None
        else:
            self.parent.right = None
            
        del self.current_node
```



#### Childe Node가 하나인 Node 삭제

* 삭제할 Node의 Parent Node가 삭제할 Node의 Childe Node를 가리키도록 한다.

```text
    elif self.current_node.left != None and self.current_node.right == None:
        if value < self.parent.value:
            self.parent.left = self.current_node.left
        else:
            self.parent.right = self.current_node.left
    elif self.current_node.left == None and self.current_node.right != None:
        if value < self.parent.value:
            self.parent.left = self.current_node.right
        else:
            self.parent.right = self.current_node.right
```



#### Childe Node가 두개인 Node 삭제

1. 삭제할 Node의 오른쪽 자식 중, 가장 작은 값을 삭제할 Node의 Parent Node가 가리키도록 한다.
2. 삭제할 Node의 왼쪽 자식 중, 가장 큰 값을 삭제할 Node의 Parent Node가 가리키도록 한다.



#### 삭제할 Node의 오른쪽 자식 중, 가장 작은 값을 삭제할 Node의 Parent Node가 가리키게 할 경

* 삭제할 Node의 오른쪽 자식 선택
* 오른쪽 자식의 가장 왼쪽에 있는 Node를 선택
* 해당 Node를 삭제할 Node의 Parent Node의 왼쪽 Branch가 가리키게 함
* 해당 Node의 왼쪽 Branch가 삭제할 Node의 왼쪽 Child Node를 가리키게 함
* 해당 Node의 오른쪽 Branch가 삭제할 Node의 오른쪽 Childe Node를 가리키게 함
* 만약 해당 Node가 오른쪽 Childe Node를 가지고 있었을 경우에는, 해당 Node의 본래 Parent Node의 왼쪽 Branch가 해당 오른쪽 Childe Node를 가리키게 함.

```text
    elif self.current_node.left != None and self.current_node.right != None: # Child Node가 두개인 Node
        if value < self.parent.value: # 삭제할 Node가 왼쪽에 있는 경우
            self.change_node = self.current_node.right
            self.change_node_parent = self.current_node.right
            
            while self.change_node.left != None:
                self.change_node_parent = self.change_node
                self.change_node = self.change_node.left
            self.change_node_parent.left = None
            
            if self.change_node.right != None:
                self.change_node_parent.left = self.change_node.right
            else:
                self.change_node_parent.left = None
            
            self.parent.left = self.change_node
            self.change_node.right = self.current_node.right
            self.change_node.left = self.current_node.left
    
        else:
            self.change_node = self.current_node.right
            self.change_node_parent = self.current_node.right
        
            while self.change_node.left != None:
                self.change_node_parent = slef.change_node
                self.change_node = self.change_node.left
        
            if self.change_node.right != None:
                self.change_node_parent.left = self.change_node.right
            else:
                self.change_node_parent.left = None
        
            self.parent.right = self.change_node
            self.change_node.left = self.current_node.left
            self.change_node.right = self.current_node.right
        
    return True
```



#### 테스

* 0 - 999 숫자 중에서 임의로 100개를 추출해서, 이진 탐색 트리에 입력 / 검색 / 삭제
  * random 라이브러리 활용
  * random.randint\(첫 번째 숫자, 마지막 숫자\) : 첫 번째 숫자부터 마지막 숫자 사이에 있는 숫자를 랜덤하게 선택해서 리턴함.
    * e.g.\) random.randint\(0, 99\) : 0에서 99까지 숫자 중 특정 숫자를 랜덤하게 선택해서 리턴해줌

```text
import random

# 0 - 999 중 100개의 숫자를 랜덤으로 선택
bst_nums = set()

while len(bst_nums) != 100:
    bst_nums.add(random.randint(0, 999))
    
# 선택된 100개의 숫자를 이진 탐색 트리에 입력, 임의로 루트노드는 500을 넣기로 함.
head = Node(500)
binary_tree = NodeManagement(head)

for num in bst_nums:
    binary_tree.insert(num)
    
# 입력한 100개의 숫자 검색( 검색 기능 확인 )
for num in bst_nums:
    if binary_tree.serarch(num) == False:
        print('search failed', num)

# 입력한 100개의 숫자 중 10개의 숫자를 랜덤으로 선택
delete_nums = set()
bst_nums = list(bst_nums)

while len(delete_nums) != 10:
    delete_nums.add(bst_nums[random.randint(0, 99)])

# 선택한 10개의 숫자를 삭제( 삭제 기능 확인 )
for del_num in delete_nums:
    if binary_tree.delete(del_num) == False:
        print('delete failed', del_num)
```



## 7. 이진 탐색 트리의 시간 복잡도

#### 시간 복잡도\( 탐색시 \)

* depth\( 트리의 높이 \)를 h라고 표기한다면 O\(h\)
* n개의 노드를 가진다면, h = log2 n에 가까우므로 시간 복잡도는 O\(log n\)
  * 참고: Big-O 표기법에서 log n에서의 log의 밑은 10이 아니라 2이다.
    * 한 번 실행시마다 50%의 실행할 수도 있는 명령을 제거한다는 의미이다. 즉, 50%의 실행시간을 단축시킬 수 있다는 것을 의미한다.



