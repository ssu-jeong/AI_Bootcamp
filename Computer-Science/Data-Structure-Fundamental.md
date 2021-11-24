# ADT(추상자료형)와 자료구조

---

- [자료구조를 알아야 하는 이유](https://youtu.be/OH7prOt3vQA)
<br>

- [무조건 알아야하는 자료구조/ADT](https://youtu.be/Nk_dGScimz8)

---

### 자료구조 핵심 : ADT(Abstract Data Type)와 연결리스트, 큐, 스택

---

#### 추상자료형이란?

> 추상적 자료형(Abstract Data Type, 줄여서 ADT)은 기능의 구현 부분을 나타내지 않고 순수한 기능이 무엇인지 나열한 것.

- 프로그래밍에서 테이터처리를 위한 자료형 존재.
<br>

- 파이썬에서 프로그래밍을 위한 도구 -> **기본자료형(숫자, 문자열, 리스트, 딕셔너리 등)**
<br>

- ADT는 추상적으로 필요한 기능을 나열한 일족의 명세서(로직).
<br> 

   - ADT는 기본자료형(대표적으로 리스트, 숫자, 문자열)을 활용하여 **사용자에 의해 구현**

###### 🌱 abstract

- 소프트웨어가 발전하면서 프로그램의 크기나 복잡도가 같이 증가하였는데, abstract는 프로그램의 **핵심부분을 간단하게 설명** 가능하게 한다.

![image](https://github.com/Maiven/data-science/blob/main/ADT.png?raw=true)

#### 추상자료형의 필요성

> 추상 자료형은 구현자와 사용자를 분리해 준다. 라이브러리를 가져다 쓰거나 내장 함수를 사용하는 것도 추상 자료형이 정의되어 있기 때문. 또한 추상 자료형에 대한 구현은 외부로 부터 숨겨져 정보 은닉 (Information Hiding)이 이루어지게 된다. 

- 이렇게 추상자료형으로 작성이 된 코드는 코드의 단위성이 높아지기 때문에 스캔에 대한 구현코드가 바뀌어도 그 코드를 사용하는 다른 코드들 까지 수정해야 할 필요가 없어져서 유지보수에도 효율적.

###### 추상자료형의 예

- 리스트

- 스택

![image](https://media.vlpt.us/images/lisapark6956/post/cc00e9e0-4c61-4ccc-80d6-46f64a0c0eaf/image.png)

- 큐

![image](https://media.vlpt.us/images/lisapark6956/post/87bdab24-c62f-483d-b8e3-4317876b67fe/image.png)

- 맵

---

## liked-list(연결리스트)

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%E1%84%85%E1%85%B5%E1%84%89%E1%85%B3%E1%84%90%E1%85%B3_%E1%84%85%E1%85%B5%E1%84%89%E1%85%B3%E1%84%90%E1%85%B3.png?raw=true)

- 연결리스트는 리스트들을 **연결**해준다.
<br>

   - 연결은 프로그래밍에서 **참조의 기능**으로 구현되고,

   - 연결리스트는 **리스트의 길이를 별도로 지정해줄 필요 없다.**

   - 연결리스트는 별도의 인덱스를 지정할 필요없이 연결되는 구조

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%85%E1%85%B5%E1%84%89%E1%85%B3%E1%84%90%E1%85%B3%E1%84%87%E1%85%A2%E1%84%8B%E1%85%A7%E1%86%AF%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%E1%84%85%E1%85%B5%E1%84%89%E1%85%B3%E1%84%90%E1%85%B3.png?raw=true)

- 배열은 요소를 직접 접근하여 저장하고 인덱스를 활용
<br>
- 연결리스트의 각 요소는 참조하는 **노드**에 저장.

   - 각 노드는 연결리스트의 다음 노드에 대해 **참조(또는 '포인터")**를 한다.

      - 참조기호 :  ( **.** )

      - 삽입, 할당기호 : ( **=** )

```python
# 연결리스트의 노드를 저장하는 첫 단계

class Node:
  def __init__(self,value,next=None):
    self.value = value  # 노드의 값을 나타내는 value
    self.next = next  # 노드의 다음위치를 가리키는 next의 초기값은 None

class linked_list:
  def __init__(self,value):
    self.head = Node(value) # 초기 클래스에 head노드선언

  def add_node(value):
    print('head.value:', head.value)
    print('head.next:', head.next)
    node = head           # 첫번째 위치에 해당하는 head를 생성하고, node 변수에 저장해둔다.
    while node.next:      # head노드의 다음위치에 노드가 생성될 때까지 반복문 진행한다.
      node = node.next    # head노드의 다음위치에 노드가 있는 경우(두번째 노드라고 가정),
      print('print in while:', node.next)
                          # 두번째 노드부터 node변수에 저장
    node.next = Node(value) # 데이터를 노드 다음위치에 저장
```

```python
# 연결리스트의 노드값들에 대해서 봐보자.

head = Node(5)    # head노드에 값5를 저장
linked_list.add_node(11) # 값11을 추가

print(head.value) # head노드의 값은 5
print(head.next.value) # head노드의 다음위치노드의 값은 11
```

- 연결리스트의 핵심개념은 **연결**이고, 이것은 참조되는 노드의 '**위치바꾸기**'라고할 수 있다.

```python
# 리스트를 연결해보자.

node1 = Node(3)
node2 = Node(4)

node3 = Node(5)
node4 = Node(6)

node1.next = node2
node2.next = node3
node3.next = node4

node = node1        # 첫번째노드부터 시작한다.
while node:         # 노드별로 반복문을 수행
  print(node.value) 
  node = node.next  # 다음노드를 현재노드에 저장하면서 위치를 바꾼다.

```

- 연결리스트도 리스트의 메소드와 같은 기능들을 구현할 수 있다.

   - 삽입 / 삭제 / 검색

```python
#주석 참고하여 삭제기능 구현

# 클래스에 연결리스트 구현
class Node:
  def __init__(self, value):
    self.value = value
    self.next = None

class linked_list:
  def __init__(self, value):
    self.head = Node(value)

  def add_node(self, value):
    if self.head == None:
      self.head = Node(value)
    else:
      node = self.head
      while node.next:
        node = node.next
      node.next = Node(value) # init함수의 value

  # 연결리스트의 삭제구현
  def del_node(self,value):
    if self.head == None:
      # 해당 값에 대한 노드는 없다.
      # 의미없는 조건에서 함수는 아무것도 반환하지 않는다. 
    elif self.head.value == value:
      # 노드의 위치를 변경시킨다.
      # 변경된 노드에 대해서 삭제를 진행한다.
    else:
      node = self.head
      while node.next:
        if node.next.value == value:
         # 노드의 위치를 변경시킨다.
         # 변경된 노드에 대해서 삭제를 진행한다.
        else : 
         # 다음 노드의 위치를 현재 노드에 넣어준다.

  # 연결리스트의 노드출력을 위한 기능
  def ord_desc(self):
    node = self.head
    while node:
      print(node.value)
      node = node.next 
```

```python
# 노드출력 테스트
linkedlist = linked_list(0)
linkedlist.ord_desc()

# 노드 삽입 테스트
for value in range(1,10):
  linkedlist.add_node(value)
linkedlist.ord_desc()

# 연결리스트의 head의 주소를 확인함으로써 메모리상에 연결리스트가 존재함을 확인
linkedlist.head
```

```python
# 노드삭제 테스트 1
print('test1 ---------')
linkedlist = linked_list(0) # 노드 초기값 설정
linkedlist.del_node(0)  # 노드삭제
linkedlist.del_node(0)  # 노드삭제
linkedlist.ord_desc()

# 노드삭제 테스트 2
print('test2 ---------')
linkedlist = linked_list(0) # 노드 초기값 설정
linkedlist.add_node(1)
linkedlist.del_node(0)  # 노드삭제
linkedlist.ord_desc()

# 노드삭제 테스트 3
print('test3 ---------')
linkedlist = linked_list(0) # 노드 초기값 설정
for value in range(1,5):
  linkedlist.add_node(value)
linkedlist.del_node(3)  # 노드삭제
linkedlist.ord_desc()

""" 
위의 소스코드의 경우 주소의 위치를 바꿔주면서 '교체'한다.
"""
```

- 노드간의 ''**동적**'이라는 개념을 컴퓨터 프로그래밍에서는 '**연결**'이라는 개념으로 접목시켰다.

   - 연결하면서 값의 위치가 바뀌고 위치가 바뀌면 값도 바뀐다.

```python
# 연결리스트에서 검색구현
class Node:
  def __init__(self, value):
    self.value = value
    self.next = None

class linked_list:
  def __init__(self, value):
    self.head = Node(value)

  def add_node(self, value):
    if self.head == None:
      self.head = Node(value)
    else:
      node = self.head
      while node.next:
        node = node.next
      node.next = Node(value) # init함수의 value

  # 연결리스트의 삭제구현
  def del_node(self,value):
    # head의 참조값이 없는 경우
      # 해당 값에 대한 노드는 없다.
      # 의미없는 조건에서 함수는 아무것도 반환하지 않는다. 
    # head의 값이 현재 값과 같은 경우
      # 노드의 위치를 변경시킨다.
      # 변경된 노드에 대해서 삭제를 진행한다.
    # 나머지 경우
      node = self.head
      while node.next:
        if node.next.value == value:
         # 노드의 위치를 변경시킨다.
         # 변경된 노드에 대해서 삭제를 진행한다.
        else : 
         # 다음 노드의 위치를 현재 노드에 넣어준다.

  # 연결리스트의 노드출력을 위한 기능
  def ord_desc(self):
    node = self.head
    while node:
      print(node.value)
      node = node.next 
          
  # 연결리스트 검색함수
  def search_node(self,value):
    node = self.head
    # 노드가 있는 경우 아래 작업을 반복한다.
      # 노드의 값이 현재 값과 같은 경우
        #노드를 반환한다.
      # 노드의 값이 다른 경우
        # 다른 노드의 위치를 현재 노드에 넣어준다.
```

```python
linkedlist = linked_list(0) # 연결리스트 초기화

# 연결리스트에 노드 다시 추가
for value in range(1,11):
  linkedlist.add_node(value)
linkedlist.ord_desc()

# 4라는 값을 갖고 있는 노드를 연결리스트에서 검색해보자.

node = linkedlist.search_node(4)
print(node.value)
print(node.next.value)      # 4 다음 값 검색
```

- 위의 head 노드를 삭제하는 것도 head 자체를 바로 삭제하는 것이 아니라, head의 **위치를 바꿔주는 것**이다.
<br>

- 기존방식이었던 인덱스를 통해 함수로 삼입/삭제/검색이 가능했었지만, 연결리스트는 인덱스의 기능을 할 수 있도록 **노드별로 위치를 변경**해줘야한다는 다른 점이 있다.

## Queue(큐)

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%8F%E1%85%B2_%E1%84%89%E1%85%A1%E1%86%BC%E1%84%89%E1%85%A6.png?raw=true)

- 큐는 항목을 FIFO(선입 선출) 순서로 저장하는 자료구조
<br>

- **deque**(double-ended queue)
<br>

   - 큐에서 **양방향**으로 데이터를 처리
<br>

   - double은 자료구조에서 양방향을 의미

      - [리스트를 큐로 사용하기](https://docs.python.org/ko/3/tutorial/datastructures.html?highlight=deque)

      - [collections 모듈의 deque](https://docs.python.org/ko/3/library/collections.html#collections.deque)

```python
# 리스트 메소드를 사용해서 큐를 만들어보기

from collections import deque
queue = deque(["Eric", "John", "Michael"])
queue.append("Terry")           
queue.append("Graham")

print('queue:', queue)
print('queue.popleft():',queue.popleft())
print('queue.popleft():',queue.popleft())
print('queue:', queue) 
```

- Queue 클래스의 경우, 먼저 init 메서드를 정의
<br>
   - 이 메서드에서 front(앞)와 rear(뒤) 인스턴스변수를 초기화 해야한다.

```python
class Queue:
    def __init__(self):
        self.front = None
        self.rear = None
```

- 큐의 Time and Space Complexity(시간, 공간 복잡도)
<br>

   - Enqueue(대기열에 넣기)
     -> 데이터를 큐에 추가하면 (데이터를 큐 rear에 추가) O(1) 시간이 걸린다.
<br>

   - Dequeue(대기열에서 빼기)
     -> 데이터를 큐에서 빼면 (데이터를 큐 front에서 제거) O(1) 시간이 걸린다.

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%8F%E1%85%B2.png?raw=true)

```python
# 연결리스트를 이용한 큐 구현
class LinkedListNode:
    def __init__(self, data):
        self.data = data
        self.next = None

class Queue:
    def __init__(self):
        self.front = None
        self.rear = None

    # 대기열에서 넣기(큐에 값을 집어넣는 함수)
    def enqueue(self, item):
        new_node = LinkedListNode(item)
        # 큐가 비어있는지 체크
        if self.rear is None:
            self.front = new_node
            self.rear = new_node
        else:
            # 새로운 노드를 rear 다음에 삽입
            self.rear.next = new_node
            # 새로운 노드를 rear 재할당
            self.rear = new_node
        return new_node.data

    # 대기열에서 빼기(큐에서 값을 빼내는 함수)
    def dequeue(self):
        # 큐가 비어있는지 체크
        if self.front is not None:
            # front값을 old front에 삽입
            old_front = self.front
            # old front 다음 값을 front값에 삽입
            self.front = old_front.next

        # 큐가 비어있는지 체크
        if self.front is None:
            # rear를 None으로 지정한다.
            self.rear = None

        return old_front.data
    
    # 연결리스트의 노드출력을 위한 기능
    def ord_desc(self):
        node = self.front
        while node:
            print(node.data)
            node = node.next
```

```python
print('1,2,3 차례대로 추가하기:')
q = Queue()
q.enqueue(1)
q.enqueue(2)
q.enqueue(3)
q.ord_desc()

print('대기열에서 빼기:')
q.dequeue()
q.ord_desc()

"""
실제로 값을 빼거나 삭제시키는 개념 아님!!
"""
```

- enqueue에서는 새로운 노드의 저장공간(변수)를 만들어주고, 그 저장공간에 노드를 넣어주는 개념
<br>

- dequeue는 삭제할 노드를 위해 저장공간(변수)를 만들어주고, 그 저장공간에 삭제노드를 넣어주는 개념


### Stack(스택)

- 책을 쌓는 것처럼 차곡차곡 쌓아 올린 형태의 자료구조

![image](https://github.com/Maiven/data-science/blob/main/stack.png?raw=true)

```python
# 리스트 메소드를 사용해서 스택만들어보기

stack = [3, 4, 5]
stack.append(6)
stack.append(7)
print(stack)

stack.pop()
print(stack)

stack.pop()
print(stack)

stack.pop()
print(stack)

# 위의 코드처럼 push와 pop을 활용해서 공간에 값이 유동적으로 변한다.(동적처리)
```

```python
# 리스트 사용하여 스택 구현
class Stack:
    def __init__(self):
        self.data = []    # 동적처리(리스트값이 정해져있지 않음, 대괄호만 선언 및 저장)
```

- push 함수는 파이썬의 리스트개념과 리스트메소드(append, pop)를 사용하여 인덱스를 추가

- pop 함수는 인덱스의 마지막 노드를 추출

```python
class Stack:
    def __init__(self):
        self.data = []

    def push(self, item):
        self.data.append(item)

    def pop(self):
        if len(self.data) > 0:
            return self.data.pop()
        return "The stack is empty"
```

```python
# 내장함수 아닌, 연결리스트 개념고 단순변수를 사용하여 스택 구현

class LinkedListNode:
    def __init__(self, data):
        self.data = data
        self.next = None

class Stack:
    def __init__(self):
        self.top = None
```

- push 함수 : 연결리스트의 헤드에 새 노드 삽입
연결리스트의 헤드(최상단)에 있는 노드 추출
<br> 

- pop 함수 : 연결리스트의 헤드(최상단)에 있는 노드 추출
<br>

- 스택의 소스코드도 큐와 동작은 유사하지만, 입출력의 순서는 반대!!

```python
# [연결리스트를 이용한 스택 구현]
# 아래의 코드는 스택이 내부적으로 어떻게 작동되는지 확인하기 위해 작성되었다.
# 파이썬에서 자체적으로 제공하는 리스트의 append, pop 메소드를 활용하면 쉽게 구현될 수 있지만,
# 아래처럼 다른 방법으로도 구현하는 코드를 보면서 스택에 대한 이해도를 높일 수 있다.

class LinkedListNode:
    def __init__(self, data):
        self.data = data
        self.next = None

class Stack:
    def __init__(self):
        self.top = None

    def push(self, data):
        # 신규 노드 생성
        new_node = LinkedListNode(data)
        # 최상단의 노드를 신규 노드 다음 노드로 삽입
        new_node.next = self.top
        # 신규 노드를 최상단에 삽입
        self.top = new_node
        return new_node.data

    def pop(self):
        # 스택이 비어있는지 확인
        if self.top is not None:
            # 최상단의 노드를 삭제할 노드로 삽입
            popped_node = self.top
            # 삭제할 노드 다음 노드를 최상단의 노드로 삽입
            self.top = popped_node.next
            # 삭제할 노드로부터 값 리턴
            return popped_node.data

    # 연결리스트의 노드출력을 위한 기능
    def ord_desc(self):
        node = self.top
        while node:
            print(node.data)
            node = node.next
```

```python
# 스택에 내부적으로 값을 쌓고 pop하는 과정을 살펴본다.
s = Stack()

print('1,2,3 차례대로 추가하기:')
s = Stack()
s.push(1)
s.push(2)
s.push(3)
s.ord_desc()

print('대기열에서 빼기:')
s.pop()
s.ord_desc()
```

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%85%E1%85%B5%E1%86%BC%E1%84%8F%E1%85%B3%E1%84%83%E1%85%B3%E1%84%85%E1%85%B5%E1%84%89%E1%85%B3%E1%84%90%E1%85%B3_%E1%84%89%E1%85%B3%E1%84%90%E1%85%A2%E1%86%A8.png?raw=true)

### Review

---

**오늘 배운 것**

```
1) 자료구조에 대한 이론
2) 자료구조의 기본이 되는 도구들
3) 자료구조 활용 시 고려해야 되는 것들
```

**오늘 해야할 것**

```
1) 자료구조의 기본 도구들에 대해 익숙해지기
2) 자료구조에서 배운 이론들에 대해서 코드로 살펴보기
```

### Reference

---

- [파이썬의 문법을 활용한 자료구조](https://docs.python.org/ko/3/tutorial/datastructures.html)
<br>
- [파이썬 복잡도 상세내용](https://www.ics.uci.edu/~pattis/ICS-33/lectures/complexitypython.txt)
<br>
- [데이터의 7V](https://3months.tistory.com/348)
<br>
- [자료구조 - 스택, 큐](https://devuna.tistory.com/22)