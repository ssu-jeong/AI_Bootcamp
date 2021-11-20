# OOP

---

>OOP (Object-Oriented Programming)이란 객체 지향적인 프로그래밍. 즉, C언어같은 절차 지향적인 프로그래밍이 아닌 객체의 관점에서 프로그래밍을 한다는 것.
OOP는 객체를 기준으로 코드를 나누어 구현한다. 그 구성 부분 단위가 클래스 인데, 클래스는 설계도 인스턴스는 직접일을 하는 구현체이다.

쉽게 생각해서 세상에 있는 실체가 모든 물체를 클래스와 인스턴스, 함수, 변수라는 object로 변화시켜서 프로그램을 구성하는 것!
OOP의 기본전제는 기능(함수, 변수) **재사용이 가능하도록 설계 및 프로그래밍** 했는지!

<정리>

- OOP는 객체의 관점에서 프로그래밍하는 것을 의미
   * C언어는 절차 지향 프로그래밍으로 프로세스가 함수 단위로 순서대로 진행된다.

- OOP는 사람의 사고방식과 더 가깝다.

- OOP는 객체들의 유기적인 관계를 통해 프로세스가 진행된다.

- 애플리케이션을 구성하는 요소들을 객체로 바라보고, 객체들을 유기적으로 연결하여 프로그래밍 하는 것을 말한다. 

```python
# 난수 다루기(1~100 사이 정수형 난수를 구하자.)
# 정수를 입력받고, 입력숫자가 출력될 때까지 입력숫자만큼 반복하여 난수를 출력하고 1개의 종료메시지를 띄우시오.

import random

input_num = int(input())

for i in range(input_num):
  ran_num = random.randint(1,100)
  print(ran_num, end = ' ')

  if ran_num == input_num:
    print("input random number print")
    continue

else:
  print('exit')
```

#### OOP 이전 프로그래밍 과정

---

![image](https://github.com/Maiven/data-science/blob/main/oop_beforeOop.png?raw=true)

- 배열과 함수, 변수를 많이 생성하고 활용하여 최대한 많은 기능을 적은 양의 소스코드 파일에 담았다.

- 속성과 기능이 증가할 떄 마다 배열과 함수를 계속 생성 -> 소스코드 관리에 비효율

###### OOP의 필요성

> data-driven(데이터기반 의사결정), 컴퓨터 하드웨어성능, 데이터양 증가에 따라 OOP활용도 증가

  - 프로그래밍 패러다임 : OOP, Procedural Programming, Functional Programming

  - 함수형 : 프로그래밍 코드를 특정 상황에 특성함수를 사용하기 위해 고안된 방법
  -> 함수의 사용을 극대화 시켜서 코드의 가독성을 높여준다.

  - 특정 컴퓨터 환경과 특정 대용량 개발환경에서 많이 쓰이고 있다.
  -> 절대적으로 좋은 프로그래밍은 아님!!

![image](https://github.com/Maiven/data-science/blob/main/oop_pp.png?raw=true)

###### OOP와 일상생활

- 일상생활에서 볼 수 있는 것, **실제로 머릿속에서 떠올릴 수 있는 것**을 프로그래밍하는 것이 중요.

- 기능별로 개체가 효율적으로(**재사용 가능하도록**) 분리되어야 한다. -> 그래서 설계 중요!!

```python
# 절차 프로그래밍(Procedural Programming, 일명 PP)
# 조건 또는 기능이 증가할 때마다 함수와 변수 같은 요소가 계속 증가할 수 있으므로 비효율적이다.

# 케이스 1 : 함수활용
def carAttribute():
  speed = 50
  color = 'black'
  model = 'CarModel'
  return speed,color,model

# return값을 통해 함수 요소값을 확인할 수 있다.
print("Car Attribute: ", carAttribute())

# 케이스 2 : 변수활용
speed = 50
color = 'black'
model = 'CarModel'

# 해당 변수를 각각 명시해주어야 한다.
print("Car Attribute: ", speed,color,model)
```

```python
# OOP / 기능에 따라 Car클래스 안에 있는 함수와 변수만 추가해주면 된다.
# 아래와 같이 클래스 선언 순서에 관계없이 실행된다.
# 절차 프로그래밍과 다르게 기능별로 수행되기 때문이다.
class Bus:
  def __init__(self, speed, color):
      self.speed = speed
      self.color = color
  
  def drive_bus(self):
    self.speed = 70

class Car:
  def __init__(self, speed, color, model):
    self.speed = speed
    self.color = color
    self.model = model
  
  def drive(self):
    self.speed = 50
  
myCar = Car(0, "green", "testCar")
print("--------Car Object Create Complete--------")
print("Car Speed: ", myCar.speed)
print("Car Color: ", myCar.color)
print("Car Model: ", myCar.model)
print("Bus color: ", myBus.color)

myBus = Bus(0, 'black')
print("--------Bus Object Create Complete--------")
print("Bus color: ", myBus.color)


# 운전 중이 아니므로 speed는 0을 출력한다.
print("--------Car/Bus Speed 1--------")
print("Car Speed by drive: ", myCar.speed)
print("Bus Speed by drive: ", myBus.speed)

# Car/Bus object method Call
myCar.drive()
myBus.drive_bus()

# 각각의 개체가 각자의 속도로 움직이고 있다.
print("--------Car/Bus Speed 2--------")
print("Car Speed by drive: ", myCar.speed)
print("Bus Speed by drive: ", myBus.speed)
```

# OOP의 특징

---

#### 캡슐화

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%8F%E1%85%A2%E1%86%B8%E1%84%89%E1%85%B2%E1%86%AF%E1%84%92%E1%85%AA.png?raw=true)

- 하나의 객체에 대해 그 객체가 특정한 목적을 위한 필요한 변수나 메소드를 하나로 묶는 것

- 따라서 클래스를 우리가 만들 때, 이 클래스에서 만들어진 객체가 특정한 목적을 잘 수행할 수 있도록 사용해야할 변수와 그 변수를 가지고 특정한 액션, 즉 메서드를 관련성있게 클래스에 구성해야한다. 

###### 정보은닉
캡슐화를 하는 중요한 목적은 정보은닉. 유저 정보를 가지고 있는 User라는 객체에서 유저의 정보가 public으로 선언되어 있다면, 누구든 접근해서 유저 정보를 변경할 수 있다. 그렇기 때문에 private로 해서 데이터 보호 및 접근을 제한해야한다.

이렇게 보호된 변수는 getter나 setter 등의 메서드를 통해서만 간접적으로 접근이 가능하도록 하는 것이 캡슐화의 중요한 목적이다.(setter도 아무생각 없이 만들면 안된다.)

#### 상속과 포함

![image](https://github.com/Maiven/data-science/blob/main/inheriance_composition.png?raw=true)

- object의 종류는 현실 세계에 있는 대부분이기 때문에, 설계될 수 있는 다양한 object가 있다.

###### 상속(Inheritance)

- 상속이란 기존 상위클래스에 근거하여 새롭게 클래스와 행위를 정의할 수 있게 도와주는 개념

- 기존 클래스에 기능을 가져와 재사용할 수 있으면서도 동시에 새롭게 만든 클래스에 새로운 기능을 추가할 수 있게 만들어 준다. 

```
"개는 동물이다." 또는 "선생님은 직장인이다.
"라는 관계로서 설명된다.
```

###### 포함(Composition)
```
"개는 몸을 갖고 있다." 라는 관계로서 설명된다.

기본개념 : 다른 클래스의 일부 기능(함수)만을 재사용한다.
```

```python
# 상속코드

# 클래스 선언
class Person:
    def __init__(self, name):
        self.name = name
        
class Student(Person):      # Person 클래스 상속받음(name 변수를 파라미터로 재사용)
    def study(self):
        print (self.name + " studies hard")

class Employee(Person):     # Person 클래스 상속받음(name 변수를 파라미터로 재사용)
    def work(self):
        print (self.name + " works hard")

# object 생성
s = Student("Dave")
e = Employee("David")

# object 실행
s.study()
e.work()

# 포함코드

# 클래스 선언
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def printPerson(self):
        print('Person_printPerson')

class Student(Person):
    def __init__(self, name, age, id):
        Person.__init__(self, name, age)
        Person.printPerson(self)
        self.id = id

    def test(self, score):
        if score > 80:
            print (self.name + " studies hard")
        else:
            print (self.name + " needs supplementary lessons")


# object 생성
# 한 번 생성된 object는 파라미터가 변하지 않는 이상 출력값 또한 변하지 않는다.
s = Student("Dave", 20, 1)

# object 실행
print("s.age:", s.name)   # result : Dave
print("s.age:", s.age)   # result : 20
print("s.id:", s.id)   # result : 1
print('\n')

# 객체 하나 더 생성하기
s2 = Student("Jamie", 25, 2)
print("s2.age:", s2.name)   # result : Jamie
print("s2.age:", s2.age)   # result : 25
print("s2.id:", s2.id)   # result : 2
print('\n')

# 점수입력
print('-- test score result --')
s.test(52)
s2.test(88)

# 포함코드

# 클래스 선언
class Bill():
    def __init__(self, description):
        self.description = description


class Tail():
    def __init__(self, length):
        self.length = length


class Duck():
    def __init__(self, bill, tail):
        self.bill = bill
        self.tail = tail

    def about(self):
        print(
            f"This duck has a {self.bill.description} and a {self.tail.length}.")

# object 생성
duck = Duck(Bill('bill object'), Tail('tail object'))

# object 실행
duck.about()
```

#### 추상화

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%8E%E1%85%AE%E1%84%89%E1%85%A1%E1%86%BC%E1%84%92%E1%85%AA.png?raw=true)

- 목적과 관련이 없는 부분을 제거하여 필요한 부분만을 표현하기 위한 개념

- 구체적인 사물들간의 공통점을 취하고 차이점을 버리는 일반화를 사용하거나, 중요한 부분을 강조하기 위해 불필요한 세부사항을 제거함으로써 단순하게 만든다. 
   -> 불필요한 코드 제거하고 중요한 부분 살린다!!
  - object의 기능에 다라 추상클래스(상위클래스)를 상속받아 개별적으로 클래스(하위클래스)를 생성.

  - 기본적으로 추상메소드를 선언, 실제 실행되는 기능은 보이지 않으며 선언된 추상클래스를 상속받은 다른 클래스의 메소드에서 확인가능.
예) for, while, do~while 등과 같은 문법은 반복문을 추상화 한 것. 실제로는 CPU의 명령을 통해서 반복이 구현되지만 여기서 **반복**이라는 개념을 뽑아내서 for, while, do~while 등으로 추상화 한 것.

- 추상적으로 끄집어 낸 개념들을 큰 틀에서 클래스로 만드는 것이 바로 **추상클래스**.
  
  - 추상클래스를 사용하는 이유
    -> 대형 프로젝트를 진행하는 경우, 프로그램이 복잡해지는 경우 1차적인 설계를 위해 기능을 추상화 시켜놓고, 활용여부는 차후 결정하기 위함.

#### 다형성

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%83%E1%85%A1%E1%84%92%E1%85%A7%E1%86%BC%E1%84%89%E1%85%A5%E1%86%BC.png?raw=true)

- 상속을 통해 기능을 확장하거나 변경하는 것을 가능하게 함.
  
   - 즉, 다형성은 형태가 같은데 다른 기능을 하는 것을 의미(같은 동작이지만 다른 결과물이 나올 때 다형!)
- 다형성은 구형되는 **하위클래스에 따라 클래스를 다르게 처리**하는 기능
  
  - 상속과 유사하지만, 상속은 상위클랙스의 기능(함수, 변수)을 재사용

  - 위의 그림과 같이 다형성은 상위클래스의 기능을 변경하여 사용.(그대로 재사용하지 않음)

```python

class Person:
  def run(self):
    print("I'm a human: ", end='')
    print('run')

  def play(self):
    print("I'm a human: ", end='')
    print('play')
  
class Student(Person):
  def run(self):
    print("I'm a student: ", end='')
    print('fast run')
  
  def play(self):
    print("I'm a student: ", end='')
    print('play')
  
class teacher(Person):
  def teach(self):
    print("I'm a teacher: ", end='')
    print('teach')

  def play(self):
    print("I'm a teacher: ", end='')
    print('teach play')


# 리스트를 생성한다.
number = list()
# 생성한 리스트에 다형성 개념을 위해 다른 클래스(Student, teacher)가 상위 클래스(Person)를 참조할 수 있도록 한다.
number.append(Student())  # 리스트 끝에 서브 클래스 Student()를 넣습니다. 
number.append(teacher())  # 다시 리스트 끝에 서브 클래스 teacher()를 넣습니다.

print("=========")
for Runner in number:
    Runner.run()     # 상위클래스인 Person의 run은 상속하여 사용하지만 내용은 다르다.


print("=========")
for Player in number: 
    Player.play()    # 상위클래스인 Person의 play는 상속하여 사용하지만 내용은 다르다.
```

✋🏻헷갈리지 않도록 코드 작성! 연산자 효율적으로 활용!

- 연산자 1개(is not) : A는 B가 아니다.

- 연산자 2개(not, is) : A가 아닌 것은 None이다.

```python

# 오해하지 않도록 코드를 작성하자.
# foo: 프로그래밍 상에서 임시로 변수이름을 지정해줘야 할 때 주로 쓰이는 변수 이름이다.
foo = ''

# 가독성 좋음
if foo is not None: # 한 번만 해석하면 된다. (A는 B가 아니다.)
  print('가독성 좋음')

# 가독성 좋지 않음
if not foo is None: # 두 번 해석해야된다. (A가 아닌 것은 None이다.)
  print('가독성 좋지 않음')
```

###### Overriding & Overloading

OOP에서 다형성의 개념을 녹여내는 방법

![image](https://github.com/Maiven/data-science/blob/main/%E1%84%86%E1%85%A6%E1%84%89%E1%85%A9%E1%84%83%E1%85%B3%E1%84%8B%E1%85%A9%E1%84%87%E1%85%A5%E1%84%85%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%83%E1%85%B5%E1%86%BC.png?raw=true)

- 오버라이딩

  : 부모 클래스에서 상속받은 자식 클래스에서 부모클래스에서 만들어진 메서드를 자식 클래스에서 자신의 입맛대로 다시 재정의해서 사용하는 것을 말한다.

- 오버로딩

  : 같은 이름의 메서드를 사용하지만 메서드마다 다른 용도로 사용되며 그 결과물도 다르게 구현할 수 있게 만드는 개념

   - 오버로딩이 가능하려면 메서드끼리 이름은 같지만 매개변수의 갯수나 데이터 타입이 다르면 오버로딩이 적용

   - 메서드 이름이 같아도 문법 에러 ❌

```python

class Bicycle():
     def exclaim(self):
       print("부모클래스 자전거")

class Specialized(Bicycle):            # 부모클래스를 상속받음
    def exclaim(self, specialized):    # 메소드 오버라이딩(specialized 파라미터 추가, return 추가)
         print("자식클래스 재정의:",specialized)
         return 'return 자식클래스 재정의: '+specialized


a_bike = Bicycle()
a_specialized = Specialized()

# 출력1 - 부모클래스 메소드
print('출력1:')
a_bike.exclaim()

# 출력2 - 오버라이딩된 자식클래스 메소드(파라미터 추가, return 추가)
print('출력2:')
a_specialized.exclaim('specialized test')
```

```python
class Bicycle():
    def exclaim(self):  
        print("부모클래스 자전거")

class Specialized(Bicycle): # 부모클래스를 상속받음
    def exclaim(self):    # 메소드 오버라이딩
        super().exclaim() # super는 위의 부모클래스 메소드를 그대로 활용한다.
        print('super를 활용한 부모클래스의 메소드입니다.')
         


a_bike = Bicycle()
a_specialized = Specialized()

# 출력1 - 부모클래스 메소드
print('출력1:')
a_bike.exclaim()

# 출력2 - super : 부모클래스 메소드 그대로 활용
print('출력2:')
a_specialized.exclaim()
```

## 클래스 설계와 사용

---

클래스 설계와 사용

- 클래스 설계가 중요한 이유는 **코드 재사용성**

- 코드설계시 바로 소스코드를 작성하지 않고, 먼저 그림과 글을 통해 자신의 방법으로 코드블록을 구성해본다!

1단계
 
- 코드설계시 사용할 object 파악

```
Users
 -Customers
 -Vendors
 -Admin

Products

Purchases
```

2단계

 - 코드 작성 전, 각 object별로 요구되는 속성과 어떤 기능을 위해 생성되었는지 설계

 ```
Users
 - Attributes(속성)
   - 이름
   - 사용자가 관리자인지?
 - Customers
   - Attributes
    - 이름
    - 구매목록
 - Vendors
   - Attributes
    - 이름
    - 상품목록
 - Admin
   - 이름
   - 사용자가 관리자임을 나타내는 구분값

Products
  - Attributes
   - 이름
   - 가격
   - 공급업체

Purchases
  - Attributes
   - 제품
   - 고객
   - 가격
   - 구매완료기간
```

3단계 

- object간의 관계에 대해 생각해 본다 

  - 판매자는 1개 이상의 제품을 갖고 있다.

  - 고객은 1개 이상의 구매를 한다.

  - 구매는 1개 이상의 제품을 구매 하는 것.

```python
# 기본이 될 수 있는 User 클래스 생성

class User:
    def __init__(self, name, is_admin=False):
        self.name = name
        self.is_admin = is_admin
```

```python
# User로부터 상속받는 3개의 클래스를 정의
"""
부모 클래스에서 정의한 함수와 변수는 자식 클래스에서 정의한 것처럼 사용할 수 있습니다.

부모 클래스에서 정의한 함수와 자식 클래스에서 정의한 함수 이름이 같은 경우,
부모 클래스의 함수를 호출하려면 두 가지 방법 중 하나를 사용해야 합니다.
1) 부모클래스명.함수명()
2) super().함수명()

즉, super()는 자식클래스에서 부모클래스에 있는 함수를 사용하고 싶고,
플러스 해당 함수명이 자식클래스에 중복되어 있을 때 사용할 수 있는 코드입니다.
"""

class User:
    def __init__(self, name, is_admin=False):
        self.name = name
        self.is_admin = is_admin

class Admin(User):
    def __init__(self, name):
        super().__init__(name, is_admin=True)

# 부모 클래스(User)로부터 상속을 받으려면 클래스를 선언할 때,
# 클래스 이름 다음에 있는 소괄호 안에 부모 클래스의 이름을 넣어주면 됩니다.
class Customer(User):
    def __init__(self, name):
        super().__init__(name)
        self.purchases = []

class Vendor(User):
    def __init__(self, name):
        super().__init__(name)
        self.products = []

```

```python
# 위의 코드에서 제품(Product)과 구매(Purchase) 클래스 생성 코드 추가

from datetime import datetime

class User:
    def __init__(self, name, is_admin=False):
        self.name = name
        self.is_admin = is_admin

class Admin(User):
    def __init__(self, name):
        super().__init__(name, is_admin=True)

class Customer(User):
    def __init__(self, name):
        super().__init__(name)
        self.purchases = []

class Vendor(User):
    def __init__(self, name):
        super().__init__(name)
        self.products = []

class Product:
    def __init__(self, name, price, vendor):
        self.name = name
        self.price = price
        self.vendor = vendor

class Purchase:
    def __init__(self, product, customer):
        self.product = product
        self.customer = customer
        self.purchase_price = product.price
        self.purchase_data = datetime.now()
```

```python
"""
현재 생성된 클래스: User(Admin, Customer, Vendor), Product, Purchase

1) 고객(Customer): 제품(Product)을 구매(Purchase)하는 행동
   => Customer 클래스에 purchase_product 메소드 추가

2) 공급업체(Vendor): 제품(Product)을 생산(Product)하는 행동
   => Vendor 클래스에 create_product 메소드 추가
"""

from datetime import datetime

class User:
    def __init__(self, name, is_admin=False):
        self.name = name
        self.is_admin = is_admin

class Admin(User):
    def __init__(self, name):
        super().__init__(name, is_admin=True)

class Customer(User):
    def __init__(self, name):
        super().__init__(name)
        self.purchases = []
    # 함수 추가
    def purchase_product(self, product):
        purchase = Purchase(product, self)
        self.purchases.append(purchase)

class Vendor(User):
    def __init__(self, name):
        super().__init__(name)
        self.products = []
    # 함수 추가
    def create_product(self, product_name, product_price):
        product = Product(product_name, product_price, self)
        self.products.append(product)

# 모델링을 위한 추가 소스코드
class Product:
    def __init__(self, name, price, vendor):
        self.name = name
        self.price = price
        self.vendor = vendor

class Purchase:
    def __init__(self, product, customer):
        self.product = product
        self.customer = customer
        self.purchase_price = product.price
        self.purchase_data = datetime.now()
```

#### 클래스의 인스턴스화

![image](https://github.com/Maiven/data-science/blob/main/OOP_object_class.png?raw=true)

클래스를 생성 했으면, 그것을 활용하기 위한 인스턴스화 필요!

- object가 생성된 이후, 소프트웨어의 **메모리할당이 되면 인스턴스**가 되는 것.

- object는 인스턴스를 포함할 수 있으며, 포괄적 의미를 갖는다.

- object는 프로그래밍 전체에서 쓰이는 포괄적인 의미를 갖으므로 인스턴스와 비교하면서 학습하는 대상은 아님.

```python
# 가장 기본적인 클래스를 생성해보고 값을 확인해본다.

class MyFirstClass:
    pass

a = MyFirstClass()  # 인스턴스화(메모리할당됨)

print(a)    # 주소값은 일반적인 정수값과 다르게 나온다.
```

# 파이썬 활용 및 OOP내용

---

#### 데이터 캡슐화와 접근제어

![image](https://4.bp.blogspot.com/-YciF7XtakGo/V0SPb9jQcII/AAAAAAAAA1k/l40Oe8cEcYU_pCCCuFM13qHDQWOgG6EKwCLcB/s1600/Encapsulation%2Bin%2BPython%2BOOP.bmp)

캡슐화 하는 이유

- 캡슐화 : object 및 소스코드 구현에 대한 상세정보를 분리하는 과정

- 모듈화 가능 (함수, 메소드, 클래스 등을 활용한 기능 분리.)

- 기능이 분리되어 **디버깅**하는 경우 편리

- 프로그램이 기능별로 분리되어 있어, 소스코드의 목적을 알기 쉽다. 

- 파이썬은 object 접근제어를 위한 **접근제어자를 제공하지 않기 떄문에** 변수, 메소드, 함수에 직접 접근할 수 있다.
 
  - 파이썬에서는 상단 표와 같이 직접 접근을 허용하지 않는 규칙을 만들었다.

  - Notation : 접근 정도를 나타내는 명칭이며 Private -> Protected -> Public 순서로 코드접근이 어려움.

- 파이썬의 변수나 함수를 감춰주는 기능으로, 외부에서 무분별한 접근을 막기 위한 개념

  - 외부 object가 속성이나 메소드에 대한 접근을 막기 위해 이중 밑줄 __을 접두사로 추가할 수 있다.

  - '_클래스이름__메소드이름' 형태로 이름을 변환시켜, 부모클래스와 서브클래스의 변수나 메소드이름을 구분.

```python
class Point:
   def __init__(self, x, y):
       self.x = x
       self.y = y
       self.__private_name = "private 접근"

class Point_sub(Point):
  def __init__(self,x, y):
    Point.__init__(self,x,y)
    self.x = x
    self.y = y
    
  def __sub(self):
    self.__x = 10
    self.__y = 20

  def sub(self):
    self.__sub()
    print(self.__x)
    print(self.__y)
 
my_point = Point(1, 2)
my_point_sub = Point_sub(10,20)


# case 1 - error case: private 으로 해당코드로 접근할 수 없다
# print(my_point.__private_name)

# case 2
# 클래스 생성자에 있는 private변수에 접근하기위해 '_클래스이름__private변수' 를 활용한다.
print(my_point._Point__private_name)

# case 3
print('case3 ------------')
my_point_sub.sub()    # 변환된 이름에 대해 값 출력
```

- 아래와 같이 클래스 이름과 속성에 대해 알고 있으면, 변형된 이름을 사용해 접근 가능!
  -> 코드상에서 접근을 강제로 막을 방법은 없다.

```python
class A(object):
  def __init__(self):
    self.__X = 3        # self._A__X 로 변환

  def __test(self):     # _A__test() 로 변환
    print('self.__X' ,self.__X)

  def bast(self):
    self.__test()

class B(A):
  def __init__(self):
    A.__init__(self)
    self.__X = 20       # self._B__X 로 변환

  def __test(self):     # _B__test() 로 변환
    print(self.__X)

  def bast(self):
    self.__test()

# 객체 생성
a = A()

# 오류 발생 코드
# a.__test()

# private 메소드 접근방법
# 1) 변형된 이름을 통해 접근가능: '_클래스이름__private메소드'
print('a ----------------------')
a._A__test()

# 2) 우회경로로 접근가능
a.bast()

# 객체 생성
b = B()

# private 메소드 접근
print('b ----------------------')
b._B__test()
b.bast()

# 오류 발생 코드
# print(a.__X)

# __X 변수 접근
print('X ----------------------')
print(a._A__X)
print(b._A__X)
print('\n')

# 상속을 받았기 때문에 B클래스의 인스턴스에서 A클래스의 함수와 변수도 확인가능하다.
# dir(객체): 파이썬 내장메소드로 해당 객체가 어떤 변수와 메소드를 가지고 있는지 나열
print('[부모클래스 A를 사용해 생성한 객체 a의 변수와 메소드]')
print(dir(a))

print('[부모클래스 B를 사용해 생성한 객체 b의 변수와 메소드]')
print(dir(b))       
```

- 속성 충돌

  - _와 __의 활용에 대해 생각

  - 프로그램이 길어지고 다양한 변수를 선언하는 경우 클래스의 속성이 충돌(변수의 중복)할 수 있다.

```python
# 속성충돌

class parent_class:
  def __init__(self):
    self.value = 30
    self._value = 40
    self.__value = 50

  def get(self):
    return self.value

class sub_class(parent_class):
  def __init__(self):
    super().__init__()
    self.__value = 20    # 위의 parent_class의 _value와 충돌(값의 중복)발생

s = sub_class()
print(s.value) # public
print(s._value)# protected

print('어떤 클래스에서 값을 받아오냐에 따라 값의 정보가 바뀜--')
print(s._parent_class__value)
print(s._sub_class__value)
print('parent_class value:',s.get(),' sub_class value:', s.value)
```

- 속성의 충돌(같은 값)이 발생하는 이유는 대체로 프로그램에서 중복되는 속성(attribute)을 활용하는 경우

- 속성명을 다르게 해줘도 되지만 파이썬에서 활용할 수 있는 '비공개 속성' 을 활용할 수 있다.

- 비공개 속성은 위에서 설명한 '__'를 활용

```python
# 속성충돌방지(언더바와 접근제어의 개념을 활용하여 같은 변수이름끼리 헷갈리지 않도록 한다.)

class parent_class:
  def __init__(self):
    self.__value = 10   # parent_class는 '__'

  def get(self):
    return self.__value # parent_class는 '__'

class sub_class(parent_class):
  def __init__(self):
    super().__init__()  # parent_class 호출을 위해 super() 사용
    self._value = 20    # sub_class는 '_'


s = sub_class()
print('parent_class value:',s.get(),' sub_class value:', s._value) 
```

#### super

- 자식 클래스가 부모클래스가 가지고 있는 모든 매개변수(파라미터, arguments)를 사용

- 상속을 통한 재사용을 하는 경우, 아래와 같이 다른 매개변수(graduation_date)도 신규 생성할 수 있다

```python
class Student:    # 부모클래스
     def __init__(self, name):
         self.name = name
         print(self.name)

class Graduate(Student):    # 부모클래스 상속받음
     def __init__(self, name, graduation_date): 
         super().__init__(name)   # super를 활용하여 부모 메소드를 호출하여 name 매개변수 재사용(super를 사용하면 부모클래스의 상속받는다는 것을 의미함)
         self.graduation_date = graduation_date

print('출력1: ', end='')
a_student = Student('stu_class')
print('출력2: ', end='')
a_graduate = Graduate('gradu_class',11)

print('출력3: ', end='')
a_student.__init__('stu')
print('출력4: ', end='')
a_graduate.__init__('gradu',11)

# graduate 인스턴스 생성
print('출력5: ', end='')
print(a_graduate.name)

print('출력6: ', end='')
print(a_graduate.graduation_date)
```

- 리스트 반복의 경우 range와 enumerate 내장함수를 비교하면서 사용해보는게 좋다

```python
# range보다는 enumerate를 사용한다.
# range 내장 함수는 정수집합을 반복하는 상황에서 유용하다.

# 하지만 리스트에 대해서 특정 인덱스에 따라 반복을 하는 경우, list의 길이를 알아야하고(len함수 써야함), 
# 인덱스를 사용해 배열원소에 접근해야 한다.(index함수 써야함)

# case 1 - range를 통한 반복
fla_list = ['A','B','C','D']

len_list = len(fla_list)            # len을 통해 리스트 길이 확인
index_list = fla_list.index('B')    # index를 통해 배열원소 접근

for i in range(0, len_list):
  print('range with len method : ',i)

print('index method : ',index_list)
```

```python
# 리스트 반복의 경우 enumerate 내장함수를 사용해보는게 좋다.

# case 2 - enumerate 활용
fla_list = ['A','B','C','D']
enu_list = enumerate(fla_list)
# print(enu_list)
# print(next(enu_list))
# print(next(enu_list))

# enumerate는 인덱스와 값을 함께 출력해주기 때문에 상황에 따라 다양하게 활용해볼 수 있다.

for i,enu_list in enumerate(fla_list):
  print(f'{i+1}: {enu_list}')
```

```python
# 위의 방법을 range로 해보고 비교해보자.

for i in range(0,len(fla_list)):
  fla = fla_list[i]
  print(f'{i+1}: {fla}')
```

# Review

---

###### 오늘 배운 것

```
1) 프로그래밍 패러다임을 통한 작동방식
2) OOP 기본코드설계
3) OOP관련 개념
```

###### 오늘 해야 할 것

```
1) OOP 기본 용어 익숙해지기
2) OOP 개념관련 그림 및 소스코드 익숙해지기
3) 자신이 알기쉽게 정리해보기(자신만의 예시)
```

# Reference
[실제 사례로 살펴보는 좋은 설계](https://velog.io/@codemcd/%EC%9A%B0%EC%95%84%ED%95%9C%ED%85%8C%ED%81%AC%EC%84%B8%EB%AF%B8%EB%82%98-%EC%9A%B0%EC%95%84%ED%95%9C%EA%B0%9D%EC%B2%B4%EC%A7%80%ED%96%A5-%EC%9D%98%EC%A1%B4%EC%84%B1%EC%9D%84-%EC%9D%B4%EC%9A%A9%ED%95%B4-%EC%84%A4%EA%B3%84-%EC%A7%84%ED%99%94%EC%8B%9C%ED%82%A4%EA%B8%B0-By-%EC%9A%B0%EC%95%84%ED%95%9C%ED%98%95%EC%A0%9C%EB%93%A4-%EA%B0%9C%EB%B0%9C%EC%8B%A4%EC%9E%A5-%EC%A1%B0%EC%98%81%ED%98%B8%EB%8B%98-vkk5brh7by)

[파이썬 더블 언더스코어: Magic Method](https://corikachu.github.io/articles/python/python-magic-method)

[파이썬 슬라이싱 기본과 예제](https://twpower.github.io/119-python-list-slicing-examples)

###### 참고
[OOP와 함수의 연관성](https://youtu.be/rbWSTXBYNFA)

[클래스와 인스턴스](https://youtu.be/8B2Wxks5Sig)

[객체지향 핵심 개념](https://gracefulprograming.tistory.com/130)

[OOP란](https://velog.io/@hkoo9329/OOPObject-Oriented-Programming-%EA%B0%9D%EC%B2%B4-%EC%A7%80%ED%96%A5-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%EC%9D%B4%EB%9E%80)

[언더스코어(_)](https://mingrammer.com/underscore-in-python/)