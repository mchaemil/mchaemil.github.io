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

[ERD Cloud](https://www.erdcloud.com/d/o7q5xcQuyHSf8MtfP) 를 관계형 데이터베이스에서 사용될 수 있는 논리적 모델로 바꾸는 연습을 해보았다.

> 아직은 부족한 부분이 많지만 이 한 걸음을 시작으로..! 계속 발전해야겠다.! 그래도 아직까지는 어렵다는 생각보다는 이런 걸 그려본다는 사실이 신기하고 재미있다!

![ERD_1](https://user-images.githubusercontent.com/40027211/71552913-ac99e480-2a48-11ea-99b8-6e2517b0553c.PNG)


- 중첩 도큐멘트는 일대일
- 배열 구조는 1:N이 나온다...!


데이터의 성격을 알아내면 데이터를 꺼낼 수 있다. 어떠한 속성을 이용해서...! 
변수를 통해 저장해두면 다른 곳에서 쓸 수 있다.
find를 통해 반환한 커서는 연속적인 객체다. 지나가버리면 잊혀지므로! findOne을 사용해 document를 활용해야 한다.

- find 는 cursor를 반환한다.
- findOne은 document를 반환한다.

