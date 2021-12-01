# Graph

---

- 키워드: 크래프, 트리, 순회

- [자료구조와 그래프](https://youtu.be/cUEQmPh57MU)

---

## 그래프

### 그래프의 기본 컨셉

---

![image](https://github.com/Maiven/data-science/blob/main/graph.jpeg?raw=true)

- 자료구조에서 배운 트리와 연관된 개념

- 노드 간에 연결될 수있다는 점을 제외하고는 트리와 비슷하며, **루프를 형성할 수도 있다.**

- **트리에서는 노드를 탐색하는 경우 제한이 있지만,** 그래프는 루프형성이 가능하기 때문에 다른 범위의 개념으로 필요한 자료구조이다.

   - 예) **object간의 관계를 표현**할 때 유용.(SNS, 도로상의 차량 검색, 운송시스템)

![image](https://i.imgur.com/Eb2SkhH.jpg)

- 그래프는 기본적으로 vert(노드 또는 정점)와 edge(간선)으로 연결되어 있다.

#### 그래프와 트리의 특징

- 그래프는 **노드간의 관계**, 트리는 **노드간의 계층**을 표현

- 그래프와 트리는 서로 다른 개념이다.

   - 트리에는 그래프에 없는 **계층**개념이 있다.

   ![image](https://github.com/Maiven/data-science/blob/main/%E1%84%90%E1%85%B3%E1%84%85%E1%85%B5%E1%84%8B%E1%85%AA%E1%84%80%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B3.png?raw=true)<br>

### 그래프의 유형

---

- 그래프의 특성은 **directed(방향성)** 또는 **undirected(무방향성).**

- 그래프가 "한쪽 방향(one-way)"으로 설명될 수 있다면 directed(방향성) 그래프가 적합

- 방향성에서는 순서가 있으므로 **마지막 노드(리프, leaf)** 가 있다. (-> 그림에서는 'F')

![image](https://i.imgur.com/vfwRrDR.jpg)

- directed(방향성)그래프는 **bidirectional(양방향)** 이 될 수도 있다. 

   - 예) 도로가 일방통행이기 때문에 도로지도는 방향이 지정되지만, 대부분의 거리는 양방향도로로 구성된다.

![image](https://i.imgur.com/m8mA3go.jpg)

- 관계의 목적이 **상호 교환**이라면, **undirected(무방향성)** 그래프가 가장 적합

- **"교환"관계는 항상 상호이므로 undirected(무방향성)** 그래프가 여기에서 가장 의미 있다.

- 무방향성은 방향(화살표)이 따로 지정되어 있지 않다.

- 간선으로 연결된 노드들끼리는 서로 인접(adjacent)해있다고 하며, 이웃(neighbor)라고 칭한다.

#### Cyclic and Acyclic Graphs(순환 및 비순환 그래프)

- **순환(루프)을 형성할 수 있는 경우(예: 방문한 노드에 다시 방문) 그래프는 순환그래프**

   - 예) 이미지에서 B에서 시작한 다음 **가장자리를 따라 C, E, D**로 이동한 다음 **B(이미 방문한 노드)로 돌아갈 수 있다.**

![image](https://i.imgur.com/XvMDal0.jpg)

![image](https://i.imgur.com/LXAm7mv.jpg)

- **undirected** 그래프는 항상 동일한 노드에 재방문할 수 있으므로 **순환 그래프**

- 순환을 형성할 수 없는 경우(예: 모서리를 따라 이미 방문한 노드에 방문할 수 없음) **비순환 그래프**

### Weighted Graphs(가중 그래프)

- **가중그래프에는 edge(간선)** 와 관련된 값이 있다.

- 각 edge의 가중치에 할당된 특정값을 호출.

- 가중치는 서로 다른 그래프에서 서로 다른 데이터를 나타냄

   - 예) 도로 구간을 나타내는 그래프에서 가중치는 도로의 길이를 나타낼 수 있다. 

- 그래프에서 **경로의 총 가중치가 높을수록 경로이동시간(비용)** 이 길어진다.

   - 가중치는 모든 경로 비교 시, 어떤 경로를 선택할 지에 사용

![image](https://i.imgur.com/rjMjqk3.jpg)

###### 순회(traversal)

- 그래프에 **연결된 노드를 탐색**

- 중요한 것은 **아직 방문하지 않은 노드의 순회 순서**

### Directed Acyclic Graphs (DAGs)

- **방향석 비순환 그래프(DAG)는 순환되지 않고 특정한 단방향** 그래프

- edge가 순서대로 향하도록 DAG의 노드를 **선형(단방향)으로 정렬**할 수 있다.

![image](https://i.imgur.com/nqhM7uz.jpg)

## 그래프의 활용

---

### 그래프의 활용

---

- 그래프를 나타내는 방법: 인접리스트(adjacency lists)과 인접행렬(adjacency matrices)

- 그래프를 구현할 때 저장할 데이터 유형과 그래프에서 실행해야하는 작업을 이해하는 것이 중요

- 각 방법을 사용할 때, verts C와 D 사이의 관계를 어떻게 표현하는지가 중요

![image](https://i.imgur.com/siGmq8X.jpg)

#### 인접리스트(Adjacency List)

- 인접리스트에서 그래프는 **전체 노드 목록을 저장**

![image](https://i.imgur.com/GiStmNh.jpg)

- vertices(정점)는 **O(1)상수시간에 각 edge(간선)에 접근**
   - edge가 set에 포함되어 있기 때문에 O(1) 상수시간에 edge가 있는지 확인 가능 (예: A가 G set에 포함)

```python
# 위 그림에 대해 딕셔너리를 사용한 인접리스트 예시
# 노드가 키가 되고, 인접노드가 값이 되는 딕셔너리이다.
# 가장자리 노드들은 set으로 구현되어 있다.

class Graph:
    def __init__(self):
        self.vertices = {
                            "A": {"B"},   # 여기서 {"B"}가 set의 형태이다.
                            "B": {"C", "D"}, # {"B" : {}}의 형태는 딕셔너리
                            "C": {"E"},     # 즉, 딕셔너리 안에 set이 있는 것이다.
                            "D": {"F", "G"},
                            "E": {"C"},
                            "F": {"C"},
                            "G": {"A", "F"}
                        }
```

#### 인접행렬(Adgacency Matrix)

![image](https://i.imgur.com/GiStmNh.jpg)

- 소스코드로 작성하ㅣ 전에, 0과1로 구성되는 행렬부분(노드간 연결)이 어떤 부분인지 그림으로 그려본다.

   - 행노드와 연결되는 열노드에 대해서 1값이 된다.

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%8C%E1%85%A5%E1%86%B8%E1%84%92%E1%85%A2%E1%86%BC%E1%84%85%E1%85%A7%E1%86%AF.png?raw=true)

- 행렬은 리스트 안에 리스트가 있는 2차원 배열로 표현

   - 구현을 통해 기본 제공되는 행렬간에 **edge weights(간선 가중치)** 를 알 수 있다. 

   - **0은 관계가 없음**을 나타내지만 다른 값은 **edge label 또는 edge weight**를 나타낸다.

   - 인접행렬의 단점은 **노드 값과 해당 인덱스 사이에 연관성이 없다**는 것.

- 실제로 인접리스트와 인접행렬을 모두 구현하면 Vertex(정점) 및 Edge(간선) 클래스를 포함하여 더 많은 정보를 파악할 수 있다.

#### 그래프에서의 복잡도

- **인접리스트는 리스트**의 개념을 활용하고, **인접행렬은 코드에서 볼 수 있듯이 배열**의 개념을 활용

   - 인접행렬의 장점: **구현이 쉽다**

   - 인접행렬의 단점: **특정노드에 방문한 노드들을 알기 위해서는 모든 노드를 확인**해야 한다. (시간복잡도 O(N))

      - 단점을 보완하기 위해 인접리스트로 표현방식이 생김

- 인접리스트는 실제 연결된 관계만을 저장해주어 실행시간에 영향을 적게 준다.

   - 인접리스트의 단점: **특정 노드간의 연결관계를 확인하기 위해서 반복문이 활용**되어야 한다. (시간복잡도 O(N)이상)

![image](https://i.imgur.com/yi1P4AF.jpg)

###### 인접리스트 구현

- 위의 인접리스트와 차이점은 edge(간선)에 **가중치(weight)** 를 부여 할 수 있다는 것!!

```python
# 인접리스트 구현
class Graph:
    def __init__(self):
        self.vertices = {
                            "A": {"B": 1},  # 가중치 부여
                            "B": {"C": 3, "D": 2},  # 가중치 부여
                            "C": {},
                            "D": {},
                            "E": {"D": 1}   # 가중치 부여
                        }
```

###### 인접행렬 구현

- 행렬의 한 가지 이점은 간선 가중치를 표현하는 것이 쉽다.

```python
# 인접행렬 구현

class Graph:
    def __init__(self):
        self.edges = [[0,1,0,0,0],
                      [0,0,3,2,0],
                      [0,0,0,0,0],
                      [0,0,0,0,0],
                      [0,0,0,1,0]]
```

## 순회(Traversal)

### 순회 기본개념

---

순회는 Traversal로 명명되며, 그래프 또는 트리처럼 연결된 구조에서 **노드를 한 번씩 탐색**하는 개념이다.

- 순회의 목적은 모든 노드 또는 특정 **노드를 방문하는 방법**을 찾는 것

- BST(이진검색트리)와 다른 규칙이 적용되며 **방향에 따라 탐색방법**이 달라질 수 있다. 

#### 그래프와 트리의 순회구분

- 그래프의 순회는 DFS(깊이우선탐색), BFS(너비우선탐색) 방법이 있다.

   - **DFS, BFS는 탐색 알고리즘**

- 트리의 순회 -> 전위, 중위, 후위순회

   - 그래프는 루트, 부모, 자식노드 개념이 없지만 **전위, 중위, 후위순회의 순회개념을 활용하여 DFS, BFS**를 구현

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%90%E1%85%B3%E1%84%85%E1%85%B5%E1%84%89%E1%85%AE%E1%86%AB%E1%84%92%E1%85%AC.png?raw=true)

- 전위순회(preorder traverse) : 루트를 먼저 방문

- 중위순회(inorder traverse) : 왼쪽 서브트리를 방문 후 루트방문

- 후위순회(postorder traverse) : 순서대로 서브트리(왼쪽->오른쪽)를 모두 방문 후 루트를 방문

###### 순회구현

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%80%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B3%E1%84%89%E1%85%AE%E1%86%AB%E1%84%92%E1%85%AC.png?raw=true)

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%89%E1%85%A5%E1%84%87%E1%85%B3%E1%84%90%E1%85%B3%E1%84%85%E1%85%B5%E1%84%80%E1%85%A2%E1%84%82%E1%85%A7%E1%86%B7.png?raw=true)

- 서브트리를 구분하여 어떤 결과가 나올 것인지 예상

   - 루트는 1개(10)이다.

   - 부모노드는 트리별 1개씩이니 총 4개(8, 1, 9, 12)

```python
# 수도코드로 배우는 트리순회

# 먼저 순회를 진행하기 위해 트리형태의 노드들을 생성한다.
class node:

  # root -> left -> right 방향대로 노드 생성
  def __init__(self, value, left=None, right=None): 
    value  
    left    
    right  

root_node = node(10,
                 node(8, 
                      node(7),  
                      node(1, 
                           node(3), node(2)
                           )
                      ),
                 node(9, 
                      node(11), 
                      node(12, 
                           node(13)
                           )
                      )
                 )

# 전위 순회 
def pre_order(node):

  print(node.value)       # 루트노드
  pre_order(node.left)    # 왼쪽노드
  pre_order(node.right)   # 오른쪽노드

# 중위 순회
def in_order(node):

  in_order(node.left)    # 왼쪽노드
  print(node.value)      # 루트노드
  in_order(node.right)   # 오른쪽노드

# 후위 순회
def post_order(node):

  post_order(node.left)   # 왼쪽노드
  post_order(node.right)  # 오른쪽노드
  print(node.value)       # 루트노드
```

### Review

---

**오늘 배운 것**

```
1) 그래프 사용 이유
2) 그래프의 유형
```

**오늘 해야할 것**

```
1) 실제  그래프 활용사례
2) 그래프로 코드 작성해보기
```

### Reference

---

- [그래프와 트리의 관계에 대한 고찰](https://shoark7.github.io/insight/rationality/relationship-between-graph-and-tree)

- [kakao의 오픈소스 Ep1 – 대용량 분산 그래프DB “S2Graph”](https://tech.kakao.com/2016/01/29/opensource-1-s2graph/)

- [그래프에 대한 문제해결](https://programmers.co.kr/learn/courses/30/parts/14393)

- [그래프를 활용한 다양한 상황](https://leetcode.com/problemset/all/?topicSlugs=graph&difficulty=Medium)