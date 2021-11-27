# Data Structure(자료구조)

---

- [자료구조를 알아야 하는 이유](https://youtu.be/OH7prOt3vQA)

- [무조건 알아야하는 자료구조/ADT](https://youtu.be/Nk_dGScimz8)

---

## 알고리즘과 자동화

### 알고리즘의 다양성

---

- 정렬: 쉽게 말해 숫자 두개의 크기를 비교하고 바꿔주는 작업을 **반복하여 조건에 맞게 순서를 맞춰주는 작업**
 
   - 정렬을 구성하는 논리적인 개념은 **모든 알고리즘의 기반

- 자료구조와 알고리즙의 연관성은 배우는데, 구구단을 외우는 것과 유사한 맥락대로 익힌다.(예, 숫자와 곱셈의 개념을 알아야 구구단을 **빠르고 쉽게 수행**할 수 있다.)

   - 자료구조는 숫자이고, 알고리즘은 곱셈이다.

   - 즉 자료구조는 기반이 되는 개념이고, 알고리즘은 방법이다. 

```python
# 인트로 코딩

intro_list=[]     # 리스트 생성
for div_number in range(2000, 3201):    # 반복문
    if (div_number%7==0) and (div_number%5!=0): # 조건문, and 조건
        intro_list.append(str(div_number))      # 리스트 메소드 append 사용, 파이썬 내장함수 str 사용

print(','.join(intro_list))   # 리스트 메소드 join 사용
```

```python
# 입력된 소문자알파벳의 위치를 찾아보자.

character = input()
for i in range(26):   # 알파벳갯수만큼 반복
  word = character.find(chr(i+97))  # chr 메소드 사용
  #replace_word = word.replace('-1', 'F')

  print(word, end = " ")   # 아스키코드가 97~122(a~z)인 경우, 영어소문자단어를 나타냄
```

- 프로그래밍에서 다양한 입력에 대한 예외처리를 진행하는 경우 코드가 복잡해지거나 일관성이 떨어질 수 있다.

- 파이썬에서는 문자열관련 메소드를 제공한다.

- 해당 메소드와 조건문을 함께 활용하면 로직과 코드의 복잡도를 낮출 수 있다. 

   - 문자열 메소드 참고: [문자열 메서드 표준 설명](https://docs.python.org/ko/3/library/stdtypes.html?highlight=endswith#string-methods)

```python
# 다음 예시를 통해 문자열처리 메소드의 효율성을 알아보자.

# strip 메소드는 문자의 앞뒤공백을 제거해준다.
# split 메소드는 문자열을 특정기준을 통해 리스트형태로 나눠준다.

stringtest_strip_split = input().strip().split(' ')
if stringtest_strip_split[0] == '':
  print(0)
else:
  print(len(stringtest_strip_split))
```

### 교환(SWAP)

---

SWAP알고리즘은 말 그대로 두 변수에 있는 수를 교환하는 방법.

![image](https://codetorial.net/tips_and_examples/_images/variable_swap_00.png)

```python
# 첫번째 방법
a = 3
b = 1

temp = a
a = b
b = temp

print(a,b)

# 두번째 방법
a = 3
b = 1

a, b = b, a # 파이썬에서는 한 줄로 변경가능

print(a,b)
```

## 탐색 알고리즘 기본(Search Algorithm Basic)

### 선형 및 이진검색

---

- 선형 검색(liner search)
<br>

   - 선형 검색은 기본적인 검색 알고리즘으로 **한번에 하나씩 모두 검색**하는 것
<br>
   - 아래 소스코드처럼 반복문을 활용해 배열의 변수*코드에서는 반복자 i)만큼 검색을 진행.

![image](https://github.com/Maiven/data-science/blob/main/linearSearch.png?raw=true) 

```python
def linear_search(linear_arr, search_number):
    for i in range(len(linear_arr)):
      if linear_arr[i] == search_number:
        return i

linear_arr = [5,22,87,1,3]
search_number = 1
print("search index : ",linear_search(linear_arr, search_number))
```

- 이진 검색(Binary search)
<br>

   - **반복을 통해 숫자를 반으로 줄이면서** 검색을 진행하기 때문에 선형보다 속도가 빠름

   - 이진 검색 방법은 데이터가 **이미 정렬된 경우**에만 작동

      - 프로그래밍에서 로그에 대해 이야기를 할 때 항상 log2()를 의미, 그 이유는 컴퓨터가 **2진수 시스템**에서 작동하기 때문

- 리스트를 처음 얻을 때 두개의 다른 리스트(참조요소)를 설정해야 한다,

   - low는 리스트의 첫번째 항목

   - high는 리스트의 목록의 마지막 항목

```python
def binary_search(test_list):
  
    low = 0
    high = len(test_list) - 1


def binary_search(test_list):
  
    low = 0   # 인덱스가 0(리스트의 첫번째 항목)으로 주어진다.
    high = len(test_list) - 1   # 인덱스의 마지막 항목(리스트길이-1)

    while low <= high:
        middle = (low + high) // 2
        guess = test_list[middle]
```

![iamge](https://github.com/Maiven/data-science/blob/main/binarySearch1.png?raw=true)


- 조건에 따라 값 **비교하며 검색**

![image](https://github.com/Maiven/data-science/blob/main/binarySearch2.png?raw=true)

```python
def binary_search(test_list, search_item):

     low = 0
     high = len(test_list) - 1

     while low <= high:
         middle = (low + high) // 2   # middle을 지정해서 검색속도를 빠르게 한다.
         guess = test_list[middle]

         if guess == search_item:
             return middle
         if guess > search_item:
             high = middle - 1
         else:
             low = middle + 1
     return None

test_list = [6,12,17,23,38,45,77,84]   # 이미 정렬된 리스트에서 검색 진행
print('binary_search',binary_search(test_list, 12))
```

![image](https://github.com/Maiven/data-science/blob/main/binarySearch3.png?raw=true)

**이진검색을 통해 보는 알고리즘 원리**

- 알고리즘을 활용하는데 있어서 기본적으로 **상수계산**부터 시작된다.

- 상수계산은 쉽지만 복잡한 계산을 하기에는 반복을 만이 해야되므로 **시간과 메모리**를 많이 소비

   - 떄문에 **반복문과 조건문, 연산자** 등을 활용하여 효율적 알고리즘이 생성된다.

- 이진검색도 **정렬된 선형의 숫자들** 중 특정 숫자를 효율적으로 검색하기 위해 나온 방법

   - 즉, 모든 알고리즘의 기본원리는 숫자와 조건을 활용하면서 발전시킨다고 생각해야한다.

## 반복정렬(Iterative Sorting)

### 선택정렬(Selection Sort)

![image](https://github.com/Maiven/data-science/blob/main/selectionsort.png?raw=true)

1. 먼저 **가장 작은 노드(노드13)를 선택

2. **왼쪽부터 가장 작은 노드와 비교하면서 교환** 시작

3. 교환을 한번 하고 나면, 교환된 노드를 제외한 나머지 노드들(배열)을 기준으로 하여 가장 작은 노드를 다시 선택하고, 위의 작업을 **반복**

![image](https://github.com/Maiven/data-science/blob/main/selection_sort2.png?raw=true)

**선택정렬: 최소노드 선택 > 왼쪽부터 비교 > 교환**

###### 복잡도분석(Complexity Analysis)

- **서로 이웃하지 않은 노드르라 교환**하므로, 안정적이지 않다. 
<br>

-  데이터의 개수가 n개라고 했을 때,
    첫 회전에서의 비교횟수 : 1 ~ n-1 => n-1
    두번째 회전에서의 비교횟수 : 2 ~ n-2 => n-2
                  .
                  .
                  .
    (n-1) + (n-2) + .... + 2 + 1 => n(n-1)/2

    즉, 간단히 말해 비교하는 것이 상수시간에 이루어진다는 가정아래, n개의 주어진 리스트를 이와 같은 방법으로 정렬하는 데에는 O(N^2)만큼의 시간이 걸린다. 

```python
# 예시 리스트
our_numbers = [5,9,3,6,2,1,7,8,4]

# 선택정렬 소스코드

def selection_sort(items):
    
>>    for i in range(0, len(items) - 1):    # 외부 반복문(루프)

        cur_index = i
        smallest_index = cur_index
        
>>        for j in range(cur_index + 1, len(items)):  # 내부루프
>>               # 최소값찾는 로직
                smallest_index = j

        # 로직에 따라 최소값을 찾고, 교환을 위한 작업을 아래와 같이 수행한다.
        # items[smallest_index]와 items[cur_index] 값을 Swap(교환) 한다.

        # 첫번째 swap 방법
        # temp = items[smallest_index]
        # items[smallest_index] = items[cur_index]
        # items[cur_index]= temp 

        # 두번째 swap 방법
>>        items[smallest_index], items[cur_index] = items[cur_index], items[smallest_index]
 
    return items

# 정렬된 결과값 출력
print(selection_sort(our_numbers))
```
### 삽입정렬(Insertion Sort)

- 자료배열의 모든 요소를 앞에서부터 차례대로 **이미 정렬된 배열 부분과 비교**하여, 자신의 위치를 찾아 삽입함으로써 정렬을 완성하는 알고리즘

   - 선택정렬과 비슷하지만, 값이 가장 작은 원소를 선택하지 않는다.

   - 삽입정렬은 비교 후, 삽입을 동시에 진행한다

   - 삽입정렬은 **소량의 데이터**를 정렬하기 위한 효율적인 알고리즘

      - 선택과 버블정렬과 달리, 삽입정렬은 정렬을 진행하면서 비교 및 탐색해야할 정렬 범위가 넓어진다.

![image](https://runestone.academy/runestone/books/published/pythonds/_images/insertionpass.png)

1. 노드31에 대해 이미 정렬된 배열과 비교

2. 노드31보다 **작은 값을 갖고 있는 노드가 나올때까지 비교**

3. 최종적으로 31보다 작은 26을 발견했고, **노드26 오른쪽 인덱스에 노드31을 삽입**

4. 위의 비교 및 삽입과정을 44,55,20에 대해서도 진행

###### 복잡도 분석

- 최악의(역으로 정렬되어 있는) 경우 선택정렬과 마찬가지로, (n-1) + (n-2) + .... + 2 + 1 => n(n-1)/2
   즉, O(N^2)이 된다.

-  Optimal한(모두 정렬이 되어있는) 경우 한번씩 밖에 비교를 안하므로 O(n) 의 시간복잡도

- 또한 이미 정렬되어 있는 자료구조게 자료를 하나씩 삽입/제거하는 경우에는 현실적으로 최고의 정렬 알고리즘이 된다.
   
   -> 탐색을 제외한 오버헤드가 매우 적기 때문

- 선택정렬이나 거품정렬과 같은 O(N^2) 알고리즘에 비교하여 **빠르다**

```python
# 삽입정렬 소스코드

def ins_sort(unsort_list):

    loop_number = len(unsort_list)          # 반복횟수를 위한 길이설정

    # 앞쪽에 있는 노드들을 검색하기 위한 반복문
>>    for compare_index in range(loop_number):    # 비교하려는 위치부터 loop_number만큼 반복
        compare_value = unsort_list[compare_index]  
>>        prev_position = compare_index - 1   # 이전 노드값에 대한 인덱스를 가리킴
        
        # 비교연산 후 삽입을 진행하는 반복문
>>        while prev_position >= 0 and unsort_list[prev_position] > compare_value:    
>>              # 1-1차작업 : swap을 위한 작업
            prev_position = prev_position - 1
>>             # 1-2차작업 : 비교된 더 큰 값을 (이전노드+1) 인덱스에 삽입

    return unsort_list
            
test_arr = [5,3,1,6]
ins_sort(test_arr)
```

### 버블정렬(Bubble Sort)

- **서로 이웃한 두 원소의 크기를 비교한 결과에 따라 교환을 반복**하는 알고리즘(단순교환 정렬이라고도 함)

- 버블 정렬은 가장 간단한 정렬 알고리즘 중 하나이며, 매우 비효율적

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%87%E1%85%A5%E1%84%87%E1%85%B3%E1%86%AF%E1%84%8C%E1%85%A5%E1%86%BC%E1%84%85%E1%85%A7%E1%86%AF.png?raw=true)

1. 컬렉션의 첫 번째 항목과 두번째 항목을 비교한다. 
   
   -> 첫 번째 항목이 두 번째 항목보다 크면 항목을 교체
2. 다음 두 번째 항목과 세번째 항목을 비교, 두 번째 항목이 세 번째 항목보다 크면 항목을 교체

3. 오름차순 목록으로 정렬될 때까지 모든 항목에 대해 위의 작업을 반복수행 

###### 복잡도

- 목록이 이미 정렬되어 있어도 목록의 모든 항목을 검사해야한다.

- 배열 전체를 쭉 살펴보는 과정을 무조건 n번하기 때문에, (n-1) + (n-2) + .... + 2 + 1 => n(n-1)/2
   즉 O(n2)이다.

- 버블정렬은 한번이ㅡ 순회를 마칠 때 마다 **비교대상이 하나씩 줄어든다**
  
   -> 한 회전이 끝나면 배열안에서 가장 큰 값이 맨 뒤로 가기 때문!

- 버블정렬은 옆에 있는 **이웃노드만 교환하므로 안정적**이다.

```python
# 버블정렬 소스코드
def bubble_sort(li):
    length = len(li) - 1
>>         # 외부 반복문(아래 그림에서 전체 리스트에 대해 정렬이 완료되었는지 검사하고 패스해줌)
>>          # 내부 반복문(아래 그림에서 하나의 리스트의 개별 값을 비교하고 교체시킨다)
>>            # 현재 인덱스의 값과 다음 인덱스의 값 비교
>>                # 비교한 것에 따라 정렬을 위한 인덱스 교환 작업

li = [10, 2, 1, 7, 4, 3, 0]
bubble_sort(li)
print(li)
```

### Review

---

##### 오늘 배운 것

```
1) 기본 프로그래밍 방법으로 문제해결하기
2) 기본적인 반복정렬 알고리즘
```

##### 오늘 해야할 것

```
1) 파이썬 코드로 문제를 해결하는데 익숙해지기
2) 반복문과 조건문의 다양한 활용
```

### Reference

---

- [문자열 메소드 참고](https://docs.python.org/ko/3/library/stdtypes.html?highlight=endswith#string-methods)

- [Python에서 시간측정하기](https://jeongukjae.github.io/posts/python%EC%97%90%EC%84%9C-%EC%8B%9C%EA%B0%84%EC%B8%A1%EC%A0%95%ED%95%98%EA%B8%B0/)

- [정렬(Sort) 알고리즘 정리노트
](https://deepinsight.tistory.com/160)

- [정렬 알고리즘 정리](https://zeddios.tistory.com/20)