# 알고리즘(Algorithm)

---
- 키워드 : 분할정복과 재귀 / 퀵정렬과 병합정렬


- [다양한 알고리즘을 모두 알아야할까?](https://youtu.be/_eroIZisOCA)

- [stable sort 및 필수 스킬](https://youtu.be/igAj3kmhgMA)

---

## 분할정복을 활용한 알고리즘

### 분할정복(Divide and Conquer)방법

---

- 복잡하거나 큰 문제를 여러 개로 나눠서 푸는 방법

   - 특징: 병렬적으로 무네를 해결할 수 있다.
          하지만, 문제를 해결하기 위해 **문제해결함수가 재귀적으로 호출**될 수 있으므로 메모리가 추가적으로 사용될 수 있다.

###### 재귀호출과 분할정복의 차이

- 재귀호출은 **같은 함수코드를 재호출**(같은 함수코드 사용)

- 분할정복은 **비슷한 작업을 재진행**(같은 함수코드는 아닐 수 있음)

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%87%E1%85%AE%E1%86%AB%E1%84%92%E1%85%A1%E1%86%AF%E1%84%8C%E1%85%A5%E1%86%BC%E1%84%87%E1%85%A9%E1%86%A8.png?raw=true)

- 분할정복은 **비슷한 크기로 문제를 분할**하고, 해결된 문제를 제외하고 동일한 크기로 문제를 다시 분할한다. 

```python
# 주어진 숫자에 대해서 덧셈을 실행하는 경우(문제에 따라 분할하는 정도가 다를 수 있다.)
[1, 2, 3, 4, 5]

# step 1
sum([1,2,3,4,5]) = sum([1]) + sum([2,3,4,5])     # Divide

# step 2 
sum([2,3,4,5]) = sum([2]) + sum([3,4,5])         # Divide

# step 3 
sum([3,4,5]) = sum([3]) + sum([4,5])             # Divide

# step 4
sum([4,5]) = sum([4]) + sum([5])                 # Divide

# step 5
sum([5]) = 5                                     # Conquer

-> 서브문제 sum([5])에 대한 답이 나왔고, 나머지 서브문제 sum([4]), sum([3]) 등에 대한 문제들도 Conquer를 진행
-> 개별적으로 Conquer 후 Merge 
```

- Divide: step1 -> step5 순으로 진행

- Conquer: step5까지 conquer된 것을 기반으로 **Conquer and Merge 진행

```python
# 분할정복 의사코드
함수 f(x):
  if f(x) is simple then : # base case
    return f(x) 계산된 값 # Conquer ==> result

  else:
    x를 x1, x2로 분할   
    call f(x1), f(x2) # Divide
    return f(x1), f(x2)로 f(x)를 구한 값    # combine => conquer & merger
```

- 분할정복의 과정

   - 문제를 서브문제로 분할(divide)

   - 서브문제의 답을 구한 경우, 해당 답을 본 문제에 대한 답이 되도록 병합(Merge)

   - 문제를 분할 할 수 없거나, 할 필요없는 경우에 대한 답을 구함(base case, 기본케이스)

- 분할정복의 조건

   - (Divide)문제를 서브문제로 분할 가능한가?

   - (Merge, Conquer)서브문제의 답을 병합하여 문제이 답을 구하는 것이 효율적인가?

```python
# 재귀 : 1부터 10까지의 합

def func(num):
  if num < 1:
    return 0
  else:
    return num + func(num-1)

func(10)

# 분할정복 : 1부터 10까지의 합

def func(num):
  if num == 1:
      return 1
  if num % 2 == 1:
      return func(num - 1) + num
  else:
      return func(num / 2) * 2 + (num / 2) * (num / 2) 

func(10)
```

### 퀵정렬과 병합정렬(Quick Sort and Merge Sort)

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdHM5Ug%2FbtqEepz8KMW%2FfqWWDOChxUnm9IiOiwsfQ1%2Fimg.png)

- 일반적으로 퀵정렬 시간복잡도가 병합정렬보다 크다.(둘다 nlogn)

#### 퀵정렬(Quick Sort)

- **전체 탐색을 할 때, 좌우로 나눠서 재귀적으로 수행**하기 때문에 병합정렬보다 빠르다

- 한정적인 범위에서 데이터를 정렬하기 때문에 캐시를 덜 활용하고, 하드웨어적으로 효율적

   - 퀵정렬은 분할정복을 통해 정렬하고, **피벗이라는 별도의 노드를 지정해두고 재귀적으로 수행**하기 때문에 더 빠르다.

   - 하지만 성능이 우수함에도 **성능편차가 크고, 피벗(노드)설정 등 다루기 어려운 점**이 존재하여 실무에서는 활용되기 어렵다.

1) 퀵정렬 최선의 경우

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%8F%E1%85%B1%E1%86%A8%E1%84%89%E1%85%A9%E1%84%90%E1%85%B3_%E1%84%8E%E1%85%AC%E1%84%89%E1%85%A5%E1%86%AB.png?raw=true)

2) 퀵정렬 최악의 경우

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%8F%E1%85%B1%E1%86%A8%E1%84%89%E1%85%A9%E1%84%90%E1%85%B3_%E1%84%8E%E1%85%AC%E1%84%8B%E1%85%A1%E1%86%A8%E1%84%8F%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%89%E1%85%B3.png?raw=true)

- 퀵정렬은 불안정 정렬의 대표적인 겨웅로, 노드의 값이 중복되는 경우에는 **계속해서 교환(swap)을 시도**한다. 

- 퀵정렬은 최악의 경우, 첫번째 노드를 피벗으로 설정하고 **불균형하게 분할정복을 시도**하여 성능이 안 좋아진다.

   - 속도는 알고리즘을 처리하고 결과를 도출하는 속도(주로 소프트웨어에 영향을 주고 받음)

   - 성능은 메모리에 영향을 주는 정도(주로 하드웨어에 영향을 주고 받음)

```python
# 퀵소트 기능을 하는 부분의 의사코드

quick_sort(node, first, last)

if first < last then
    pivot := partition(node, first, last) # 피벗에 따라 양 옆으로 나누고
    quick_sort(node, first, pivot-1)      # 첫번째 재귀호출을 한다.
    quick_sort(node, pivot+1, last)       # 두번째 재귀호출을 한다.

    # 퀵소트도 재귀호출을 여러번 하는 분할 정복 구조를 갖고 있다.
"""
위의 의사코드는 퀵정렬의 메인함수 부터 시작

- 파티션(영역)을 나눈다
- 정해진 피벗을 중심으로 양옆으로 영역을 나눈다
- 나눠진 영역을 중심으로 재귀호출을 진행하는 분할벙복구조를 갖고 있다.
"""

# 퀵소트 파이썬 부분코드
def quick_sort(node, first, last):
  ...
  if first < last:
    pivot = partition(first, last)

    quick_sort(node, first, pivot - 1)
    quick_sort(node, pivot + 1, last)


# 파티션을 나누는 의사코드
partition(node, first, last)

  pivot = node[last]
  i = first

  for j = first to last 
    if node[j] < pivot then
      swap node[i] <-> node [j]
      i = i + 1
  swap node[i] <-> node[last]
  return i


# 퀵소트 파이썬 코드 case - 1 : partition부분
# 계속 분할하면서 정복 진행
def partition(first, last):

  pivot = node[last]
  left = first

  for right in range(first, last):
    if node[right] < pivot:
      node[left], node[right] = node[right], node[left]
      left += 1
  node[left], node[last] = node[last], node [left]
  
  return left


# 퀵소트 파이썬 코드 case - 1 : 전체코드
def quick_sort(node, first, last):
  def partition(first,last):
    pivot = node[last]
    left = first
    #print(pivot, first,last)    # 확인용
    for right in range(first, last):
      if node[right] < pivot:
        node[left], node[right] = node[right], node[left]
        left += 1
    node[left], node[last] = node[last], node[left]
    return left

  # 첫번째 노드가 마지막 노드보다 작은 경우, 재귀진행
  if first < last:
    pivot = partition(first, last)
    quick_sort(node, first, pivot - 1)
    quick_sort(node, pivot + 1, last)


node = [54,26,93,17,77,31,44,55,20]
quick_sort(node,0,8)

print(node)


# 퀵소트 파이썬 코드 case - 2 : 전체코드
def quick_sort(ARRAY):
    ARRAY_LENGTH = len(ARRAY)
    if( ARRAY_LENGTH <= 1):
        return ARRAY
    else:
        PIVOT = ARRAY[0]
        GREATER = [ element for element in ARRAY[1:] if element > PIVOT ]
        LESSER = [ element for element in ARRAY[1:] if element <= PIVOT ]
        return quick_sort(LESSER) + [PIVOT] + quick_sort(GREATER)

ARRAY = [54,26,93,17,77,31,44,55,20]
print(quick_sort(ARRAY))
```

#### 병합정렬(Merge Sort)

- 병합정렬은 분할정복(divide and conquer)로직으로 인해, 전체 데이터를 기준으로 **처음과 끝을 계속해서 탐색**하기 때문에 퀵정렬에 비해 느리다.

- 병합정렬이 활용되는 이유는 퀵정렬보다 빠르지는 않지만, 안정(stable)정렬이기 때문에 **데이터가 중복되었더라도 영향을 덜 받는다.**

![image](https://www.101computing.net/wp/wp-content/uploads/Merge-Sort-Algorithm.png)

- 병합정렬은 분할과 교체를 반복.

- 병합정렬은 일단 시간을 들여서 1개의 서브리스트가 나올때까지 분할을 진행.

   - 이후 배열값을 반복문을 통해 **비교 -> 정렬 -> 교환** 후 합치는 과정을 연속적으로 진행

```python
# MergeSort 소스코드

def mergeSort(arr): 
    if len(arr) >1: 
        mid = len(arr)//2       # 1)배열의 중간을 찾는다.

        L = arr[:mid]           # 중간이 정해지면, 전체배열을 두 부분으로 나눈다. L은 나눠진 왼쪽 부분
        R = arr[mid:]           # R은 나눠진 오른쪽 부분

        mergeSort(L)            # 2)왼쪽 부분에 대해 정렬 함수 호출을 통해 정렬(재귀적으로 값을 분할정복)
        
        mergeSort(R)            # 3)오른쪽 부분에 대해 정렬함수 호출을 통해 정렬(재귀적으로 값을 분할정복)
        
        i = j = k = 0
          
        # Merge 정렬 과정(배열의 인덱스를 참조하여 비교->정렬->교환한다는 것을 알아야 한다.)
        while i < len(L) and j < len(R):  
            if L[i] < R[j]:     # 오른쪽값 > 왼쪽값
                arr[k] = L[i]   # 왼쪽값을 결과를 위한 값에 저장한다.
                i+= 1           # 왼쪽배열값의 인덱스를 +1 증가시키고, 결과를 위한 배열에 저장한다.
            else:               # 왼쪽값 > 오른쪽값
                arr[k] = R[j]   # 오른쪽값을 결과를 위한 값에 저장한다.
                j+= 1           # 오른쪽배열값의 인덱스를 +1 증가시키고, 결과를 위한 배열에 저장한다.
            k+= 1

  
        
        #왼쪽부분과 오른쪽부분에 대해 중간정렬결과를 확인해볼 수 있다.
        #print(L)
        #print(R)

        # 왼쪽에 남은 요소가 있는지 확인
        while i < len(L):     
            arr[k] = L[i]       # 정렬된 왼쪽값을 결과를 위한 배열에 저장
            i+= 1
            k+= 1
        
        # 오른쪽에 남은 요소가 있는지 확인
        while j < len(R):     
            arr[k] = R[j]       # 정렬된 오른쪽값을 결과를 위한 배열에 저장 
            j+= 1
            k+= 1

        
# 정렬된 결과 출력
def printList(arr): 
    for i in range(len(arr)):         
        print(arr[i], end =" ") 
    print() 
  
# 위의 정렬 알고리즘을 테스트하기 위한 테스트 코드
arr = [7,3,2,16,24,4,11,9]  
print ("정렬되기 전 테스트 배열", end ="\n")  
printList(arr) 

# 병합정렬 알고리즘을 적용하기 위해 처음으로 병합정렬 함수를 호출한다.
mergeSort(arr) 

print("병합정렬로 정렬된 결과 배열: ", end ="\n") 
printList(arr) 
  
# 참고자료1 : https://www.geeksforgeeks.org/merge-sort/
# 참고자료2 : https://www.101computing.net/merge-sort-algorithm/

```

### Review

---

**오늘 배운 것**

```
1) 재귀와 분할 정복
2) 문제해결을 위한 고려사항
```

**오늘 해야할 것**

```
1) 재귀와 분할 정복에 대해 익숙해지기
2) 현재까지 배운 자료구조와 알고리즘 기본정리
3) 문제해결을 위한 고려사항에 대해 인지하기
```

### Reference

---

- [자료구조의 필요성과 핵심원리](https://book.naver.com/bookdb/book_detail.nhn?bid=20847102)

- [다양한 알고리즘](https://en.wikipedia.org/wiki/Sorting_algorithm)

- [퀵정렬(Quick Sort)](https://ratsgo.github.io/data%20structure&algorithm/2017/09/28/quicksort/)

- [알고리즘. 분할정복](https://ohdowon064.tistory.com/197)

