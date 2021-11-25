# 자료구조의 활용

---
- 

- 
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

- 특정 노드를 추가하거나 삭제를 위해서는 검색이 우선
<br>

- 다양한 **알고리즘을 활용**하는 경우, 최적 알고리즘 경로를 측정하는데 쓰인다.
<br>

- 검색 알고리즘은 배열이 정렬되지 않은 경우 **순차 검색(sequential search)**

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

- 재귀함수 : 자기 자신을 다시 호출하는 함수

- 재귀의 개념은 수학적 사고에 기반하고, 코드를 작성하기 전에 문제를 해결하는 재호출 로직을 발견해야한다.

- 재귀 호출은 스택의 개념이 적용되며, 함수의 내부는 스택처럼 관리된다.(LIFO, 후입선출)

   - 단점 : 재귀를 사용하면 **함수를 반복적으로 호출**되는 상황이 벌어지므로, 메모리를 더 많이 사용한다. 

- 재귀로 문제 해결
  
    ->