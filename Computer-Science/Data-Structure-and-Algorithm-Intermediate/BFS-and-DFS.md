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
            





