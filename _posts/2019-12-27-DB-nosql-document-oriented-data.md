---
layout: article
title: Database/Data | NoSQL - Document Oriented Data
tags: NoSQL

---

## **Today What I Learend**  

MongoDB 가 왜 도큐먼트 지향 데이터 모델인지 좀 더 자세히 학습하는 시간을 가졌다.. 아직은 너무 어렵고... 낯설지만..!
이해하기 위해 노력하는 시간을 가져야지

그리고 모델링을 그려보는 시간을 가졌는데, 이를 더 잘할 수 있도록 
노력해봐야겠다. 뭔가 재밌는 거 같다..ㅋㅋㅋ 잘 맞는 공부이기를...!


---
**Today I Learend**

- DB 스키마 설계의 원리
- MongoDB Document를 보고 관계형 DB로 테이블 모댈링 하기
- 

---

### DB 스키마 설계의 원리

스키마 설계는 애플리케이션에 대한 요구사항을 데이터가 가장 잘 소화할 수 있는 최적의 표현을 찾아내는 과정이다.

데이터의 타입, 길이, 값을 유지해야 하는가, 선택적인가 하는 특성을 반영해서 스키마를 정의를 한다.

#### Schema less

타입에 따라서 디테일이 달라질 수 있다.
관계형 데이터베이스는 Null 값을 가지고 있는 녀석이 많을 수 있다.

#### RDBMS에서는 Null이 어떠한 영향을 주는가?

관계형 데이터베이스에는 Null 을 처리하기 위한 함수들이 따로 있다. Null은 카운트가 되지 않는다. 그러므로 따로 처리를 해주어야 하는데, Null Value Function과 같은 것으로 적절하게 Null 값을 변환시켜야만
원하는 값을 얻을 수 있다.

> 저는 아직 관계형 데이터베이스에서 Null 값을 변환하는 처리를 해본 적이 없습니다.. 더 연습해야 할 부분..!

#### 데이터 분석에서 Null은 어떠한 영향을 미치는가?
**Null: 결측값**
데이터 분석에서 Null은 결측값이라고 해서 전처리를 해야 한다. 분석을 위한 전처리는 비용이 많이 들어가는 일이다. 일단 이 값이 왜 Null인지 찾아야 하며..! 어떻게 바라봐야 할 것인지 등.. 어려움이 많다..!


### MongoDB Document를 보고 관계형 DB로 테이블로 모델링 하기

> 데이터를 보면서 데이터 구조에 대해 떠올릴 수 있어야 하므로..! 이러한 요구를 해주신 건 아닐까?

```mongodb
doc =
{ _id: ObjectId("6a5b1476238d3b4dd5000048"),
  user_id: ObjectId("4c4b1476238d3b4dd5000001"),
  // 존재하지 않는 것을 참조할 수 있다. MongoDB는 참조 무결성이 없다.
  purchase_data: new Date(),

  state: "CART",

  // 주문항목이 실제로는
  // 몇건이 있는지 조회하기는 위해 line_items_count.를 만들어서 조회해오게 설계한다.
  line_items:  [ 
    { _id: ObjectId("4c4b1476238d3b4dd5003981"),
      sku:  "9092",
      name:  "Extra Large Wheel Barrow",
      quantity:  1,
      pricing:  {
        retail:  5897,
        sale:  4897,
      }
    },
    // id를 가지고 있으면 참조가 쉽다.
    { _id:  ObjectId("4c4b1476238d3b4dd5003981"),
      sku:  "10027",
      name:  "Rubberized Work Glove, Black",
      quantity:  2,
      pricing: {
        retail:  1499,
        sale:  1299,
      }
    }
  ],

  shipping_address:  {
     street: "588 5th Street",
     city: "Brooklyn",
     state: "NY",
     zip: 11215
   },

  sub_total:  6196
}
```

#### 관계형 DB 테이블 구조로 변환해서 ERD 작성

[ERD Cloud](https://www.erdcloud.com/d/o7q5xcQuyHSf8MtfP)   
MongoDB Document를 보고 관계형 데이터베이스에서 사용할 수 있는 논리적 모델로 바꾸는 연습을 해보았다.

> 아직은 부족한 부분이 많지만 이 한 걸음을 시작으로..! 계속 발전해야겠다.! 그래도 아직까지는 어렵다는 생각보다는 이런 걸 그려본다는 사실이 신기하고 재미있다!

![ERD_1](https://user-images.githubusercontent.com/40027211/71552913-ac99e480-2a48-11ea-99b8-6e2517b0553c.PNG)


- 중첩 도큐멘트는 일대일
- 배열 구조는 1:N이 나온다...!


데이터의 성격을 알아내면 데이터를 꺼낼 수 있다. 어떠한 속성을 이용해서...! 
변수를 통해 저장해두면 다른 곳에서 쓸 수 있다.
find를 통해 반환한 커서는 연속적인 객체다. 지나가버리면 잊혀지므로! findOne을 사용해 document를 활용해야 한다.

- find 는 cursor를 반환한다.
- findOne은 document를 반환한다.

---


#### 오브젝트 아이디가 배열 안에 들어와 있다면????
오브젝트.. 아이디에 대한 값이 배열 안쪽에 들어오면
참조에 대한 이야기이므로
다대다..! N:M으로 이해하면 된다. 

업무 => 숙련
숙련된 작업자는 SKU로 검색을 한다.
숙련된 사람들은 SKU로 검색을 한다. 


인덱스를 다는 데에는 정석과 같은 정답은 존재하지 않는다.
다만 일을 하다보면 인덱스가 대상이 되는...! 

explain을 증명을 위해서 사용까지 해봤다. 

#### Mongo Code
db.products.createIndex({'name':1}) 를 통해서 None Unique 인덱스를 만들 수 있다.
db.products.getIndexes() 를 통해서 인덱스 구성을 확인할 수 있다. 


executionStats

> db.categories.insert(doc)
> db.categories.find().pretty()
> db.products.find({category_ids: ObjectId("6a5b1476238d3b4dd5000048")})
> db.products.find({category_ids: ObjectId("6a5b1476238d3b4dd5000048")}).pretty()

> db.products.createIndex({'slug':1}, {unique:true})
> db.products.getIndexes()
> db.products.findOne({"slug" : "wheel-barrow-9092"})

#### it
cursor = db.numbers.find() 

cursor.next()
cursor.hasNext()


find() 는 기본적으로 파싱이 이루어져서 가장 베스트한 결과를 가지고 온다.
파인드를 했을 때 실제로 메모리상에 있던 어떤 문서에서 
데이터를 메모리의 어떤 영역으로 올릴 때
데이터 버퍼라고 하고..!
메모리 영역으로 올렸다가 그 내용을 우리에게 전달하는 과정에서
만들어지는 메모리 영역을 커서(cursor)라고 부른다.
커서는 첫번쨰 행은 first, 첫번쨰 앞은 before first
마지막 행은 rest..! rest 바로 뒤는...! after rest


커서를 반환해주는 함수냐..! 
다큐멘트를 반환해주는 함수냐에 따라 차이가 생긴다.!!

#### findOne은 다큐멘트를 반환해주는 함수이므로 explain이 작동하지 않았다!!.
커서를 반환해주는 함수냐..! (find는 cursor를 반환해줌..!)
다큐멘트를 반환해주는 함수냐에 따라 차이가 생긴다.!!
findOne은 이 녀셕, var ret = cursor.next(); 을 반환해줌...! 


cursuor.next()



prod를 입력해보면 다큐먼트가 나오는데

find()로 찾으면...!prod 변수에 담은 녀석은 커서이다...!

findOne()으로 찾아야...! 객체가 된다...!

#### 퀴리 셀렉터를 사용할 때
hasNext()가 된다면...! 
findOne을 사용하자!!! 


#### 이 프로덕트가 어떤 카테고리에 속해있는지 알고 싶을 떄


아이디를 가지고 있는 경우
아이디가 없으면 종속된다. 종속되는 경우는 identifying relationship


#### reviews!
db.reviews.insert(doc)

"slug" : "wheel-barrow-9092" 

인 상품에 관련되어 있는 상품평 리뷰정보를 조회해 보기

1. 일단은 어디에서 질의를 해야 하는가?
1. db.reviews.find()
1. db.product.find({"slug" : "wheel-barrow-9092"})
1. product = db.product.findOne({"slug" : "wheel-barrow-9092"}) 를 통해서 프로덕트 정보를 얻은 후
1. db.reviews.find({product_id: product._id}).pretty() 를 통해서 알 수 있다.
1. db.reviews.find({product_id: product._id}, {helpful_votes: 1})
1. db.reviews.findOne({product_id: product._id}, {helpful_votes: 1})

```
db.reviews.findOne({product_id: product._id}, {helpful_voter_ids: 1})
doc.voter_ids
```

```
### 교재에 없는 내용
db.createCollection('user_actions',
    {capped: true, size: 16384, max:100},
)

#### 바꾸어서 진행해보기
db.createCollection('user_actions',
    {capped: true, size: 8192, max:20},
)


for(i = 0; i < 25; i++){ 
doc = {username:'hong', action_code: Math.floor(Math.random() * 4), time: new Date(), n: i} 
db.user.actions.insert(doc) 
}

> db.createCollection('user.actions', {capped:true, size:8192, max: 20})
{ "ok" : 1 }
> for(i=0; i<25; i++) {
... doc = {time: new Date(), n:i}
... db.user.actions.insert(doc)
... }
WriteResult({ "nInserted" : 1 })
> db.user.actions.find().pretty()

```




### TTL 

#### Time To Live

생존시간에 대한 개념을 집어넣어서 사용한다. 
어떠한 기능을 애플리케이션에서 만들어서 쓰는 경우와
만들어진 기능을 가져다 쓰는 경우..! 가 있다..!


### JS 자료형
문자열, 전부다 문자열이다. "",'' 


#### 숫자!
자바스크립트는 태생적으로 
정확한 수 계산을 위해서 만들어진 언어가 아니므로!
정밀하고,, 범용성이 높은 규격을 선택했다..! 

IEEE 754 (아이트리플E 라는 규격을 따르고 있다)
IEEE 754 는 크기가 64비트이기 때문에 정밀한 값을 표현하는데 좋다.
플로팅 포인트 넘버(floating point number), 부동소수점 숫자 = 정밀한 숫자!! 정밀하다는 것은 정확하다는 뜻이 아니다. 
1.0 과 1은 다르다. 1.0은 1에 아주 근사(근접)한 수이다. 

픽스드 포인트 넘버(fixed point number), 고정소수점 숫자
정수는 항상 오른쪽에 소수점이 고정되어 있어서 
소수부를 사용하지 않는다. 

#### 정확한 수는 계산할 때 사용한다!!


스탑워치는 정밀해야 한다.
정밀과 정확은 다르다.!! 


n = 5라면
5가 정수가 아니라 더블형이다.  


##### 숫자의 길이 
int는 32비트
long은 64비트

넘버 인트로 저장했다면 16

데이터를 정확하게 다루고자 한다면 타입을 지정해야 한다!!


#### Root and Category
최상위 카테고리가 널인 것들을 뽑으면...!
키테고리가 된다.
parent가 없으면 최상위, 즉 루트 카테고리가 된다..!!


