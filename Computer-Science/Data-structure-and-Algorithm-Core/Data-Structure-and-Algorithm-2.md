# 02. 연결 리스트

---

## a.연결 리스트와 배열과 배열리스트

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

##### 저장된 노드가 이쓴 경우

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
