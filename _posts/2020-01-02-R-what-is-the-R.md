---
layout: article
title: R/DataAnalysis | R 첫걸음!
tags: R

---

## **Today What I Learend**  

R이란 통계를 위한 언어이다..
내가 R을 통해서 얻을 수 있는 건 무엇일까 고민해보면서!!

더 잘 배울 수 있는 사람이 되자.
더 잘 학습해서 잘 활용하도록..! 


---
**Today I Learend**

- R vs Python 
- R 환경 설정
- R의 변수와 연산
- 벡터(R의 자료구조)
- 벡터 연산
- List & Factor
- 2차원 데이터를 분석하기 위한 자료구조
- Matrix
- DataFrame
- Matrix와 DataFrame 제어

---



### R vs Python 

|  | R | Python |
|---|:---|:---|
| 장점 1 |  데이터 시각화 | 높은 활용도를 가진 언어 |
| 장점 2 | 생태계 | 개발연동이 쉬움 |
| 장점 3 | 데이터 사이언스 공통어 | IPython Notebook |
| `단점 1` | 개발 연동이 어려움 | 시각화 |
| `단점 2` | 분석을 위해선 숙련도가 요구됨 | 후발주자 |


R의 장점은 Python보다 쉽지만 개발 연동이 어려운게 단점이고, Python의 단점은 R보다 어렵지만 개발 연동이 가능한게 장점이다. 통계는 R이 우위를 점하지만 Python은 머신러닝, 딥러닝에서 우위를 점하고 있다.

머신러닝, 딥러닝 등의 최신 지식을 활용하는 데는 Python이 유리하다.
통계 관점에서만 업무를 하려면 R이 훨씬 편리하다. 다만 개발까지 스택을 고려한다면 Python을 선택하는 게 더 유리하다. 

일반적인 개발시장에서 R은 가산점을 받을 수가 없다.

가장 좋은 선택은 둘 다 활용하는 것이다. 



> python 훨씬 더 유리하다.. 파이썬은... 원래 출발 목적은 코딩을 쉽게 배울 수 있었으면 좋겠다는 목적으로 출발 개발자가 아니어도 배울 수 있게끔.. 쉬운 개발, 코딩 언어로 포지셔닝을.. 지금우리가 사용하는 파이썬 3는 2에 비해서 현재의 니즈를 반영한 언어 인터프리팅 언어란 장점으로 인해 괜찮으면 인터넷에 올리므로.. 다 만들어서 써야 하므로.. 커뮤니티가 활발해지고 생태계가 좋아졌다.. pip는 여러 라이브러리들이 하나로 모아진 결과이다. 생태계가 상당히 발전하게 됨..

R은 태생자체가 통계학자들에 의해서, 통계학을 위해서 개발된 까닭에 통계에서 강점을 가집니다. 
그리고 개발용으로 만들어진 언어가 아니므로 파이썬과 비교했을 때 배우기가 쉽고, 통계학자, 분석가들을 타겟으로 만들어진 언어

SPSS와 비교했을 때 R은 GUI를 제공하지 않으므로 명령어를 다 알아야 한다.



EDA 
탐색적 데이터 분석
데이터를 한 번 쭉 보는데
이렇게도 보고, 저렇게도 봐서 분석 업무를 수행하겠다는 뜻

결측치, 이상치에 대한 제거 및 대치에 대한 방법과 도구 그리고 전략을 구성하는 일이 중요하다..!


어설프게 시각화하면 욕먹는다..
고객들은 보는 눈이 아주 높다..

30년전... 
데이터에 대한 권한도 없고, 숫자로 받아가서 자기가 알아서 만들어야 한다.

20년전 
웹으로 바뀜
데이터를 프레임 안에 넣고
엑셀로 데이터로 만들어서
웹에 엑셀 버튼이 있어서 그걸 다운받고, 
시각화는 그들의 영역...!


10년전...
고객들은 보는 눈이 높아짐..



홀로그램으로..
그 사람을 재현할 수 있는 수준까지.. 옴..


### R 환경 설정

설치 과정 중 설정사항은 모두 Default 값을 유지한다.  
[R 설치](https://cran.seoul.go.kr/)  
[RStudio 설치](https://rstudio.com/products/rstudio/)  




### R 의 변수와 연산

수집한 데이터를 저장하고, 다시 사용하기 위해서 변수를 생성한다.   
**R 에서 변수는 동적할당을 허용하므로 값이 오염될 가능성을 염려해야 한다.**  
**RStudio에서 `<-`를 편하게 입력하기 위해 `Alt + -`를 사용하면 단축키가 적용된다.**
```r
a <- 1
b <- 2
c <- a + b # 3

# 은 주석
```

```r
sqrt(36) # 6
max(3,6,9) # 9
abs(-25) # 25
```


#### R의 변수 표기법
1. 첫글자는 알파벳으로 시작하지만 Dot(.)를 쓰는 경우도 있다.
1. 두 번째 위치하는 글자부터는 알파벳, 숫자, Dot(.), 언더바(_) 를 사용할 수 있다.
1. 대소문자의 구분

```r
var.1, num_sum, s1
num_a, num_A # 서로 다른 값

```


### 벡터(R에서 자료구조를 지원하는 수단, 도구)

**배열**
- 동일한 메모리 공간
- 동질의 데이터

데이터 분석 작업을 통해 접하게 되는 데이터는 대부분 1차원 배열 형태이거나 2차원 배열 형태이다. 
1차원 배열 데이터는 데이터가 일직선상에 위치한다.


|학생 10명의 키 |
|---|
| 159 | 
| 175 |
| 178 |
| 177 |
| 183 |
| 178 |
| 165 |
| 181 |
| 179 |
| 159 |

- 교육생 10명의 키
- 교육생 20명의 시험 성적
- 2학년 학생들이 선호하는 유튜버 자료


#### 2차원 배열 데이터


| 사람 | 국어 | 영어 | 수학 |
|---|---|---|---|
| `강감찬` | 20 | 70 | 50 |
| `이순신` | 30 | 20 | 90 |
| `을지문덕` | 40 | 60 | 10 |


### 워밍업 벡터

#### 벡터 만드는 법

벡터를 만드는 함수는 소문자 c를 활용한 `c()` 이다. c는 connect의 첫 글자를 따온 의미대로 여러개의 값을 연결하고 묶어주는 역할을 한다. 
1. 벡터에는 동일한 종류의 자료형이 저장되어야 한다.

```r
x <- c(1,2,3) # 숫자형 벡터
y <- c('a','b','c') # 문자형 벡터
z <- c(FALSE, TRUE, TRUE, FALSE) # 논리형 벡터

> x
[1] 1 2 3
> y
[1] "a" "b" "c"
> z
[1] FALSE  TRUE  TRUE FALSE
```

벡터에는 동일한 종류의 자료형이 저장되지 못하면 자료형이 변환되는 경우가 생긴다. 

```r
w <- c(1,2,3, 'char')
> w
[1] "1"    "2"    "3"    "char"
```


#### 연속적인 숫자로 이루어진 벡터의 생성
```r
v_1 <- 50:90
v_1

# 50 ~ 90 까지의 값이 생성됨
```

#### 일정한 간격의 숫자로 이루어진 벡터 생성
seq(start, end, step) 함수를 이용하여 일정한 간격으로 이루어진 벡터를 생성할 수 있다.

```r
v3 <- seq(1, 100, 3)
v3

# 1부터 100까지 3의 간격으로 이루어진 정수 벡터 생성
```

#### 반복된 숫자로 벡터 생성
seq(start, end, step) 함수를 이용하여 일정한 간격으로 이루어진 벡터를 생성할 수 있다.

```r
re1 <- rep(1:5, times=3)
re1
# 1 ~ 5까지의 연속정인 정수가 3번 반복됨
```


#### 벡터의 원소에 이름 지정

```r
score <- c(90, 85, 70)
names(score) <- c('Min', 'Tom', 'Haemil')
score

> score
  John    Tom Haemil 
	90     85     70
```

#### 벡터에서 값을 추출!

- 벡터에서도 index를 통해서 걊의 위치에 접근할 수 있다. 
- index는 **1부터 시작**한다.
- 벡터에서 값을 추출하는 방법은 다양하다.

```r
num <- c(1,2,3,4,5,6,7)

num[c(1,3,5)] # 1 3 5
num[c(4:7)] # 4 5 6 7
num[seq(1,7,2)] # 1 3 5 7
num[-2] # 1 3 4 5 6 7
num[-c(3:5)] # 1 2 6 7

```

```r
time <- c(45, 30, 45)
names(time) <- c('Hongdae', 'Sindorim', 'Kkachi')
time[1]
time['Hongdae']
time[c('Sindorim', 'Kkachi')]

```

#### 벡터의 원소에 재할당

```r
vec <- c(1,3,5,7,9)
vec # 1 3 5 7 9

vec[2] <- 2
vec # 1 2 5 7 9

vec[c(1, 5)] <- c(10, 20)
vec # 10 2 5 7 20
```

### 벡터 연산

분석하려는 데이터가 담긴 1차원 배열 형태의 데이터가 벡터에 저장된 상태라면 다양한 연산이 가능하다. 산술연산뿐만 아니라 벡터와 벡터간의 연산도 가능하다. 


#### 산술 연산
```r
a <- c(1,2,3,4,5)
a + 2 # 3 4 5 6 7

b <- c(1,4,3,7,8)
b*2 # 2 8 6 14 16

```

#### 벡터와 벡터간의 연산

```r
a <- c(1,2,3,4,5)
b <- c(1,4,3,7,8)
a + b # 2 6 6 11 13

```

#### 벡터에 적용 가능한 다양한 함수

| 함수 | 설명 | 
|---|---|
| `sum()` | 벡터에 포함된 원소들의 합 | 
| `mean()` | 벡터에 포함된 원소들의 평균 | 
| `median()` | 벡터에 포함된 원소들의 중앙값 | 
| `var()` | 벡터에 포함된 원소들의 분산 | 
| `sort()` | 원소들의 정렬(asc가 기본) | 
| `range()` | 벡터에 포함된 원소들의 범위 |
| `length()` | 벡터에 포함된 원소 개수 | 
| `sd()` | 벡터에 포함된 원소들의 표준편차 | 
| `max()`, `min()` | 벡터에 포함된 원소의 최대, 최소값 | 




```r
ten <- c(1,2,3,4,5,6,7,8,9,10)
sum(ten) # 55
sum(ten * 2) # 110
length(ten) # 10, 원소의 개수
mean(ten[5:10]) # 7.5, 5 ~ 10 값들의 평균
max(ten) # 10
min(ten) # 1
sort(ten) # 1 2 3 4 5 6 7 8 9 10, 오름차순 정렬

```


#### 벡터와 논리연산자의 조합

```r
ten <- c(1,2,3,4,5,6,7,8,9,10)
ten[ten > 5] # 6 7 8 9 10
sum(ten > 5) # 5보다 큰 원소의 개수
sum(ten[ten > 5]) # 5보다 큰 원소의 합
ten == 5 # FALSE FALSE FALSE FALSE TRUE FALSE FALSE FALSE FALSE FALSE
```

### List

벡터(Vector)가 같은 자료형의 값들을 1차원 형태로 저장하는 자료구조라면 
리스트는 서로 다른 자료형들을 저장하는 자료구조이다.  

```r
rank <- c(90, 85, 79, 84)

my.info <- list(name='ham', age=30, status=TRUE, score=rank)
my.info
```

### Factor

팩터는 문자형 데이터가 저장된 벡터의 한 종류이다. Vector에 저장되는 값들을 몇 종류의 값들로 구분지을 수 있을 때 Factor를 사용한다. 

```r
bloodtype <- c('A', 'O', 'B', 'O', 'AB', 'AB', 'B')
bloodtype.new <- factor(bloodtype)
bloodtype #  "A"  "O"  "B"  "O"  "AB" "AB" "B" 
bloodtype.new
# [1] A  O  B  O  AB AB B 
# Levels: A AB B O

levels(bloodtype.new) # "A" "AB" "B" "O" 

```

#### Easy Test

- 벡터 생성하기  

```r
vec1 <- c(10, 20, 30, 40, 50)
vec1
```

- 100부터 200까지 짝수로 증가하는 벡터 만들기

```r
vec2 <- seq(100, 200, 2)
vec2

```

- TRUE 20개 만들기

```r
vec3 <- rep(TRUE, times=20)
vec3

```

- 표를 보고 문제에 답하기

| `월` | jan | feb | mar | apr | may | jun | jul | aug | sep | oct | nov | dec |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| `지각횟수` | 5 | 4 | 7 | 7 | 5 | 5 | 7 | 6 | 5 | 4 | 4 | 3 |

```r
late <- c(5, 4, 7, 7, 5, 5, 7, 6, 5, 4, 4, 3)
names(late) <- c('jan', 'feb', 'mar', 'apr', 'may', 'jun', 'jul', 'aug', 'sep', 'oct', 'nov', 'dec')
late

# 7, 9월의 지각횟수를 구하라
late[c('jul', 'sep')]

# 상반기 결석 평균
mean(late[1:6])

# 하반기 결석 횟수
sum(late[7:12])
```


### 2차원 데이터를 분석하기 위한 자료구조

데이터 분석 영역에서 분석가가 만나는 데이터는 2차원 구조를 가진 경우가 더 많다. R에서는 이를 위해 Matrix와 DataFrame 이라는 형태의 자료구조에 저장한 후 분석한다. 

R에서는 하나의 주제를 가진 데이터를 1차원 형태로 나타내고 Vector라는 자료구조를 통해서 관리할 수 있지만 

| `국어점수` |
|---|
| 20 |
| 30 |
| 40 |


하나의 대상에 대해 여러 주제의 데이터를 수집했다면 이는 아래 표처럼 **2차원 형태의 데이터**로 나타내야 한다. 

| 사람 | 국어 | 영어 | 수학 |
|---|---|---|---|
| `강감찬` | 20 | 70 | 50 |
| `이순신` | 30 | 20 | 90 |
| `을지문덕` | 40 | 60 | 10 |

2차원 데이터는 표를 통해서 나타낼 수 있다.   
행과 열이 교차로 만들어지는 영역을 Cell(셀)이라고 표현한다.  
row 또는 observation이라고 한다. 
column 또는 variable 이라고 한다.  

| `row or col` | col | or | variable |
|---|---|---|---|
| `row` | row | or | observation |
| `row` | row | or | observation |
| `row` | row | or | observation |


### Matrix(매트릭스)

#### Matrix 만드는 법

매트릭스는 2차원 형태의 자료구조이다. 매트릭스의 셀에는 동일한 자료형이 저장되어야 한다.

```r
m <- matrix(1:20, nrow = 4, ncol = 5, byrow = T)
m
```

#### Matrix를 cbind, rbind 함수를 통해 제어하기

cbind, rbind 함수를 통해 벡터와 벡터, 벡터와 매트릭스, 매트릭스와 매트릭스를 묶을 수 있다.
이를 통해서 Matrix를 새롭게 만들 수 있다.

```r
x <- 1:4
y <- 5:8
m1 <- cbind(x, y)
m2 <- rbind(x, y)
m1
m2

m3 <- cbind(m, m1)
m3

```
#### Matrix의 원소값 출력하기

Matrix의 원소값에 접근하기 위해서는 매트릭스 변수명 뒤에 `[]` 2개의 인덱스를 전달하면 된다.
그리고 2개의 인덱스 중 하나를 생략하면 행이나 열의 모든 값을 가져올 수 있다. 인덱스를 전달하지 않으면
전체 매트릭스가 출력된다. 



```r
m <- matrix(1:16, nrow = 4, ncol = 4)
m # m[] 과 같음, 인덱스를 전달하지 않은 것과 같은 값

m[5, 5]
m[4,]  
m[,4]  




```

그리고 여러개의 인덱스를 추출하기 위해선 `c()`함수를 이용하거나 `:` 연산자(연속적인 숫자의 벡터를 만드는)를 이용할 수 있다.

```r
m[2, 1:3]
m[1,c(1,2,4)]

m[1:2, ]
m[,c(2,4)]  
```

#### Matrix의 row, col에 이름 붙이기

Matrix의 row, col에 이름 붙이면 데이터에 대해 더 쉽게 이해를 얻을 수 있다. 
그리고 이름을 인덱스로 사용할 수 있다.

```r
m <- matrix(1:16, nrow = 4, ncol = 4)
m
rownames(m) <- c('1q', '2q', '3q', '4q')
colnames(m) <- c('1c', '2c', '3c', '4c')
m

m['1q',]
```





### DataFrame

각기 다른 자료형을 저장하기 위해 DataFrame은 사용되며 `data.frame()` 함수를 이용해서 만들 수 있다. 
보통 서로 다른 자료형의 벡터를 결합해서 생성한다. 주의사항은 데이터 프레임의 경우 열을 잘라서 보았을 때는 해당 열의 자료형이 동일해야 한다는 것이다. 

```r
medici <- c('은경', '득규', '건우')

medici.rank <- data.frame(medici, rank)
medici.rank

medici.rank[,1]
# [1] 은경 득규 건우
# Levels: 건우 득규 은경
```

#### iris 데이터셋을 활용해서 DataFrame 제어

```r
iris
iris[, c('Sepal.Length','Sepal.Width','Species')]
iris[1:5,]

iris[1:5, c(1,2,5)]
```

### Matrix와 DataFrame 제어

#### Matrix와 DataFrame 에서 사용하는 기본적인 함수

| 함수 | 설명 | 
|---|---|
| `dim()` | 행과 열의 개수 | 
| `nrow()` | row의 개수 | 
| `ncol()` | column의 개수 | 
| `colnames()` | column의 이름 출력 |
| `names()` | colnames와 결과 동일 | 
| `head()` | 데이터셋의 앞부분 6row | 
| `tail()` | 데이터셋의 뒷부분 6row |
| `str()` | 요약된 정보 보기 | 
| `unique()` | Factor 요소의 중복 제거 | 
| `table()` | Factor의 요소별 개수 세기 |


```r
iris[, 5] # 품종의 데이터 150개를 보여줌
unique(iris[, 5]) # 데이터가 몇개의 Levels 로 구성되어 있는지 보여줌
table(iris[, 5]) # 그룹별로 몇개인지 개수를 보여줌

```

#### Matrix와 DataFrame 행과 열의 계산하는 함수

| 함수 | 설명 | 
|---|---|
| `colSums()` | column의 합 | 
| `colMeans()` | column의 평균 | 
| `rowSums()` | row의 합 | 
| `rowMeans()` | row의 평균 |


```r
colSums(iris[, -5])
colMeans(iris[, -5])
rowSums(iris[, -5])
rowMeans(iris[, -5])
```

#### transpose Matrix 

2차원 형태의 데이터의 행과 열의 방향을 바꾸기 위해 `t()`를 사용한다. 

```r
z1 <- matrix(1:20, nrow=5, ncol = 4, byrow = T)
t(z1)

t(iris)

```


#### Condition DataFrame(조건에 맞는 행, 열값 추출)

`subset()` 함수는 인자로 두 개의 값을 전달받는데, 첫 번째 인자로는 데이터셋을 받고, 두 번째 인자로는 데이터를 추출할 조건을 받는다.   
**subset 함수는 DataFrame의 자료구조 사용가능하므로, Matrix에서도 사용하고 싶다면 자료구조를 변환해야 한다.**  

```r
IR.1 <- subset(iris, Species=='setosa')
IR.1

IR.2 <- subset(iris, Sepal.Length > 5.0 & Sepal.Width > 4.0)
IR.2
IR.2[, c(2, 4)]
```

#### Matrix 산술 연산

Matrix간 산술 연산을 하기 위해서는 행과 열의 크기가 같아야 한다.

```
a <- matrix(1:20, 4, 5)
b <- matrix(21:40, 4, 5)

a - b
a + b
a * b
```

#### Matrix, DataFrame의 자료구조 확인 및 변환



| 함수 | 설명 | 
|---|---|
| `class()` | 자료구조 확인 | 
| `is.matrix()` | 자료가 Matrix인지 확인 | 
| `is.data.frame()` | 자료가 data.frame인지 확인 | 



```r
class(iris) # "data.frame"
is.matrix(iris) # FALSE
is.data.frame(iris) # TURE

c <- matrix(1:50, 10, 5)
c
class(c) # "matrix"
is.matrix(c) # TRUE
```

| 함수 | 설명 | 
|---|---|
| `as.matrix()` | 문자열열은 제외하고 숫자형만 매트릭스로 변환 | 
| `data.frame()` | matrix를 DataFrame으로 변환 | 

DataFrame을 Matrix로 변환할 때 주의할 점은 DataFrame의 모든 값들이 동일한 자료형이어햐 한다는 것이다.

```r
st.df <- data.frame(state.x77)
head(st.df)
class(st.df)

iris.m <- as.matrix(iris[, 1:4])
head(iris.m)
class(iris.m) # "matrix"
```

#### 데이터 프레임의 열을 제어할 때 주의사항

```r
iris$Species # 벡터, 데이터 프레임만 됨
iris['Species'] #  DataFrame만 추출 가능
iris[, 'Species'] # Vector, Matrix, DataFrame 가능

iris[5] # DataFrame만 추출 가능
iris[,5] # Vector, Matrix, DataFrame 가능
```


#### 데이터 프레임에 대한 예제

```r
state.x77
class(state.x77) # matrix

st <- data.frame(state.x77) # data.frame
class(st)

colnames(st)
rownames(st)
dim(st)
str(st)

# Florida의 모든 정보
st['Florida', ]
# Income 컬럼 정보 출력
st['Income']
# Texas의 Area
st['Texas', 'Area']
# Ohio의 Population와 Income
st['Ohio', c('Population', 'Income')]
# Population이 5000 이상인 곳
subset(st, st['Population'] > 5000)

# Income 이 4500이상인 주의 Population, Income, Area
q14 <- subset(st, st['Income'] > 4500)
q14[c('Population', 'Income', 'Area')]

# Income 이 4500이상인 주의 개수
nrow(subset(st, st['Income'] > 4500))

# & 연산자를 활용한 다중 조건
subset(st, st['Area'] >= 100000 & st['Frost'] >= 120)

# & 연산자를 활용한 다중 조건
subset(st, st['Population'] < 2000 & st['Murder'] < 12)

# Illiteracy가 2.0 이상인 주의 평균수입
q18 <- subset(st, st['Illiteracy'] >= 2.0)
colMeans(q18['Income'])

# 문맹률에 따른 평균 수입의 차이 구하기
q19.more <- subset(st, st['Illiteracy'] >= 2.0)
q19.less <- subset(st, st['Illiteracy'] < 2.0)
colMeans(q19.more['Income'])
colMeans(q19.less['Income'])

colMeans(q19.less['Income']) - colMeans(q19.more['Income'])

# Life.Exp 가 가장 높은 주(범위 확인 후 작성)
rownames(subset(st, st['Life.Exp'] == 73.60))

# Pennsylvania 보다 수입이 높은 주를 출력
rownames(subset(st, st['Pennsylvania','Income'] < st['Income']))


```


---

#### 문제정의 및 계획 
기획이 필요하지만... 현장에서 작업을 하게 된다면.. 선배들이 하게 되는 영역이다.
문제 정의 및 기획에 대한 일을 맡는다.


#### 데이터 수집...!

관련되어 있는 데이터 수집..!
데이터베이스 이외 많은 곳에서 데이터가 흩어져 있다.
usb, 엑셀, 아직 디지털화되지 않은 정보들 등...


#### 정제..!
필요한 자료를 정제 및 전처리를 해야 한다.

데이터 전처리와 관련된 책..!
- 파이썬을 활용한 데이터 길들이기...(데이터 전처리와 관련된 기술이 집약된 대표적인 책) -2.x 문법의 책
- 데이터 전처리 대전.. 장점: 파이썬 및 SQL, R 등 으로 같이 쓰어짐..

탐색적 데이터 분석


결론을 보여줄 때 가장 좋은 게 이미지..
그 다음 그에 대한 근거를 보여주면..! 



#### 가상환경에 익숙해지는 게 좋다.


#### 64, 32 의 가장 큰 차이는 사용할 수 있는 메모리의 그릇 차이다. 


#### R 명령어
> print(10 + 1)
[1] 11
> getwd()

install.packages('ggplot2')




시각화 표준도구
dplyr 데이터 정제, 도구 
대용량의 데이터를 읽어들일 때 사용 
tidyr 피봇하거를 사용, 롱포맷을 숏으로.. 숏포맷을 롱포맷으로..
tbble - 데이터 포맷을 확장한..



#### 왜 로그를 쓸까

10의 6승, 7승, 8승...
데이터가 이렇게 커지면...


누군가는 돈을 많이 가졌다면...! 누구는 적게 가졌고..

이 떄에 로그를 적용한다면..! 
9천만원은 9
1천만원은 1

**편차...를 줄이기 위해서** 로그를 사용한다. 

극단적으로 나타나면 극단화되어 있는 데이터로 드러나기가 쉽다
데이터를 분석하거나 다룰 때 로그를 많이 적용하기도 한다.

로그를 통해 얻는 또 다른 부수적인 효과


주제에 따른 가설을 설정..!
가설을 검정을 통과하기 위해서는...
도구의 분포가 정규분포를 따르던지, 따르지 않았을 때...!

정규분포를 따른다고 했을 떄..
정규분포를 적용하기 위해서는 로그1p 를 적용한다.
정규분포에 가까운 형태로 드러난다.

1~9형태로 바뀐다..

돈이 많은 사람은 아주 극소수


#### 고등학교에 나오는 표 , T분표, 정규분포

고등학교를 졸업할 때 배우는 3개의 분포..
그 이후 분포는 새로배워야 한다..
이것 이외의 분포...
이항분포.. 등 여러가지가 존재하는데
분포는 왜 필요한가..
분포를 왜 배워야 하는가..

#### 분포표는 어디다가 써먹는가?

통계학은 이런 학문이다.
분포는 비교하기 위한 데이터이다. 
내가 연구하는 데이터가 이 분포에서 어떤 유형을 보이는지 알기 위해서..!

어떤 분포를 따르는 데이터를 만들겠다.
비교하는 데이터를 만들겠다..
어떤 특정 구간에 들어갈 확률은 얼마나 되느냐...

이 도구가 그냥 다 한다...



#### 값에 의해서 타입이 결정되는 언어이므로 class, typeof와 같은 데이터 타입 검사가 필요하다.



#### 벡터 원소 a는 변수로 2를 하나 가지고 있다...
1,2,3,4,5

모든 변수는 다 참조를 갖는다. (즉, 주소를 가짐)



### Indexing 
값을 추출할 때 사용하는 게 
인덱싱이다.

자 그러면 이제 슬라이싱이라고 하는 것이 대표적인게..
시퀀스 연산자를 사용하는 것이다..! 
시퀀스 연산자를 사용하는 방법으로 요게 있다.!


#### 통계학과 교수처럼 가르칠 수는 없다..
다만, 용어를 정확하게 설명할 수 있다..
R을 가지고 하는 동안에는 통계하고 사용하는 동안에는 
겹치지 않을 것이다. 

통계에서는 이렇게 얘기하고 이렇게 얘기한다는 것을... 얘기한다..
정리하면서 얘기한다..

통계학 용어에서는 모수.. 파라미터이다.

모집단은 전체집단을 얘기한다... 전체집단의 특징을 나타내는 매개변수를 모수라고 한다.

모평균과 모표준편차를
가지고 무엇을 만드냐면... 정규분포 데이터를 만들 수가 있다. 
전체 데이터를 만들어놓은 것이다. 

모평균과 모편준편차를 찾아내야 한다.
모집단 데이터를 랜덤하게 만들어내야 한다. '
그 크기를 첫번쨰 매개변수로 둔다.'
그 크기를 따르느 ㅔㄷ이터를 천만건, 백만건을 만들겠다.. 

반환값이 벡터인데 엘리어스가...!
이렇게 나오는게 아니라 0%, 25%, 50%, 75% 이렇게 나온다...! 
q타일 함수는 계산을 하고...

e... 4

75% 는 인덱스가 4...

dnorm(x, mean = 0, sd = 1, log = FALSE) 
디놈은 무엇에 쓰는 함수인가..?!
68이 min이고, 미디안이다. 
x이고 덴서티이다.



pnorm(q, mean = 0, sd = 1, lower.tail = TRUE, log.p = FALSE)
qnorm(p, mean = 0, sd = 1, lower.tail = TRUE, log.p = FALSE)
rnorm(n, mean = 0, sd = 1)


dnorm,pnorm, rnorm 을 기억해야 한다..!
가장 중요한 것...! 3가지..!


디놈, 피놈, 알놈..!


통계를 도구로 쓰는 사람들..
최소한.. 통계에 대한 역량은 획보해야 한다..!

꾸준히 해야 한다..! 
혼자 공부할 때보다 같이 공부해야 오래가기 쉽다..!


벡터에 저장된 원소의 값...!

### Broadcasting Op
vec1 <- 1:3
vec2 <- 2

Broadcasting 연산이 발생한다. 

1,2,3과 2가 계산이 될 때
이에 동일 위치를 맞추기 위해 

1,2,3
2,2,2
Broadcasting 연산이 된다.

v1 <- 1:3
v2 <- 2
(v3 <- v1 + v2)
v4 <- 1:3
v5 <- 1:2
(v6 <- v4 + v5)

#### Quiz..! 
위치가 필요하면 which를 쓰면 된댜. 
얘는 만족하는 값이 나오는 함수는?
만족하는 값이 나오는 인덱스가 출력되는 함수는?


#### p.81 팩터...!

통계에서의 변수는 두 가지로 나뉜다.
연속형 변수와 범주형 변수 두 가지로 나뉜다.

연속형 변수는 continus 수치들이 대표적인 예시가 된다.

범주는 특정 범주를 한시적으로 분류할 때...! 
ABCDEF 까지 존재한다..! 
유효한 어떤 정보들 몇가지로 범주형 데이터를 유지할 때 벡터를 사용한다. 

bt.new 라는 ㅔㅂㄱ터를 하나 

팩터는 유니크한 값들을 여기가 가지고 있는 수준이 되는 데, 이를 레벨 정보라고 한다. 


#### 팩터는 왜 쓰는가? Why -> Factor
R은 범주형 데이터를 다루기 위해 팩터를 쓴다..
범주형 데이터를 다룰 수 있는 방법이 필요하다.

데이터를 분석한다는 것은 데이터를 분석하는 과정에서 범주형 데이터를 연속형데이터로 변환해향 한다. 

통게에서 변수는 연속형과 범주형이 있는데, 연속형 데이터는 x축과 y축에 표현이 가능한데
범주형 데이터는 위치를 알 수가 없음...
범주형 데이터는 분석과정에서 반드시 인코딩이라는 과정이 필요하다. 

인코딩에 대한 기본적인 정보를 유지하고 있느게 팩터이다.! 
그래서... 

팩터라는 것을 만들어놓는다. 
일반적으로 R은 문자열을 읽으면 팩터로 바꾸려고 한다. 
그러한 기능이 활성화되어 있다. 
다 팩터로 바뀌어 있는 경우도 있는데..!

그냥 써야 하는 경우는..?! 언제인가?!
이름은 char이어야 한다.
반면, 직급은 팩터형 데이터여야 한다.!! 

사는 주소는 케바케..!이다. 
서울, 경기 처럼 구분을 해놓으면 범주
상세 주소를 쭉 나열해놓는 경우는 나열해놓은 문자열 데이터이다. 

문자열로 되어 있는 범주형 정보는 연속형 정보로 변환하기 위한 인코딩 과정을 거쳐야 한다. 
Onehot 인코딩!!! 
범주형 데이터를 연속형 데이터로 바꾸느 원핫 인코딩을 한다. !

팩터를 준비해놓으면 변환과정을 자동으로 넘어갈 수 있다. 


#### 팩터를 제대로 공부해놓지 않으면 고생한다.
팩터를 제대로 공부해놓을 필요가 있다.
팩터에서는 레벨이 중요하다..!

문자열이었다면 발생하지 않았을 제약인데..! 
여기에 오면 문제가 생긴다..! 




#### 1차원 구조의 배열은 벡터, 2차원 구조의 배열은 매트릭스

하나의 컬럼은 동일한 데이터 타입
로우로 보면 이질적인 데이터 타입...! 

and row 


#### 기존 매트릭스에 벡터를 추가하여 새로운 매트릭스 만들기 
cbind -> 열 방향으로 결합

rbind -> 행 방향으로 결합..!



#### 데이터 프레임은 모든 문자열을 전부 팩터로 바꾼다..!
코드.3-6, P101

### 


범주형에 대한 기초통계를 만드는 건..
집계표는 무엇으로 만드는지 주의해서 볼 필요가 있다. 


### 전체 실습 코드

```
a = 10
b <- 20
c <- TRUE
d <- F
e <- 'abc'

data(iris) # 번들 되어 있는 데이터, 지금 로딩된 것 아니고, 
           # 앞으로 로딩될 것... 
           # 
iris

typeof(iris)
typeof(a)
typeof(c)
typeof(d)
typeof(e)

typeof(as.integer(a))

class(iris)
class(a)
class(c)
class(e)

typeof(NaN)
class(NaN) # 타입은 숫자임..

typeof(Inf)
class(Inf)

a <- 1:5 # 시퀀스를 만드는 것...! 
class(a)
typeof(a)


a <- c(1,2,3,4,5)
class(a)
typeof(a)

a <- as.integer(a)
class(a)
typeof(인티저)


scores <- c(90, 88, 99, 100, 100, 92)
scores
scores[1]
scores[0]
scores[6]

names(scores)
names(scores) <- c('A', 'B', 'C', 'D', 'E', 'F')

scores['A']

arr_1d <- c(1,2,3.14) # Numeric으로 저장됨, Double임
arr_1d <- c(1,2,'3') # character/char으로 저장됨, char, string임
arr_id <- c(1,2,T) # numeric/double
# 타입에 대한 부분을 정리를 잘해야 한다.

# rm(arr_id)
# ls()
rm(list = ls())


arr <- 1:100
arr2 <- as.integer(seq(1, 100, 1)) # numeric 타입으로 만들어진다 
# 정수로 만들어야 한다면 형변환!!

# arr3 <- seq.int(1, 100, 1) # 이런 형태로 안씀.. 
# 시퀀스로 만들고 형변환을 함...
# 시퀀스로 만들고 형변환을 하는 경우는 오버로딩..?!
# ...!

# 매개변수가 가변이다. times, each 
(arr3 <- rep(1:3, 3))
(arr3 <- rep(x = 1:3, times = 3, each = 2)) # 두 번째 매개변수가 times이다.

scores <- c(90,95,100)
names(scores)
names(scores) <- c('KOR', 'MATH', 'ENG')
scores

names(scores[2])
names(scores)[2] <- 'MAT'
names(scores) <- c('KOR', 'MAT', 'ENG')

names(scores)


letters # 26개의 알파벳을 저장하고 있는 벡터
LETTERS

(vec <- sample(letters, 5, replace = T))
# 복원추출.. 꺼내고 
# 로또는 비복원추출이다... 

(vec <- sample(letters, 5, replace = F))



# 비복원 추출은 F이다. 

vec3 <- rnorm(1000000, 68, 5)
(q <- quantile(vec3))
q['25%']
q['75%']

range(vec3)


v1 <- 1:3
v2 <- 2
(v3 <- v1 + v2)
v4 <- 1:3
v5 <- 1:2
(v6 <- v4 + v5)

set.seed(123) # 현재시간을 정수로 계산해서..! 롱타입의 정수로 지정되어 있다.
vec <- sample(letters, 200, replace = T) # 200개가 안되므로
vec > 's' # logical 벡터가 됨... 관계 연산자와 논리연산자를 사용하면 
vec[vec > 's']         # Logical Vector가 됨...
# True에 해당하는 값들만 쭉 출력됨.. Boolean Indexing...
# 조건을 만족하는 데이터를 찾아낼 때 쓴다.
# 조건을 만족하는 인덱싱을 찾아낼 때 쓴다..
# Logical Boolean Indexing

which(vec > 's') # 값이 있는 위치정보가 나옴, 인덱스값 
                # 조건을 만족하는 데이터의 위치를 얻는 행위를 더 많이 함




# seed를 이용해서 난수를 만들면 동일한 결과를 얻게 된다.


vec2 <- c(T, F, T, T, F, F)
sum(vec2) # 조건을 만족하는 값의 개수 


myinfo <- list(name='Tom', age=30, status=T,score= c(90,85,70,84))
myinfo
myinfo$name
myinfo[1]
myinfo[[1]] # 첫 번쨰 항목에 들어가 있느 정보를 볼 때는 [[1]] 두개를 쓴다.

myinfo$score
myinfo[[4]] # 두 가지 방법 중에 하나로 쓸 수 있다. 

myinfo$score[3]
myinfo[[4]][3] # 두 가지 방법 중에 하나로 쓸 수 있다. 
# 개별 정보를 꺼내는 방법..!


set.seed(123)
(bt <- sample(c('A', 'B','AB','O'), 100, replace = T))

(bloodType <- as.factor(bt)) # 팩터로 바꾸는 가장 쉬운 방법

unique(bt)
typeof(bloodType) # 내부 데이터는 숫자로 되어 있는 정보이다.
class(bloodType)
bloodType[1]
as.integer(bloodType[1]) # 출력되는 것만 AB이고, 2로 되어 있다.

# 팩터를 수동으로 생성하는 방법

(bloodType2 <- factor(bt, levels = c('A', 'B', 'AB', 'O'))) # 레벨을 우리가 결정한다.
bloodType2[1]
as.integer(bloodType2[1])
# 팩터는 보이는 정보와 계산되는 정보가 다르다. 
# 바깥에 보여지는 것은 문자열...!

bloodType2[1] <- 'A'
bloodType2[1]

bloodType2[1] <- 'C'
bloodType2[1]
# 카테고리를 관리하는 데 있어서는 아주 유효한..!
# 레벨은 어떠헥 알 수 있나?
levels(bloodType2)
levels(bloodType2) <- c('A', 'AB', 'B', 'O')


bloodType2[1] <- 'AB'
as.integer(bloodType2[1])



(mtx1 <- matrix(1:20, nrow = 4))
(mtx1 <- matrix(1:20, nrow = 4, byrow = T))
dim(mtx1)
dim(mtx1) <- c(5, 4) # 메타정보를 바꾸면 행과 열의 크기가 바뀜

mtx1
dim(mtx1) <- NULL
mtx # 디멘션 정보는 원래 벡터이다. 여기에 차원에 대한 정보를 더한 것뿐이다.

mtx1
dim(mtx1) <- c(4,5)
mtx1
mtx1[2, 2]

mtx1[1, ]
mtx1[, 1]

mtx1[1, 2:4] # 범위 인덱싱을 이용해서 뽑아볼 수도 있다.
mtx1[-2, ]

mtx1
rownames(mtx1)
colnames(mtx1)

(colnames(mtx1) <- c('c1', 'c2', 'c3', 'c4', 'c5'))
(rownames(mtx1) <- c('R1', 'R2', 'R3', 'R4'))
mtx1

mtx1['R2', 'c2']
# mtx1['R2', 'c2':'c4'] <= numeric 이어야 한다.

mtx1['R2', c('c2', 'c3', 'c4')]

city <- c('Seoul', 'Tokyo', 'Washington')
rank <- c(1,3,2)
city.info <- data.frame(city, rank, stringsAsFactors = F)
city.info
str(city.info)
city.info$city <- as.factor(city.info$city)
str(city.info)



str(iris)
levels(iris$Species) # setosa 1, versicolor 2, virginica 3

dim(iris) # 행과 열과 관련된 정보!
dim(iris)[1]
dim(iris)[2]
nrow(iris)
ncol(iris)
colnames(iris)

colnames(iris)[5] <- 'species'
colnames(iris)
head(iris, 3)
tail(iris, 3)

iris[, 'species']

table(iris[, 'species'])


c1 <- rnorm(1000000, 250, 10)
c2 <- rnorm(1000000, 160, 5)
df <- data.frame(c1, c2)
str(df)

df2 <- subset(df, c1 < 240 & c2 > 170)
head(df2)
(idx <- as.integer(rownames(df2)))
colnames(df2)

typeof(rownames(df2)) # 인덱스는 넘버이다..!
head(df)

#df[-idx, ]$c1
#df[-idx, 'c1']

range(df[-idx, 'c1'])
range(df[-idx, 'c2'])






```