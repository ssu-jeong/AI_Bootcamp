# (Python) 프로그래밍

```python
# 인트로 코딩
# case 1 - 반복문
i = [] 
x = 0
for x in range(1,50):
  i.append(x)
  print(i)

# case 2 - 컴프리헨션
[i for i in range(1,50)]
```

```python
# case 1
for i in range(1,51):
  if i%3==0 and i%5==0:
    print(i)

# case 2
[i for i in range(1,51) if i%3==0 and i%5==0]
```

```python
for i in range(2,21):
  if i == 8:
    print()
    continue
  print(i , end= ' ')
  ```

  ## 문제해결

  ---

  프로그래밍에서의 문제해결개념

  - 의사코드(슈도코드, pseudocode)를 작성하면서 **로직을 코드로 표현하는 방법**을 배운다.

- 알고리즘과 같이 수식이나 **익숙하지 않은 개념**에 대해 접근하는 경우를 위해 의사코드 작성

- 프로그래밍을 통해 **논리적으로 문제를 생각하는 방법**에 대해 알아보기

- 프로그래밍을 통해 **논리적으로 문제를 생각하는 방법**에 대해 알아보기

#### 문제해결 프로세스

- **문제를 단위별로 쪼갠다.**

- 문제에 대해 **최소한의 시간을 활용하여 분석**하기 위함

- 어려운 문제의 경우 **전체 문제 중에 해결할 수 있는 부분**을 찾는다.

#### 의사코드 (pseudocode, 슈도코드)

- 슈도코드를 통해 실행되는 소스코드 작성 전, **자신이 이해할 수 있는 코드를 작성**

- **요구사항이나 알고리즘을 해석**하기 위해 사용

- 프로그램의 크기, 어려움, 협업 정도에 따라 필요유무가 달라짐

```python
# 의사코드 예시1 

print 5 # pseudocode

print(5) # 실제 실행되는 코드
```

```python
# 의사코드 예시2

function div
For반복문 (i = 1부터 i<=10까지, 반복할때마다 i값 1씩 증가) 
{
    If i가 3으로 나눠지는 경우,
        print 3으로 나눠진다.
    If i is divisible by 5
        print 5로 나눠진다.
    If print_number, print i.
    print 줄바꿈.
}
```

```python
# 의사코드 예시2에 대한 실제 실행되는 코드

def div():
  for i in range(1,11):
    if i % 3 == 0: # i를 3으로 나눴을 때 나머지가 0인 경우
      print('숫자',i, '=>','3으로 나눠짐')
    elif i % 5 == 0: # i를 5로 나눴을 때 나머지가 0인 경우
      print('숫자',i, '=>','5로 나눠짐')
    # if i % 5 == 0: # i를 5로 나눴을 때 나머지가 0인 경우
    #   print('숫자',i, '=>','5로 나눠짐')
    else: 
      print('그외',i, '=>','숫자 3과 5로 나눠지지 않음')
    
div()
```

# 시뮬레이션

## 컴프리헨션(comprehension)

---

실제 프로그래밍에서 **한 줄로 파이썬 기능을 구현할 수 있는 기능**

- 코드간소화를 위해 사용되며 직관적이고 속도가 빠름

- 조건이 복잡해지는 경우에는 직관성이 떨어지고, 메모리 사용량이 증가하여 사용이 어렵다.

```python
numbers = [1, 2, 3, 4]
squares = []

for n in numbers:
  squares.append(n**2)

print(squares) 

#컴프리헨션
numbers = [1, 2, 3, 4]
squares = [n**2 for n in numbers]

print(squares)
```

```python
list_a = [1, 2, 3, 4]
list_b = [2, 3, 4, 5]

common_num = []

for a in list_a:
  for b in list_b:
    if a == b:
      common_num.append(a)
      
print(common_num)

#컴프리헨션
list_a = [1, 2, 3, 4]
list_b = [2, 3, 4, 5]

common_num = [a for a in list_a for b in list_b if a == b]

print(common_num)
```

```python
# 딕셔너리 컴프리헨션

test = {'A': 5, 'B': 7, 'C': 9, 'D': 6, 'E': 10} 

test = {na:test for na,test in test.items() if na != 'E'}
print(test)
```

```python
# 아래와 같이 조건을 반복문 대신 조건을 먼저 쓸 수 있다.
# 조건을 위해 if를 사용하는 경우 else를 작성해줘야된다.
numbers = {'amy': 7, 'jane': 9, 'sophia': 5, 'jay': 10}
pas = {name: 'PASS' if numbers > 8 else 'NO PASS' for name, numbers in numbers.items()}
print(pas)

# 아래처럼 반복문을 연속으로 작성가능하다.
# set은 특성상 중복값을 제외한다.
print('list for loop : ',[n for n in range(1, 5+1) for n in range(1, 5+1)])

print('set for loop : ',{n for n in range(1, 5+1) for n in range(1, 5+1)})


# 두개의 리스트를 하나의 딕셔너리로 합침. 
# 하나는 key, 또 다른 하나는 value로 사용한다
subjects = ['math', 'history', 'english', 'computer engineering']
scores = [90, 80, 95, 100]
score_dict = {key: value for key, value in zip(subjects, scores)}
print(score_dict)

# 튜플 리스트를 딕셔너리 형태로 변환
score_tuples = [('math', 90), ('history', 80), ('english', 95), ('computer engineering', 100)]
score_dict = {t[0]: t[1] for t in score_tuples}
print(score_dict)
```

## 지역변수와 전역변수

---

- 코드가 복잡해지거나 기능이 많아지는 경우, 변수사용에 따라 **함수 및 클래스의 접근**이 달라진다.

- 변수이름설정, 변수활용도에 따른 **변수설계**가 중요.
 
  - **지역변수** : 해당 변수가 포함된 **함수 안**에서만 수정하고 읽을 수 있다.
  
  - **일반 전역변수** : **하나의 파이썬 파일전체**에서 값을 읽을 수 있다. 
    되도록이면 함수 안에서 **사이드이펙트 및 가독성**을 위해 값을 수정하지 않도록 한다. 
  - **global 전역변수** : 일반 전역변수와 다른 점은 변수가 생성되는 시점!

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%8C%E1%85%B5%E1%84%8B%E1%85%A7%E1%86%A8%E1%84%80%E1%85%AA%E1%84%8C%E1%85%A5%E1%86%AB%E1%84%8B%E1%85%A7%E1%86%A8%E1%84%87%E1%85%A7%E1%86%AB%E1%84%89%E1%85%AE%E1%84%8B%E1%85%B4%20%E1%84%87%E1%85%A5%E1%86%B7%E1%84%8B%E1%85%B1.png?raw=true)

- 지역변수는 이름이 같더라도, 소속된 함수가 다르면 다른 변수로 취급된다.

- 전역변수는 하나의 파이썬 파일에 있는 모든 함수에 쓰일 수 있다.

```python
# 아래 소스코드를 한 줄씩 실행하면서 지역변수와 전역변수에 대해 파악한다.

g_var = 'g_var'   # 전역변수

  
# 값 수정후(수정값)
def variables():
  
  global glo_var  # global 전역변수
  glo_var = 'glo_var' # global 전역변수에 새로운 값 할당
  lo_var = 'lo_var'   # 지역변수

  print()
  print('(값 수정후)함수 안에서 g_var(전역변수) : ', g_var)  # 수정되지 않고 초기값을 출력함
  print('(값 수정후)함수 안에서 glo_var(global 전역변수) : ', glo_var)  # 함수에서 수정된 후 값을 출력함
  print('함수 안에서 lo_var(지역변수) : ', lo_var)    # 특정 함수에서만 출력되는 지역변수

# 전역변수를 파라미터로 담은 함수
def second_variables(glo_var,g_var):
  glo_var = 'glo_var in second_variables()'
  g_var = 'g_var in second_variables()'
  lo_var = 'second lo_var'
  print('서로 다른 함수에서 지역변수이름이 같은 경우 :',lo_var)
  
  return glo_var,g_var

# 값 수정전(초기값)
g_var = 'g_var_new_value'
glo_var = 'glo_var_new_value'
print('(값 수정전)함수 밖에서 g_var(전역변수) : ', g_var)  
print('(값 수정전)함수 밖에서 glo_var(global 전역변수) : ', glo_var) # 새로 할당된 값으로 수정됨
# print('함수 밖에서 lo_var(지역변수) : ', lo_var) # 특정 함수 안에서만 사용하는 지역변수이므로 출력안됨

# 전역변수의 값 수정
#print('함수의 파라미터가 전역변수인 경우 :', second_variables(glo_var, g_var))

# 지역변수를 갖고 오는 경우
#print('함수의 파라미터가 지역변수인 경우 :', second_variables(glo_var, lo_var))

# 함수에서 수정된 전역변수 재호출
print('전역변수값 :',glo_var, g_var)

variables()
```

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%8C%E1%85%B5%E1%84%8B%E1%85%A7%E1%86%A8%E1%84%87%E1%85%A7%E1%86%AB%E1%84%89%E1%85%AE%E1%84%8C%E1%85%A5%E1%86%AB%E1%84%8B%E1%85%A7%E1%86%A8%E1%84%87%E1%85%A7%E1%86%AB%E1%84%89%E1%85%AE.png?raw=true)


## 예외적 상황

---

###### if/else , try/except

- for~else 구문에서는 break에 따라 수행여부 달라짐.

- if/else 구문에서 else는 '앞의 구문이 수행되지 않으면 else구문을 수행하시오' 라는 뜻

- try/except 구문 또한 이 구문 앞의 try 구문을 수행하다가 예외발생 시, except 구문을 수행하시오' 라는 뜻

```python
# 루프가 반복 수행하는 내부 구문 바로 다음에 if없이도 else 구문을 추가 할 수 있다.
for i in range(3):
  print('loop : ', i) # 1) 루프반복수행
else : 
  print('Else statement') # 2) else 구문 추가수행
```

```python
# 그렇다면 break문이 있다면?
for i in range(3):
  print('loop : ', i) # 1) 루프반복수행
  if i == 1:
    break     # break는 어떤 영향을 줄 것인가?
else : 
  print('Else statement') # 2) else 구문 추가수행

# 반복문에 빈 리스트를 넣으면 어떻게 될까?
for i in []:
  print('loop : ', i) # 1) 루프반복수행
else : 
  print('Else statement') # 2) else 구문 추가수행

# 반복문에 빈 리스트를 넣으면 어떻게 될까?
for i in []:
  print('loop : ', i) # 1) 루프반복수행
else : 
  print('Else statement') # 2) else 구문 추가수행
```

###### assert조건, '에러메세지'

assert()는 방어적 프로그래밍(defensive programming)방법 중 하나이며 코드를 점검하는데 사용

- 조건이 True인 경우 그대로 코드 진행, False인 경우 에러메시지(Assertion Error)

- 에러메시지: 앞에 조건이 False인 경우 AssertionError와 함께 남길 메시지를 남겨줄 수 있다. (이 부분은 생략 가능)

###### try/except/raise/finally

예외처리를 위한 키워드

- try : 처리하고자 하는 부분을 넣는다

- except : try구문 안에서 발생할 것으로 예상되는 예외를 처리

- raise : 예외상황일 때 명시적으로 처리

- finally : 마지막으로 실행하는 코드

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%8B%E1%85%A8%E1%84%8B%E1%85%AC%E1%84%8E%E1%85%A5%E1%84%85%E1%85%B5.png?raw=true)

- 위와 같이 코드 상황에 따라 예외처리 키워드 발동

- try/finally : 에러가 발생하더라도 마지막 코드를 수행해야 할때

- try/except/else : else 구문을 사용하면 예외구분을 위해 try 구문 안에 들어갈 코드를 최소화시켜 가독성이 좋아짐

```python
def my_divide():
    try:
        # 문제가 없을 경우 실행할 코드
        x = input('분자의 숫자를 입력하세요 ~ ')
        y = input('분모의 숫자를 입력하세요 ~ ')
        return int(x)/int(y)
    except:
        # 문제가 생겼을 경우 실행할 코드
        return '나누기를 할 수 없습니다'

print(my_divide())

# try / except
try:
  print(3/0)
except:
  print('except case')

# try / except
try:
  print(5/0)
except ZeroDivisionError:
  print('except case ZeroDivisionError')
```

```python
# try / except / else
try:
  print(3/1)
except:
  print('except case')
else:
  # except 절을 만나지 않았을 경우 실행하는 코드
  print('else case')
```

```python
# try / except / finally
try:
  print(5/0)
except:
  print('except case')
finally:
  # 오류 발생 유무와 상관없이 무조건 실행하는 코드
  print('finally case')

# try / except / finally
try:
  print(5/0)
  print(try test)
except NameError as n:
  print(n)
except ZeroDivisionError as z:
  print(z)

# try / raise / except
try:
  print('try test')
  num = int(input("0 이상의 값 입력: "))
  
  if num < 0:
      raise NotImplementedError # 예외사항에 대해 처리하는 raise!
  print('num : ',num) 

except NotImplementedError:
  print('NotImplemented Error')
```

- except 조건에 따라 None을 return해주는 상황존재
  -> 하지만  None을 return하고 전달받아 활용하게 되는 경우 오류가 발생할 수 있다.

```python
# None을 return 하는 경우

def none_test(num1, num2):
    try:
        return num1 / num2
    except ZeroDivisionError:
        return None       # None 반환

# 문제없음, 단순히 None이 있는지 없는지 판단함
# result = none_test(0,2)
# print(result)
if result is None:
    print('result is None')

# 문제발생
result = none_test(0, 2)
print(result)
# 조건식에서 not을 활용하는 경우, 파이썬에서는 None, 빈문자열, 빈리스트, 0을 모두 False로 판단한다
# 단순히 결과값이 0인데도 not result 조건으로 인해 False 처리된다.
# if not result:              
#     print('not result')


# None을 return 하지 않는다.

def not_none_return(num1, num2):
  try:
    return num1 / num2
  except ZeroDivisionError as z:
    raise ValueError('숫자 입력값이 잘못된 경우') from z  
  else:
    print(result)

try:
    #result = not_none_return(2, 0) # case 1 - 정상적으로 except 처리
    #result = not_none_return(0, 2) # case 2 - 값 반환
except ValueError:
    print('숫자 입력값이 잘못된 경우')  # None을 반환하는 대신 예외를 발생시킨다.
else:
    print(result)
```

