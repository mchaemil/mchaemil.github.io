---
layout: article
title: Database/Data | 데이터란 무엇인가?
tags: SQL

---

## **Today What I Learend**  


SQL 문을 통해 데이터를 정제할 수 있는 다양한 연산자를 학습하고
이를 활용하여 데이터를 정제하는 방법을 연습해보자


---
**Today I Learend**

- 데이터는 무엇인가?
- 데이터 베이스는 무엇인가?
- MariaDB 환경 설정
- SQL 이란?


---


### 데이터란 무엇인가?


**[위키백과](https://ko.wikipedia.org/wiki/%EC%9E%90%EB%A3%8C)**
> 자료(資料, data, 데이터, 문화어: 데타)는 수, 영상, 단어 등의 형태로 된 의미 단위이다. 보통 연구나 조사 등의 바탕이 되는 재료를 말하며, 자료를 의미있게 정리하면 정보가 된다.

**[나무위키](https://namu.wiki/w/%EB%8D%B0%EC%9D%B4%ED%84%B0#s-1)**
> Data[1]는 라틴어 단어 Datum의 복수형인 Data에서 유래했으며 라틴어에서 Datum의 뜻은 "present/gift, that which is given, debit" 이다

1. 이론을 세우는 데 기초가 되는 사실. 또는 바탕이 되는 자료.
1. 관찰이나 실험, 조사로 얻은 사실이나 자료.
1. 컴퓨터가 처리할 수 있는 문자, 숫자, 소리, 그림 따위의 형태로 된 자료


#### 데이터(Data)의 특성

데이터는 신호,기호,숫자,문자 등으로 기록되며, 정보를 위한 기초적인 자료를 말한다. 데이터는 가공을 거치지 않으면 정보라는 단위가 되지 못한다. 그러므로 데이터는 정보로서의 가치가 부족하며, 가공되지 않고, 의미를 갖지 않은 상태의 개체라 할 수 있다.

**자료(data)를 가공해 얻는 것이 정보(information)다**


#### 정보(Information)의 특성

특정한 의사결정을 위해서 Data를 의미와 목적에 맞게 가공한 형태를 정보라고 할 수 있다. 

**직접 생각해본 예시**
- 겨울날 아침에 나가는 데 옷을 얼마나 따듯하게 입어야 할지 몰라서 확인하는 것은 정보가 됨
- 공휴일은 시내로 사람들이 많이 몰리므로 약속 장소를 어디로 잡을지 판단하는 정보가 됨

이처럼 정보(Information)는 데이터를 의미와 목적에 맞게 판단하는 일이 된다. 정보는 사용하는 사람이나 상황에 따라서 의미와 가치가 달라질 수 있으므로 어떠한 맥락에서 정보가 사용되었는지 이해하는 것이 중요하다



### 데이터 베이스는 무엇인가?

여러 사람이 공유하고 사용할 목적으로 관리되는 통합적인 정보의 집합을 얘기하며, 데이터가 논리적으로 모인 집합을 의마한다. 


### MariaDB Download

[MariaDB는 무엇인가요? - 출처: 위키백과](https://ko.wikipedia.org/wiki/MariaDB)
> MariaDB는 오픈 소스의 관계형 데이터베이스 관리 시스템(RDBMS)이다. MySQL과 동일한 소스 코드를 기반으로 하며, GPL v2 라이선스를 따른다. 오라클 소유의 현재 불확실한 MySQL의 라이선스 상태에 반발하여 만들어졌으며, 배포자는 몬티 프로그램 AB(Monty Program AB)와 저작권을 공유해야 한다.




#### MariaDB 폴더 구조

```
MariaDB 10.5
├── bin
├── data
├── include
├── lib
└── share

```


### 데이터 베이스를 공부하기 위해 학습해야 할 용어

#### Entity(엔터티)
사용자가 추적하고자 하는 어떤 사물


#### Attribute(속성)
엔터티는 엔터티의 특징을 기술해주는 여러개의 속성을 가진다.

#### Relationship(관계) 
까마귀발 부호는 관계의 다(Many)를 보여주는데 사용된다.
타원(Oval), 해쉬 마크 및 까마귀 발의 다양한 조합은 그림참고

#### Unique Identifier(식별자)
Entity(엔터티)는 그들을 지칭하거나 식별해주는 속성인 식별자를 가지고 있다.
속성의 식별자는 엔터티의 상단에 나타난다

#### Sub-type(식별자)
서브타입은 배타적 또는 포괄적일 수 있다. 만일 배타적이라면 슈퍼타입은 많아야 1개의 서브타입과 관련될 수 있
다. 만일 포괄적이라면 슈퍼타입은 1개 또는 그 이상의 서브타입과 관련될 수 있다.
[그림 4-1-40]에서 A는 슈퍼타입, B와 C는 배타적 서브타입이다. 구분자는 보이지 않고 있다. 관계는 실선으로 그
려져 있다.
[그림 4-1-41]에서 A는 슈퍼타입, B와 C는 포괄적 서브타입이다. 관계는 실선으로 그려져 있다


#### 의미가 같은 단어들이 너무 많다..! 그렇기에 다 알아야 한다.
의미를 나누는 일은 약속을 정하는 일이므로 모든 약속에 대한 이해를 위해서 같은 단어에 대해서 잘 익혀두자!

튜플(tuple), 속성(attribute), 행,로우(row), 열,컬럼(column), 인스턴스(instance), 필드(field)
엔터티(Entity), 테이블(Table), 레코드(record) 




### SQL
Structured Query Language, 데이터베이스에서 데이터를 저장하거나 얻기 위해서 사용하는 표준화된 언어


**[SQL - 위키백과](https://ko.wikipedia.org/wiki/SQL)**
> 구조화 질의어, SQL은 관계형 데이터베이스 관리 시스템(RDBMS)의 데이터를 관리하기 위해 설계된 특수 목적의 프로그래밍 언어이다. 관계형 데이터베이스 관리 시스템에서 자료의 검색과 관리, 데이터베이스 스키마 생성과 수정, 데이터베이스 객체 접근 조정 관리를 위해 고안되었다. 많은 수의 데이터베이스 관련 프로그램들이 SQL을 표준으로 채택하고 있다.




-- 기본적인 쿼리문을 사용해보자
SELECT <FIELD명>, <FIELD명>, ... 
FROM <TABLE명> 


#### USE
사용할 데이터 베이스를 미리 지정해준다.
아래 코드에서는 employees 데이터베이스를 사용하겠다는 뜻이다.

```sql

USE employees;

```


#### SELECT
셀렉트 뒤의 구문은 테이블에서 컬럼을 가져오라는 명령, 그리고 * 는 모든 것을 지칭!!

```sql
SELECT emp_no, hire_date 
FROM employees 
LIMIT 5
;
```

| emp_no | hire_date | 
|---|:---:|---:|
| `10001` | 1986-06-26 |
| `10002` | 1985-11-21 |  
| `10003` | 1986-08-28 |  
| `10004` | 1986-12-01 | 
| `10005` | 1989-09-12 |  


-------------------


#### 존재하는 테이블 목록 보기

```sql
SHOW TABLES
;

```

#### 질문을 하나 던지기!, 사원 테이블에서 사원들의 이름만 가져와 보자

```sql
SELECT first_name, last_name
FROM employees
;
```


#### WHERE 
##### WHERE 조건: 조건에 만족하는 데이터만 가져온다. 
##### Q. 사원 테이블에서 이름이 'Elvis'인 사람의 정보를 가져와 보자
**데이터 검증**
쿼리문을 작성한 이후 얻어온 데이터에서 내가 원하는 데이터가 들어있는지, 혹은 제외시켰는데 들어가 있는지 꼭 확인해보아야 한다.

```sql
SELECT * 
FROM employees
WHERE first_name = 'Elvis'
;

```

##### Q. 사원테이블에서 성이 'Simel'인 사람인 정보를 가져와 보자.

```sql
SELECT *
FROM employees
WHERE last_name = 'Simmel'
;
```


```sql



```



```python






# 테이블에서 내가 원하는 데이터를 뽑아내느게 능력이다. 스스로 조건에 맞는 처리를 할 수 있어야 한다. 


-- 사원 중에서 사번이 20000번 이하인 사람들의 정보를 출력해보자. 
-- >=, <, <=,  둘다 같지 않다.  <>, != 
SELECT *
FROM employees
WHERE emp_no <= 20000
;

-- 사원 중에서 사번이 20000 이상이고, 20100 이하인 사람들의 
-- 이름과 성별을 출력해보자 
-- AND 연산자는 조건을 추가할 때,
-- 또는 A AND B: A와 B의 조건을 다 만족할 때
-- 마지막에는 데이터를 검증하는 차원에서 추가로 가져와야할 데이터가 필요할 수 있다.

SELECT emp_no, first_name, gender
FROM employees 
WHERE emp_no >= 20000
 

-- 같은 조건인데 다른 쿼리문, 
-- betwweb a and b
-- a 이상 b 이하인 데이터를 가져오는 방법  
--  
SELECT emp_no, first_name, gender
FROM employees 
WHERE emp_no BETWEEN 20000 AND 20100

-- 사원 테이블에서 14000을 초과하고 15000 보다 작은 
-- 사원의 이름을 가져오시오
SELECT emp_no, first_name, last_name
FROM employees
WHERE emp_no > 14000 
AND emp_no < 15000
;

SELECT emp_no, first_name, last_name
FROM   employees
WHERE  emp_no BETWEEN 14001 AND 14999
;

-- 사원 중에 입사한 일자가 '19850101' ~ '19860101'인 
-- 사원들의 정보를 출력해보자 
-- 한 방에 데이터를 뽑으려고 하지 말고 조금씩 업그레이드 해간다. 
-- 일단은 데이터를 보고서 시작을 한다.
-- 날짜를 처리하는 함수를 처리할 때는 DATE_FORMAT(<field 명>), '내가 보고자 하는 날짜 형식')
-- DATE_FORMAT(<field 명>, '%Y') : 연도를 출력
-- DATE_FORMAT(<field 명>, '%M') : 월을 출력
-- DATE_FORMAT(<field 명>, '%D') : 알저를 출력
-- DATE_FORMAT(<field 명>, '%Y%M%D') : 20191217 
-- DATE_FORMAT(<field 명>, '%Y-%M-%D') : 2019-12-17 
-- DATE_FORMAT(<field 명>, '%Y%M%D %H-%i-%p') : 20191217 14-12 pm (24) 대문자는 24
-- DATE_FORMAT(<field 명>, '%Y%M%D %h-%i-%p') : 20191217 14-12 pm (12) 소문자는 12
-- 컨트롤 스페이스 엔더를 누르면 자동완성 기능을 사용할 수 있다. 

 
SELECT DATE_FORMAT(hire_date, '%Y%M%D')
FROM   employees
;

SELECT *
FROM   employees
WHERE  DATE_FORMAT(hire_date, '%Y%M%D') >= '19850101'
AND    DATE_FORMAT(hire_date, '%Y%M%D') <= '19860101'
;

SELECT *
FROM   employees
WHERE  DATE_FORMAT(hire_date, '%Y-%M-%D') BETWEEN '1985-01-01' AND '1986-01-01'
-- AND    DATE_FORMAT(hire_date, '%Y-%M-%D') <= '1986-01-01'
;

-- 나온 결과를 정렬해서 확인해보자 
-- 사원 중에 입사한 일자가 '1985-01-01' ~ '1986-01-01' 인 사원들의
-- 정보를 출력해보는...! 것을 해보자. 최근에 입사한 입사자가 맨 위로 올 수 있도록 정렬하자!
-- ORDER BY <필드명> ASC(1 -> 10) or DESC(10 -> 1)

SELECT *
FROM   employees
WHERE  DATE_FORMAT(hire_date, '%Y-%M-%D') BETWEEN '1985-01-01' AND '1986-01-01'
ORDER BY hire_date DESC
;

-- ASC는 자동으로 붙으므로 큰 것부터 정렬할 때만 DESC를 붙이면 된다. 
SELECT *
FROM  employees
WHERE DATE_FORMAT(hire_date, '%Y%m%d') = '19850101'
ORDER BY hire_date DESC
;



-- 입사년도가 1990년인 사원의 정보를 출력해주세요
SELECT *
FROM   employees
WHERE  DATE_FORMAT(hire_date, '%Y') = '1990' 
ORDER BY hire_date
;


-- 사원들 중에서 성이 'Genin'이거나 'Facello'인 사원의 정보를 출력해보자
-- or 연산자
-- 조건 or 조건 : 둘 중에 하나만 만족해도 출력하는 데이터
 
SELECT *
FROM employees 
WHERE last_name = 'Genin'
OR last_name = 'Facello'
ORDER BY last_name
;


-- IN 연산자를 사용해보자. 
-- OR 와 동일한 결과를 나타낸다. 
-- <필드명> IN ('A값', 'B값') 
-- A값 또는  B값을 만족하는 데이터를 가져온다.
-- IN이 성능이 더 좋다. 


SELECT *
FROM employees 
WHERE last_name IN ('Genin', 'Facello')
ORDER BY last_name
;


-- Alias 별칭
-- <필드명> as 사용하고 싶은 이름 
-- <필드명> 이름에 공백이 있는 경우 '별 칭' 싱글 쿼테이션으로 묶어 준다.

SELECT last_name AS 이름, first_name AS 성
FROM employees 
WHERE last_name IN ('Genin', 'Facello')
ORDER BY last_name
;


SELECT hire_date AS 입사년도
FROM   employees
WHERE  DATE_FORMAT(hire_date, '%Y-%M-%D') BETWEEN '1985-01-01' AND '1986-01-01'
ORDER BY hire_date DESC
;


-- 테이블을 여러개를 조인을 할 때 긴 이름을 가지고 있다면 를 줄여주기 위해서 
-- 테이블 이름을 줄이는 용법
-- table 에 Alias 적용하기
SELECT emp.hire_date AS 입사년도
FROM   employees emp
WHERE  DATE_FORMAT(emp.hire_date, '%Y-%M-%D') BETWEEN '1985-01-01' AND '1986-01-01'
ORDER BY emp.hire_date DESC
;


SELECT *
FROM employees emp
WHERE first_name = 'Parto' AND DATE_FORMAT(emp.hire_date, '%Y') = 1990
;


-- 사원 중에 읾이 s 로 시작하는 사원의 정보르 ㄹ출력해보자 
-- LIKE 연산자 
-- <필드명> LIKE 's' : s 를 포함하는 데이터
-- <필드명> LIKE 's%' : s로 시작하는 데이터
-- <필드명> LIKE '%s' : s로 끝나는 데이터

-- <필드명> LIKE '%s%' : s를 중간에 포함나는 데이터
-- <필드명> LIKE '__s' : 3글자인데 2글자를 모르면 _로 채우고 조회한다. 
-- wild card : % / 무언가를 포함하는 데이터를 찾을 때 좋다.!!

SELECT *
FROM employees emp
WHERE emp.first_name LIKE 's%'
;

SELECT *
FROM employees emp
WHERE emp.first_name LIKE 'Staff___'
;


-- 이러한 조건으로 검색을 진행할 수 있다. 
-- 이러한 방법으로 %연산자를 통해 데이터를 활용할 수 있겠다.  
SELECT *
FROM   board
WHERE  id = '%jisun'
OR     title = 'icecream%'



-- 사원 중에 직무가 'Engineer'와 'Senior Engineer'인 
-- 사원의 사번을 출력해보세요
-- employees의 필드에는 직무가 없다..!
-- titles에는 데이터가 있다. 
-- 테이블에 대한 의미와 연결고리를 가져와야 한다.

-- 성능이 IN이 더 좋다.

SELECT *
FROM   titles
WHERE title IN ('Engineer', 'Senior Engineer')
;


-- 문2)사원중에서 직무가 'Engineer'로 끝나는 사람과
-- 직무가'Staff' 로 끝나는 사람의 사번을 출력해보세요

SELECT emp_no, title
FROM   titles
WHERE  title LIKE  '%Engineer' 
OR     title LIKE '%Staff' 
;


SELECT emp_no, title
FROM   titles
WHERE  title IN ('Engineer', 'Staff')  
;

SELECT emp_no, title
FROM   titles
-- 위의 값과 똑같다.
AND title = 'Engineer' 
AND title = 'Staff'
;

-- 요청 데이터를 어떻게 이해했는가에 따라서 나오는 쿼리가 달라진다. 
-- 직무가 staff 로 끝나는 사ㅏㄻ의 사번을 출력해주세요



-- NULL 값이 없다. 
-- <필드명> IS NULL : 값이 없을 경우
-- <필드명> IS NOT NULL : 값이 NULL이 아닐 경우
-- 사원 중에서 salary가 NULL이 아닌 사원의 정보를 가져와 보자.

SELECT *
FROM   salaries
WHERE salary IS NOT NULL 
ORDER BY salary
;


-- 문제3) 사원 중에서 직무가 'Development' 이거나 
-- 								  'Sales'인 사람들 중에서 
-- 1992년 01월 01일 이후에 배치된 사람 사번을 구해봅시다. 

SELECT *
FROM   departments
-- WHERE title = 'Sales'
-- WHERE  title IN ('Development', 'Sales') 
-- AND    DATE_FORMAT(emp.hire_date, '%Y%m%d') = 1990
; 

-- 한 번에 쿼리를 하는 것으로는 안 된다. 
-- 지금 우리가 안 배웠으니까. 데이터가 있는지를 확인하는 게 우선 작업이다. 

SELECT dept_no
FROM   departments
WHERE  dept_name IN ('Development', 'Sales') 
;

-- d005, d007

SELECT emp_no
FROM dept_emp
WHERE dept_no IN ('d005', 'd007') LIMIT 10
;

-- 뎁트 넘버로 사번으 떙긴다. 사번으로 입사한 날짜로 제한을 주면 끝낸다. 

SELECT *
FROM   dept_emp
WHERE  dept_no IN ('d005', 'd007')
AND    DATE_FORMAT(from_date, '%Y%m%d') >= '19920101'
AND    DATE_FORMAT(to_date, '%Y%m%d') = '99990101'
ORDER BY from_date DESC
;



```
