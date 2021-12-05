# BFS와 DFS

---

- 키워드: BFS, DFS

- [BFS와 DFS의 개념에 대해 다양한 그림으로 생각](https://youtu.be/-wsYtm0x3nw)

---

## BFS와 DFS에 대한 설명

### BFS & DFS

---

BFS, DFS는 BFT(breadth-first traversal), DFT(depth-first traversal)이라고도 불리는데, traversal은 트리에서 배웠던 순회와 같은 용어

- 순회는 트리와 그래프 같은 연결구조에서 **노드를 방문**하는데 사용

- **BFS와 DFS는 순회(방문)하면서 탐색하는 탐색 알고리즘**

   - 단, **출발지 노드와 그래프/트리 구조**에 따라 탐색하는 순서와 노드가 달라질 수 있다.

#### BFS(breadth-first search) - 너비우선탐색

![image](https://codestates-urclass.s3.ap-northeast-2.amazonaws.com/urclass-reference-contents/Immersive/Basic-CS/Algorithms/DFS+BFS+Backtracking/Breadth-First+Search.jpg)

- BFS는 큐의 개념이 사용

   - 노드 'S' 부터 저장되고 사용된다. (FIFO)

   - 순서: S->1->2->3->4->5->6->7

- BFS의 활용

```
      길 찾기, 라우팅
      BitTorrent와 같은 P2P 네트워크에서 인접 노드 찾기
      웹 크롤러
      소셜 네트워크에서 멀리 떨어진 사람 찾기
      그래프에서 주변 위치 찾기
      네트워크에서 방송
      그래프에서 주기 감지
      연결된 구성 요소 찾기
      몇 가지 이론적 그래프 문제 풀기
```

- BFS 의사코드

```python
BFS(graph, startVert):
    for v of graph.vertexes:
        v.color = white

    startVert.color = gray
        queue.enqueue(startVert)# 시작

    while !queue.isEmpty():
        u = queue[0]  # 큐의 헤드 (S)

        # 이웃문을 체크하는 것이 핵심부분
        for v of u.neighbors:
            if v.color == white:
                v.color = gray
                queue.enqueue(v)

        queue.dequeue()# 끝
        u.color = black
```

###### <의사코드 해석>

-  그래프의 각 노드를 보고 **방문할 노드에 대해 구분**

   - 일단 모든 verts(정점 또는 노드)를 방문하지 않은 상태(white)

- **시작 노드를 gray로 표시**

   - **gray**는 사작 노드의 이웃을 탐색

   - 시작 노드를 큐에 넣는다.

      - 이는 while 루프에 들어가면서 **첫 번째 vert**가 될 것임을 의미

      - while 루프의 시작 부분에서 확인하는 조건은, **큐가 비어 있지 않은지 여부**

      - 비어있지 않으면 큐의 첫 번째 항목을 변수에 저장(u = queue[0])

         - 각 이웃의 vert에 대해 반복문 수행

         - 방문하지 않았는지 (white) 확인

         - 방문하지 않은 경우 **gray**로 표시(이웃을 탐색한다는 의미)

      - 탐색한 현재 vert를 대기열에서 빼고(deque), 해당 vert를 **black**으로 표시(방문한 것으로 표시)

- 그래프의 모든 **verts를 탐색할 때까지** 위의 프로세스를 계속 진행

###### BFS는 큐 자료구조를 활용하고 재귀호출은 활용 않음!

- BFS(너비우선탐색)은 **노드가 적은 경우 최단 경로**를 탐색할 때 유용

- 너미우선적으로 노드를 탐색하는 경우, **큐를 활용**하므로 노드가 많아지는 경우 메모리 저장공간이 증가하는 단점 존재

- BFS는 재귀적으로 동작하지 않는데, **인접한 노드에 대해 먼저 탐색**을 하기 때문에 재귀적으로 재호출할 필요가 없다.

#### DFS(depth-first search) - 깊이우선탐색

![image](https://codestates-urclass.s3.ap-northeast-2.amazonaws.com/urclass-reference-contents/Immersive/Basic-CS/Algorithms/DFS+BFS+Backtracking/Depth-First+Search.jpg)

- 깊이우선탐색은 LIFO로서 스택의 개념을 사용

   - 순서 : 1->2->4->5->3

- 깊이우선탐색 알고리즘은 다른 경로를 **역추적**하고 탐색하기 전에 가능한 그래프를 **분할**

   - 분할은 깊이별로 탐색을 진행, 내부적으로 그래프가 분할된 후 탐색을 진행한다는 것

   - 그림에서 1->2->4->5 까지 탐색을 진행하고, 분할이 진행된 후 3을 탐색

- DFS의 활용

   - 가중 그래프의 최소 스패닝 트리 찾기
   
   - 길 찾기

   - 그래프에서주기 감지

   - 미로 문제

- DFS는 그래프의 **모든 노드를 방문**하는 경우 사용

   - 단점: **최단 경로를 찾지 못하고, 시간이 오래 걸릴 수 있다.**

- DFS 의사코드

```python
DFS(graph):#초기상태
    for v of graph.verts:
        v.color = white
        v.parent = null

    for v of graph.verts:
        if v.color == white:
            DFS_visit(v)

DFS_visit(v):
    v.color = gray

    for neighbor of v.adjacent_nodes:
        if neighbor.color == white:
            neighbor.parent = v  #트리, 그래프 -> 부모개념없다
            DFS_visit(neighbor) ## 역추적

    v.color = black
```

###### <의사코드 해석>

- 첫 번째 함수인 DFS( )는 그래프를 매개변수로 사용하고 모든 verts를 방문하지 않음(white)으로 표시

   - 각 vert의 부모를 **null**로 설정

   - 다음 루프는 그래프의 각 vert를 방문

   - 방문하지 않은 경우, 해당 vert를 두 번째 함수 DFS_visit( )에 전달

- 두 번째 함수인 DFS_visit( )는 vert를 **gray**로 표시하여 시작(탐색과정에서)

   - 그런 후, **방문하지 않은 모든 노드(인접노드)**의 갯수만큼 반복문을 수행

   - 이 루프에서 부모를 설정한 다음, **DFS_visit( )를 재귀적으로 호출**

   - **모든 이웃 탐색이 완료**되면 vert를 **black(방문함)**으로 표시

###### backtracking

백트래킹: DFS에서 활용되는 방법인데, 쉽게 말해서 노드가 있을만한 곳을 되돌아가서 모두 살펴본다는 개념

- 위의 그림처럼 DFS는 깊이우선적으로 탐색을 진행하고, 재귀적으로 아래에서부터 탐색하지 않은 정점이 있는지 확인하는 방법
            
#### BFS와 DFS에 대한 중간 비교

**DFS 장점**

- 찾는 노드의 depth가 깊을수록 빠르다.

- **메모리를 적게 차지**

**DFS 단점**

- 노드가 무한한 갯수로 존재하는 경우, **무한반복(무한루프)**에 빠진다.

**BFS 장점**

- **최단경로**를 찾기 적합

- 찾는 노드가 **인접한**경우 효과적

**BFS 단점**

- Queue를 이용해 노드를 저장하기 때문에 **노드의 수가 많을수록 메모리를 많이 소비**

## BFS와 DFS에 대한 소스코드

### BFS 소스코드

---

BFS는 큐, 딕셔너리, 리스트, 내장함수 개념을 활용

- deque(double-ended queue)

   - **양방향처리(큐의 양쪽 끝에서 삽입과 삭제 모두 가능)** 를 의미

   - 파이썬에서 양방향 삽입삭제: [파이썬의 Deque](https://www.geeksforgeeks.org/deque-in-python/)

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%8F%E1%85%B2%E1%84%8B%E1%85%AA%E1%84%83%E1%85%A6%E1%86%A8.png?raw=true)

```python
# deque를 위해 자료구조의 큐에서 배웠던 내용을 복습
from collections import deque
queue = deque(["Eric", "John", "Michael"])
queue.appendright("Terry")        # append : 오른쪽끝 삽입   
queue.appendright("Graham")          
#print(queue.pop()) 
print(queue.popleft())       # popleft : 왼쪽끝 빼오기          

#print(queue.popleft())   

print(queue) 
```

```python
# 큐를 이용하여 BFS의 개념을 구현해본다.

bfs_graph = {   # 그래프를 인접리스트로 표현
    1: [2,3,4],
    2: [1,5,6],
    3: [1,6],
    4: [1],
    5: [6,7],
    6: [5],
    7: [6],
}

def bfs_queue(start_node):
  bfs_list = [start_node]
  queue = [start_node]
  while queue:#외부반복문
    node = queue.pop(0)
    for i in bfs_graph[node]: #내부반복문 
      ##### 내부반복문에 대한 로직을 작성해보세요 #####

  return bfs_list

bfs_queue(2)
# 1차 : 그래프 연결관계 2차 : edge 연결부분
```

![image](https://github.com/Maiven/data-science/blob/main/BFS_graph.png?raw=true)

- 인점리스트가 구성되어 있는 상태에서 너미우선탐색의 로직에 따라 탐색을 진행 (검정화살표: 인접리스트구성, 주황화살표: 너미우선탐색진행)

- 화살표를 통한 노드이동방향이 정해져 있고, 시작노드가 1인 경우

   - 만약 화살표가 없고 시작 노드가 바뀐다면??


### DFS 소스코드

---

기본그래프가 주어져있을 때, 깊이 우선탐색을 2가지로 진행할 수 있다.

```python
# 재귀를 활용한 DFS 구현하기
dfs_graph = {   # 그래프를 인접리스트로 표현
    1: [2,3,4],
    2: [5],
    3: [6],
    4: [],
    5: [7],
    6: [5],
    7: [6],
}

def dfs_recur(node, dfs_list=[]):
  dfs_list.append(node)   # 리스트에 인접한 노드를 덧붙이는 형태

  for i in dfs_graph[node]:   # 노드의 인접한 노드를 기준으로 반복한다. 
    ##### 재귀개념에 대한 로직을 작성해보세요 #####
  return dfs_list

dfs_recur(2)  # 시작노드
```

```python
# 스택을 활용한 DFS 구현하기 

def dfs_stack(start_node):

  dfs_list = []
  stack_list = [start_node]

  while stack_list:
    node = stack_list.pop() # 리스트 메소드
    ##### 스택개념을 활용하여 로직을 작성해보세요 #####
  return dfs_list 

dfs_stack(7)    # 시작노드
```

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%8C%E1%85%A2%E1%84%80%E1%85%B1%E1%84%8B%E1%85%AA%E1%84%89%E1%85%B3%E1%84%90%E1%85%A2%E1%86%A8(%E1%84%80%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B3).png?raw=true)

- 그림처럼 깊이우선탐색이 2가지 방법(재귀, 스택)으로 진행 (검정화살표: 인접리스트, 초록화살표: 재귀, 파랑화살표: 스택)

- 그림은 시작노드가 1인경우

###### DFS에서 재귀와 스택의 차이점

- 스택은 리스트의 메소드만을 활용, 때문에 **위에서 아래로 코드를 해석**

   - 실행속도가 재귀보다 빠르다.

   - 스택은 **후입선출** 개념을 적용하였기 때문에, 마지막에 삽입된 노드를 기준으로 깊이우선탐색을 진행 (**재귀와 다르게 역순으로 진행**)

- **재귀구현의 경우는 자기함수를 호출**하는 형태, 때문에 코드가 간결

### Review

---

**오늘 배운 것**

```
1) 그래프의 응용유형
2) BFS, DFS의 그림을 통한 이해와 코드흐름
```

**오늘 해야할 것**

```
1) 그래프가 실제 활용되는 예시를 찾아보며 그래프에 대해 이해
2) BFS와 DFS에 대한 소스코드 및 그림예시 익히기
```

### Reference

- [그래프·트리 순회(깊이우선탐색, 너비우선탐색)](https://jocoma.tistory.com/entry/%EA%B7%B8%EB%9E%98%ED%94%84%C2%B7%ED%8A%B8%EB%A6%AC-%EC%88%9C%ED%9A%8C%EA%B9%8A%EC%9D%B4%EC%9A%B0%EC%84%A0%ED%83%90%EC%83%89-%EB%84%88%EB%B9%84%EC%9A%B0%EC%84%A0%ED%83%90%EC%83%89)

- [DFS - 위키백과](https://ko.wikipedia.org/wiki/%EA%B9%8A%EC%9D%B4_%EC%9A%B0%EC%84%A0_%ED%83%90%EC%83%89)






