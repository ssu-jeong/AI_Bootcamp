# 자료구조의 활용

---
- [재귀는 하나의 데이터활용방법이다.](https://youtu.be/a4Qy4tSadSI)

- [[자료구조 알고리즘] Tree의 종류](https://youtu.be/LnxEBW29DOw)

---

## 검색과 재귀(Searching and Recursion)

---

```python
# 인트로 코딩
# 중첩반복문 복습

numbers = [1,2,3,4]
len_numbers = len(numbers)
for i in range(0, len_numbers):   # 반복인덱스 : 0,1,2,3
  for j in range(1, len_numbers): # 반복인덱스 : 1,2,3
    print("i:",i," j:",j)
  print()
```

```python
# 입력된 리스트에서 요소들의 합을 큰 순서대로 구해보자(조건 : 모든 요소들의 합이 아니다.)
# 리스트의 메소드와 반복문을 활용해야 한다.

def remain_sum(numbers):
  result = []
  init_value = 0

  # 왼쪽인덱스부터 합을 구한다.
  # 반복문 : 0부터 4까지 result 리스트에 값을 append 한다.(반복인덱스 : 0,1,2,3)
  for i in range(0, len(numbers)):
    result.append(init_value)
    print("left sum - result[",i,"]:",result[i])
    init_value = init_value + numbers[i]    # append되는 index와 value를 구분해야 된다.

  init_value = 0   # 값 초기화(왼쪽에 대한 합을 구했으니, 이제 오른쪽인덱스부터 합구하기)

  # 구해진 값을 활용하여 오른쪽인덱스부터 더하면서 최종 리스트값을 구한다.
  # 반복문 : 3부터 -1까지 -1줄어들면서 result 리스트에 값을 더한다.(반복인덱스 : 3,2,1,0)
  for i in range(len(numbers)-1, 0-1, -1):
    result[i] = result[i] + init_value
    print("final sum - result[",i,"]:",result[i])
    init_value = init_value + numbers[i]

  return result

numbers = [int(numbers) for numbers in input("리스트값을 입력하세요 : ").split(',')]
print("결과:",remain_sum(numbers))
``` 

#### 검색(Searching)

> 특정 노드를 추가하거나 삭제를 위해서는 검색이 우선
<br>
다양한 **알고리즘을 활용**하는 경우, 최적 알고리즘 경로를 측정하는데 쓰인다.
<br>

- 검색 알고리즘은 배열이 정렬되지 않은 경우 **순차 검색(sequential search)**
<br>

   - **선형 검색**이라고도 하며, 말 그대로 일직선으로 쭉 훑어보는 방법이다. 크기 순서대로 정렬되어 있어도 그것을 전혀 사용하지 않는다.
   때문에 list의 길이가 n일 경우, 최악의(원하는 값이 list 끝에 있을) 경우 n개의 원소를 모두 검색해야함

      -> 때문에 O(N)이라는 복잡도를 갖는다.
<br>

- 정렬되어 있는 경우 **이진 검색(binary search)**

   - 이미 정렬된 list에서 "lower", "middle", "upper" 이 세가지를 활용하여 리스트를 반으로 쪼개어 나가면서 검색하는 효율적인 방식이다.

      -> 정렬되어 있는 경우 이진 검색이 압도적으로 빠르지만, 정렬이 필요할 경우 오히려 선형 검색보다 오래 걸릴 수 있다.
<br>

- 검색하는 컬렉션이 무작위이고 정렬되지 않은 경우, 선형검색이 기본!

```python
# 선형 검색 알고리즘
# 하나의 반복문과 리스트의 인덱스, 조건문을 활용하여 특정값을 검색할 때까지 반복한다.

def linear_search(arr, target):

    # 입력 배열의 각 항목을 반복
    for idx in range(len(arr)):
        # 현재 인덱스의 항목이 비교 대상과 같은지 확인
        if arr[idx] == target:
            # 현재 인덱스를 일치 항목으로 반환
            return idx
            
    # 전체 배열을 반복할 수 있다면, 비교 대상은 존재하지 않는다.(의미없는 -1 값 반환)
    return -1

print(linear_search([0,1,2], 2)) # case 1 - true
print(linear_search([0,1,2], 3)) # case 2 - false
```

#### 재귀(Recursion)

> **재귀함수** : 자기 자신을 다시 호출하는 함수
<br>
재귀의 개념은 수학적 사고에 기반하고, 코드를 작성하기 전에 문제를 해결하는 재호출 로직을 발견해야한다.
<br>

- 재귀 호출은 스택의 개념이 적용되며, 함수의 내부는 스택처럼 관리된다.(LIFO, 후입선출)

   - 단점 : 재귀를 사용하면 **함수를 반복적으로 호출**되는 상황이 벌어지므로, 메모리를 더 많이 사용한다. 
<br>

- 재귀로 문제 해결
  
    ->하위 문제를 쉽게 해결할 수 있을때 까지 **문제를 더 작은 하위 문제로 나누는 것**을 의미
<br>

 - **분할 정복법**

    - 재귀는 **해결을 위한 특정 기능을 재호풀**한다는 측면, 분할정복은 **문제를 분할하고 해결하는 구체적인 방법론**

    - 분할정복법을 활용하기 위해서는 재귀개념(기능 재호출)이 필요

**-> 재귀에서 중점적으로 생각해야될 부분은 조건에 따른 반복 계산!!!**

```python
my_list = [1,2,3,4,5]
def sum_list(items):
    sum = 0
    for i in items:
        sum = sum + i
    return sum

sum_list(my_list)
```

```python
# 문제를 두개의 하위 문제로 분리하여 시작!
1 + 2 + 3 + 4 + 5
(1 + (2 + 3 + 4 + 5))
(1 + (2 + (3 + 4 + 5)))
(1 + (2 + (3 + (4 + 5))))
(1 + (2 + (3 + (4 + (5)))))

#문제를 두개의 하위 문제로 나눌 수 없을 때까지 계속 진행
```

```python 
# 분리된 내용을 의사코드를 활용하여 먼저 로직 해석
sum_list(items)
    if the length of items is 1
        return the 1 item in the list
```

```python
sum_list(items)
    if the length of items is 1
        return the 1 item in the list
    otherwise
        return the first item from the list + sum_list(the rest of the items)
```

```python
def sum_list(items):
    if len(items) == 1:
        return items[0]
    else:
        return items[0] + sum_list(items[1:])  
```

###### 재귀의 조건 1)
<br>

- base case(기본 케이스 또는 조건)
<br>

   - 알고리즘은 특성상 반복을 중지할 수 있다.

```python
# 여기서 반복을 중지하도록 하는 조건은??

def sum_list(items):
    if len(items) == 1: # Base Case
        return items[0]
    else:
        return items[0] + sum_list(items[1:])

# test case 
#sum_list(1)
#sum_list([1,3])
```

###### 재귀의 조건 2)

- 추가조건과 기본케이스의 차이

```python
"""
sum_list에 전달된 items는 한 항목씩 감소
-> 첫 번째 재귀에서 항목은 [2,3,4,5]이고 다음 재귀에서는 내부적으로 items [3,4,5]
"""

def sum_list(items):
    if len(items) == 1: # Base Case(항목이 1개인 경우가 기본 케이스)
        return items[0]
    elif len(items)>1:
        print("items:",items[0:])
        return items[0] + sum_list(items[1:]) # items[:]는 한 항목씩 감소한다.
        
print("sum_list:",sum_list([2,3,4,5]))
```

###### 재귀의 조건 3)

- 반드시 자기자신(함수)를 호출해야함
<br>

   - 함수의 마지막 줄에서 재귀작업을 수행

```python
def sum_list(items):
    if len(items) == 1: # Base Case
        return items[0]
    else:
        return items[0] + sum_list(items[1:]) # 반복적으로 자기자신을 호출한다.
```

```python
# 다양한 활용법
def add_two(num): # 매개변수
  return num + 2  # 반환값

def add_four(num):  # 매개변수
  return add_two(add_two(num))  # 반환값으로 매개변수가 있는 함수를 넣는다.

print(add_two(2))
print(add_four(6))
```
```
위의 함수에 대한 수행과정

 1) add_two(num) 함수 선언
 2) add_four(num) 함수 선언
 3) print(add_two(2)) 코드 읽기
 4) 선언된 add_two 호출
 5) return 4 값반환
 6) print(add_four(6)) 코드 읽기
 7) 선언된 add_four 호출
 8) return add_two(add_two(6)) 반환
 9) 선언된 add_two(6) 함수 호출
 10) return 8 값반환
 11) 선언된 add_two(8) 함수 호출
 12) return 10 값반환
```

## 트리

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%90%E1%85%B3%E1%84%85%E1%85%B5%E1%84%8C%E1%85%A5%E1%86%AB%E1%84%8E%E1%85%A6%E1%84%89%E1%85%A5%E1%86%AF%E1%84%86%E1%85%A7%E1%86%BC.png?raw=true)

![image](https://res.cloudinary.com/practicaldev/image/fetch/s--fKHLjpeK--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://thepracticaldev.s3.amazonaws.com/i/jm2p1at8cth0gu5dakug.png)

- 루트(root): 가장 위쪽에 있는 노드, **트리별 하나**만 있다.
 
   - 루트와 부모는 다름, 부모노드는 자식노드가 1개 이상 있는 경우에만 존재
<br>

- 서브트리: 자식노드이면서 부모노드역할을 하는 노드가 있는 트리
<br>

- 차수: 노드가 갖고 있는 최대 자식노드 수

   - 위의 경우 차수는 2개 (10의 차수, 8의 차수, 9의 차수, 1의 차수)
<br>

- 리프(leaf): 레벨렬로 가장 마지막에 있는 노드, 단말노드(terminal node), 외부노드(external node)라고도 하며, **리프는 트리별로 여러 개**가 있을 수 있다. 
<br>

- 레벨 : 루트노드에서 **얼마나 멀리 떨어져 있는지 각각 나타낸다.** 루트노드의 레벨은 0이며, 아래로 내려갈때마다 1씩 증가.
<br>

- 높이: 루트에서 가장 멀리 떨어진 리프노드까지의 거리이며, **리프레벨의 최대값**을 높이라 함. (위의 경우 3)
<br>

- sibilg(형제) 노드: 부모가 같은 두 개의 노드

#### 바이너리 트리(이진 트리)

- 이진트리는 각 노드별로, 최대 2개의 서브노드를 갖음.(left, right)
<br>

- 이진트리는 여러 트리종류 중에서 가장 기본이 되면서 많이 활용된다.
<br>

- 이진 트리는 **루트노드를 중심으로 두개의 서브트리**로 나눠 지며, 나눠진 두 서브트리도 모두 두개의 서브트리를 갖는다.

   -> **서브트리의 노드가 반드시 값을 갖고 있을 필요는 없다!**

```python
# 기본코드

class BinaryTreeNode:
    def __init__(self, value):
        self.left = None  # 왼쪽서브노드
        self.value = value
        self.right = None # 오른쪽서브노드
```

- **포화 이진트리**: **모든 리프노드들이 동일한 레벨**을 갖는 경우 

![image](https://tk-assets.lambdaschool.com/36747e43-d96d-40c9-b8ab-d318f6da8aed_binary-tree-example-levels.001.png)

- **완전 이진트리**
<br>

   - 노드가 **위에서 아래**로 채워져있다.

   - 노드가 **왼쪽에서 오른쪽** 순서대로 채워져 있다.

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%8B%E1%85%AA%E1%86%AB%E1%84%8C%E1%85%A5%E1%86%AB%E1%84%8B%E1%85%B5%E1%84%8C%E1%85%B5%E1%86%AB%E1%84%90%E1%85%B3%E1%84%85%E1%85%B5.png?raw=true)

##### **Binary Search Trees(BST)** - 이진검색트리

> 이진탐색트리는 **노드를 정확하게 정렬해야하는** 특정 유형의 이진트리<br>
  목적: 단순 이진트리보다 빠른 **노드탐색**<Br>
    -> insert node에서 중복을 처리해주는 것이 아니라 '**값 크기 조건**'에 맞도록 값을 넣어준다.<br>
    -> 만약 '**값 크기 조건**'을 지키지 않고 값을 삽입하는 경우 단순이진트리의 로직으로 '탐색'이 진행되므로 더 느린 탐색이 진행

- **값 크기 조건**: 오른쪽 서브노드의 값(right child) > 루트(부모)노드의 값(root node) > 왼쪽 서브노드의 값(left child)
<br>

   - 중복값의 노드가 없어야 한다.
<br>

   - 왼쪽 서브트리노드들의 값은 루트(부모)노느값보다 작아야 한다.
<br>

   - 오른쪽 서브트리노드들의 값은 루트(부모)노드값보다 커야한다.

📍위에 대한 규칙은 **왼쪽부터 오른쪽으로 검색하는 구조**이기 때문! 트리와 같은 자료구조는 기본이 되는 연결리스트를 참조해서 만들어진 개념이다.
 
- 특징

   - 위와 같은 규칙에 따라 구조가 단순

   - base node/검색할 노드/자식노드존재여부에 따라 검색되는 노드의 순서가 달라진다.

   - 검색이 일반 이진트리보다 빠르기 때문에 노드삽입이 쉽다.

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%8B%E1%85%B5%E1%84%8C%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A5%E1%86%B7%E1%84%89%E1%85%A2%E1%86%A8%E1%84%90%E1%85%B3%E1%84%85%E1%85%B5.png?raw=true)

- 소스코드를 통한 BST
   
   - 흐름을 매핑하면서 이해하는 것이 중요

   - 자료구조에서 연결리스트, 큐, 스택을 구현한 로직과 비슷한 맥락

   - **로직에 따라 값을 교환하는 흐름**을 봐야한다.

```python
# 노드 클래스 생성(해당 클래스는 검색알고리즘에 필요한 기본클래스이다.)

class node:
  def __init__(self, value):
    self.value = value
    self.left = None
    self.right = None
```

```python
# 이진검색트리에 노드삽입 함수추가

class binary_search_tree:
  def __init__(self, head):
    self.head = head

  def insert_node(self, value):
    self.base_node = self.head
    while True:
      if value < self.base_node.value:
        if self.base_node.left != None:
          self.base_node = self.base_node.left
        else:
          self.base_node.left = node(value)
          break
      else:
        if self.base_node.right != None:
          self.base_node = self.base_node.right
        else:
          self.base_node.right = node(value)
          break
```

```python
# 이진검색트리를 위한 기본노드생성

head = node(1)  # 루트노드 지정
bt = binary_search_tree(head) # binary_search_tree(node(1))

# 이진검색트리에 값 삽입

bt.insert_node(2)
```

```python
# 이진검색트리에 노드검색 함수추가

class binary_search_tree:
  def __init__(self, head):
    self.head = head

  # 노드삽입
  def insert_node(self, value):
    self.base_node = self.head

    while True:
      if value < self.base_node.value:
        if self.base_node.left != None:
          self.base_node = self.base_node.left
        else:
          self.base_node.left = node(value)
          break
          
      else:
        if self.base_node.right != None:
          self.base_node = self.base_node.right
        else:
          self.base_node.right = node(value)
          break

  # 노드검색
  def search_node(self, value):
    self.base_node = self.head

    while self.base_node:
      if self.base_node.value == value:
        return True
      ###### 검색부분 미구현 ######
    return False
```

```python
# 노드삽입

head = node(10)  # 루트노드지정
bt = binary_search_tree(head)

bt.insert_node(2)
bt.insert_node(5)
bt.insert_node(0)
bt.insert_node(-1)
```


### Review

---

오늘 배운 것

```
1) 검색과 재귀
2) 트리에 대한 기본개념
```

오늘 해야할 것

```
1) 개념에 대한 차이점 이해
2) 소스코드를 통한 이해
```

### Reference

---

- [이진 탐색 트리(BST)와 불균형 이진 트리 문제 해결](https://m.blog.naver.com/PostView.nhn?blogId=qbxlvnf11&logNo=221371437794&proxyReferer=https:%2F%2Fwww.google.com%2F)

- [트리정리](https://www.fun-coding.org/Chapter10-tree.html)