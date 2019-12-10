---
layout: article
title: Python/Class | 파이썬의 객체지향
tags: python

---

## **Today What I Learend**  

장고를 학습하기 위한.. 과정의 하나로 파이썬의 객체지향


---
**Today I Learend**
- 객체지향 이야기
- Class 
- ㄹㄹㄹ

---




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

# 상속, 다중 상속
print('\n====상속, 다중 상속====')

# 부모에게 물려받는 것을 말한다. 상속은 객체지향에서 주는 이점이 너무 많다.
# python은 다중상속을 지원한다. (대신 자바는 인터페이스)
