---
layout: article
title: Database/Data | NoSQL - MongoDB CRUD, index, explain
tags: NoSQL
comments: true

---

## **Today What I Learend**  

MongoDB 에서 자바스크립트 셸을 통해서 document를 CRUD하는 과정을 통해 조금은 MongoDB와 친해지는 시간을 가지려 노력했다.


---
**Today I Learend**

- MongoDB 실행
- MongoDB의 CRUD
- CREATE
- READ
- UPDATE
- DELETE

---


### update

두 가지가 가장 중요하다. 아래 내용을 이해했는가?
1. $set 
2. 대치

index와 성능의 문제! => 성능에 대한 것을 살펴보기 위해서는
explain이라는 도구를 사용해서 성능의 개선 여부를 확인해볼 수 있다.

index를 만들 때는 
db.|collection name| create index 로 인덱스를 생성하고
getIndex()로 확인해볼 수 있다.

### 몽고는 index를 어디에다가 걸어야 하는가?
#### 몽고는 Index를 조건으로 사용하는 키에다가 걸면 된다!


#### 범위질의에 대한 이해 

find({key: {$gt}})





### MongoDB의 실행

MongoDB의 실행은 명령 프롬프트에 아래와 같이 입력을 통해 할 수 있다. 셸 프로그램이 시작했다면 MongoDB의 버전과 현재 선택된 데이터 베이스를 볼 수 있다. 

```
mongo

MongoDB shell version v3.6.16
```


### MongoDB의 CRUD


### CREATE

```
> db.users.insert({user:'haemil'})
WriteResult({"nInserted": 1})
```

### READ

#### find의 인자로 query selector 넘기기(질의 술어)

query selector는 컬렉션에 있는 모든 도큐먼트에 대해 일치 여부를  검사하기 위한 조건으로 사용된다. 

```
> db.users.find({user:'haemil'})
{ "_id" : ObjectId("5e02da57816fc7cac0c038cd"), "name" : "haemil" }
```


#### or 와 and를 사용할 때의 기본적인 규칙
**암시적인 and**를 활용하는 방법  
질의 술어는 반환되는 document와 같다.

```
db.users.find({name:'haemil', country:'대한민국'}).pretty()
{
	"_id" : ObjectId("5e02da57816fc7cac0c038cd"),
	"name" : "haemil",
	"country" : "대한민국"
}

```

**명시적인 and 연산자**를 활용하는 방법


```
db.users.find({ $and: [
	{name:'haemil'}, 
	{country:'대한민국'}
]}).pretty()
{
	"_id" : ObjectId("5e02da57816fc7cac0c038cd"),
	"name" : "haemil",
	"country" : "대한민국"
}

```

**명시적인 or 연산자**를 활용하는 방법

```
db.users.find({ $or: [
	{name:'haemil'}, 
	{username:'smith'}, 	
]}).pretty()

{ "_id" : ObjectId("5e02da57816fc7cac0c038cd"), "name" : "haemil", "country" : "대한민국" }
{ "_id" : ObjectId("5e0a18dea7691c2bb31710aa"), "username" : "smith" }

```

#### or, and 연산자는 암시적인 방법과는 다르게 질의 그 자체가 하나의 도큐먼트이다. 





### UPDATE

이 업데이트 쿼리는 name이 haemil인 document를 찾아서 country값을 '대한민국'으로 바꿀 것을 지시한다. 

```
> db.users.update({name:'haemil'}, {$set:{country: '대한민국'}}))
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.users.find({name:'haemil'})                            '}})
{ "_id" : ObjectId("5e02da57816fc7cac0c038cd"), "name" : "haemil", "country" : "대한민국" }
```

#### Progressive update







### DELETE

remove 메서드의 인자로 document가 주어지지 않으면 collection의 모든 도큐먼트를 지운다. 

```
> db.users.remove()

```

조건에 해당하는 document를 지워야 할 때에는 remove 메서드의 인자로 query selector인 document를 넘겨주면 된다.

```
> db.users.remove({name:'smith'})
WriteResult({ "nRemoved" : 1 })

```


#### find는 콜렉션에서 조건에 해당 하는 것을 찾을 때 
find의 인자로 넣는 값인 문서가 조건을 나타낸다. 
즉, 조건질의를 할 때 사용하는 문서를 나타낸다.
해당 조건에 들어가는 문서를 반환해준다.



#### MongoDB에서 문서의 키로 사용할 연산자들은 $가 붙어있다. 
연산자들은 $가 붙어있다. 

##### $and

가령, $and 다음에는 배열 리터럴이 온다.
배열 리터럴 다음 값을 줄 수가 없으니 
키하고 값을 쓴다. 
문서질의를 위해서 어떻게 만드는지 이해하는 게 중요하다.


##### $or

or는 일종의 합집합이다. 
아래와 같은 구조로 진행된다. 
```
$연산자: [
    {},
    {}
]
```

#### 갱신 

**SQL에서의 방법**
update Table
set C = O
where 조건 


**NoSQL에서의 방법**
1. find를 수행해서 문서를 찾고
2. 어떤 키와 키에 들어갈 value를 찾고(이 작업을 수행하는 건 업데이트 함수)
3. 첫 번째 

```
users.update({username:'smith'}, {$set: {country: 'Canade'}})
```


#### 업데이트는 2가지 방법이 존재한다.


#### unset 

unset 연산자.
```
db.users.update({username:'smith'}, {$unset: {country: 1}})
```

**숫자 1은 의미가 없다, 관용적으로 1을 주거나 널을 준다. 키만 준다** 
```
{
    username: 'tmaltm'
    favorites: {
        cities: [],
        movies: []
    }

}
```
위의 것을 관계 모델로 만들면
테이블이 최소 3개가 필요하다.
배열 구조가 나오면 하나의 테이블로 여기는데

관계 모델에서 다대다라면...!! 
연결해주는 가운데 테이블이 와야한다.!!! 
그럼 테이블이 5개까지 된다...! 

T_User

T_F_cities
T_F_movies


관계형에서는 데이터가 없다면
null 을 집어넣는다.

스키마에 대한 제약이 없으므로..! 
문서마자 얼마든지 속성을 달리 적용할 수 있다. 



#### 자바스크립트는 객체에서 두 가지를 다 지원한다.!! 
연관배열표현법, 
Dot Notation 







#### 유연성이 높아서 괜찮을 수 있지만...!
여러 사람이 개발하다 보면 
표준이 필요한데, 
스키마라는 표준이 없으므로 
몽고디비에서는 옵셔널 하므로 
관리하기가 어렵다...! 


#### 드라이버를 쓰는 이유는 표준화가 되어있으므로 
드라이버를 쓰는 이유는 표준화가 되어있으므로 
언어가 다른 것에 대해 번역이 필요하므로 
Driver가 이 영역을 맡는다.

App 과 DB가 통신을 한다. 

ㅋㅋ..
Node.js 쓴다고 해도 결국에는 드라이버를 써야 한다.
그게 더 편함
API를 직접 호출하는 경우는 너무 해야 할 일이 많으므로 적절하지 않다...!


#### MEAP???

#### 표준이란 무엇인가?

HTML5 는 HTML, CSS3, JS(ES5)가 결합되어 있는 표준이다. 
이것이 HTML5이다...!

웹은 표준화가 안 되어있었는데
HTML5에 와서야 표준화가 이루어졌다...!

#### 사실상의 표준과 실제 표준의 차이점은 무엇인가?

1. 사실상의 표준(de facto) => 대세
누구나 많이 쓰는 것.. 대세!!! 
사실상의 표준이므로...! 

2. 공식적으로 스탠다드한 게 표준, 시장에서는 오히려 많이 안 쓸 수도 있다...


Node.js 는 서버사이드 자바스크립트 구현체로 이해하면 된다.


웹 브라우저를 만들 떄 3개의 컴포넌트가 가장 기본..!
웹 브라우저의 성능을 좌지우지 하는 가장 중요한 건 Javascript 엔진이다.

Javascript - V8
Interpreter 언어의 약점은 속도이다..
그래서 성능을 높이기 위해서...!
C++로 코드를 해석해하는 엔진..! 

자바스크립트를 읽어서 씨플플 코드를 만들어서
네이티브 코드로 만든다...
그러면 그것이 엄청나게 성능이 좋다.
이러한 구조로 V8엔진은 설계되어 있다. 


과거 게임 시장은 씨플플로 만들었지만..!
요즘은 게임들의 생명 및 주기가 짧으므로 Node.js를 선택하는 추세이다.

C++로는 개발해서 납품하기 어려우므로, 생산성이 떨어진다.
모바일 시장에서 게임 서버를 개발할때는
Node.js 를 사용한다..! 




#### 자료구조의 특징

tuple
list
set 
dict


#### 파이썬의 대표적인 자료구조 비교

> 공부를 할 때는 하나의 표로 작성해보는 연습을 해보면 좋다..! 도움이 많이 된다고 한다..! 비슷한 특징을 비교해볼 수 있다. 

| 특징 | ordered | duplicated(중복) | mutable | literal |
|---|:---:|:---:|:---:|:---:| 
| tuple | O | O  |  X  | ()  |
| list | O | O | O | [] |
|  set | x, 인덱스가 없음 | X | O | set() |
| dict | x, 키에대한 해쉬값을 가짐 | key:X, val:O  | O | { } |


Set 은 유니크한 것을 이야기해준다.(유니크한 값을 표현)
이미 값이 있으면 안 들어가고, 없다면 값이 들어간다. 

db.users.update

upsert 여부..! (UPDATE insert)를 말한다.
트루이면..! 업데이트 없으면..! 값을 넣는다.
값이 false라면 업데이트로만 동작한다. 
기본값이, default가 False이다.


4번째 인자로는 허용할 것인지에 대한 여부 
조건을 만족하는 게 여러개면 다 업데이트 한다. 
```
 if (multi) { multi가 트루라면!
        updateOp.update(obj); # 다 업데이트 해준다!
    } else {
        updateOp.updateOne(obj); # 첫 번째 문서만 업데이트 해준다!
    }
```

```
db.users.remove({'favorites.cities': "Cheyenne"})
```
Cities 정보를 가지고 있는 문서를 제거하고 싶을 때는 
remove 라는 fucntion을 사용한다. 

favorites.cities 를 없애고 싶다면!!!!! unset을 사용한다. 


#### 컬렉션을 지우고 싶을 떄는!!
```
db.users.drop()
```






----

##### db.numbers.save

```
function (obj, opts) {
    # 객체가 없다면
    if (obj == null)
        throw Error("can't save a null");

    # 객체만 저장할 수 있다. 
    if (typeof(obj) == "number" || typeof(obj) == "string")
        throw Error("can't save a number or string");

    # 다큐먼트 아니라면..! 키를 생성해서 삽입
    if (typeof(obj._id) == "undefined") {
        obj._id = new ObjectId();
        return this.insert(obj, opts); # 여기서 디스는 콜렉션!!!
    } else { # 아이디가 있을 경우 문서가 있으므로 업데이트
        return this.update({_id: obj._id}, obj, Object.merge({upsert: true}, opts));
    }
}
```

obj는 다큐멘트, 
이런 것을 편의함수라고 한다. !!!

Sava() 라는 녀석이 동작을 한다. 


#### 데이터 베이스 매커니즘 

매커니즘은 이미 있었지만..! 
설명이 불충분했을 수도 있으므로..!


모든 디비가 그런것은 아니지만
대용량의 디비들은 어떠한 매커니즘을 따른다. 



1만건 중의 일부가 
메모리상에 올라온다. 


단계별로 처리할 수 있도록 매커니즘이 구성된다.

fetch 량을 컨트롤 할 수 있는...!

저장되어 있는 건 500건인데
가져온 게 100건이라면
fetch 옵션이 있다.!!!
그러므로 항상 확인해야 하는 건 count이다

관게형에서도 
실제 카운트와 select해온 데이터와 수량이 같은지 확인해보아야 한다.

iterator(반복자)

커서의 커런트 위치에서 스무개를 다시 fetch를 한다.

greater than 초과
greater than equal 이상 

less than 미만
less than equal 이하


db.numbers.find({num:{'$gt':20, '$lt': 25}})

```
> for(i=0; i < 20000; i++){
... db.numbers.save({num: i})
... }
WriteResult({ "nInserted" : 1 })

> db.numbers.count()
20000

```

30에서 35 사이

#### 연산자 종류

$ne = not equal 




#### 데이터베이스가 동작하는 방식

일반적으로 버퍼라고 함

##### 게시판을 예로 든다면..!!

처음 화면은 여러명이 보는 쿼리가 같다!
여러명이 본다면 생각보다 고비용이다.!! 

최초에는 하드파싱을 한다! 

플랜을 세운다.
데이터를 어떻게 꺼내올 것인가.
인덱스를 쓸 것인가 
풀스캔을 쓸 것인가. 


실행계획을 수립을 하는데 
여러개의 실행계획이 수립될 때
각각에 포스트가 생성됨


유니크 인덱스
Non Unique Index ...!

인덱스 만들 때
create index를 했었는데, 이는 Non Unique Index ...!와 관련이 있다.


B-tree를 만들어준다.

유니크 인덱스를 만들기 위해서는!! 
create Unique Index ...!


##### 인덱스를 걸어야할 대상, 인덱스가 필요한 이유!! 성능!
join 하는 컬럼에 인덱스를 건다(조건문으로 검색하는 요소에 보통 인덱스를 많이 건다.)
pk에는 클러스터 인덱스가 걸려있다. 

FK에 인덱스를 만들어두면 조인과 관련된 성능이 개선된다.
의미 있는 검색을 하기 위해서 사용되는 컬럼들이
인덱스를 걸어야 할 대상이 된다..!!

where 조건절에 나오는 대상들을 검색해서 인덱스를 걸어야 한다...!!

인덱스를 많이 만든다고 좋은 건 아니다.인덱스는 메모리상에 올라가므로 성능이 안 좋아질 수 있다. 
이러한 이슈를 해결하기 위해서 잘 조절해야 한다!

##### Document 지향의 데이터베이스라고 해서 인덱스는 예외가 아니다!!

20000개의 복잡한 필드가 구성되어 있을 때 인덱스가 없다면! 
풀스캔을 통해 데이터를 다 확인하는 해야 하는 불상사가 생김. 

결국에는 내용을 다 서치해야 한다! 
20000개 정도되면 많은 문서가 아니다!
2만개 정도 문서를 만들면 인덱스 유무에 대한 이슈가 생긴다! 

##### 근거와 결과는 어디서 꺼내는가? index

RDBMS 옵티마이저가 만들어진 결과

익스플레인이라는 명령이 있다. 

select explain ...!
이 녀셕에 대한 실행계획과 관련된 내용이 쭉 나온다...!
통계정보가 나온다.. 

몽고디비 또한 explain이라는 함수 존재한다!!!
성능이 얼마나 개선되었는지..!
explain 이라는 함수를 통해서 확인할 수 있다.

###### find 는 커서가 반환하고, explain 또한 결국 커서가 반환한다.
커서에 익스플레인이라는 메서드가 존재한다..! 
실행통계 괸련 내용을 보여줘


```
db.numbers.find({num:{'$gt': 19995}}).explain('executionStats')
```


collection 전체 스캔...!

filter 스캔 ... !

ns, 이름공간은 다른 이름과 충돌을 방지하기 위해서 사용한다.

##### 계구간
( ]

계구간, 폐구간...! 

인덱스에 걸려있는 4개의 값을 사용했다는 것은
4개의 문서만 접근했다는 이야기가 된다. 
네..! 제출일을 월요일로 미루기..! 

#### B-tree 에 대한 이해가 필요한 이유
월요일에 쿼리 옵티마이즈/..!
인덱스에 대한 매커니즘을 이해하지 못하면...!
이해할 수 없는 영역의 이야기가 나온다...! 
읽어들이는 메모리의 크기가 달라진다. 



#### 할당 단위 크기

컴퓨터가 데이터를 표현하는 최소단위.

| 특징 | 단위 | 표현 | 
|---|:---:|:---:|:---:| 
| bit | 컴퓨터가 정보를 표현하는 최소단위 | 1bit  |
| byte | 정보를 읽고 쓰는 최소단위 | 8bit |  
| word | 연산의 최소 단위, 워드의 크기가 int의 크기와 같다 | 32bit | 
| block | 파일 시스템의 입출력 단위 |  4KB, (4096바이트) | 


하나의 파일에 대해서 한 번 쓸 때, 혹은 한 번 읽을 때 얼만큼씩 읽고, 쓰는지에 대한 단위
예로 40kb 인 파일을 복사하게 된다면 10번 읽어들여서, 10번 쓰게 된다.  
40 / 10 = 4, 4 * 10 = 10

#### 파일 시스템의 블록사이즈에 따라서 읽고 쓰는 속도가 달라진다. 

할당단위크기를 높이면 디스크의 단편화가 발생한다. 
블록사이즈보다 큰 파일을 읽어들이는 경우가 많아야 효과를 본다.!!
그래야 남는 공간이 없다. 

2kb 파일을 읽고 쓰기 위해
4kb를 쓰는 것이 나은지, 8kb를 쓰는 것이 나은지는
조금만 비교해보면 알 수 있다.
더 적게 공간을 낭비해야 경제적?!

파일사이즈가 크면 블록사이즈가 큰 게 유리하다.
블록들을 구성할 때 만든게 extents
여러개의 블록을 구성해서 만든게 extents


#### 유니코드란 무엇인가?

정수를 유니코드 테이블하고 맵핑했을 때 '가'가 된다. 

16진수 1개가 4bit
       2개가 8bit, 1byte


유니코드는 모든 문자를 2바이트 체계에 다 집어넣었다.
영어같은 언어는 1바이트 안에 다들어간다.! 

그럼 1바이트가 남는다...! ]

상용하는 글자들도 사용하는 영역에 있어야 하므로 

우리가 사용하는 버전은 utf-8, 이것은 인터넷 표준이다.

코딩, 인코딩과 관련되어 있는 부분은 utf-8이다...!

인코딩은 프로토콜..! 데이터 교환에 대한 약속이다..!!


AC00 ~ D7AF
유니코드에서 한글 음운이 정의되어 있는 곳..!
초성 + 중성 + 종성 => 11172자의 음운이 등록되어 있다...

UTF-8은 한글은 한글자가 3바이트임









