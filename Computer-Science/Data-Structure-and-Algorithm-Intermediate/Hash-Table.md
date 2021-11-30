# Hash Table

---

- 키워드: 해시테이블, 자료구조와 딕셔너리
<br>

- [해시테이블에 대한 의견](https://youtu.be/S7vni1hdsZE)

---

## 해시

---

- 딕셔너리 코드와 관련되어 활용되는 개념

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-08-20%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%203.09.16.png?raw=true)

## 해시테이블

---

- 키를 활용하여 값에 직접 접근이 가능한 구조

   - 해시구조: 키(Key)와 값(Value)쌍으로 이루어진 데이터 구조를 의미합니다. Key를 이용하여 데이터를 찾으므로, 속도를 빠르게 만드는 구조

- 해싱의 목적은 **검색**으로 검색알고리즘의 역할도 한다.

   - 장점: **데이터 양에 영향을 덜 받으며** 성능이 빠르다.
          -> 키를 통해 값을 검색

- 파이썬의 **딕셔너리는 내부적으로 해시테이블 구조로 구현**

   - 해시테이블은 검색을 위한 역할도 하고, 딕셔너리를 위한 자료구조의 역할도 한다. 

###### 용어

- 해시(Hash): 함수를 통해 나온 **값**

- 해시테이블: 키를 빠르게 **저장 및 검색할 수 있는 테이블형태의 자료구조**

- 해시함수: 여러 키를 분할하기 위해 키를 해시값(정수값)으로 **매칭시키는 역할**

- 해시 값(해쉬 주소, Hash Value or Address): 키값을 해시 함수에 넣어서 얻은 주소값

- 슬롯(Slot): 한개의 데이터를 저장할 수 있는 공간(buckets)

- 해싱(Hashing): **다 흩뜨려놓고, 키와 매칭되는 값을 검색하는 과정**

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FRf9ew%2FbtqBD2nxuS2%2FNcjU5klHVOqPfEm28syiFk%2Fimg.png)

```python
# case 1 - 딕셔너리로 활용되는 해시테이블을 확인할 수 있다.

test_code = {2.5: 'A' ,'2.0': 'B', '1.0': 'C'}
print(test_code[2.5]) 
print(test_code['1.0'])
print(test_code['2.0'])

# case 2 - 리스트와 튜플을 활용해서 해시테이블을 확인한다.
# 데이터는 튜플로 저장된다.

test_code = [(2.5, 'A'), ('2.0', 'B'), ('1.0', 'C')]
 
def insert(item_list, key, value):
    item_list.append((key, value))
 
def search(item_list, key):
    for item in item_list:    # 데이터를 검색하려면 딕셔너리보다 오래 걸린다.(키,값 쌍이 없어서 개별 값으로 반복해서 검색하기 때문이다.)
        if item[0] == key:
            return item[1]      
    print('not matching')       
    
print(search(test_code, '2.0'))
print(search(test_code, 2.5))
search(test_code, '2.5')
```

- 해시테이블에 대한 간단한 예시

```python
"""
# 예시: 키(aqua)와 값(#00FFFF)이 정렬되지 않은 형태로 있는 경우, 색상에 해당하는 코드를 찾는 상황
이러한 경우, 반복문과 조건문을 활용한다면 선형시간 O(N)
색상이 알파벳순서대로 이미 정렬되어 있다면 이진검색을 할 수 있다.(O(logn))
"""
# 수도코드

[("aqua", "#00FFFF"), ("beige", "#F5F5DC"), ("chartreuse", "#7FFF00")]

for i in range(0, len(dictionary)):
  1)알파벳순서대로 정렬되어있음
  2)알파벳찾기(예를 들어, "beige"를 찾아보겠다.)
  3)이진검색 알고리즘 활용
  4)로그시간 성능이 나온다.
```

- 파이썬의 딕셔너리는 자료구조의 해시테이블로 구현

```python
# 먼저 값이 없는 딕셔너리를 선언한다.
dict = {}

# 값추가
dict['a'] = 1
dict['b'] = 2
dict['c'] = 3
dict
>>> {'a': 1, 'b': 2, 'c': 3}

"""
- 결과값은 {'키': 값} 쌍
- 해시테이블 dict의 값을 읽어오는데 사용되는 문자열이 "키"
- 해시테이블에 저장된 데이터(값)에 접근하려면 키를 알아야한다.
"""
# 아래와 같이 키를 통해 값을 알 수 있다.
dict['c']
>>> 3
```

```python
# 해시테이블에 반복문을 적용시켜보자.

for key in dict.keys():
  print(dict[key])

# (키,값) 쌍을 출력해본다.

for key, value in dict.items():
  print('(키',key,',','값',value,')')
```

### 해시함수

---

- 해시함수: 입력값의 형태는 다양하고, **출력값의 형태는 숫자**
<br>

- 키를 해시테이블 내의 버킷(=hashes=해시값)으로 매핑
<br>

- 하나의 해시함수가 입력 데이터 별로 다른 숫자와 매핑된다면, 그것은 **완벽한 해시함수**이다.
<br>

   - 해시함수가 입력데이터에 따라 다른 숫자를 반환하게 되면 **해시충돌을 최소화**하는 것.
<br>

- 조건
<br>

   - **입력값이 같다면, 동일한 출력값**을 받아야 한다.
<br>

   - 입출력값이 일정하지 않다면 적절한 해시함수가 아니다.
<br>

      - 예) 입력값 'aqua'가 4를 반환한다면, 입력값 'beige'는 4를 반환할 수 없다.
<br>

      - 해시함수는 특정 범위 안에 있는 숫자를 반환.


#### 기본 해시함수

- 해시함수는 보통 문자열 입력값에 정수형 출력값을 반환
<br>

- 정수형에서 문자열로 변환하기 위해 해시함수는 문자열에 해당하는 개별적인 단어를 활용

```python
"""
# 예제: 파이썬에서 .encode() 메소드를 활용해서 문자열에서 바이트 코드로 인코드하는 것
# 인코딩된 후에, 정수형은 각 단어를 나타냄
"""

# 인코딩 예제
bytes_representation = "hello".encode()

for byte in bytes_representation:
    print(byte)
```

- 여러개 정수들을 하나의 문자열로 변환

```python
# 정수값의 합 반환
bytes_representation = "hello".encode()

sum = 0
for byte in bytes_representation:
    sum += byte

print(sum)

# 해시함수를 만들고 활용해보자.
def my_hashing_func(str, list_size):
    bytes_representation = str.encode()    
    sum = 0
    for byte in bytes_representation:
        sum += byte

    print('sum:', sum)
    print('list_size', list_size)
    print('sum%list_size:', sum % list_size)
    return sum % list_size
```

- 추가학습

```python
# 먼저 5개의 빈 슬롯이 들어가는 리스트를 초기화
my_list = [None] * 5

"""
# 리스트에 있는 적합한 인덱스에 색상 이름문자열에 매핑되기 위해 해시함수를 사용
- 인덱스에 헥사코드값을 저장
- 해시함수를 사용하여 값을 검색가능
"""
# 위의 my_hashing_func이라는 해시함수를 활용하여 아래처럼 값을 확인할 수 있다.
my_list = [None] * 5

my_list[my_hashing_func("aqua", len(my_list))] = "#00FFFF" # 리스트에 값을 입력

print(my_list[my_hashing_func("aqua", len(my_list))]) # 리스트에 있는 값을 출력

print(my_list)
```

#### 해시성능

- 해시테이블 자체는 충돌을 해결해주지 않는다. 
<br>

- O(1) 시간복잡도 안에 검색, 삽입, 삭제를 할 수 있다.
<br>

   - 상수 시간(O(1))은 해시테이블의 사이즈에 관계없이 동일한 양의 계산
<br>

      - 해시충돌로 인해 모든 bucket의 value를 찾아야 하는 경우(반복문)도 있다.
<br>

- 해시테이블이 하나의 요소를 갖고 있다면, 해시테이블 인덱스 갯수에 관계없이 프로그램 수행시간이 비슷

   -> 해시함수 떄문!!
<br>

- 검색 / 삽입 / 삭제 무엇을 하든지 해시함수는 키를 통해 저장된 값에 연관된 인덱스를 반환한다.(즉, 키와 인덱스가 매칭되야함)
<br>

- 시간 복잡도
<br>

   - 일반적인 경우(충돌이 없는 경우): O(1)
<br>

   - 최악의 경우(모든 경우에 충돌이 발생하는 경우): O(n)

## 해시충돌

---

### 해시충돌

---

- 해시 함수가 항상 다른 입력을 다른 인덱스에 매핑된다는 것은 모든 데이터를 알고 있어야만 가능. 그렇지 않으면 완벽한 해시 함수 작성은 불가능.

- 해시충돌은 키가 들어갈 자리(버킷)가 없는 경우 발생



   - 예) 키 B와 C 같은 경우가 해시함수를 통해 계산된 상태에서 버킷4에서 충돌이 발생

   - 따라서 **충돌이 적은 해시함수를 만드는 것**이 해시테이블의 가장 중요한 목적.

![image](https://github.com/Maiven/data-science/blob/main/hash_collision.png?raw=true)

``` python
# 해시테이블의 기본 구조
# 빈 값이 있는 사이즈가 5인 해시테이블을 생성해본다.
hashtable = [None] * 5
print(hashtable)


# 위의 해시테이블과 연결지어 해시함수를 만들어볼 수 있다.
def hash_function(key):
    return key % len(hashtable)
 
print(hash_function(10)) 
print(hash_function(20)) 
print(hash_function(31))


# 해시테이블에 데이터를 삽입해볼 수 있다.
def insert_hash(hashtable, key, value):
    hash_key = hash_function(key)
    hashtable[hash_key] = value 

insert_hash(hashtable, 10, 'A')   # 해시함수로 계산되어 0번째 인덱스에 A가 삽입됨
print(hashtable)
 
insert_hash(hashtable, 23, 'B')   # 3번째 인덱스에 B가 삽입됨
print(hashtable)

# 위의 예시를 활용해서 충돌이 일어나는 상황을 살펴보자.

# 현재 0번째 인덱스에 A, 3번째 인덱스에 B가 저장되어있다.
# 아래와 같이 해시함수를 통해 계산된 0번째 인덱스에 'Collision' 값을 삽입할 경우, 충돌이 발생한다.
# 그리고 'A'값은 'Collision'으로 대체(충돌)된다.
insert_hash(hashtable, 20, 'Collision')
print(hashtable)
```

#### 충돌 방지 방법 - Chaining(체이닝)

![image](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d0/Hash_table_5_0_1_1_1_1_1_LL.svg/450px-Hash_table_5_0_1_1_1_1_1_LL.svg.png)

- 체이닝은 리스트를 활용하여 해시함수에서 매핑된 후, bucket에서 연결될 수 있는 entry에 **제한을 두지 않는 체인 형태**로 연결하는 것
<br>

- 해시 테이블에서 **동일한 해시값**에 대한 충돌이 일어난다면, 그 **위치에 있던 버킷에 키값을 뒤이어 연결**
<br>

- 데이터의 형태는 위 그림처럼 연결리스트의 형태를 갖는다.
<br>

   - 체이닝의 원리

      1) 키의 해시값을 계산
      2) 해시값을 이용해 리스트의 인덱스를 구한다.
      3) 같은 해시값이 있다면(충돌한다면) 리스트로 연결
<br>

- 충돌을 줄이기 위해, 각 리스트에 대해 연결(리스트 형태)
<br>

   - 따라서 특정 해시값에 대해 충돌이 발생해도, 체이닝을 통해 값을 찾을 수 있다.

##### 충돌상황 재현

- 체이닝은 **연결리스트**의 원리를 사용하기 때문에 **해시값이 같은 노드**를 연결하는 모습을 보임
<br>

- 해시값이 **인덱스** 역할. ( 0,1,2,3,...,8)
<br>

- **나누기방법(division method)**: 나누기 방법은 쉽기 때문에 많이 사용되는 기본적인 해시 함수로서 키값이 정수로 가정
<br>

   - 아래 해시함수의 공식은 '키의 값 % 13'
<br>

   - 따라서 **매핑되는 해시값(버킷)이 '13으로 나눈 나머지값'**을 나타내도록 구성
<br>

   - 해시값 4에서 충돌이 발생되므로 체이닝을 통해 연결시키는 것을 확인

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%8E%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%B5%E1%86%BC_%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%E1%84%85%E1%85%B5%E1%84%89%E1%85%B3%E1%84%90%E1%85%B3.png?raw=true)

```python
# 체이닝을 예시코드로 배워보자.
# 아래와 같이 리스트안에 중첩되는 리스트를 만들어서 연결개념으로 해시테이블을 생성한다.
chain_hash_table = [[] for _ in range(10)]  # 이번에는 10의 길이로 테스트를 진행한다.(0~9, 총 10개의 인덱스)
print(chain_hash_table)


# 해시함수는 위와 동일하게 테스트할 수 있다.
def chain_hash_func(key):
    return key % len(chain_hash_table)
 
print(chain_hash_func(10)) 
print(chain_hash_func(20)) 
print(chain_hash_func(25)) 


# append를 활용해서 키-값 쌍을 해시테이블에 삽입한다.
def chain_insert_func(chain_hash_table, key, value):
    hash_key = chain_hash_func(key)
    chain_hash_table[hash_key].extend(value)
    
chain_insert_func(chain_hash_table, 10, 'A')
print (chain_hash_table)

chain_insert_func(chain_hash_table, 25, 'B')    # 5번째 인덱스에 B가 삽입된다.
print (chain_hash_table)

# 아래 결과값과 같이 중첩되는 결과값이 있더라도 값이 대체(충돌)되는 것이 아니다.
# 리스트 메소드 개념(list.append)이 활용되어 값을 이어 붙인다.('A' -> 'C')
chain_insert_func(chain_hash_table, 20, 'C')    
print (chain_hash_table)
```

#### 충돌 방지 방법 - open addressing(오픈어드레싱)

- 하나의 bucket에 하나의 entry만 들어갈 수 있는 형태로 **다른 로직의 함수를 활용하기 때문에 open address**라 한다.
<br>

   - **비어있는 배열 슬롯이 발견될 때까지 array의 위치를 검색하여 해시 충돌을 해결**
<br>

   - 충돌이 일어나는 경우, **탐사(Probing)를 진행하면서 빈 공간을 찾아야 해결**
<br>
       
      - 체이닝과 다르게 **저장공간**이 정해져 있다.

###### 파이썬과 해시테이블

- 해시테이블로 구현된 파이썬의 자료형은 **딕셔너리**
<br>

- 해시테이블 충돌 시
<br>

   - **체이닝의 경우 연결리스트를 활용**하고, **오픈어드레싱은 내부적으로 공간이 어느정도 정해진 배열을 활용**하여 설계
<br>

   - **파이썬의 경우, 내부적으로 오픈어드레싱 방식을 활용**

   - 파이썬에서 오픈어드레싱을 활용하는 경우 빈 공간이 없는 경우 시간이 오래 걸릴 수 있다.

      - 때문에 **로드팩터를 작게 설정하여 성능저하 문제를 해결**

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%92%E1%85%A2%E1%84%89%E1%85%B5.png?raw=true)


**Load Factor(로드 팩터)**

![image](https://tk-assets.lambdaschool.com/59d00218-52e2-4f3d-9680-2b2d8baad3ae_S5-M3-O1LoadFactor.001.jpeg)

- 해시테이블에 저장된 항목 수(해시테이블에 입력된 키 갯수)를 슬롯 수(해시 테이블 전체 인덱스 갯수)로 나눈 값
<br>

   - 오픈어드레싱을 사용하면 최대 로드팩터는 1정도
<br>

   - **체이닝**을 사용하면 **로드팩터는 오픈어드레싱보다 좋은 성능(로드팩터 <=1>)**을 보일 수 있다. 
<br>

      - **로드팩터를 낮추면 해시에 대한 성능이 올라간다.**
<br>

- 로드 팩터 비율에 따라 **해시함수 재작성여부, 해시테이블 크기조정여부**가 결정
<br>

   - 로트팩터값을 통해 해시테이블의 성능정도 파악 가능
<br>

##### 해시테이블 실생활 사례

해시테이블은 무언가를 찾을 수 있도록 **한 사물에서 다른 사물로 매핑**해야하는 경우에 적합

- 전화 번호부 (사람의 이름을 전화 번호에 매핑)

- DNS 확인 (웹 주소를 IP 주소에 매핑)

- 학생 기록 (고유한 학생 ID가 학생 정보에 매핑)

- 도서관 시스템 (책의 고유 식별자가 자세한 책 정보에 매핑)
<br>

##### 좋은 해시함수란?

- 키와 값의 계산과정이 쉬워야 한다.(위에서 설명한 나누기방법처럼 쉬워야 한다.)<br>
 
- 충돌을 피할 수 있어야한다.<br>
 
  - 계산과정이 쉬운 경우<br>

  - 체이닝(연결리스트)이 제대로 활용된다면 **반복작업없이 해시의 검색 알고리즘을 활용하여 O(1)의 검색시간**을 확보<br>

  - 해시값은 **해시되는 데이터**에 의해 완전히 결정<br>

      - **해시함수는 모든 입력 데이터를 사용**<br>

  - 충돌을 피할 수 있는 경우<br>

    - 해시함수는 가능한 해시값의 전체 집합에 데이터를 **균일하게 배포**<br>

       - 해시함수는 유사한 문자열에 대해 **다흔 해시값을 생성**

- 해시 사용시 주의점<br>

   - 키 데이터타입에 맞는 **좋은 해시함수**가 있는지 확인<br>

   - 적절한 **해시테이블 크기(배열크기)**


### Review

---

**오늘 배운 것**

```
1) 해시관련 기본내용
2) 해시테이블을 활용하는 경우 발생하는 상황
```

**오늘 해야할 것**

```
1) 해시관련 질문에 대해 조사하며 이해한다.
  - 해시테이블은 어떻게 작동될까? 
  - 해시함수란 무엇인가? 
  - 해시충돌이란 무엇이며 어떻게 처리될까? 
  - 해시테이블이 가득 차면 어떻게 해야할까?
2) 파이썬으로 구현될 수 있는 해시관련 소스코드 이해한다.
```

### Reference

---

- [해시테이블의 기본특징](http://wiki.hash.kr/index.php/%ED%95%B4%EC%8B%9C%ED%85%8C%EC%9D%B4%EB%B8%94)

- [Basics of Hash Tables](https://www.hackerearth.com/practice/data-structures/hash-tables/basics-of-hash-tables/tutorial/)


