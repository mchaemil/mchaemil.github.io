---
layout: article
title: R/DataAnalysis | R 두 번째 걸음! R 통계를 위해 만들어진 프로그래밍 언어이다!
tags: R

---

## **Today What I Learend**  

R이란 통계를 위한 언어이다..
내가 R을 통해서 얻을 수 있는 건 무엇일까 고민해보았다.
R을 사용하면 통계를 모르는 나도.. 
기본적인 통계치를 구할 수가 있다.

R은 2차원 데이터를 다룰 일이 많다. 대량의 데이터를 다룰 때 성능상의 이유로 조건문과 반복문을 쓰지 않는다. 대신 함수를 사용하는데 이에 익숙해지는 시간을 갖자!

---
**Today I Learend**

- ifelse
- apply
- 사용자 정의 함수
- 자료의 종류
- 단일변수란 무엇인가?
	- 단일변수 범주형 자료 탐색방법
	- 단일변수 연속형 자료 탐색방법

---



### R에서는 조건문 대신 ifelse()를 사용하자

R에서 조건에 따라 두 가지의 값 중 한 가지를 선택해야 한다 ifelse 함수를 사용하자! 성능상의 이슈를 줄일 수 있다. 

```r
a <- 20
b <- 10

c <- ifelse(a>b, a, b)
c
```

### apply

2차원 데이터를 분석하는 경우에는 성능상의 문제를 해결하기 위해서 for, while 대신 apply 를 사용해야 한다. 

> Vector Op 에 대한 장점도 얻을 수 있다. 

`apply(데이터셋, row/col 방향지정, 적용할 함수)`
- 1은 row 방향
- 2는 col 방향


```r
iris[, 1:4]
apply(iris[, 1:4], 1, mean)
apply(iris[, 1:4], 2, mean)

```

#### aplly 로 해결하는 간단한 예제

- iris 데이터셋의 row별 합계 추출하기
- iris 데이터셋의 column별 최대값 추출하기

```r
apply(iris[, 1:4], 1, sum)
apply(iris[, 1:4], 2, sum)

```



### 사용자 정의 함수

사용자 정의 함수를 생성하여 복잡한 작업을 해결하는 실마리를 얻을 수 있다. 
R은 데이터 분석, 통계에 특화된 언어이므로 이와 관련된 다양한 함수를 제공하는데, 사용자 정의 함수를 통해 기능을 확장할 수 있다. 

- 최소값과 최대값을 출력하는 함수 

```r
maxmin <- function(x) {
  maxmin.max <- max(x)
  maxmin.min <- min(x)
  return(list(min=maxmin.min, max=maxmin.max))
}

v1 <- c(7,1,2,8,9)

result <- maxmin(v1)
result
result$max
result$min

```

- 정수 두 개를 인자로 입력 받았을 때, 두 수의 최대 공약수를 반환하는 함수

```r
gcd <- function(a, b) {
  ifelse(a %% b == 0, return(b), return(gcd(b, a %% b)))
}
gcd(10, 8)
```


### 자료의 종류

자료는 특징점을 가지고 다양하게 분류할 수 있다. 이ㄴ



### 단일변수 범주형 자료 탐색방법





### 단일변수 연속형 자료 탐색방법


#### 사분위수

평균이나 중앙값에 비해 사분위수는 보다 풍부한 해석이 가능하다.
사분위수를 통해 얻은 3개의 값을 통해 특성을 추정하는 데 사용되며, 평균이나 중앙값에 비해서 풍부한 해석과 정보를 얻을 수 있다. 


---


표준편차는 거리고

variance 는 면적이므로..!
일반적으로 표준 편차를 이용한다.
데이터가 일반적으로 중심으로부터 얼마나 떨어져 있는가를 확인한다.

기초 통계는..!정보는
디비를 쓰면 얼마든지 구할 수 있다. 


각직급별 성별 인건비 현황
성별 회사크기별 등
성별 지역별

여기서 별별은 그룹을 의미한다.
메인 그룹과 서브 그룹...!
이러한 도구를 통칭해서 집계 프레임워크라고 부른다. 

가지고 있지 않으면 반정규화, 비정규화...!
를 하게 되면 중복이 늘어난다.
중복이 늘어나서 데이터 품질에 문제가 생기는 경우가 있고, 
아닌 경우도 있다.

중복을 최소화하기 위해서 하는데..!
문서 모델은 
반정규화를 통해서 데이터 품질에 문제가 
생기지 않을수도 있다..
한 문서에 통으로 두고 관리하는 경우가 있으므로...!

함수형 프로그래밍은 함수의 입력, 반환값으로 사용하는 경우를 말한다.


자바스크립트 closure 는 함수로 리턴

객체지향에서 숨기는 방법으로 클로저를 쓴다.
클로저는 함수를 반환하는 구조이다. 

자바스크립트는 private하지 못하므로 숨겨야 하는데
숨기는 방법으로 클로저를 쓴다. 

inner function의 지역변수는 값을 반환하는데
이를 사용하기 위해서.. 클로저..?!




global scope

더글라스 크락포드...
언어가 제공하는 게 아니라 
closure는 기법이다.

```
outterFn = function() {
    var local_x = 0;
    var innerFn = function() {
        local_x += 1;
        console.log(local_x);
    };
    return innerFn;
}

id = outterFn()
ƒ () {
        local_x += 1;
        console.log(local_x);
    }
id()
id()
id()

```





#### 아이디에 해당하는 다큐먼트를 찾아서
거기서 이름을 찾아서
새롭게 집어넣고 결과 컬렉션이 집어넣으면 거기에 이름이 들어간다...

```
> db.products.aggregate([
... {'$group': {_id:'$main_cat_id', 'count': {'$sum':1} }} ])
{ "_id" : ObjectId("6a5b1476238d3b4dd5000048"), "count" : 2 }
> db.products.aggregate([ {'$group': {_id:'$main_cat_id', 'count': {'$sum':1} }} ]).forEach(
... function(doc){
... var catDoc = db.categories.findOne({_id: doc._id})
... doc.catName = catDoc.name
... db.summary.insert(doc)
... })
> db.summary.find()
{ "_id" : ObjectId("6a5b1476238d3b4dd5000048"), "count" : 2, "catName" : "Gardening Tools" }

```


#### 위의 의사조인 코드는 최적화가 안 되었다.
이 코드는 따로 콘텍스트를 구성하므로 느린 단점을 안고 있다.
하지만 많이 활용하는 대표적인 기법 중의 하나이다. 

forEach 를 사용가능한 이유는 결과값으로 커서가 반환되었기 때문이다.
결과물이 커서이다.!! 결과물 여러개를 읽어오는 구조는 전부 커서이다. 

find 다음에 forEach를 할 수 있다.. !
aggregate 다음에 forEach를 할 수 있다. 
하지만 findOne은 forEach를 할 수 없다. 

커서를 반환하므로 커서를 통해서 문서를 하나하나씩
조작할 수 있다..!


db.products.findOne()

"total_reviews" : 4 에다가 곱하기 이를 하면 된다..!

```

db.products.find({}, {total_reviews: 1}).forEach(
    function(doc) {
        doc.total_reviews *= 2
        db.summary2.insert(doc)
    }
)

> db.summary2.find()
{ "_id" : ObjectId("4c4b1476238d3b4dd5003982"), "total_reviews" : 8 }
{ "_id" : ObjectId("4c4b1476238d3b4dd5003981"), "total_reviews" : 8 }


```


결과물을 컬렉션으로 떨구는 작업은 아웃을 통해서 가능하다. 
문서들이 이 안으로 저장이 된다. 


//unwind를 통해서 배열의 요소가 독립적인 문서가 된다. 
unwind는 배열의 대상으로 해서
하나의 문서를 만들어놓는 것...!

배열의 모든 원소를 문서와 연결시켜서 배열을 만든다. 

카테고리 아이디즈는 더 이상 배열이 아니다. 
그룹핑해서..! 
몇 건이 있는지.. 알 수 있다.

집계 결과를 카운트바이카테고리에 저장을 한다. 

```
db.tests.aggregate([
    {'$unwind': '$contents'}, 
    {'$group':
        {
            '_id': '$contents',
            'cnt': {'$sum': 1}
        }
    },
    {'$sort': {'_id': 1}},
    {'$out': 'groupByContents'}
])
```

각 아이디별로 건수가 만들어짐

배열에 들어가있는 값들로 그룹핑하기 전에는
unwind 작업이 필요하다.
아이디와 관련된 형태로 배열을 확장시켜야 한다.

그리고 이러한 작업 전에 project로 필요한 컬럼, 값만 선택해야 한다. 
특히 그룹핑할 때는 매우 중요한 개념..!

배열이 동일 테이블이 아닌 곳에서 사용하면, 
다른 곳에 있는 아이디와 연결을 하면 조인이 된다.

unwind는 자기자신과 할 때는 배열을 확장해주는 역할을 하고
unwind 다른 곳에 있는 아이디와 할 때는 조인이 된다..@ 


#### 파이프라인 매커니즘을 이해하기 위해서는 작업을 끊어서 하면 좋다.

위로는 자바스크립트& 몽고디비
--- 



#### white space 옵션을 제거하는 
가비지 값들이 어마어마하게 들어가있는데,

#### strip.white = FALSE,  옵션은 쓰는 것을 권장한다.

read.csv 함수가 상속 버전으로 만들어져 있고..
read, table 에 있는 것들을 잘 확인해야 한다. 


#### 벡터의 연산은 브로드케스팅 오퍼레이터
모든 연산은 벡터 연산을 한다는 것을 잊지 말자
원소가 하나짜리인것 끼리만 비교할 수 있다

#### 제어구조들을 가지고 있으므로 제어문을 거의 사용하지 않는다. 권장하는 방법이 아님
if문, for문은 거의 사용하지 않는다. 상당히 성능이 느림 
그러므로 벡터 오퍼레이터 연습을 더 많이 하는 게 중요하다.

큰 데이터, Big한 데이터를 다룰 때는 거의 쓸모가 없다. 100%는 아니지만.. 거의 쓸모 없다. 

**ifelse는 많이 쓴다.**


#### Factor는 크게 두 가지로 동작을 한다
- 순서 있는 Factor
- 순서 없는 Factor <- 대소비교가 안되는 팩터 순서가 필요하다면 매길 수가 있다..! 
H, M<, L 의 순서르 비교하려면..!



#### apply() 함수

실행 가능한 코드를 어플라이 한다.
행과 열에다가 

a,b,c 
각 컬럼에 대해서 sum()을 한다음에
apply는 컬럼의 방향으로 섬하는 함수를 주면
그 컬럼에 대해서 섬의 값을 만든다... 그렇게 사용하는 게 어플라이
함수적 프로그래밍 언어의 공통 분모 같은 것이다.!!

반복 작업이 필요한 현우은 

**apply(데이터셋, 행/열방향 지정, 적용함수)**

axis 가 1, 2 들어가면 된다..!

해

apply(iris[, 1:4], 2, mean) # 150개에 대한 평균..!



#### 함수를 설계할 때
외부 의존성을 갖지 않는 형태로 만드는 것이 중요하다..!

사용자 정의 함수를 만들고 사용하기 
가급적 반복구조를 사용하지 말아라..!

반복구조를 쓸 때는 벡터 오퍼레이터, 어플라이를 사용하면
반복문을 없앨 수 있다. 

함수가 반환하는 결과값이 여러 개일 때의 처리 

#### R에서 벡터 연산을 안 하는 연산자는 없다. 

mpg cyl 


### chapter.5 단일변수와 자료탐색
useNA = c("no", "ifany", "always"),
예제 사용코드..!

```r
vec[50:52] <- NA
table(vec)
table(vec, useNA = 'ifany')
```

```
prop.table(table(vec, useNA = 'ifany')) # 빈도 계산된 걸 가지고 %로 나타내줌...!
```

#### 빈도표는 범주형 데이터..!
단일변수 = 일변량..! 


#### quantile
quantile(x,  probs = c(0.1, 0.5, 1, 2, 5, 10, 50, NA)/100)


#### 분위수 계산,
조각을 몇퍼센트인지 확인할 수 있다.

#### 벡터 연산을 해버리면 된다.
quantile(mpg$hwy, probs = 0:10/10)
0:5/5 분위수...! 를 만들 때는
벡터 연산을 해버리면 된다. 


101 ..! 101명 안에 살아남으려면 컷.. 커트라인이 중요하다.
커트라인이 제일 중요하다.
프로그램을 만드는 사람 입장에서는 시청률이 제일 중요하다..



#### 박스플롯...!

boxplot(mpg$hwy) # 박스플롯을 그리면 이상치의 여부를 확인할 수 있다. 

전처리할 때 반드시 팔요하다고 하면서
이상치 판단의 근거로 설명한...!

IQR:

Q1 Q2 Q3 

[선생님이 보여주신 그림을 보여드리기](boxplot 이미지)


### 산포
값들이 퍼져있는 정도를 말하며, 자료를 파악할 수 있는 특징 중 하나이다...

#### 분산, 표준편차

펴균하고 얼마나 가까운가
평균으로부터 얼마나 퍼져있는가를 나타내기 위해서


[60,70) -> 60 이상 70미만..! 


두 개 이상의 변수를 이용해서 사용할 때 산점도는 어떻게 데이터를 보여줄 수 있는가 같이 살펴보자

다중 산점도를 나타낼 때는 데이터가 300개 미만으로 표현하길 권장한다.
대표성을 가진 데이터로 표현하기를 권장한다. 
너무 많으면 불편..!


#### 데이터 사이언티스트에게 요구되는 역량


1. 전처리 역량
1. 변수를 선택하는 역량


#### 상관관계는 범주형 데이터로 하지 않는다..
팬달의 상관관계는 범주형 데이터로 한다..@
국한하고 있다.
일하는.. 방법;..

의미가 있다 없다를 말하기 전에...! 가장 큰 값 두개를 뽑아낸다..!
0.2 보다 낮다...!
사회과학

낮은 상관관계도 의미를 두고 작업을 하는 경우가 맣다. 

### 전체코드
```
data(iris)
data(state)

class(iris)
class(state.x77)
str(state.x77)

dim(state)

colnames(state.x77)
rownames(state.x77)


df <- data.frame(state.x77)
str(df) # str을 해보면 df 임을 알 수 있고, 
# $를 통해 컬럼으로 구성되어 있음을 알 수 있다.

str(iris)
iris[, -5] # 앞에 있는 4개의 컬럼만 가능
iris[1:2]


# 아이리스를 매트릭스로 만들기 

mtx <- as.matrix(iris[, -5])
mtx # 2차원 구조에서 넘어오면 as.matrix를 써야 한다.

colnames(mtx)

iris[, 'species']
iris[, 5]



aq <- read.csv('airquality.csv') # 기본적으로 데이터 프레임을 만든다.
str(aq)

set.seed(3)
col <- sample(letters, 153, replace = T) # 153개의 관측치를 가지므로 같은 길이로 만든다.
# 데이터 프레임은 편한다..!
aq$NewCol <- col
str(aq)

write.csv(aq, 'airquality2.csv', row.names = F)

aq2 <- read.csv('airquality2.csv', stringsAsFactors = F) 
# 팩터로 지정할 의향이 없다면 캐릭터..!
str(aq2)

aq3 <- read.csv('airquality3.csv', stringsAsFactors = T, header = F)
# 헤더는 기본적으로 트루이므로 첫번쨰 라인이 컬럼 이름이 되므로.. 
# 펄스로 지정해야 한다... 
str(aq3)

colnames(aq3) <- c('C1', 'C2', 'C3', 'C4', 'C5', 'C6', 'C7')
str(aq3)



# for Loop를 사용하면 오히려 늦다.
# python pandas for
# 벡터 오퍼레이터가 사용된 유니버셜 펑션을 뉴 평선으로 사용하는 것과 같다.

iris$Label <- ifelse(iris$Petal.Length >= 5.1, 'H', 
       ifelse(iris$Petal.Length > 1.6, 'M', 'L')
)

str(iris) # 벡터로 바꿀 때...! 
# 레벨을 지정하지 않으면 사전 순으로 된다.
# 펙터를 지정할 떄 레벨을 수동으로 만들어서 써라
# 

unique(iris$Label)
iris$Label <- factor(iris$Label, 
                     levels = c("L", 'M', 'H'),
                     ordered = T
                     )

str(iris) # 라벨이 팩터로 바뀌어 있다..
# 순서가 필요할 때는 대소비교가 가능한 팩터로 만들 수 있다. 
# 팩터의 심화내용, 팩터가 가장 많이 쓰이는 두 가지 방법


apply(iris[, 1:4], 2, mean) # 150개에 대한 평균..!



rowIndex <- (iris$Petal.Length > 6)

iris[rowIndex, ]



data('mtcars')
str(mtcars)
head(mtcars)
rownames(mtcars)

colnames(mtcars)

# mpg, hp, wt

apply(mtcars[, c('mpg', 'hp', 'wt')], 2, mean)

apply(iris[, 1:4], 2, mean) # 150개에 대한 평균..!



vec <- sample(letters[1:3], 100, replace = T)
table(vec)

length(vec)
vec[100]
vec[101]

vec[101] <- 'a'
vec

vec[50:52] <- NA
table(vec)
table(vec, useNA = 'ifany')
prop.table(table(vec, useNA = 'ifany'))


season <- c('spring', 'summer', 'fall', 'winter')
set.seed(3) # 난수를 생성할 때, 똑같은 데이터를 재연하기 위한 값값
favorite <- sample(season, 100, replace = T)
favorite2 <- factor(favorite, levels = season)

table(favorite)

table(favorite2)

barplot(table(favorite2), col = c('red', 'green', '#B54D31', 'gray'))
# 시각화는 ggplot2를 사용한다.

install.packages('dplyr')

library(ggplot2)
library(dplyr)


data(mpg)
str(mpg)
mpg %>%
  ggplot(aes(x = class))
  geom_bar()
  

  
ds <- table(favorite)
ds
pie(ds, main = 'favoirte season')

mean(mpg$cty)
mean(mpg$hwy)

apply(mpg[c('cty', 'hwy')], 2, mean)

# 연속형 변수이므로 평균을 만들 수 있다. 
# .. 해서 보시다시피..! 평균과 중앙값과 같은 데이터들..!

# hwy 에 대해서 데이터가 어떠한 경향을 보이는지..!

# quantile 은 분위수이다.
quantile(mpg$hwy) # 디폴트가 4분위수가 나온다.


# 5분위수
quantile(mpg$hwy, probs = c(0, 0.25, 0.5, 0.75, 1))

quantile(mpg$hwy, probs = c(0, 0.2, 0.4, 0.6, 0.8, 1))

# 벡터 연산을 해버리면 된다.

quantile(mpg$hwy, probs = 0:10/10)
0:5/5





boxplot(mpg$hwy)
# 박스플롯을 그리면 이상치의 여부를 확인할 수 있다. 


mpg %>%
  ggplot(aes(x = class, y = hwy)) + geom_boxplot()



(q <- quantile(mpg$hwy))
q1 <- q['25%']
q3 <- q['75%']
iqr <- q3 - q1
mpg$hwy

mpg$hwy > q3 + 1.5 * iqr # 여기서 트루로 나오는 것들이 이상치..!
# 이상치에 대한 인덱스를 확인해서 
# 아웃라이어 인덱스를 구하려면 위치를 써야 한다.
(outlier_idx1 <- which(mpg$hwy > q3 + 1.5 * iqr)) 
(outlier_idx2 <- which(mpg$hwy < q1 - 1.5 * iqr)) # 여기서는 아웃라이어가 없으므로
# 박스플롯을 그려보라고 하면...! 
# 아웃라이어 인덱스를 하면된다. 

boxplot(mpg$hwy[-outlier_idx1])
quantile(mpg$hwy[-outlier_idx1])
quantile(mpg$hwy)



set.seed(123)
scores <- sample(seq(35, 100, 5), 1000, replace = T)
# 35, 100 사이의 값을 인터벌로 5까지 1000개 꺼내는데, 
# 당연히 복원추출이 필요하다.

cut(scores, breaks = c(0, 60, 70, 80, 90, 100), include.lowest = T,
    right = F,
    labels = c("F", 'D','C','B','A')
    )
# 자동으로 범주형 데이터가 만들어지는데, 여기에 옵션을 필요로 한다.
# 왼쪽 폐구간, 오른쪽을 개구간..! 
# right = F 를 통해서 개폐구간을 바꾸어주는 게 좋다. 
# 연속형데이터를 범주형 데이터로 바꾸는 이유가 왜 중요할까?
# age에 대해서 구간화 작업을 한다. 
# 연속형 데이터에 대해서 범주형 데이터, 구간화를 만들어야 한다.
# 연속형 데이터에 브레이크를 걸어서 범주형 데이터, 팩터를 만들었다. 
# R에서 많이 사용하는 전처리 기법이다. 


iris.2 <- iris[,3:4]
point <- as.numeric(iris$Species)
point


iris[1:4] # 데이터 프레임에서 이렇게 기록하면 컬럼 

# 상관계수는 반드시 두 개의 변수가 연속형 변수이어야 한다. 
# 연속형 변수가 아니면 에러가 난다..

cor(iris$Sepal.Length, iris$Sepal.Width)
cor(iris$Sepal.Length, iris$Petal.Length)
cor(iris$Sepal.Length, iris$Petal.Width)

cor(iris[-(5:6)])[1, ] # 첫 번째 행을 꺼낸다... 
cor(iris[-(5:6)])[1, -1]
# 다변량은 변수가 두개 이상이므로...! 
# 변수가 20개라면..! 관계니까 요것만 사용하세면 한 꺼번에 그게 만들어진다. 

# 상관의 정도가 가장 큰 수를 선태갷보라 
# 변수를 소트해서 정렬하고 2개를 선택 ..>1 

sort(cor(iris[-(5:6)])[1, -1], decreasing = T)[1:2]
# 가장 큰 상관관게를 보일 수 있는 정도이다.
# 분석의 출발점. 변수들 중 상관성이 높은 것들이.. 첫번째 대상이다.


library(MASS)
data('birthwt')
str(birthwt)

(m <- birthwt[c('bwt', 'age', 'lwt','ptl','ftv')])

(c <- cor(m)[1, -1])
sort(abs(c), decreasing = T)[1:2]





```

#### 전체 코드 두 번째
```


install.packages('mlbench')
library(mlbench)
data('BostonHousing')

myds <- BostonHousing[, c("crim", "rm", "dis", "tax","medv" )]

grp <- c() 

for(i in 1:nrow(myds)) {
  if (myds$medv[i] >= 25) {
    grip[i] > 'H'
  } else if (myds$medv[i]) {
    grip[i] <- 'L'
    
  } else {
    grp[i] <- 'M'
  }
  
}
grp <- factor(grp)
grp <- factor(grp, levels = c('H', 'M', 'L'))

myds <- data.frame(myds, grp)

housing_df <- read.table("housing.data", stringsAsFactors = F)
str(housing_df)

colnames(housing_df) <- c("CRIM",
                          "ZN",                         
                          "INDUS",     
                          "CHAS",   
                          "NOX",       
                          "RM",       
                          "AGE",      
                          "DIS",       
                          "RAD",      
                          "TAX",      
                          "PTRATIO",  
                          "B",       
                          "LSTAT",    
                          "MEDV")

str(housing_df)
str(housing_df[-4])
cor(housing_df[-4])

(c <- cor(housing_df[-4])[, "MEDV"])

length(c)
abs(c[-length(c)])
sort(abs(c[-length(c)]))

sort(abs(c[-length(c)]), decreasing = T)[1:5]


# 다섯 개의 중요변수들을...!? 추출할 수 있다구??!

df <- housing_df[c('CRIM', 'RM', 'DIS', 'TAX', 'MEDV')]

housing_df$GRP <-ifelse(housing_df$MEDV>=25.0, 'H',
                        ifelse(housing_df$MEDV<=17.0, 'L', 'M'))
housing_df$GRP<-factor(housing_df$GRP,
                       levels = c('L','M','H'))
table(housing_df$GRP)



opar <- par(mfrow = c(2, 3)) # 리턴될 객체를 저장
for(i in 1:5) {
  hist(df[,i],main = colnames(df)[i], col = yellow)
}

par(opar)




opar <- par(mfrow = c(2, 3)) # 리턴될 객체를 저장
for(i in 1:5) {
  boxplot(df[,i],main = colnames(df)[i], col = yellow)
}
par(opar)

housing_df %>%
  ggplot(aes(x = GRP, y = CRIM))
  geom_boxplot()
  
housing_df %>%
  ggplot(aes(x = GRP, y = RM))
  geom_boxplot()
  
str(df)

pairs(df)  





data <- c(1,2,3, NA, 5, NA, NA, 8)
is.na(data) # 로지칼 벡터를 반환


(na_idx <- which(is.na(data)))
data[-na_idx]
data
as.vector(na.omit(data))
# na.omit 을 모르더라도..! which 에 대한 이해가 깊다면..! 다 해결할 수 있다.

#이것은 배웠던 내용에 대한 정리
sum(is.na(data))
sum(data, na.rm = T) # NA 값이 있는 상태에서 연산을 하면 블랙홀처럼 사라진다.


x <- iris
x[1,2] <- NA; x[1,3] <- NA
x[2,3] <- NA; x[3,4] <- NA
head(x)

col_na <- function(y) {
  return(sum(is.na(y)))
}

na_count <- apply(x, 2, FUN=col_na) >= 2
na_count


idx <- which(apply(x, 1, function(row) {
  return(sum(is.na(row)))
}) >= 2)

x2 <- x[-idx, ]
x2


```





