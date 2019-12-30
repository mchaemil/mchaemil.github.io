---
layout: article
title: Database/Data | B-tree 란 무엇인가? B-tree에 대한 이해를 통해서 무엇을 얻을 수 있을까?
tags: Text

---

## **Today What I Learend**  

B-tree 를 학습하기 전 모아둔 질문들... B-tree에 대해서 학습하면서 아래의 의문들이 해결되기를 기대해본다...

- B-tree와 인덱스 무슨 관계가 있을까?
- B-tree를 이해하기 위해 미리 이해하고 있어야 하는 개념은 무엇인가?
- B-tree란 무엇인가
- 관계형 DB와 문서 지향형 DB에 대한 이해가 깊지 않은 상황에서 B-tree에 대한 이해가 필요한 이유는 무엇일까?
- B-tree는 어디에 쓰일까?
- B-tree에 대한 이해는 전체 DBMS를 이해하는 과정 속에서 어느 곳에 위치하는 것일까?
- 쿼리 옵티마이저를 이해하기 위해 필요한 B-tree

이러한 의문들을 해결해나가는 과정을 밟아나가다보면 자연스레 B-tree에 대한 이해도 키워질 것이라고 생각한다.


---
**Today I Learend**

- 학습 목표
- B-tree와 인덱스 무슨 관계가 있을까? 글을 시작하며 생각해보는 B-tree와 인덱스의 관계
- 인덱싱을 이해하는 게 중요한 이유
- B-tree란 무엇인가
- B-tree와 인덱스 무슨 관계가 있을까? 글을 마치며 생각해보는 B-tree와 인덱스의 관계 


---

### 학습 목표

MongoDB를 통해 높은 성능을 얻기 위해서는 효율적인 쿼리를 설계해야 하며, 이를 위해서는 인덱스를 적절하게 생성해야 한다. 
인덱스가 왜 중요하며, 쿼리 옵티마이저가 어떻게 인덱스를 선택하고 찾아나가는지에 대해 이해하는 과정을 통해서 MongoDB에서 성능을 높이기 위한 방법에 대해 고민해본다!

### B-tree와 인덱스 무슨 관계가 있을까? 글을 시작하며 생각해보는 B-tree와 인덱스의 관계


#### B-tree를 이해해야 MongoDB의 효율적으로 사용할 수 있다. 
MongoDB 를 효율적으로 사용하고 하드웨어 자원을 최대한으로 이용하려면 인덱싱을 이해해야 한다. B-tree는 MongoDB의 인덱스를 내부에서 구현하고 있는 데이터 구조이다.


### 인덱싱을 이해하는 게 중요한 이유

#### B-tree를 이해하기 위한 선행개념
- 인덱스
- 복합 인덱스
- 인덱스 효율

#### 인덱싱
인덱싱을 이해하기 위해서는 요리법이 담긴 1만 페이지의 책을 상상하면 쉽게 이해할 수 있다. 가령, 여기서 시금치가 들어간 감자샐러드를 찾으려 한다면 유일한 방법은 해당 요리법이 나올 때까지 책을 훑어나가는 것이다. 만약 그 요리법이 8,999페이지에 존재한다면.. 8,999페이지까지 책을 보아야 한다.

#### 단일 인덱스
책을 전부 살펴보는 방법으로 요리법을 찾는 것은 큰 비용이 발생하는 일이다. 이를 효율적으로 수행하기 위해서 좋은 방법 중 하나는 이름으로 요리법을 찾는 것이다. 모든 요리법의 이름과 페이지 번호를 나열해 놓는다면 이 책은 인덱스가 된 것이다.
- 시금치 감자샐러드 8,999
- 양파 카레 24

요리법의 이름을 안다면 인덱스를 이용한다면 신속하게 찾을 수 있다.

#### single key index
**_id로 생성되는 기본 인덱스는 빠른 검색을 위해 인덱스에 저장된다.**

#### 복합 인덱스
재료에 대한 요리법 목록만 필요하다면 단일 인덱스로 충분하지만, 요리법에 대해 어떤 다른 정보를 찾고 있다면 단일 인덱스로는 부족한 점이 많다. 

이러한 지점을 보완하기 위해서 복합 인덱스는 재료-요리 이름의 순서로 사용한다. 요리할 재료 목록에서 해당 재료를 포함하고 있는 모든 요리법을 얻을 수 있다. 

#### compound-key index

> 아래 코드에서 `$gt` 를 `gt`로 표현

```mongodb
db.products.find(
	{item:'monitor'},
	{price:{
		gt:3000
	}},	
)
```


위의 쿼리를 통해 30달러보다 비싸고 품목이 모니터인 상품을 찾을 때, 단일 키 인덱스에 대해 실행하면 두 개의 인덱스 가운데 하나면 사용되며 쿼리 옵티마이저는 두 인덱스 중에서 가장 효율적인 인덱스를 선택하지만, 그렇게 효율적이지 않다.

효율을 높이기 위해서는 복합 인덱스를 사용해 각 엔트리를 하나 이상의 키로 구성한다. compound-key index를 사용하면 품목이 모니터이고 가격이 3000이상인 첫 번째 엔트리를 시작으로 품목이 모니터가 아닌 엔트리를 발견할 때까지 인덱스 내의 엔트리를 스캔한다. 

> 이를 통해 compound-key index에서 키의 순서는 매우 중요하고, 쿼리에서 적용하는 방법에 대해서 학습하면서 더 깊이 이해하는 과정이 중요할 것 같다!



#### 인덱스 효율을 위해 고민해야 할 지점
쿼리의 성능을 높이기 위해 인덱스가 필요하지만 인덱스를 생성하는 데 비용이 발생하므로 주의를 가지고 생성해야 한다.

인덱스가 적합하게 만들어졌을지라도 인덱스와 현재 작업 데이터를 램에서 다 처리하지 못한다면 성능상의 이슈가 발생할 수 있다.

데이터가 요청될 때마다 운영체제는 그 데이터가 램에 있는지 확인해야 한다. 만약 램에 없다면 Page Fault를 발생시키고 디스크에 액세스하여 램으로 불러들여야 한다. 그런데 최악의 경우 데이터의 크기가 사용 가능한 램의 크기보다 크다면, 모든 작업(읽기 및 쓰기)에 대해 디스크 액세스를 해야 하는 성능저하 상황이 발생할 수 있는데 이를 Thrashing이라고 한다. 




### B-tree란 무엇인가

앞서 말했지만 B-tree는 MongoDB의 인덱스를 내부에서 구현하고 있는 데이터 구조이다. MongoDB는 B-tree로 인덱스를 생성한다.

> 1970년대 말부터 DB의 레코드 및 인덱스로 B-tree 는 많은 곳에서 사용되었다.

B-tree에 대한 이해가 있다면 인덱싱에 관한 대부분의 지식을 MongoDB에서도 그대로 활용할 수 있고, 이해도 높일 수 있다.


#### 관계형 DB와 문서 지향형 DB에 대한 이해가 깊지 않은 상황에서 B-tree에 대해 어느 정도 수준까지 이해할 수 있을까?
B-tree는 Database 인덱스에서 두 가지의 특성을 지닌다. 
1. 정확한 일치, 범위조건, 정렬, 프리픽스 일치 등 다양한 쿼리를 수월하게 처리해준다.
1. 키가 추가되거나 삭제되더라도 균형 잡힌 상태를 유지한다.

> B-tree 쿼리를 수월하게 처리해준다고 한다. 쿼리를 수월하게 처리하는 매커니즘을 이해한다면 데이터베이스 자체에 대한 이해도 깊어질텐데 아직까지는 낯설다..! 더 익숙해지기 위해 노력해야겠다..!


#### B-tree 에 대해 이해를 높이기 위한 정리
가령, 생성한 인덱스를 추상적으로 표현했을 때, B-tree구조는 트리 구조와 비슷한 데이터 구조를 갖는다. 

![주석 2019-12-30 042259](https://user-images.githubusercontent.com/40027211/71561659-a3e2f600-2abc-11ea-8190-451f61bd7fe5.png)


MongoDB에서 구현된 B-tree는 새 노드에 대해 8,192바이트를 할당하는데, 인덱스의 평균 크기에 따라 달라질 수 있지만 하나의 노드가 수백 개의 키를 가질 수 있다는 것을 의미한다. 

각 노드는 빈 공간을 가지고 있다. 이를 통해 인덱스 사이즈가 어떻게 설정되어 있는지 조금은 이해할 수 있게 된다. B-tree 노드는 60% 정도만을 사용하도록 의도적으로 설정되어 있다. 이 정보에 대해 이해가 있다면 인덱스를 업데이트 하는데 필요한 공간 및 시간적인 부분을 통해서 인덱스가 비용이 드는 이유를 알 수 있다. 

### B-tree와 인덱스 무슨 관계가 있을까? 글을 마치며 생각해보는 B-tree와 인덱스의 관계 

**'B-tree에 대한 이해가 생기면 컬렉션에 인덱스를 생성해야 할 시기와 인덱스를 피해야 할 시기를 결정할 수 있다.'** 고 추론할 수 있다..! 



---


### 쿼리 옵티마이저를 이해하기 위해 필요한 B-tree

쿼리 옵티마이저는 쿼리를 가장 효율적으로 실행하기 위해 어떠한 인덱스를 사용할지 결정하는 소프트웨어이다. 

> 아직은.. 쿼리 옵티마이저를 이해하기 위해 B-tree가 어떠한 역할을 하는지 모르겠다.. 이 부분에 대한 이해가 생기면 추가로 채워 넣어야겠다..

