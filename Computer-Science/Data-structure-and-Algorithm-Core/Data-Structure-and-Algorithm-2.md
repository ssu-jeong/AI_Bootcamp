# 02. 연결 리스트

---

## a. 연결 리스트와 배열과 배열리스트

---

### 여러 데이터를 저장하는 구조

---

여러 데이터를 저장하는 자료형은 대표적으로 배열(Array)와 리스트(List)가 있다.

### 배열

---

![image](https://wikidocs.net/images/page/34226/02%EB%B0%B0%EC%97%B41.png)

- 여러 데이터를 저장한 자료형 중에 월등히 빨리 접근할 수 있으며 다차원 표현이 가능하다.(2차원 또는 3차원 배열)
<br>

   - 하지만 처음 생성시 얼만큼 사용할 건지 미리 정해야 되서, 실제 사용보다 너무 크게 크기를 정하면 메모리 낭비
<br>

   - 배열의 크기가 너무 큰 경우 이만큼 할당할 수 있는 메모리 공간을 찾기 힘들 수 있음.
<br>

   - 배열이 꽉 차면 사이즈 변경이 불가하기 때문에 새로 만들어 복사해야함

### 배열 리스트

---

![image](https://wikidocs.net/images/page/34226/02%EB%B0%B0%EC%97%B4%EB%A6%AC%EC%8A%A4%ED%8A%B81.png)

- 배열과는 다르게 사이즈 변경이 가능하여 데이터 삽입 및 삭제가 가능
<br>

   - 하지만 구조는 배열처럼 붙어있어서 너무 크면 메모리 할당이 힘들 수 있다.
<br>

   - 따닥 붙어있는데 삽입 삭제는 가능한 구조라서 다차원을 구현할 수 없다.

### 연결 리스트

---

![image](https://wikidocs.net/images/page/34226/02%EC%97%B0%EA%B2%B0%EB%A6%AC%EC%8A%A4%ED%8A%B81.png)

- 속도는 앞에 나온 것들보다 느리지만, 삽입과 삭제 등의 연산과 다차원 구조가 가능.

- 필요한 메모리를 띄엄띄엄 둘 수 있어서 메모리 할당의 어려움도 없다.

**결론: 데이터의 삽입과 삭제 연산이 잦고, 크기의 유동폭이 큰 경우에는 연결리스트를 사용하며, 단일연결리스트, 이중연결리스트, 환형연결리스트가 있다.**

## b. 단일 연결 리스트(singly linked list)

---

## 1. 구조

---

### 기본구조

---

![image](https://wikidocs.net/images/page/34225/02%EB%8B%A8%EC%9D%BC%EC%97%B0%EA%B2%B0%EB%A6%AC%EC%8A%A4%ED%8A%B8.png)

- next: 따로 떨어져 있는 있는 노드의 다음에 연결된 노드를 가리켜줄 변수 

- head: 맨 처음 노드가 어디 있는지 저장해주는 변수

#### 코드구현

위의 구조만 가지는 노드와 리스트 클래스 구현. 변수은닉화(앞에 __붙이는 것)생략

```python
#단일 링크드 리스트
class SLinkedList:

    #S_L_list에서 쓸 노드
    class Node:
        def __init__(self, v, n = None):
            self.value = v #저장된 데이터
            self.next = n #다음 노드 가리키는 변수

    #S_L_List에서 필요한 변수
    def __init__(self):
        self.head = None #첫 생성시 내부에는 노드가 없으므로


##테스트
if __name__=="__main__":
    sl = SLinkedList()
```

## 2. 삽입

---

### 삽입
___

단일 연결 리스트의 삽입은 head쪽에 노드를 계속 추가하며 집어넣는 방식

##### 저장된 노드가 없는 경우

- 아무런 노드도 없는 경우는 head값이 None.

![image](https://wikidocs.net/images/page/34315/02b%EB%8B%A8%EC%9D%BC%EC%82%BD%EC%9E%85%EC%97%86%EB%8A%94.png)

##### 저장된 노드가 있는 경우

- 기존 노드가 밀려나는 식으로 새로운 노드가 들어온다. 

   -> 따라서 새로운 노드의 next에 현재 head값을 저장하고, head에는 새로운 노드를 저장시킨다.

![image](https://wikidocs.net/images/page/34315/02b%EB%8B%A8%EC%9D%BC%EC%82%BD%EC%9E%85%EC%9E%88%EB%8A%94.png)

#### 코드 구현

```python
#단일 링크드 리스트
class SLinkedList:

    #S_L_list에서 쓸 노드
    class Node:
        def __init__(self, v, n = None):
            self.value = v #저장된 데이터
            self.next = n #다음 노드 가리키는 변수

    #S_L_List에서 필요한 변수
    def __init__(self):
        self.head = None #첫 생성시 내부에는 노드가 없으므로

    #삽입
    def insertNode(self, v): #추가할 데이터
        #만일 처음 노드일 경우 -> head값이 None임
        if self.head is None :
            #head에 새 노드를 저장
            self.head = self.Node(v)
        else: #이미 노드가 있는 경우
            # head에 새 노드를 저장
            # 기존 head에 저장된 노드는 새로 생성할 노드의 next로 저장
            self.head = self.Node(v,self.head)

##테스트
if __name__=="__main__":
    sl = SLinkedList()
    sl.insertNode('1st')
    sl.insertNode('2nd')
    sl.insertNode('3rd')
```

## 3. 출력

---

### 출력

---

- head가 가리키는 노드부터 순차적으로 접근 가능
<br>

- head를 통해서 첫 노드에 접근하고, 이후 노드가 가지고 있는 변수 next를 통해 다음 노드로 이동
<br>

- next의 변수가 None이라면 해당노드가 마지막 위치의 노드!

##### 지정된 노드가 없을 때

- 그냥 '없다'라는 출력

##### 저장된 노드가 있을 때

- 먼저 head가 가리키는 Node의 value를 출력 

- 이후 변수 next가 None이 아니라면 next를 통해 다음노드로 이동하고 value를 출력

- 이 과정을 next가 None일 때까지 반복

#### 코드 구현

```python
#단일 링크드 리스트
class SLinkedList:

    #S_L_list에서 쓸 노드
    class Node:
        def __init__(self, v, n = None):
            self.value = v #저장된 데이터
            self.next = n #다음 노드 가리키는 변수

    #S_L_List에서 필요한 변수
    def __init__(self):
        self.head = None #첫 생성시 내부에는 노드가 없으므로

    #삽입
    def insertNode(self, v): #추가할 데이터
        #만일 처음 노드일 경우 -> head값이 None임
        if self.head is None :
            #head에 새 노드를 저장
            self.head = self.Node(v)
        else: #이미 노드가 있는 경우
            # head에 새 노드를 저장
            # 기존 head에 저장된 노드는 새로 생성할 노드의 next로 저장
            self.head = self.Node(v,self.head)

    def printNode(self):
        #데이터가 없을 때
        if self.head is None:
            print("저장된 데이터가 없음")
            return
        else:
            print("<현재 리스트 구조>", end='\t') #end로 print 마지막 개행을 변경할 수 있습니다.
            link = self.head #처음은 head를 지정. 이후부터는 현 노드의 next를 지정

            #link가 가리키는 노드가 없을 때까지 반복
            #None,0,""는 조건판단에서 False 처리, 그 외는 True로 처리된다.
            while link :
                print(link.value, '->' , end = ' ')
                link = link.next #link를 현 위치 노드의 next로 변경
            print() #줄바꿈 용

##테스트
if __name__=="__main__":
    sl = SLinkedList()
    sl.printNode()  # 출력
    sl.insertNode('1st')
    sl.insertNode('2nd')
    sl.insertNode('3rd')
    sl.printNode() #출력
```

## 4. 삭제

---

### 삭제

---

- C언어의 경우 메모리의 할당 및 해제를 직접 코드에 적어줘야 한다.(malloc과 free)
<br>

   - 즉, 관리에서 벗어날 데이터는 할당되었던 메모리를 해제하는 것까지 신경써야함.
<br>

- JAVA나 Python은 관리에서 벗어난 데이터의 경우 알아서 처리해주는 가비지 컬렉션(Garbage Collection) 개념을 사용.
<br>

   - 우리는 삭제된 데이터의 메모리 해제는 신경쓰지 않고, 관리 체계에 대해서만 생각하면 됨.

##### 저장된 노드가 없을 때

- 삭제연산 경우에서 제외

```python
#단일 링크드 리스트
class SLinkedList:

    #S_L_list에서 쓸 노드
    class Node:
        def __init__(self, v, n = None):
            self.value = v #저장된 데이터
            self.next = n #다음 노드 가리키는 변수

    #S_L_List에서 필요한 변수
    def __init__(self):
        self.head = None #첫 생성시 내부에는 노드가 없으므로

    #삽입
    def insertNode(self, v): #추가할 데이터
        #만일 처음 노드일 경우 -> head값이 None임
        if self.head is None :
            #head에 새 노드를 저장
            self.head = self.Node(v)
        else: #이미 노드가 있는 경우
            # head에 새 노드를 저장
            # 기존 head에 저장된 노드는 새로 생성할 노드의 next로 저장
            self.head = self.Node(v,self.head)

    def printNode(self):
        #데이터가 없을 때
        if self.head is None:
            print("저장된 데이터가 없음")
            return
        else:
            print("<현재 리스트 구조>", end='\t') #end로 print 마지막 개행을 변경할 수 있습니다.
            link = self.head #처음은 head를 지정. 이후부터는 현 노드의 next를 지정

            #link가 가리키는 노드가 없을 때까지 반복
            #None,0,""는 조건판단에서 False 처리, 그 외는 True로 처리된다.
            while link :
                print(link.value, '->' , end = ' ')
                link = link.next #link를 현 위치 노드의 next로 변경
            print() #줄바꿈 용

    #삭제
    def deleteNode(self):
        #노드가 없으면 skip
        if self.head is None :
            print("삭제할 노드가 없습니다.")
            return

##테스트
if __name__=="__main__":
    sl = SLinkedList()
    sl.deleteNode()
```

##### 저장된 노드가 있을 때

- head가 가리키고 있는 노드가 삭제. 결과적으로 head에 다음 노드를 가리키도록 변경하면 된다.
<br>

   - 파이썬에선 딱히 메모리 해제를 하지 않으니 삭제라기 보단 관리에서 제외시킨다는 개념으로 생각.

![image](https://wikidocs.net/images/page/34327/02b%EB%8B%A8%EC%9D%BChead%EC%82%AD%EC%A0%9C.png)

#### 코드 구현

```python
#단일 링크드 리스트
class SLinkedList:

    #S_L_list에서 쓸 노드
    class Node:
        def __init__(self, v, n = None):
            self.value = v #저장된 데이터
            self.next = n #다음 노드 가리키는 변수

    #S_L_List에서 필요한 변수
    def __init__(self):
        self.head = None #첫 생성시 내부에는 노드가 없으므로

    #삽입
    def insertNode(self, v): #추가할 데이터
        #만일 처음 노드일 경우 -> head값이 None임
        if self.head is None :
            #head에 새 노드를 저장
            self.head = self.Node(v)
        else: #이미 노드가 있는 경우
            # head에 새 노드를 저장
            # 기존 head에 저장된 노드는 새로 생성할 노드의 next로 저장
            self.head = self.Node(v,self.head)

    def printNode(self):
        #데이터가 없을 때
        if self.head is None:
            print("저장된 데이터가 없음")
            return
        else:
            print("<현재 리스트 구조>", end='\t') #end로 print 마지막 개행을 변경할 수 있습니다.
            link = self.head #처음은 head를 지정. 이후부터는 현 노드의 next를 지정

            #link가 가리키는 노드가 없을 때까지 반복
            #None,0,""는 조건판단에서 False 처리, 그 외는 True로 처리된다.
            while link :
                print(link.value, '->' , end = ' ')
                link = link.next #link를 현 위치 노드의 next로 변경
            print() #줄바꿈 용

    #삭제
    def deleteNode(self):
        #노드가 없으면 skip
        if self.head is None :
            print("삭제할 노드가 없습니다.")
            return
        else:
            #head를 현 head의 next. 즉, 다음 노드로 변경.
            self.head = self.head.next

##테스트
if __name__=="__main__":
    sl = SLinkedList()
    sl.insertNode('1st')
    sl.insertNode('2nd')
    sl.insertNode('3rd')
    sl.printNode()  # 출력
    sl.deleteNode()
    sl.deleteNode()
    sl.printNode()  # 출력
    sl.deleteNode()
    sl.deleteNode()
    sl.printNode()  # 출력
```

## 5. 탐색

---

### 탐색

---

- 출력에서 했던 방식과 동일하게 노드를 이동하되, 찾고자 하는 데이터를 가진 노드ㅏ 발견되면 이동을 중지

- 찾고자 하는 값을 찾으면 해당 노드가 몇번째인지를 반환하고, 못찾으면 탐색실패의 의미인 None을 반환

#### 코드 구현

```python
#단일 링크드 리스트
class SLinkedList:

    #S_L_list에서 쓸 노드
    class Node:
        def __init__(self, v, n = None):
            self.value = v #저장된 데이터
            self.next = n #다음 노드 가리키는 변수

    #S_L_List에서 필요한 변수
    def __init__(self):
        self.head = None #첫 생성시 내부에는 노드가 없으므로

    def printNode(self):
        #데이터가 없을 때
        if self.head is None:
            print("저장된 데이터가 없음")
            return
        else:
            print("<현재 리스트 구조>", end='\t') #end로 print 마지막 개행을 변경할 수 있습니다.
            link = self.head #처음은 head를 지정. 이후부터는 현 노드의 next를 지정

            #link가 가리키는 노드가 없을 때까지 반복
            #None,0,""는 조건판단에서 False 처리, 그 외는 True로 처리된다.
            while link :
                print(link.value, '->' , end = ' ')
                link = link.next #link를 현 위치 노드의 next로 변경
            print() #줄바꿈 용

    # 삽입
    def insertNode(self, v):  # 추가할 데이터
        # 만일 처음 노드일 경우 -> head값이 None임
        if self.head is None:
            # head에 새 노드를 저장
            self.head = self.Node(v)
        else:  # 이미 노드가 있는 경우
            # head에 새 노드를 저장
            # 기존 head에 저장된 노드는 새로 생성할 노드의 next로 저장
            self.head = self.Node(v, self.head)

    # 삭제
    def deleteNode(self):
        # 노드가 없으면 skip
        if self.head is None:
            print("삭제할 노드가 없습니다.")
            return
        else:
            # head를 현 head의 next. 즉, 다음 노드로 변경.
            self.head = self.head.next

    #조회
    def searchNode(self,v):
        # 데이터가 없을 때
        if self.head is None:
            print("저장된 데이터가 없음")
            return
        else:
            link = self.head  # 처음은 head를 지정. 이후부터는 현 노드의 next를 지정
            index  = 0 #몇 번째 노드인지 기록
            while link:
                #내가 찾는 노드인지 확인
                if v == link.value:
                    return index #위치를 반환
                else:
                    link = link.next  # link를 현 위치 노드의 next로 변경
                    index += 1 #위치값 1 증가
            #여기까지 왔다 == 해당 v값을 가진 노드가 없다.
            #print("일치되는 값이 없습니다.")

##테스트
if __name__=="__main__":
    sl = SLinkedList()
    sl.insertNode('1st')
    sl.insertNode('2nd')
    sl.insertNode('3rd')

    #탐색
    print("<위치 탐색>")
    result = sl.searchNode('1st')
    print("1st의 위치 : {}".format(result))

    result = sl.searchNode('555')
    print("555의 위치 : {}".format(result))
```

## c. 이중 연결 리스트(doubly linked list)

---

## 1. 구조

---

### 기본구조

---

- 단일 연결 리스트는 단방향(head쪽)으로 만 삽입, 삭제, 조회가능.

- 이중 연결 리스트는 양방향 이동을 구현하므로 다음 노드와 이전 노드의 이동이 가능하도록 구성

   - 때문에 노드에 변수 next로 다음노드를, 변수로 prev로 이전노드를 지정하여 이동할 수 있도록 한다.

- 리스트에서 변수 head만 아니라 변수 tail도 만들어 리스트의 앞과 뒤로 접근 가능하도록 한다.

![image](https://wikidocs.net/images/page/34342/02c%EC%9D%B4%EC%A4%91%EC%97%B0%EA%B2%B0%EB%A6%AC%EC%8A%A4%ED%8A%B8%EA%B8%B0%EB%B0%98.png)

#### 코드구현

```python
#이중 링크드 리스트
class DLinkedList:

    #D_L_list에서 쓸 노드
    class Node:
        def __init__(self, v, n = None, p = None):
            self.value = v #저장된 데이터
            self.next = n #다음 노드 가리키는 변수
            self.prev = p #이전 노드 가리키는 변수

    #D_L_List에서 필요한 변수
    def __init__(self):
        self.head = None #첫 생성시 내부에는 노드가 없으므로
        self.tail = None

##테스트
if __name__=="__main__":
    dl = DLinkedList()
```

## 2. 삽입

---

### 삽입

---

이중 연결 리스트의 삽입 방법은 단일 연결 리스트 처럼 head로 넣는 방법과 같은 방법으로 tail을 통해 넣는 방법이 있다.

- 각 상황에 따라 노드의 next와 prev값을 다음노드와 이전노드로 지정

#### 지정된 노드가 없는 경우(head, tail)

아무런 노드도 없는 경우는 head와 tail값이 None이다. 따라서 head를 통해 넣든, tail을 통해 넣든 결과가 같다.

![image](https://wikidocs.net/images/page/34404/02c%EC%97%86%EC%9D%84%EA%B2%BD%EC%9A%B0%EC%82%BD%EC%9E%851.png)

#### 코드구현

```python
#이중 링크드 리스트
class DLinkedList:

    #D_L_list에서 쓸 노드
    class Node:
        def __init__(self, v, n = None, p = None):
            self.value = v #저장된 데이터
            self.next = n #다음 노드 가리키는 변수
            self.prev = p #이전 노드 가리키는 변수

    #D_L_List에서 필요한 변수
    def __init__(self):
        self.head = None #첫 생성시 내부에는 노드가 없으므로
        self.tail = None

    #head로 삽입. v : 데이터
    def insertNodeBefore(self, v):
        #없을 경우
        if self.head is None:
            self.head = self.Node(v)
            self.tail = self.head #같은 노드를 가리킴

    #tail로 삽입. v : 데이터
    def insertNodeAfter(self, v):
        #없을 경우
        if self.tail is None:
            self.tail = self.Node(v)
            self.head = self.tail #같은 노드를 가리킴

##테스트
if __name__=="__main__":
    dl = DLinkedList()
    # dl.insertNodeAfter('FirstData') #head삽입 테스트
    dl.insertNodeBefore('LastData') #tail삽입 테스트
```

#### 지정된 노드가 있는 경우(head)

새로운 노드와 기존에 head를 차지하던 노드도 신경써야한다. 기존에 있던 노드의 prev를 새로 만드는 노드를 가리키도록 해야하기 때문!

![image](https://wikidocs.net/images/page/34404/02c%EC%9D%B4%EC%A4%91head%EC%82%BD%EC%9E%851.png)

따라서 다음 수행절차 진행.

1. 현재 head가 가리키는 기존 노드의 prev를 새로 생성하는 노드로 지정

2. 새로 생성한 노드의 next를 기존 노드로 지정

3. head를 새로 생성한 노드로 변경

##### 코드구현

```python
#이중 링크드 리스트
class DLinkedList:

    #D_L_list에서 쓸 노드
    class Node:
        def __init__(self, v, n = None, p = None):
            self.value = v #저장된 데이터
            self.next = n #다음 노드 가리키는 변수
            self.prev = p #이전 노드 가리키는 변수

    #D_L_List에서 필요한 변수
    def __init__(self):
        self.head = None #첫 생성시 내부에는 노드가 없으므로
        self.tail = None

    #head로 삽입. v : 데이터
    def insertNodeBefore(self, v):
        #없을 경우
        if self.head is None:
            self.head = self.Node(v)
            self.tail = self.head #같은 노드를 가리킴
        else:
            #self.head : 기존노드, self.head.prev : 기존노드의 prev
            self.head.prev = self.Node(v,n=self.head) #1,2번을 동시수행
            #self.head.prev : 기존노드의 prev == 새로운 노드
            self.head = self.head.prev #3. head를 새로운 노드로 변경

##테스트
if __name__=="__main__":
    dl = DLinkedList()
    dl.insertNodeBefore('1st')  # head삽입 테스트
    dl.insertNodeBefore('2nd')  # head삽입 테스트
    dl.insertNodeBefore('3rd')  # head삽입 테스트

```

#### 저장된 노드가 있는 경우(tail)

head와 유사한 점이 많다. 단지 head가 tail로, prev를 next로 next를 prev로 바꿔서 생각하면 된다!

![image](https://wikidocs.net/images/page/34404/02c%EC%9D%B4%EC%A4%91tail%EC%82%BD%EC%9E%851.png)

따라서 다음 수행절차 진행

1. 현재 tail이 가리키는 기존 노드의 next를 새로 생성하는 노드로 지정

2. 새로 생성한 노드의 prev를 기존 노드로 지정

3. tail을 새로 생성한 노드로 변경

##### 코드구현

```python
#이중 링크드 리스트
class DLinkedList:

    #D_L_list에서 쓸 노드
    class Node:
        def __init__(self, v, n = None, p = None):
            self.value = v #저장된 데이터
            self.next = n #다음 노드 가리키는 변수
            self.prev = p #이전 노드 가리키는 변수

    #D_L_List에서 필요한 변수
    def __init__(self):
        self.head = None #첫 생성시 내부에는 노드가 없으므로
        self.tail = None

    #head로 삽입. v : 데이터
    def insertNodeBefore(self, v):
        #없을 경우
        if self.head is None:
            self.head = self.Node(v)
            self.tail = self.head #같은 노드를 가리킴
        else:
            #self.head : 기존노드, self.head.prev : 기존노드의 prev
            self.head.prev = self.Node(v,n=self.head) #1,2번을 동시수행
            #self.head.prev : 기존노드의 prev == 새로운 노드
            self.head = self.head.prev #3. head를 새로운 노드로 변경


    #tail로 삽입. v : 데이터
    def insertNodeAfter(self, v):
        #없을 경우
        if self.tail is None:
            self.tail = self.Node(v)
            self.head = self.tail #같은 노드를 가리킴
        else:
            #self.tail : 기존노드, self.tail.next : 기존 노드의 next
            self.tail.next = self.Node(v,p=self.tail) #1,2번을 동시수행
            #self.tail.next : 기존노드의 next == 새로운 노드
            self.tail = self.tail.next #3. tail를 새로운 노드로 변경

##테스트
if __name__=="__main__":
    dl = DLinkedList()
    dl.insertNodeBefore('1st')  # head삽입 테스트
    dl.insertNodeBefore('2nd')  # head삽입 테스트
    dl.insertNodeBefore('3rd')  # head삽입 테스트
    dl.insertNodeAfter('B1st') # tail삽입 테스트
    dl.insertNodeAfter('B2nd') # tail삽입 테스트
    dl.insertNodeAfter('B3rd') # tail삽입 테스트
```

## 3. 출력


---

### 출력

---

이중 연결 리스트의 head를 통한 출력은 단일 연결 리스트와 동일.

##### 저장된 노드가 없을 때

- 그냥 없다 라는 출럭

##### 저장된 노드가 있을 때(head)

- 단일 연결 리스트와 동일

##### 코드구현

```python
#이중 링크드 리스트
class DLinkedList:

    #D_L_list에서 쓸 노드
    class Node:
        def __init__(self, v, n = None, p = None):
            self.value = v #저장된 데이터
            self.next = n #다음 노드 가리키는 변수
            self.prev = p #이전 노드 가리키는 변수

    #D_L_List에서 필요한 변수
    def __init__(self):
        self.head = None #첫 생성시 내부에는 노드가 없으므로
        self.tail = None

    #head로 삽입. v : 데이터
    def insertNodeBefore(self, v):
        #없을 경우
        if self.head is None:
            self.head = self.Node(v)
            self.tail = self.head #같은 노드를 가리킴
            print(self.head.value)
        else:
            #self.head : 기존노드, self.head.prev : 기존노드의 prev
            self.head.prev = self.Node(v,n=self.head) #1,2번을 동시수행
            #self.head.prev : 기존노드의 prev == 새로운 노드
            self.head = self.head.prev #3. head를 새로운 노드로 변경

    #tail로 삽입. v : 데이터
    def insertNodeAfter(self, v):
        #없을 경우
        if self.tail is None:
            self.tail = self.Node(v)
            self.head = self.tail #같은 노드를 가리킴
        else:
            #self.tail : 기존노드, self.tail.next : 기존 노드의 next
            self.tail.next = self.Node(v,p=self.tail) #1,2번을 동시수행
            #self.tail.next : 기존노드의 next == 새로운 노드
            self.tail = self.tail.next #3. tail를 새로운 노드로 변경

    #head로 삭제
    def deleteNodeBefore(self):
        #없을 경우 - > 스킵
        if self.head is None :
            print("삭제할 노드가 없습니다.")
            return
        else:
            #1.현재 head가 가리키는 노드의 next를 새로운 head로 지정
            self.head = self.head.next
            #2. 새로운 head의 prev를 None으로 변경
            self.head.prev = None

    def printNodeBefore(self):
        #데이터가 없을 때
        if self.head is None:
            print("저장된 데이터가 없음")
            return
        else:
            print("<현재 리스트 구조>", end='\t') #end로 print 마지막 개행을 변경할 수 있습니다.
            link = self.head #처음은 head를 지정. 이후부터는 현 노드의 next를 지정

            #link가 가리키는 노드가 없을 때까지 반복
            #None,0,""는 조건판단에서 False 처리, 그 외는 True로 처리된다.
            while link :
                print(link.value, '<->' , end = ' ')
                link = link.next #link를 현 위치 노드의 next로 변경
            print() #줄바꿈 용


##테스트
if __name__=="__main__":
    dl = DLinkedList()
    dl.insertNodeBefore('1st')  # head삽입 테스트
    dl.insertNodeBefore('2nd')  # head삽입 테스트
    dl.insertNodeAfter('3rd')  # head삽입 테스트
    dl.insertNodeAfter('4rd')  # head삽입 테스트
    dl.printNodeBefore()
```

##### 저장된 노드가 있을 때(tail)

순회구조는 head에서 tail로, next에서 prev로 바뀐 것 밖에 없다. 대신 뒤에서부터 출력하므로 head로 할 때와는 반대

##### 코드구현

```python
#이중 링크드 리스트
class DLinkedList:

    #D_L_list에서 쓸 노드
    class Node:
        def __init__(self, v, n = None, p = None):
            self.value = v #저장된 데이터
            self.next = n #다음 노드 가리키는 변수
            self.prev = p #이전 노드 가리키는 변수

    #D_L_List에서 필요한 변수
    def __init__(self):
        self.head = None #첫 생성시 내부에는 노드가 없으므로
        self.tail = None

    #head로 삽입. v : 데이터
    def insertNodeBefore(self, v):
        #없을 경우
        if self.head is None:
            self.head = self.Node(v)
            self.tail = self.head #같은 노드를 가리킴
            print(self.head.value)
        else:
            #self.head : 기존노드, self.head.prev : 기존노드의 prev
            self.head.prev = self.Node(v,n=self.head) #1,2번을 동시수행
            #self.head.prev : 기존노드의 prev == 새로운 노드
            self.head = self.head.prev #3. head를 새로운 노드로 변경

    #tail로 삽입. v : 데이터
    def insertNodeAfter(self, v):
        #없을 경우
        if self.tail is None:
            self.tail = self.Node(v)
            self.head = self.tail #같은 노드를 가리킴
        else:
            #self.tail : 기존노드, self.tail.next : 기존 노드의 next
            self.tail.next = self.Node(v,p=self.tail) #1,2번을 동시수행
            #self.tail.next : 기존노드의 next == 새로운 노드
            self.tail = self.tail.next #3. tail를 새로운 노드로 변경

    #head로 삭제
    def deleteNodeBefore(self):
        #없을 경우 - > 스킵
        if self.head is None :
            print("삭제할 노드가 없습니다.")
            return
        else:
            #1.현재 head가 가리키는 노드의 next를 새로운 head로 지정
            self.head = self.head.next
            #2. 새로운 head의 prev를 None으로 변경
            self.head.prev = None

    def printNodeBefore(self):
        #데이터가 없을 때
        if self.head is None:
            print("저장된 데이터가 없음")
            return
        else:
            print("<현재 리스트 구조>", end='\t') #end로 print 마지막 개행을 변경할 수 있습니다.
            link = self.head #처음은 head를 지정. 이후부터는 현 노드의 next를 지정

            #link가 가리키는 노드가 없을 때까지 반복
            #None,0,""는 조건판단에서 False 처리, 그 외는 True로 처리된다.
            while link :
                print(link.value, '<->' , end = ' ')
                link = link.next #link를 현 위치 노드의 next로 변경
            print() #줄바꿈 용

    def printNodeAfter(self):
        #데이터가 없을 때
        if self.tail is None:
            print("저장된 데이터가 없음")
            return
        else:
            print("<현재 리스트 구조>", end='\t')
            link = self.tail

            while link :
                print(link.value, '<->' , end = ' ')
                link = link.prev #link를 현 위치 노드의 next로 변경
            print() #줄바꿈 용


##테스트
if __name__=="__main__":
    dl = DLinkedList()
    dl.insertNodeBefore('1st')  # head삽입 테스트
    dl.insertNodeBefore('2nd')  # head삽입 테스트
    dl.insertNodeAfter('3rd')  # head삽입 테스트
    dl.insertNodeAfter('4rd')  # head삽입 테스트
    dl.printNodeBefore()
    dl.printNodeAfter()
```

## 4. 삭제

---

### 식제

---

삽입과 마찬가지로 삭제 또한 head를 통한 삭제와 tail을 통한 삭제가 있다.

##### 저장된 노드가 없을 때

당연히 삭제연산 경우세서 제외

```python
#이중 링크드 리스트
class DLinkedList:

    #D_L_list에서 쓸 노드
    class Node:
        def __init__(self, v, n = None, p = None):
            self.value = v #저장된 데이터
            self.next = n #다음 노드 가리키는 변수
            self.prev = p #이전 노드 가리키는 변수

    #D_L_List에서 필요한 변수
    def __init__(self):
        self.head = None #첫 생성시 내부에는 노드가 없으므로
        self.tail = None

    #head로 삽입. v : 데이터
    def insertNodeBefore(self, v):
        #없을 경우
        if self.head is None:
            self.head = self.Node(v)
            self.tail = self.head #같은 노드를 가리킴
        else:
            #self.head : 기존노드, self.head.prev : 기존노드의 prev
            self.head.prev = self.Node(v,n=self.head) #1,2번을 동시수행
            #self.head.prev : 기존노드의 prev == 새로운 노드
            self.head = self.head.prev #3. head를 새로운 노드로 변경

    #tail로 삽입. v : 데이터
    def insertNodeAfter(self, v):
        #없을 경우
        if self.tail is None:
            self.tail = self.Node(v)
            self.head = self.tail #같은 노드를 가리킴
        else:
            #self.tail : 기존노드, self.tail.next : 기존 노드의 next
            self.tail.next = self.Node(v,p=self.tail) #1,2번을 동시수행
            #self.tail.next : 기존노드의 next == 새로운 노드
            self.tail = self.tail.next #3. tail를 새로운 노드로 변경

    def printNodeBefore(self):
        #데이터가 없을 때
        if self.head is None:
            print("저장된 데이터가 없음")
            return
        else:
            print("<현재 리스트 구조>", end='\t') #end로 print 마지막 개행을 변경할 수 있습니다.
            link = self.head #처음은 head를 지정. 이후부터는 현 노드의 next를 지정

            #link가 가리키는 노드가 없을 때까지 반복
            #None,0,""는 조건판단에서 False 처리, 그 외는 True로 처리된다.
            while link :
                print(link.value, '<->' , end = ' ')
                link = link.next #link를 현 위치 노드의 next로 변경
            print() #줄바꿈 용

    def printNodeAfter(self):
        #데이터가 없을 때
        if self.tail is None:
            print("저장된 데이터가 없음")
            return
        else:
            print("<현재 리스트 구조>", end='\t')
            link = self.tail

            while link :
                print(link.value, '<->' , end = ' ')
                link = link.prev #link를 현 위치 노드의 next로 변경
            print() #줄바꿈 용

    #head로 삭제
    def deleteNodeBefore(self):
        #없을 경우 - > 스킵
        if self.head is None :
            print("삭제할 노드가 없습니다.")
            return

    #tail로 삭제
    def deleteNodeAfter(self):
        #없을 경우 - > 스킵
        if self.tail is None :
            print("삭제할 노드가 없습니다.")
            return

##테스트
if __name__=="__main__":
    dl = DLinkedList()
    dl.deleteNodeBefore()
    dl.deleteNodeAfter()
```

##### 저장된 노드가 있을 때(head)

head를 통해 노드를 삭제할 경우, 곧 head가 될 노드의 prev는 None으로 변경해줘야 한다.

![image](https://wikidocs.net/images/page/34501/02c%EC%9D%B4%EC%A4%91head%EC%82%AD%EC%A0%9C.png)

따라서 다음 수행절차를 진행

1. 현재 head가 가리키는 노드의 next를 새로운 head로 지정

2. 새로운 head의 prev를 None으로 변경

##### 코드구현

```python
#이중 링크드 리스트
class DLinkedList:

    #D_L_list에서 쓸 노드
    class Node:
        def __init__(self, v, n = None, p = None):
            self.value = v #저장된 데이터
            self.next = n #다음 노드 가리키는 변수
            self.prev = p #이전 노드 가리키는 변수

    #D_L_List에서 필요한 변수
    def __init__(self):
        self.head = None #첫 생성시 내부에는 노드가 없으므로
        self.tail = None

    #head로 삽입. v : 데이터
    def insertNodeBefore(self, v):
        #없을 경우
        if self.head is None:
            self.head = self.Node(v)
            self.tail = self.head #같은 노드를 가리킴
        else:
            #self.head : 기존노드, self.head.prev : 기존노드의 prev
            self.head.prev = self.Node(v,n=self.head) #1,2번을 동시수행
            #self.head.prev : 기존노드의 prev == 새로운 노드
            self.head = self.head.prev #3. head를 새로운 노드로 변경

    #tail로 삽입. v : 데이터
    def insertNodeAfter(self, v):
        #없을 경우
        if self.tail is None:
            self.tail = self.Node(v)
            self.head = self.tail #같은 노드를 가리킴
        else:
            #self.tail : 기존노드, self.tail.next : 기존 노드의 next
            self.tail.next = self.Node(v,p=self.tail) #1,2번을 동시수행
            #self.tail.next : 기존노드의 next == 새로운 노드
            self.tail = self.tail.next #3. tail를 새로운 노드로 변경

    def printNodeBefore(self):
        #데이터가 없을 때
        if self.head is None:
            print("저장된 데이터가 없음")
            return
        else:
            print("<현재 리스트 구조>", end='\t') #end로 print 마지막 개행을 변경할 수 있습니다.
            link = self.head #처음은 head를 지정. 이후부터는 현 노드의 next를 지정

            #link가 가리키는 노드가 없을 때까지 반복
            #None,0,""는 조건판단에서 False 처리, 그 외는 True로 처리된다.
            while link :
                print(link.value, '<->' , end = ' ')
                link = link.next #link를 현 위치 노드의 next로 변경
            print() #줄바꿈 용

    def printNodeAfter(self):
        #데이터가 없을 때
        if self.tail is None:
            print("저장된 데이터가 없음")
            return
        else:
            print("<현재 리스트 구조>", end='\t')
            link = self.tail

            while link :
                print(link.value, '<->' , end = ' ')
                link = link.prev #link를 현 위치 노드의 next로 변경
            print() #줄바꿈 용

    #head로 삭제
    def deleteNodeBefore(self):
        #없을 경우 - > 스킵
        if self.head is None :
            print("삭제할 노드가 없습니다.")
            return
        else:
            #1.현재 head가 가리키는 노드의 next를 새로운 head로 지정
            self.head = self.head.next
            #2. 새로운 head의 prev를 None으로 변경
            self.head.prev = None

    #tail로 삭제
    def deleteNodeAfter(self):
        #없을 경우 - > 스킵
        if self.tail is None :
            print("삭제할 노드가 없습니다.")
            return

##테스트
if __name__=="__main__":
    dl = DLinkedList()
    dl.insertNodeBefore('1stF')
    dl.insertNodeAfter('1stB')
    dl.insertNodeBefore('2ndF')
    dl.insertNodeAfter('2ndB')
    dl.printNodeBefore()
    dl.deleteNodeBefore() #head로 삭제
    dl.printNodeBefore()
```

##### 저장된 노드가 있을 때(tail)

head 삭제방법과 방법은 일치. 다만 head가 tail로, prev가 next로 n 변경될 뿐이다.

![image](https://wikidocs.net/images/page/34501/02c%EC%9D%B4%EC%A4%91tail%EC%82%AD%EC%A0%9C.png)

따라서 다음 수행절차 진행

1. 현재 tail가 가리키는 노드의 prev를 새로운 tail로 지정

2. 새로운 tail의 next를 None으로 변경

##### 코드구현

```python
#이중 링크드 리스트
class DLinkedList:

    #D_L_list에서 쓸 노드
    class Node:
        def __init__(self, v, n = None, p = None):
            self.value = v #저장된 데이터
            self.next = n #다음 노드 가리키는 변수
            self.prev = p #이전 노드 가리키는 변수

    #D_L_List에서 필요한 변수
    def __init__(self):
        self.head = None #첫 생성시 내부에는 노드가 없으므로
        self.tail = None

    #head로 삽입. v : 데이터
    def insertNodeBefore(self, v):
        #없을 경우
        if self.head is None:
            self.head = self.Node(v)
            self.tail = self.head #같은 노드를 가리킴
        else:
            #self.head : 기존노드, self.head.prev : 기존노드의 prev
            self.head.prev = self.Node(v,n=self.head) #1,2번을 동시수행
            #self.head.prev : 기존노드의 prev == 새로운 노드
            self.head = self.head.prev #3. head를 새로운 노드로 변경

    #tail로 삽입. v : 데이터
    def insertNodeAfter(self, v):
        #없을 경우
        if self.tail is None:
            self.tail = self.Node(v)
            self.head = self.tail #같은 노드를 가리킴
        else:
            #self.tail : 기존노드, self.tail.next : 기존 노드의 next
            self.tail.next = self.Node(v,p=self.tail) #1,2번을 동시수행
            #self.tail.next : 기존노드의 next == 새로운 노드
            self.tail = self.tail.next #3. tail를 새로운 노드로 변경

    def printNodeBefore(self):
        #데이터가 없을 때
        if self.head is None:
            print("저장된 데이터가 없음")
            return
        else:
            print("<현재 리스트 구조>", end='\t') #end로 print 마지막 개행을 변경할 수 있습니다.
            link = self.head #처음은 head를 지정. 이후부터는 현 노드의 next를 지정

            #link가 가리키는 노드가 없을 때까지 반복
            #None,0,""는 조건판단에서 False 처리, 그 외는 True로 처리된다.
            while link :
                print(link.value, '<->' , end = ' ')
                link = link.next #link를 현 위치 노드의 next로 변경
            print() #줄바꿈 용

    def printNodeAfter(self):
        #데이터가 없을 때
        if self.tail is None:
            print("저장된 데이터가 없음")
            return
        else:
            print("<현재 리스트 구조>", end='\t')
            link = self.tail

            while link :
                print(link.value, '<->' , end = ' ')
                link = link.prev #link를 현 위치 노드의 next로 변경
            print() #줄바꿈 용

    #head로 삭제
    def deleteNodeBefore(self):
        #없을 경우 - > 스킵
        if self.head is None :
            print("삭제할 노드가 없습니다.")
            return
        else:
            #1.현재 head가 가리키는 노드의 next를 새로운 head로 지정
            self.head = self.head.next
            #2. 새로운 head의 prev를 None으로 변경
            self.head.prev = None

    #tail로 삭제
    def deleteNodeAfter(self):
        #없을 경우 - > 스킵
        if self.tail is None :
            print("삭제할 노드가 없습니다.")
            return
        else:
            #1.현재 tail이 가리키는 노드의 prev를 새로운 tail로 지정
            self.tail = self.tail.prev
            #2. 새로운 head의 prev를 None으로 변경
            self.tail.next = None

##테스트
if __name__=="__main__":
    dl = DLinkedList()
    dl.insertNodeBefore('1stF')
    dl.insertNodeAfter('1stB')
    dl.insertNodeBefore('2ndF')
    dl.insertNodeAfter('2ndB')
    dl.printNodeBefore()
    dl.deleteNodeBefore()  # head로 삭제
    dl.printNodeBefore()
    dl.deleteNodeAfter()  # tail로 삭제
    dl.printNodeBefore()
```

## 5. 탐색

---

### 탐색

---

출력과 탐색의 과정은 같다. 이 작업도 단일 연결 리스트와 동일하며 단지 head에서 부터인지 tail에서 부터인지로 나뉜다.

다만 tail로 탐색해서 나온 위치(인덱스)는 초기값을 -1로 주고 진행할 때마다 1씩 감소시켜서 head로 구한 인덱스와 구분시키도록 한다.(파이썬의 리스트처럼!)

##### 코드구현

```python
#이중 링크드 리스트
class DLinkedList:

    #D_L_list에서 쓸 노드
    class Node:
        def __init__(self, v, n = None, p = None):
            self.value = v #저장된 데이터
            self.next = n #다음 노드 가리키는 변수
            self.prev = p #이전 노드 가리키는 변수

    #D_L_List에서 필요한 변수
    def __init__(self):
        self.head = None #첫 생성시 내부에는 노드가 없으므로
        self.tail = None

    #head로 삽입. v : 데이터
    def insertNodeBefore(self, v):
        #없을 경우
        if self.head is None:
            self.head = self.Node(v)
            self.tail = self.head #같은 노드를 가리킴
        else:
            #self.head : 기존노드, self.head.prev : 기존노드의 prev
            self.head.prev = self.Node(v,n=self.head) #1,2번을 동시수행
            #self.head.prev : 기존노드의 prev == 새로운 노드
            self.head = self.head.prev #3. head를 새로운 노드로 변경

    #tail로 삽입. v : 데이터
    def insertNodeAfter(self, v):
        #없을 경우
        if self.tail is None:
            self.tail = self.Node(v)
            self.head = self.tail #같은 노드를 가리킴
        else:
            #self.tail : 기존노드, self.tail.next : 기존 노드의 next
            self.tail.next = self.Node(v,p=self.tail) #1,2번을 동시수행
            #self.tail.next : 기존노드의 next == 새로운 노드
            self.tail = self.tail.next #3. tail를 새로운 노드로 변경

    def printNodeBefore(self):
        #데이터가 없을 때
        if self.head is None:
            print("저장된 데이터가 없음")
            return
        else:
            print("<현재 리스트 구조>", end='\t') #end로 print 마지막 개행을 변경할 수 있습니다.
            link = self.head #처음은 head를 지정. 이후부터는 현 노드의 next를 지정

            #link가 가리키는 노드가 없을 때까지 반복
            #None,0,""는 조건판단에서 False 처리, 그 외는 True로 처리된다.
            while link :
                print(link.value, '<->' , end = ' ')
                link = link.next #link를 현 위치 노드의 next로 변경
            print() #줄바꿈 용

    def printNodeAfter(self):
        #데이터가 없을 때
        if self.tail is None:
            print("저장된 데이터가 없음")
            return
        else:
            print("<현재 리스트 구조>", end='\t')
            link = self.tail

            while link :
                print(link.value, '<->' , end = ' ')
                link = link.prev #link를 현 위치 노드의 next로 변경
            print() #줄바꿈 용

    #head로 삭제
    def deleteNodeBefore(self):
        #없을 경우 - > 스킵
        if self.head is None :
            print("삭제할 노드가 없습니다.")
            return
        else:
            #1.현재 head가 가리키는 노드의 next를 새로운 head로 지정
            self.head = self.head.next
            #2. 새로운 head의 prev를 None으로 변경
            self.head.prev = None

    #tail로 삭제
    def deleteNodeAfter(self):
        #없을 경우 - > 스킵
        if self.tail is None :
            print("삭제할 노드가 없습니다.")
            return
        else:
            #1.현재 tail이 가리키는 노드의 prev를 새로운 tail로 지정
            self.tail = self.tail.prev
            #2. 새로운 head의 prev를 None으로 변경
            self.tail.next = None

    #head로 조회(탐색)
    def searchNodeBefore(self,v):
        # 데이터가 없을 때
        if self.head is None:
            print("저장된 데이터가 없음")
            return
        else:
            link = self.head  # 처음은 head를 지정. 이후부터는 현 노드의 next를 지정
            index  = 0 #몇 번째 노드인지 기록
            while link:
                #내가 찾는 노드인지 확인
                if v == link.value:
                    return index #위치를 반환
                else:
                    link = link.next  # link를 현 위치 노드의 next로 변경
                    index += 1 #위치값 1 증가
            #여기까지 왔다 == 해당 v값을 가진 노드가 없다.

    # tail로 조회(탐색)
    def searchNodeAfter(self, v):
        # 데이터가 없을 때
        if self.tail is None:
            print("저장된 데이터가 없음")
            return
        else:
            link = self.tail
            index = 0  # 몇 번째 노드인지 기록
            while link:
                # 내가 찾는 노드인지 확인
                if v == link.value:
                    return index  # 위치를 반환
                else:
                    link = link.prev  # link를 현 위치 노드의 prev로 변경
                    index -= 1  # 위치값 1 감소
            # 여기까지 왔다 == 해당 v값을 가진 노드가 없다.


##테스트
if __name__=="__main__":
    dl = DLinkedList()
    dl.insertNodeBefore('1stF')
    dl.insertNodeAfter('1stB')
    dl.insertNodeBefore('2ndF')
    dl.insertNodeAfter('2ndB')
    dl.printNodeBefore()

    # head로 탐색
    print("<head로 위치 탐색>")
    result = dl.searchNodeBefore('2ndF')
    print("2ndF 위치 : {}".format(result))

    result = dl.searchNodeBefore('1stF')
    print("1stF 위치 : {}".format(result))

    # tail로 탐색
    print("<tail로 위치 탐색>")
    result = dl.searchNodeAfter('2ndB')
    print("2ndB 위치 : {}".format(result))

    result = dl.searchNodeAfter('1stF')
    print("1stF 위치 : {}".format(result))
```

### Reference

---

- 참조: [파이썬 자료구조 알고리즘](https://wikidocs.net/34534)
