# 자료구조

---

### 자료구조란

- 데이터 특성을 파악하여 미리 정해놓은 일정한 규칙에 따라서 체계적으로 데이터를 구조화 시키고 표현

   예) 도서관 -> 수많은 책들 속에서 쉽게 원하는 책을 찾을 수 있다.
<br>
 - 자료구조를 배워야 하는 이유

   - 개발자들이 미리 데이터를 잘 표현할 수 있는 방법을 만듬

   - 데이터에 **효율적**으로 접근할 수 있고 처리 할 수 있게 해준다.
   <br>
   <details>
   <summary>효율적인 처리란?</summary>
   <div markdown="1">       

   - 자동화

   - **빠른계산**

   - **반복** 되는 내용 처리

   - 여러개의 값을 **한번에 처리**

   - 값이 빠르게 **변경**되는 경우에 대한 처리

   - **특정변수**에 대한 처리

   - 특정 값을 **다양한 형태**로 보기 원하는 경우

   - **조건**에 따른 처리

   </div>
   </details>
<br>

- 자료구조의 시작

   - 파이썬이라는 프로그래밍 언어와는 별개로, 실생활에서 발생하는 **대용량의 다양한 데이터를 효율적으로 처리(저장)** 하기 위해 개념 개발

```python
# 인트로 코딩
# 특정 두 수의 합과 같은 인덱스값을 찾자.
def twonumbersum(numbers, result):
  for i in range(len(numbers)):
    for j in range(i+1, len(numbers)):
      if numbers[i] + numbers[j] == result:
        return [i,j]

# 리스트값을 받기 위한 코드: 리스트 컴프리헨션 & 리스트 메소드(split) 활용
# input 예시: 10,5,7
numbers = [int(numbers) for numbers in input("리스트값을 입력하세요 : ").split(',')]
# input 예시: 17
result = int(input("두 수의 합을 입력하세요 : "))

print("인덱스값 : ", twonumbersum(numbers,result))
```

```python
# 함수에 값만 전달하는 경우
def remainder(num, div):
    return num % div

print(remainder(20, 7))   # argument에 값 전달

"""
case 1 - 함수에 변수이름과 값을 함께 전달하는 경우
-> 처음 코드를 보는 사람도 함수에 전달되는 값이 무엇인지 알 수 있다.
"""
def remainder(num, div):
    return num % div

print(remainder(num = 20, div = 7))

""" 
case 2 - 함수에 디폴트값을 할당해주는 경우
 -> 함수에 전달되는 argument값이 고정값일 때 유연하게 쓰일 수 있다
"""

def remainder(test, num = 5, div = 2):
    return num % div

print(remainder(test = 7))
```


### 배열

- 가장 기초적이면서 단순하고 자주 사용되는 자료구조 형태
<br>
- 순차적으로 데이터를 나열하면서 저장
<br>
- **하나의 변수에 여러개의 인덱스**로 묶는 것
<br>
- **파이썬에서는 배열을 튜플 & 리스트로 구현가능**
<br>
- 장점:

   - **인덱스 번호를 통한 데이터 위치에 직접적인 접근** -> 빠르게 데이터 접근 가능
<br>
- 단점:

   - 미리 배열의 크기를 지정해야함 -> 데이터 추가, 제거, 수정이 불편

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%85%E1%85%B5%E1%84%89%E1%85%B3%E1%84%90%E1%85%B3%E1%84%90%E1%85%B2%E1%84%91%E1%85%B3%E1%86%AF%E1%84%87%E1%85%A2%E1%84%8B%E1%85%A7%E1%86%AF.png?raw=true)

**파이썬의 리스트와 자료구조의 리스트**
- **파이썬은 리스트 자료형이 자료구조의 연결리스트**로 기능을 지원

- 리스트는 **임의의 메모리(위치)**에 자료를 **동적으로 처리**가능

- 파이썬의 리스트는 자료구조의 배열과 연결리스트의 특징을 모두 갖고 있다.

   - 배열의 특징: **인덱스 사용**하여 노드에 접근가능

   - 연결리스트의 특징: **인덱스 크기**를 자유롭게 확장가능, **서로 다른 자료형**을 노드로 갖을 수 있다.

**=> 자료구조의 가장 기존적인 의미는 자료를 쉽게 관리하기 위해 다양한 구조로 묶는 것이다!!**

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%8C%E1%85%A1%E1%84%85%E1%85%AD%E1%84%80%E1%85%AE%E1%84%8C%E1%85%A9%E1%84%85%E1%85%B5%E1%84%89%E1%85%B3%E1%84%90%E1%85%B3_%E1%84%91%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%8A%E1%85%A5%E1%86%AB%E1%84%85%E1%85%B5%E1%84%89%E1%85%B3%E1%84%90%E1%85%B3.png?raw=true)

##### 파이썬의 리스트

- 자료구조의 기본은 **배열**, 파이썬에서는 **리스트와 튜플**

- 리스트나 튜플의 핵심은 **인덱스 사용**

- 파이썬의 리스트는 자료구조와 알고리즘에서 가장 많이 볼 수 있는 활용법

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%87%E1%85%A2%E1%84%8B%E1%85%A7%E1%86%AF%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%83%E1%85%A6%E1%86%A8%E1%84%89%E1%85%B3.png?raw=true)

```python
# 리스트 인덱싱/슬라이싱 예시

s = [11,22,33,44,55]

print('s[0:3] 결과:', s[0:3])
print('s[:3] 결과:', s[:3])
print('s[1:] 결과:', s[1:])
print('s[::2] 결과:', s[::2])
print('s[0:1:3] 결과:', s[0:1:3])
print('s[-3] 결과:', s[-3])
print('s[-3:-1] 결과:', s[-3:-1])
print('s[1:-1] 결과:', s[1:-1])
```

- 리스트를 다양한 형태로 활용 가능

   - 알고리즘의 기본이 될 수 있는 **문자열 메소드, 반복문, 조건문** 활용 

```python
# 예시1 - 회문(팰린드롬)

def ispalindrome(s):
    return_numbers = []
    for char in s:
      if char.isalnum():
        return_numbers.append(char.lower())
      
    while len(return_numbers) > 1:
      if return_numbers.pop(0) != return_numbers.pop():
        return False

    return True

test_string = input()
print(ispalindrome(test_string))

# 예시1 - 회문(팰린드롬)

def ispalindrome(s):
    return_numbers = []
    for char in s:
      if char.isalnum():
        return_numbers.append(char.lower())
      
    while len(return_numbers) > 1:
      if return_numbers.pop(0) != return_numbers.pop():
        return False

    return True

test_string = input()
print(ispalindrome(test_string))

# 예시1 - 회문(팰린드롬)

def ispalindrome(s):
    return_numbers = []
    for char in s:
      if char.isalnum():
        return_numbers.append(char.lower())
      
    while len(return_numbers) > 1:
      if return_numbers.pop(0) != return_numbers.pop():
        return False

    return True

test_string = input()
print(ispalindrome(test_string))


# 예시4 - 문자열 뒤집기(리스트에서 제공하는 메소드가 아닌, 파이썬의 내장함수 활용)
strtest3 =['a','b','c','d']
tuple_test =('a','b','c','d')

print(strtest3) 
print(list(reversed(strtest3)))
print(tuple(reversed(strtest3)))
print(strtest3)
```


# 자료구조와 효율성

---

- 복잡성이 무엇인지 알아보고, Big O 표기법을 사용하여 알고리즘의 성능을 분류
<Br>
- 빅오표기법에 대한 현실적인 활용방안 고민
<br>
- 소스코드의 효율성과 구동되는 프로그램(서비스)의 효율성의 관계에 대해 고민해보기
<Br>
### Big O 표기법(notation)

- **알고리즘 실행 효율성**에 대해 측정할 방법 필요 

   -> 빅오표기법을 활용하여 효율확인 가능
<br>
   - 빅오표기법은 해당 코드가 얼마나 수행되었는지(결과값을 출력하기 위한 **연산을 얼마나 반복**하였는지)에 따라 효율성 확인
<br>
- Big O 표기법은 **데이터 입력값 크기**에 따라 알고리즘 실행 속도의 변화를 설명하는 방법
<br>
- 알고리즘 계산 복잡도 종류
<br>
   - **시간복잡도**

      - 입력값에 따른 시간(연산 횟수)의 증가 비율

      - 시간 복잡도 측면에서의 효율적인 알고리즘 -> **입력값이 증가함에 따라 시간의 증가 비율을 최소화**한 알고리즘

      - 시간 복잡도를 더 많이 고려한다.
<br>
   - **공간복잡도**

      - 메모리(저장공간) 관련된 효율성

      - 최근에는 기술의 발전으로 컴퓨터의 메모리가 증가했기에 시간 복잡도에 비해 공간 복잡도는 크게 문제되지 않음 
<br>
- Big O 표기법은 입력값 증가에 중점을 두고 대비하여 실행시간이 얼마나 길어지는지를 설명

   - 빅오표기법(O(n))만으로 **성능을 예측**할 수는 없다.

    -> 예) 실제 실행시간이 30n + 1000와 같이 나왔더라도 빅오표기법으로는 O(n)으로 표현되기 때문에 실제 성능과 같을 수는 없다.
<br>
- 표기법

   - 입력값 n의 가장 큰 차수만 표기

   - 상수항을 고려하지 않는다

###### Big O run times  비교

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%87%E1%85%B5%E1%86%A8%E1%84%8B%E1%85%A9.png?raw=true)

- 입력값과 실행시간

![image](https://tk-assets.lambdaschool.com/e4357b5f-1d63-44cd-b8a0-4957260ae9ec_Untitled1.png)

- 입력값에 따른 차이
```
log(10) = 1           
10 = 10               
10log(10) = 10
10^2 = 100           
2^10 = 1024              
10! = 3628800           
```

- 파이썬 내장함수 시간복잡도

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%85%E1%85%B5%E1%84%89%E1%85%B3%E1%84%90%E1%85%B3_%E1%84%89%E1%85%B5%E1%84%80%E1%85%A1%E1%86%AB%E1%84%87%E1%85%A9%E1%86%A8%E1%84%8C%E1%85%A1%E1%86%B8%E1%84%83%E1%85%A9.png?raw=true)

###### 소스코드로 살펴보는 Big O run tiomes

- Contanst Time(상수시간) : O(1)
   - 입력의 크기가 소요시간에 영향을 미치지 않는 경우

```python
def print_one_item(items):
    print(items[1])       # 상수시간(단순하게 하나의 출력)

print_one_item([0,1,2])

def print_function(x,y,z):
    result = x * y * z
    return result
```

- Linear Time(선형시간) : O(N)
 
   - 입력의 크기에 소요시간이 비례하는 경우

```python
def print_every_item(items):
    for item in items:  # 하나의 반복문
        print(item)

print_every_item([0,1,2])

def print_function(list):
    for i in range(len(list)):
        print(list[i])

print_function([1,3,5,7,9])

# 만약 아래와 같다면? -> 마찬가지로 O(N)
def print_function(list):
    for i in range(len(list)):
        print(list[i])

    for i in range(len(list)):
        print(list[i])

    for i in range(len(list)):
        print(list[i])

    for i in range(len(list)):
        print(list[i])

print_function([1,3,5,7,9])

```

- Quadratic Time(제곱시간) : O(n^2)

```python
def print_pairs(items):
    for item_one in items:      # 중첩반복문
        for item_two in items:
            print(item_one, item_two)

print_pairs([0,1,2])

def print_function(list):
    for i in range(len(list)):
        for j in range(len(list)):
            print(list[i], list[j])

```

- 만약 소스코드가 아래와 같다면??

   - **선형 시간이 상수 시간보다 우선시** 되므로 상수시간은 무시되고, **반복문이 독립적**으로(중첩반복문이 아님) 수행되기 때문에 위 코드에 대한 런타임은 **선형시간인 O(N)**이 된다.

```python
def time_test(items):
    last_idx = len(items) - 1
    print(items[last_idx])      # 상수시간

    middle_idx = len(items) / 2
    idx = 0
    while idx < middle_idx:     # 반복문1
        print(items[idx])
        idx = idx + 1

    for num in range(2000):     # 반복문2
        print(num)

time_test([0,1,2])

```
- 아래와 같은 경우는 두가지로 나눠질 수 있다.

   - 처음에 있는 첫번째 아이템을 바로 찾는 경우는 **O(1)**로 끝난다.
    **->반복없이 바로 결과 반환**

   - 하지만 최악의 경우 마지막 아이템을 갖게 되므로, O(N)이 된다.
    **-> 반복문을 통해 마지막 아이템을 찾을 떄까지 검색하므로**

```python
def search_thing(items, thing):
    for item in items:
        if item == thing:
            return True

    return False

search_thing([0,1,2],3)
```

- 위 코드는 while의 반복수에 따라 달라지므로 O(1)이 될 수 없다.

- 출력값이 되는 i, 반복수행되는 횟수이자 입력값인 n이 동일한 횟수로 증가하지 않으므로 선형시간(O(N))이 될 수 없다.

- 입력값인 n에 따라 출력값인 i의 증가율이 동일하지 않기 때문에 로그시간(O(logn))으로 측정.

```python
# 두 코드 비교
def test(n):
    i = 1
    while i < n:
        print(i)
        i *= 2

test(3)

```

- 삽입정렬을 수행하는 경우 코드 실행시간은??

   - range는 필요한 정수들에 대해서만 반복자를 반환

   - j 때문에 반복문이 2개 있더라도 반환하는 경우가 1번이기 때문에 O(N)시간 소요

```python
# 아래 코드에 대해 삽입정렬을 수행하는 경우 코드 실행시간은 어떻게 될까?

def example_sort(array_test):
  array_len = len(array_test)
  print('array_len:', array_len)

  array_test.append(5) # [3, 1, 7, 5]
  array_test.extend([2,9]) # [3, 1, 7, 5, 2, 9]
  array_test.pop() # [3, 1, 7, 5, 2]
  print('array_test:', array_test)
  print('array_len:', len(array_test))

  for i in range(1, array_len): # i: 1, 2, 3, 4
    # 한 번 수행되고 더 이상 반복되지 않는 반복문이다.
    for j in range(i, 0, -1):
      if array_test[j] < array_test[j-1]:
        print(i, j)
      else:
          break

test = [3,1,7]
example_sort(test)

```

###### 정리

- 시간복잡도를 확인할 때 우선적으로 고려할 것은 **반복문**

- 반복문이 한번 수행되면 O(N)이 될 수 있고, 반복문이 중첩해서 2개가 수행되면 O(N^2)

- 단, **입출력값 로직**에 따라 달라질 수 있다.

###
