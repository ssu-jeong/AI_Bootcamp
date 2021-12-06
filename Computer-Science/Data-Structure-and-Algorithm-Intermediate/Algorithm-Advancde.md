# 알고리즘과 문제해결방법

---

- 키워드: Dynamic Programming, Greedy, Algorithm

- [실생활과 알고리즘](https://youtu.be/kM9ASKAni_s)

- [다이나믹 프로그래밍이란?](https://youtu.be/2RwlzBDhGh4)

---

## Dynamic Programming(동적 계획법)

### 개요

---

- 프로그래밍과 **연관지어 생각하고, 완성된 코드를 분석하는 습관**은 중요

- 문제를 해결하기 위해 핵심적으로 다뤄지는 Dynamic Programming과 Greedy

- 자료구조와 알고리즘을 생각해서 연결지어 학습

- 기초적인 수학공식을 순서에 적합하도록 소스코드를 분석

### Dynamic Programming(동적 계획법)

---

동적 계획법(동적 알고리즘, 동적 프로그래밍, 다이나믹 프로그래밍 등)은 보편적으로 **'문제의 일부분을 풀고 그 결과를 재활용하는 방법**을 의미

   - 하나의 문제를 **중복되는 서브문제로 나누어 푸는**방식

   - 분할정복(Divide and Conquer)과 유사한 개념

   - DP를 사용하게 되는 상황: 이진검색, 최단경로 알고리즘, 최적화문제, 외판원문제
     
      - 참고: [그래프문제의 다양한 케이스](https://ko.wikipedia.org/wiki/%EC%99%B8%ED%8C%90%EC%9B%90_%EB%AC%B8%EC%A0%9C)

   - DP와 분할정복의 차이점

      - DP는 문제를 분할하는 경우 **중복되는 서브문제가 있고**, 분할정복은 분할된 서브문제가 **독립적**

      - DP는 서브문제가 같은 경우에 **메모이제이션을 활용**하여 같은 문제에 대해 해결할 수 있고, 분할정복은 서브문제가 다르기 때문에 메모이제이션을 활용하지 않음

      - DP를 활용하면 해결할 수 있는 문제의 범위가 넓어짐

      ![image](https://media.geeksforgeeks.org/wp-content/uploads/01-DP-vs-DC-DP-vs-DC-diagram-1024x492.png)

    - DP는 분할정복에 아래 개념이 추가

       - 중복된(반복되는) 서브문제(Overlapping Subproblems)

          - 메인과 서브문제를 **같은방법(반복)으로 해결**할 수 있어야함(문제 해결관점)

       - 최적부분 구조(Optimal Substructure)

          - 메인문제 해결방법을 **서브문제에서 구하여 재사용하는 구조**여야 한다.(문제 구조관점)

        -> DP는 최적부분 구조로 구성된 중복된 서브문제를 분할정복으로 해결!!

   - DP의 방법론

      - 메모이제이션(하향식방법): 메인문제를 문할하면서 해결 하는 방법

      - 태뷸레이션(상향식방법): 가장 작은 문제를 먼저 해결하고 최종적으로 메일문제를 해결하는 법

         - 참고: [DP개념](https://namu.wiki/w/%EB%8F%99%EC%A0%81%20%EA%B3%84%ED%9A%8D%EB%B2%95?from=%EB%8F%99%EC%A0%81%EA%B3%84%ED%9A%8D%EB%B2%95)


#### DP와 분할정복

![image](https://github.com/Maiven/data-science/blob/main/DP_DC.png?raw=true)

1) DP

   - 그림과 같이 40명에 대해서 서브문제 1-1(10명), 서브문제 1-1(10명), 서브문제 1-2(20명)로 Divide

   - 서브문제1-1(10명), 서브문제1-1(10명), 서브문제1-2(20명)에 대해 Conquer

   - 20명에 대해 추가적인 서브문제2-1(10명), 서브문제2-1(10명)로 Divide

   - 중복된 서브문제2-1(10명)에 대해서는 이미 Conquer했던 서브문제1-1(10명)의 계산을 저장(메모이제이션)했다가 재사용하여 전체적인 속도를 향상

   - 설명을 위해서 1-1과 2-1로 나눴지만 결론적으로, 서브문제1-1(10명)과 서브문제2-1(10명)은 같은 문제

   2) 분할정복

      - 분할정복은 DP와는 다르게, 다른 유형의 서브문제로 나뉜다.

#### DP 로직과 소스코드 분석

```python
# 기본적인 반복문과 조건문을 활용한 덧셈
def dp_sum():
  sum = 0
  array = [1,2,3,4,5,6,7,8,9,10]

  for i in array:
    if (array[i-1] + array[10-i]) == 11:     
      sum = (array[i-1] + array[10-i]) * len(array)/2   
  
  return round(sum)   # 소수점 처리를 위해 round 내장함수 사용

dp_sum()

# DP를 활용한 피보나치 수열
# 1) 재귀를 활용하여 주어진 문제해결을 위한 함수 먼저 생성
def dp_fib_cal(num, dp_memo):
      
    if num < 3: 
      return 1
    
    if num in dp_memo:
        return dp_memo[num]
    
    dp_memo[num] =  dp_fib_cal(num - 1, dp_memo) + dp_fib_cal(num - 2, dp_memo) # 재귀
    # 계산된 값들을 dp_memo[num]에 저장해놓는다.
    
    return dp_memo[num]
    
# 2) 메모이제이션 개념을 위한 함수 생성
def dp(num):
    
    dp_memo = {}    # 메모저장을 위한 변수생성

    return dp_fib_cal(num, dp_memo)

# 3) 함수를 호출하면서 문제를 발생시키는 곳이다.
print(dp(6))



# 메모이제이션을 활용하지만 재귀는 활용하지 않는 DP
def fib_not_recur(n):
  arr = [j for j in range(n+1)]   # 메모
  if n < 2:
    return n

  for i in range(2, n+1):         # 반복
    arr[i] = arr[i-1] + arr[i-2]

  return arr[n]

print(fib_not_recur(6))


# 재귀를 활용하는 DP
def fib(n):
  if n < 3:
    return 1
  else:
    return fib(n-1)+fib(n-2)  # 재귀(부분문제 재사용)

fib(6)


# 태뷸레이션을 활용하는 DP
....
  tab = [0, 1]

  for ...           # 재귀가 아닌 for반복문을 활용하여 연산이 빠름
    tab.append...... # 반복하면서 값을 미리 다 구해놓는다.(tab 리스트에 값을 구해놓음)
....
```

![image](https://github.com/Maiven/data-science/blob/main/DP.png?raw=true)

- 그림으로 나타내면 서브문제가 같은 것을 알 수 있다.

- 메모이제이션 개념을 코드에 적용해서 저장된 동일한 값을 재사용 할 수 있다. 

**재귀와 DP코드의 차이점**

``` python
# 재귀(분할정복)로 구현한 코드
# 재귀 + 조건 ==> 분할정복 + 조건 ==> DP + 조건 => 방법론
def fib(n):
  
  if n <= 0: # base case 1 - 재귀의 무한호출을 막는 역할, 값을 재사용하는 역할 
    return 0
  if n <= 1: # base case 2
    return 1
  else: # 재귀

    return fib(n-1) + fib(n-2)

fib(4)


# DP로 구현한 코드
calculated = {}

def fib(n):
  if n == 0: # base case 1
    return 0
  if n == 1: # base case 2
    return 1
  elif n in calculated:
    print("elif calculated :",calculated) # 함수 안에만 활용되는 calculated
    return calculated[n]  # 재귀 전에 DP에서는 결과값을 저장하여 활용한다.
  else: # 재귀 단계
    calculated[n] = fib(n-1) + fib(n-2)
    return calculated[n]

#print("result calculated :",calculated) # 함수 밖에 있는 전역변수로 calculated가 할당됨
print(fib(20))
```

- DP는 이미 계산된 결과들을 이용해서 최종결과값을 계사나는 것

- 모든 DP문제들은 중복되는 서브문제를 갖고 있다.

```python
# DP를 활용한 문제해결
# 문제 : 숫자 2,4,6으로 특정 숫자 N을 덧셈으로 구하는 방법은 몇가지일까?(숫자 중복사용가능)
# 분할정복(divide & conquer)개념을 다시 생각해보자. 

def solve(n):

  # base case
   if n < 0:
      return 0
   if n == 0:
      return 1  
   
   return solve(n-2) + solve(n-4) + solve(n-6)

   # 세부과정
   # 1단계   -> solve(6) divide : solve(4) + solve(2) + solve(0)   ==> 4
   # 1-1단계 -> solve(4) divide : solve(2) + solve(0) + solve(-2)  ==> 2
   # 1-2단계 -> solve(2) divide : solve(0) + solve(-2) + solve(-4) ==> 1

   # 2단계   -> solve(0)       conquer : 1
   # 2-1단계 -> solve(마이너스값) conquer : 0

   # 3단계 -> 위의 1-2단계 conquer(merge) : 2단계해결값(1) + 2-1단계해결값(0) + 2-1단계해결값(0) = 1
   # 4단계 -> 위의 1-1단계 conquer(merge) : 1-2단계해결값(1) + 2단계해결값(1) + 2-1단계해결값(0) = 2
   # 5단계 -> 최종1단계    conquer(merge) : 1-1단계해결값(2) + 1-2단계해결값(1) + 2단계해결값(1) = 4

print(solve(6))
```

- 단계별로 볼 수 있듯이, DP는 단순히 분할정복을 하는 것뿐만 아니라, 중복되는 서브문제가 존재

- 중복문제 결과에 대해서는 다시 계산하지 않고 재사용

```python
# 위의 문제에 대해서 메모이제이션 개념을 적용해보자.
dp = {} # 딕셔너리로 메모이제이션을 위한 변수선언, 왜 딕셔너리일까?

# this function returns the number of 
# arrangements to form 'n' 
def solve(memo_num):

  # base case
  if memo_num < 0:
      return 0
  if memo_num == 0:
      return 1  

  # checking if already calculated
  elif memo_num in dp:
    return dp[memo_num]
 
  # storing the result and returning
  else:
    
    dp[memo_num] = solve(memo_num-2) + solve(memo_num-4) + solve(memo_num-6)
    
    # 딕셔너리 키와 값 단계별 전체확인
    print("dp:",dp,'\n') 

    # 딕셔너리의 키와 값 특정단계만 확인
    print('[key] memo_num :',memo_num,',','[value] solve() 반환값 :',
          solve(memo_num-2) + solve(memo_num-4) + solve(memo_num-6),'\n')

    return dp[memo_num]

print("문제해결값 : ",solve(6))
```

- 메모이제이션 변수를 딕셔너리로 할당

- 메모이제이션을 위해서 dp = {}을 선언했고, dp[memo_num] 값을 활용

   - 즉 key는 재귀되는 solve(memo_num)함수의 파라미터값 memo_num, value는 재귀되는 solve(memo_num)함수에서 반환되는 값

- 딕셔너리에서 []는 키에 매핑되는 값을 할당하거나, 값 자체에 접근할 때 활용

```python
# 딕셔너리 예시
dictionary = {} # 키와 값이 없는 비어있는 딕셔너리 생성
dictionary = {"a": 1, "b": 2} # 딕셔너리에 키와 값 할당

print(dictionary["a"]) # key("a")에 매핑되는 value(1)에 접근할 때 사용

dictionary["c"] = 3 # key("c")에 대한 value(3) 생성
print(dictionary["c"]) # 키에 매핑되는 값에 접근
```

## Greedy

### Greedy(탐욕 알고리즘)

---

DP는 중복되는 서브문제이고, Greedy는 중복되지 않는 서브문제이며, 발견법(heuristic method)의 방법 중 하나

- 발견법: 최선, 최적의 답을 찾기보다도 **주어진 상황을 한단계씩 빠른 시간 내에 해결**하기 위해 사용하는 방법론

   - backtracking(역추적)과 같이 알고리즘 수행시간이 많이 걸릴 때 사용하는 방법

- 탐욕법은 이전의 선택으로 돌아가는 역추적과는 반대개념으로, **다른 문제들과 독립적**

- 탐욕법 사용예시

    1) 여행짐싸기(물건담기):

    - 여행 배낭에 물건을 정해진 시간 내에 담으려는 경우, 우선순위가 높은 순서대로 물건을 담을 때 한번 배낭에 담은 물건은 다시 빼지 않는다.

    2) 여행경로 짜기(도시방문):

    - 도시가 많아질 수록, **도시를 방문(배열)할 수 있는 가짓수가 많아진다.**

    - **알고리즘 연산 비용도 함께 증가**한다. 이러한 상황에서 탐욕 알고리즘을 활용.

      - 1) 방문하지 않은 도시 중 가장 가까운 도시로 간다.

      - 2) 모든 도시를 방문할 때까지 반복한다.

```python
# 탐욕 알고리즘에 대해 의사코드로 이해해보자.
def greedy(items, max_weight):
  bag_weight = 0          # 정해진 가방무게
  bag_items = list()      # 가방에 담을 물건들을 리스트에 담는다.

  for each_item in sort_by_value(items):        # 각각의 물건을 우선순위에 맞게 담기 위한 반복작업
    if max_weight >= bag_weight + item.weight:  # 가방무게가 꽉차기 전까지 물건의 무게와 비교한다.
      bag_weight = bag_weight + item.weight     # 가방에 물건이 담길 때마다 가방의 무게가 찬다.
      bag_items.append(item)                    # 가방에 물건이 담긴다.
  
  return bag_items    # 가방의 물건이 무엇이 담겼는지 확인한다.
```

**탐욕법이 항상 최선일까?** 

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%90%E1%85%A1%E1%86%B7%E1%84%8B%E1%85%AD%E1%86%A8%E1%84%80%E1%85%AA%E1%84%8E%E1%85%AC%E1%84%83%E1%85%A1%E1%86%AB%E1%84%80%E1%85%A7%E1%86%BC%E1%84%85%E1%85%A9.png?raw=true)

- 최단경로의 경우 **최소비용을 고려한 경로를 전체적**으로 본다.

- **각 노드별 이동비용을 고려했을 때, 최소비용과 최단경로**가 모두 고려된 방법은 탐욕알고리즘이 아닐 수 있다.

- 고려해야하는 지표

   - 노드수

   - 각 노드에 대한 이동 비용

   - 목적

   - 기타 등등

#### Greedy 로직과 소스코드

```python
# greedy 로직

# greedy는 전체를 위한 답을 찾는 것이 아니라, 순간최적을 위한 답을 찾는다.
# 숲을 보기보다 나무를 위한 답을 찾는 것이다.
if node. weight == 같다
  같은 노드는 다시 들리지 않는다.
# 아래 상황을 고려해보자.

# 1)  동전을 각각 여러 개 갖고 있다.
# 2) 물건을 구매할 경우, 가장 적은 잔돈의 갯수를 구해야하는 로직이다.
```

```python
# 잔돈갯수를 구하자.(갖고 있는 돈 : 100원)
price = int(input('물건값을 입력하세요.'))

change = 100 - price
coin_list = [50, 40, 20, 10, 5]   # 받을 수 있는 잔돈의 종류

change_count = []   # 잔돈갯수

while change != 0:
    for coin in coin_list:    # 이 부분을 오해하지 말아야한다.(리스트에 대한 반복문이다.)
        change_bool = 0
        
        change_bool = change_bool + (change // coin)

        change_count.append(change_bool)

        change = change - (change_bool * coin)

        print(coin, change_count)
        
print('잔돈갯수 :',sum(change_count)) # 잔돈의 갯수를 합한다.(sum 내장함수 활용)
```

#### DP와 Greedy

최적 부분 구조 문제를 푼다는 점에서 비교

- DP

  1) 문제를 작은 단위로 분할하여 해결한 후, 해결된 **중복문제들의 결과를 기반으로 전체문제를 해결**

- Greedy

  1) **각 단계마다 최적해**를 찾는 문제로 접근

  2) 해결해야 할 전체 문제의 객수를 줄이기 위해 **개별적으로 문제를 해결**해나가는 선택


### Review

---


**오늘 배운 것**

```
1) DP
2) Greedy의 활용법
3) 알고리즘에 대한 전반적인 내용
```

**오늘 해야할 것**

```
1) DP에 대한 논리적 흐름 이해하기
2) Greedy에 대한 흐름 이해하기
3) 전반적인 알고리즘의 논리적 흐름 이해하기
```

### Reference

---

- [동적 계획법](https://namu.wiki/w/%EB%8F%99%EC%A0%81%20%EA%B3%84%ED%9A%8D%EB%B2%95)

- [https://velog.io/@cyranocoding/%EB%8F%99%EC%A0%81-%EA%B3%84%ED%9A%8D%EB%B2%95Dynamic-Programming%EA%B3%BC-%ED%83%90%EC%9A%95%EB%B2%95Greedy-Algorithm-3yjyoohia5#:~:text=com%2Fgreedy.php-,Greedy%20Algorithms(%ED%83%90%EC%9A%95%EB%B2%95%2C%20%ED%83%90%EC%9A%95%20%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98),%ED%95%98%EB%8A%94%20%EB%AC%B8%EC%A0%9C%20%ED%95%B4%EA%B2%B0%20%EB%B0%A9%EC%8B%9D%EC%9D%B4%EB%8B%A4.](https://velog.io/@cyranocoding/%EB%8F%99%EC%A0%81-%EA%B3%84%ED%9A%8D%EB%B2%95Dynamic-Programming%EA%B3%BC-%ED%83%90%EC%9A%95%EB%B2%95Greedy-Algorithm-3yjyoohia5#:~:text=com%2Fgreedy.php-,Greedy%20Algorithms(%ED%83%90%EC%9A%95%EB%B2%95%2C%20%ED%83%90%EC%9A%95%20%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98),%ED%95%98%EB%8A%94%20%EB%AC%B8%EC%A0%9C%20%ED%95%B4%EA%B2%B0%20%EB%B0%A9%EC%8B%9D%EC%9D%B4%EB%8B%A4.)
