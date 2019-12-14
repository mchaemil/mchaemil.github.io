---
layout: article
title: Python/Class | 파이썬의 객체지향
tags: python

---

## **Today What I Learend**  

파이썬으로 장고를 학습하기 위해서는.. 
class 개념이 대한 이해가 필요하다고 한다. 
생각해보면 모든 프로그래밍의 문법은 더 복잡한 것을 간단하게 풀어내기 위한 과정으로 수렴하는 것이 아닌가 싶다..!

현실세계에 존재하는 사물이나 대상을 가상의 세계에서 표현하기 위해 등장한 패러다임이 OOP이다. 이러한 패러다임을 적극적으로 이해한다면 나도 다른 객체지향 언어들을 잘 다룰 수 있을까?

---
**Today I Learend**
- 객체지향 이야기
- Class 
- ㄹㄹㄹ

---


### 객체지향이란?

[출처:위키백과](https://ko.wikipedia.org/wiki/%EA%B0%9D%EC%B2%B4_%EC%A7%80%ED%96%A5_%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D)
> 객체 지향 프로그래밍(영어: Object-Oriented Programming, OOP)은 컴퓨터 프로그래밍의 패러다임 중 하나이다. 객체 지향 프로그래밍은 컴퓨터 프로그램을 명령어의 목록으로 보는 시각에서 벗어나 여러 개의 독립된 단위, 즉 "객체"들의 모임으로 파악하고자 하는 것이다. 각각의 객체는 메시지를 주고받고, 데이터를 처리할 수 있다.

### class 와 객체(object)

클래스는 붕어빵의 틀에 비유할 수 있다. 붕어빵 틀이 붕어빵을 만들어내는데만 사용되는 것처럼 클래스 또한 객체를 생성하는 데만 사용된다. 
대상의 property는 변수로 표현하고, 대상의 behavior는 메서드로 표현한다. 그리고 관련된 속성과 행동을 모아서 하나의 묶어서 실제 대상을 표현한다. 

```python

americano = '아메리카노'
americano_price = 2600


```
위의 두 값은 사람이 보기에는 연관성을 지니지만 컴퓨터가 보기에는 연관성이 없다. 그렇지만 위의 두 값을 객체를 통해서 표현하면 하나의 데이터로 묶을 수 있다. 

```python

class Americano:
	def __init__(self, name, price):
		self.name = name	
		self.price = price
	def print(self):
		print(self.name, '의 가격은', self.price ,'원이니 저렴해!')

```

```python

# exam1
class UserInfo:
  # attr, method
  def __init__(self, name: str):
    print('success init')
    self.name = name
  def user_info_p(self):
    print('Name: ', self.name)
	
# 네임스페이스, 인스턴스가 가지고 있는 자신만의 저장공간
user1 = UserInfo('haemil')
user1.user_info_p()

user2 = UserInfo('ham')
user2.user_info_p()

# 인스턴스는 각각 자신만의 공간을 가지고 있다. 
# 설령 같은 데이터를 담고 있을지라도 다른 객체이다!!
print('user1의 메모리주소: ',id(user1))
print('user2의 메모리주소: ',id(user2))

print('user1의 dict: ', user1.__dict__)
print('user2의 dict: ', user2.__dict__)

```

	
```python

# 예제2
# self 의 이해
class SelfTest:
  def function1(): # class method
    print('function1 called!')
  def function2(self): # instance method
    print('function2 called')

self_test = SelfTest()
# self_test.function1()

SelfTest.function1()
self_test.function2()

```




```python

# 예제3
# 클래스변수, 인스턴스 변수(self!)

class WareHouse:
  stock_num = 0
  def __init__(self, name):
    self.name = name
    WareHouse.stock_num += 1
  def __del__(self):
    WareHouse.stock_num -= 1

user1 = WareHouse('Kim')
user2 = WareHouse('Park')
user3 = WareHouse('Lee')

print(user1.__dict__)
print(user2.__dict__)
print(user3.__dict__)
print(WareHouse.stock_num) # class Namespace, 클래스 변수를 인스턴스간에 공유한다

# 값이 공유 가능한 예시
print(user1.stock_num) # 자기 네임스페이스에 없다면, 클래스 네임스페이스 가서 찾는다.

print(user1.name)

del user1

# 자기 자신의 네임스페이스를 가진다. dir로 확인가능!!
print('user2.__dir__',user2.__dir__)
print('user2.stock_num: ',user2.stock_num)

```

### 상속(inheritance)

사용하고 있던 클래스를 다시 재사용하여 새로운 클래스를 만들어내는 것을 상속이라고 한다. inheritance 는 적은 양의 코드를 사용해서 새로운 코드를 만들어낼 수 있으므로 추가 및 변경하는 작업을 하는데 매우 편하다. 

```python

# 상속, 다중 상속
print('\n====상속, 다중 상속====')

# 부모에게 물려받는 것을 말한다. 상속은 객체지향에서 주는 이점이 너무 많다.
# python은 다중상속을 지원한다. (대신 자바는 인터페이스)

```


