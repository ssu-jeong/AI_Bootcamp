# 01.자료구조를 위한 사전 지식

---

## a. 자료구조와 자료형

---

### 객체구현

---

현실에 있는 물체, 또는 가상한 존재. 이를 **객체(Object)**라 정의하고 **Class를 이용하여 프로그래밍에 옮겨 구현.**
수치나 값에 대한 것은 **클래스의 속성(Attribute)**으로, 행동과 연산에 대한 것은 **클래스의 메소드(Method)**로 작성.

### 추상과정

---

- **프로그래밍에 옮겨 구현**

만약 자동차에 대해 코드로 옮긴다고 한다면, 자동차에 대한 값들과 기능 및 수행 작업들을 머리속에서 대강 "이렇게 문자열로 표기하면 될 것이다. 이 정보는 정수형으로 하고..." 하며 어떻게 코드에 옮길지 구상하게 된다. 

이 과정에서 필요없는 정보는 옮기지 않을 수도 있다. 그러면 필요하거나 특정 정보만 코드로 옮기게 되는데 이 것을 **추상화(Abstract)**라고 볼 수 있다. 

### 객체 구현 = 새로운 자료형의 정의 ≠ 자료구조

---

실체 또는 허구 모두 객체로 정의하여 클래스로 구현가능하나 자료구조에서 구현할 클래스와는 조금 다르다.

자료구조에서 클래스를 이용하여 구현할 객체는 **목적**이 있다. 
- 목적: 데이터를 저장 및 관리 및 정돈(정렬)을 효율적으로 하기 위한 구성체를 만듬.
<br>

- **탐색, 삽입, 삭제** 등의 연산을 고려하지 않는다면 자료구조(Data Structure)로 볼 수 없다.
<br>

   - 이 기본 3연산은 메소드로 구현되어 있어야 하며, 연산을 위한 속성(변수)들이 추가될 수 있다. 
<br>

   - 목적에 따라 기본 3연산 외에 추가적인 연산이 작성될 수 있으며 세분화시길 수도 있다.

      -> **필요연산 ≤ 구현할 메소드**
<br>

- 대표적인 자료구조 : 파이썬 **기본 자료형인 리스트**
<br>

   - 리스트는 기본 3연산인 삽입(함수 append, insert, extend), 조회(index접근, 함수 index), 삭제(명령어 del, 함수 remove, clear)와 추가적인 연산(함수 count, copy, pop, sort, reverse)가 구현되어 있다.

### 자료구조와 알고리즘

---

단순하게 if와 while로 작성하는 알고리즘이 아닌, 알고리즘(정렬 및 탐색 알고리즘)은 자료구조를 통해 나온다. 알고리즘을 구현하려면 그 알고리즘이 수행될 수 있도록 부합하는 환경, 즉 자료구조(Data Structure)를 구현할 수 있어야하기 때문! **(알고--자료구조--리즘)**

---

## b.클래스 기본적인 작성방법

---

### 클래스로 객체 구현

---

- 클래스: 객체(Object)를 프로그래밍을 위해 코드로 구현할때 사용.
   -> 붕어빵 만들때 사용하는 '틀' 같은 존재로 이를 찍어내서 생성을 한다.
<br>

- 속성(Attribute, 클래스 내의 변수): 필요한 값과 정보
<br>

- 메소드(Method, 클래스 내의 함수): 기능 및 행동
<br>

- 인자: 클래스로 무언가를 생성할 때 필요한 재료들
    
    -> 찍어내는 과정중에 바뀔 수 있는 재료들로 **클래스 생성자**에서 진행되고 메소드  __init__에서 정의
<br>

- 인스턴스: 클래스로 찍어낸 결과물

### 클래스의 기본 구조

---

```python
##클래스 사용 예제
class 클래스이름:
    #클래스 생성자 정의
    def __init__(self, 인자1, 인자2):
        self.필요한속성1 = 인자1
        self.필요한속성2 = 인자2

    #필요한 메소드 구현
    def 필요한메소드1(self):
        코드구현

    def 필요한메소드2(self):
        코드구현


##메인 코드 영역

#인스턴스 생성
c1 = 클래스이름(c1의 인자1,c1의 인자2)
c2 = 클래스이름(c2의 인자1,c2의 인자2)

#메소드 사용하여 인스턴스 활용
c1.필요한메소드1()
c2.필요한메소드1()

c1.필요한메소드2()
c2.필요한메소드2()
```

### 클래스 활용 예시

---

```python
##상황 : 자라는 아이들의 키를 관리하는 요정의 프로그램
class Child:
    #클래스 생성자 정의
    def __init__(self, Child_name, Child_height):
        self.name = Child_name
        self.height = Child_height

    #필요한 메소드 구현
    def getName(self):
        return self.name #이름 정보를 반환

    def getHeight(self):
        return self.height #키 정보를 반환

    def growHeight(self, add):
        temp=self.height #임시 지역변수. 성장전 키값 저장
        self.height += add
        print("성장했습니다.{}->{}".format(temp,self.height)) #성장결과 출력


##메인 코드 영역

#어린이 인스턴스 2개 생성
c1 = Child('Tom',150) #Child_name과 Child_height이 'Tom',150인 어린이 정보를 생성
c2 = Child('Jerry',100) #Child_name과 Child_height이 'Jerry',100인 어린이 정보를 생성

##메소드 사용하여 인스턴스 활용
#1.현재 이름과 키 정보 조회
print("현재 {}의 키는 {}cm 입니다.".format(c1.getName(), c1.getHeight()))
print("현재 {}의 키는 {}cm 입니다.".format(c2.getName(), c2.getHeight()))

#2.키를 성장
c1.growHeight(10) #growHeight 메소드의 매개변수 add값을 10 넣어준다.
c2.growHeight(30) #growHeight 메소드의 매개변수 add값을 10 넣어준다.

#3.현재 이름과 키 정보 조회
print("현재 {}의 키는 {}cm 입니다.".format(c1.getName(), c1.getHeight()))
print("현재 {}의 키는 {}cm 입니다.".format(c2.getName(), c2.getHeight()))
```

## c. 클래스의 Setter, Getter

---

### 메소드 Setter, Getter
---

Setter는 값을 **수정**하는, Getter는 값을 **조회**하는 메소드

- 클래스로 만든 인스턴스의 속성을 변경하거나 조회 및 삭제를 하려면 메소드를 거치게끔 설계 해야 함.

   -> 캡슐화(Encapsulation)와 은닉화(Hidden) 때문!!

- "인스턴스 변수를 직접 접근 및 수정을 막고 반드시 메소드를 거치도록하여 클래스 내부의 변수명을 숨기고 데이터 변조 위험성을 낮춘다"

```python
##메소드 사용하여 인스턴스 활용
#1.현재 이름과 키 정보 조회
print("현재 {}의 키는 {}cm 입니다.".format(c1.getName(), c1.getHeight()))
print("현재 {}의 키는 {}cm 입니다.".format(c2.getName(), c2.getHeight()))

#2.키를 성장
c1.growHeight(10) #growHeight 메소드의 매개변수 add값을 10 넣어준다.
c2.growHeight(30) #growHeight 메소드의 매개변수 add값을 10 넣어준다.
```

### 클래스 속성과 메소드에 대한 기본 접근 설정

---

- 파이썬에서는 다른 프로그래밍 언어와는 다르게 접근지정자(public, private 등)가 없다.

- 파이썬은 기본적으로 인스턴스의 속성에 직접 접근을 허용

###### 막아야될 접근 방법

```python
"""
예제는 직접 접근하여 인스턴스 변수 값을 수정하는 방법.
만일 이처럼 직접접근이 수행되지 않도록 하려면 은닉화해야한다.
"""
##상황 : 자라는 아이들의 키를 관리하는 요정의 프로그램
class Child:
    #클래스 생성자 정의
    def __init__(self, Child_name, Child_height):
        self.name = Child_name
        self.height = Child_height

    #필요한 메소드 구현
    def getName(self):
        return self.name #이름 정보를 반환

    def getHeight(self):
        return self.height #키 정보를 반환

    def growHeight(self, add):
        temp=self.height #임시 지역변수. 성장전 키값 저장
        self.height += add
        print("성장했습니다.{}->{}".format(temp,self.height)) #성장결과 출력


##메인 코드 영역

#어린이 인스턴스 2개 생성
c1 = Child('Tom',150) #Child_name과 Child_height이 'Tom',150인 어린이 정보를 생성

##메소드 사용하여 인스턴스 활용
#1.현재 이름과 키 정보 조회
print("현재 {}의 키는 {}cm 입니다.".format(c1.getName(), c1.getHeight()))

#2.키를 성장
#c1.growHeight(10) #growHeight 메소드의 매개변수 add값을 10 넣어준다.
c1.height+=10 #키를 증가 시킨다. ->변수에 직접 접근이 허용되있다.

#3.현재 이름과 키 정보 조회
print("현재 {}의 키는 {}cm 입니다.".format(c1.getName(), c1.getHeight()))

>>> 현재 Tom의 키는 150cm 입니다.
    현재 Tom의 키는 160cm 입니다.
```

### 은닉화

---

클래스에서 사용하는 속성 또는 메소드 앞에 __(언더바 2개)를 붙이면 외부에서 접근하여 사용할 수 없다.

(예, 클래스 생성자 메소드(__ init __)이 있다.)

-> 이렇게 하면 속성에 직접 접근할 시 에러가 발생한다. 

```python
##상황 : 자라는 아이들의 키를 관리하는 요정의 프로그램
class Child:
    #클래스 생성자 정의
    def __init__(self, Child_name, Child_height):
        self.__name = Child_name
        self.__height = Child_height

    #필요한 메소드 구현
    def getName(self):
        return self.__name #이름 정보를 반환

    def getHeight(self):
        return self.__height #키 정보를 반환

    def growHeight(self, add):
        temp=self.__height #임시 지역변수. 성장전 키값 저장
        self.__height += add
        print("성장했습니다.{}->{}".format(temp,self.__height)) #성장결과 출력

##메인 코드 영역

#어린이 인스턴스 2개 생성
c1 = Child('Tom',150) #Child_name과 Child_height이 'Tom',150인 어린이 정보를 생성

##메소드 사용하여 인스턴스 활용
#1.현재 이름과 키 정보 조회
print("현재 {}의 키는 {}cm 입니다.".format(c1.getName(), c1.getHeight()))

#2.키를 성장
#c1.growHeight(10) #growHeight 메소드의 매개변수 add값을 10 넣어준다.
c1.__height+=10 #키를 증가 시킨다.

#3.현재 이름과 키 정보 조회
print("현재 {}의 키는 {}cm 입니다.".format(c1.getName(), c1.getHeight()))


>>> 현재 Tom의 키는 150cm 입니다.
    File "파일경로/04ClassExUseT.py", line 32, in <module>
       c1.__height+=10 #키를 증가 시킨다.
    AttributeError: 'Child' object has no attribute '__height'
```

## d. 재귀호출(순환호출)

---

### 재귀호출(순환호출): Recursion

---
 
- 재귀호출: 함수 또는 메소드가 자기자신을 또 호출하는 형태

**재귀호출은 잘못하면 무한 호출이 되기 때문에 조심해야한다.**

다행히 파이썬에서는 무한 호출이 감지되면 중지시키는 RecursionError가 존재

```python
#재귀함수 예시
def aFunc():
    print("호출!")
    aFunc() #자신을 호출

##메인 코드
aFunc()

>>> 호출!
    호출!
    ....(생략)
    호출!
    호출!
    Traceback (most recent call last):
      File "파일경로/05RecursionF.py", line 9, in <module>
        aFunc()
      File "파일경로/05RecursionF.py", line 6, in aFunc
        aFunc() #자신을 호출
      File "파일경로/05RecursionF.py", line 6, in aFunc
        aFunc() #자신을 호출
      File "파일경로/05RecursionF.py", line 6, in aFunc
        aFunc() #자신을 호출
      [Previous line repeated 993 more times]
      File "파일경로/05RecursionF.py", line 5, in aFunc
        print("호출!")
    RecursionError: maximum recursion depth exceeded while calling a Python object
```

### 올바른 재귀 호출

---

재귀호출을 염두하고 만든 함수는 실행될 수 있는 재귀의 횟수를 정해놓거나, 함수가 종료될 수 있는 조건이 반드시 있어야 한다.

## e. 노드(Node) - 자료구조 기본 단위

---

### 노드(Node)

---

- 노드란? 관리할 데이터를 보관(존재)하는 곳, 즉 자료구조에서 관리하고 있는 정보들 중 하나를 저장하고 있는 단위
<br>

![image](https://wikidocs.net/images/page/33841/01%EB%85%B8%EB%93%9C%EC%84%A4%EB%AA%851.png)

대체로 자료구조를 공부할 때 이 노드를 클래스로 직접 구현하지만 구조적 설계보다 연산(메소드)이나 연산으로 인한 구조적 변화에 학습을 집중해야 될 때는 노드를 따로 구현하지 않는다. 

이 경우 기본적으로 제공하는 자료형(대표적으로 리스트)으로 주로 진행. 
-> 리스트에는 노드가 value로 구현이 되어 있기 때문.

### Reference

---


- 참조: [파이썬 자료구조 알고리즘](https://wikidocs.net/33825)

- [자료구조와 알고리즘 시각자료](https://visualgo.net/en)