---
layout: article
title: Python/Manage Collection, Module, Except, Manage File
mathjax: true
tags: python

---

**Today What I Learend**  
파이썬의 컬렉션을 관리하는 고급 기법, import를 통해 수학, random, 시간 관련 모듈을 활용하는 방법 및 직접 모듈을 만들어보는 법, 
프로그래밍의 꽃인 예외를 작성하는 법, 파일 입출력 등을 학습했다. 

프로그래밍의 본질에 가깝지는 않지만 복작한 작업을 더 간단하게 해주고, 실수를 줄여주는 다양한 도구들을 익히는 시간을 가졌다.

---
**Today I Learend**
- Manage Collection
- Module
- Except
- Manage File

---


### 컬렉션 관리 함수

여러개의 값을 저장하는 컬렉션은 관리하는 방법이 비슷한데, 그 중 컬렉션을 관리하는 함수는 enumerate, lambda 등이 있다.


#### enumerate
enumerate는 순서값과 요소값을 같이 구해주는 컬렉션의 내장 함수이다. 

```python

score = [30, 40, 50, 60, 70, 80]
count = 1
for i in score:
    print(i, '번 학생의 성적:', i)
    count += 1

for check, value in enumerate(score, 1)
    print(check, '번 학생의 성적', value)

```

#### zip
여러개의 값을 저장하고 있는 컬렉션을 요소별로 짝지어서 하나로 합칠 경우에는 zip 함수를 사용한다.   
- 리스트의 길이가 달라도 상관없고, 짧은 리스트를 기준으로 튜플 리스트를 만듦

```python
yoil = ['월', '화', '수', '목', '금']
date = ['12월 2일', '12월 3일', '12월 4일', '12월 5일']
for y, d in zip(yoil, date):
    print("{}요일은 {}입니다.".format(y, d))

# 월요일은 12월 2일입니다. ...
```

#### lambda 함수 `success`{:.success}
lambda 함수는 함수를 정의하는 축약된 방법으로 인수로 전달하기 위한 함수를 축약 표현에 따라 간편하게 작성하는 방법을 말한다. 
함수를 파라미터로 전달할 때 함수의 이름으로 전달하지 않고, 실행 코드를 전달함으로써 얻는 직관적인 이해가 람다 함수의 사용을 통해 얻을 수 있는 이점이다. 
- 함수 이름을 직접 찾으러 가는 불편함을 줄일 수 있고
- 직관적인 코드 흐름을 만들어낼 수 있다.
- 단, 여러곳에서 반복해서 쓰일 때는 함수로 빼는 게 낫다.


###### 함수의 파라미터로 함수를 넘기는 방식을 보니 javascript의 화살표 함수가 생각이 났다

```python

lambda x: x + 1 # 파이썬의 lambda function 
(x) => {x + 1} // javascript의 arrow function

```

#### filter - lambda function
조건에 맞는 요소 골라낼 때 filter 함수를 사용할 수 있다. 

```python
score_list = [30, 40, 50, 60, 70, 80]
for score in filter(lambda x: x > 60, score_list):
    print(score) # 70 80
```

#### map - lambda function  
원하는 타입으로 데이터를 가공해야 할 때 map 함수를 사용할 수 있다. 

```python

score_list = [3, 4, 5, 6, 7, 8]
for score in map(lambda x: x * x, score_list):
    print(score) # 9 16 25 36 49 64

```

### 컬렉션 불변성을 위한 기법
기본형 변수는 대입 연산자로 값을 복사했을 경우 독립적인 값을 유지하는 반면, 컬렉션에서는 독립적인 값을 유지하지 못한다. 이는 원본과 복사한 값이 같은 메모리를 가리키고 있기 때문인데, 이로 인해 원본의 불변성을 지키기 위해서는 copy() 메소드를 사용해 복사한다.

- copy 메서드는 원본과 똑같은 컬렉션을 만들어서 반환한다.

```python
import copy
numbers1 = [1,2,3]
numbers2 = numbers1.copy()

numbers2[2] = 77
print(numbers1)
print(numbers2)

```

- deepcopy 메서드는 컬렉션의 불변성을 돕는 함수이다. copy모듈의 deepcopy 함수의 인자로 복사할 컬렉션을 전달한다.

```python
import copy

list1 = [1,2,3]
list2 = [list1, 4, 5]
list3 = copy.deepcopy(list2)

list3[0][1] = 99
print(list1) # [1,2,3]
print(list2) # [[1,2,3], 4, 5]
print(list3) # [[1,99,3], 4, 5]
```


