---
layout: article
title: Database/Data | SQL - 문제 풀어보기
tags: SQL
comments: true

---

## **Today What I Learend**  

SQL의 문제들을 풀어보면서 쿼리문을 다양하게 작성해보는 경험을 가졌다. 문제들을 풀어보면서 이렇게 다양하게 쿼리를 작성할 수 있구나.. SQL이 결코 만만한 영역이 아니구나라고 생각하게 되었다...! 아직 초반이니 너무 잘해야 할 필요는 없다고 생각한다. 다만 열심히 즐겁게 하자..! 즐거움이 꾸준함을 가져다 주리라 믿는다.


---
**Today I Learend**

- 준비단계
- SQL Test
- 

---

### 준비단계

아래의 테이블을 생성하고, 테이터플 입력하여 준비를 마친다.

```sql
DROP TABLE IF EXISTS dept;
DROP TABLE IF EXISTS salgrade;
DROP TABLE IF EXISTS emp;
CREATE TABLE salgrade(
grade int(4) not null primary key,
losal decimal(10,2),
hisal decimal(10,2));
CREATE TABLE dept(
deptno int(2) not null primary key,
dname varchar(50) not null,
location varchar(50) not null);
CREATE TABLE emp(
empno int(4) not null primary key,
ename varchar(50) not null,
job varchar(50) not null,
mgr int(4),
hiredate date,
sal decimal(10,2),
comm decimal(10,2),
deptno int(2) not null);
insert into dept values (10,'Accounting','New York');
insert into dept values (20,'Research','Dallas');
insert into dept values (30,'Sales','Chicago');
insert into dept values (40,'Operations','Boston');
insert into emp values (7369,'SMITH','CLERK',7902,'93/6/13',800,0.00,20);
insert into emp values (7499,'ALLEN','SALESMAN',7698,'98/8/15',1600,300,30);
insert into emp values (7521,'WARD','SALESMAN',7698,'96/3/26',1250,500,30);
insert into emp values (7566,'JONES','MANAGER',7839,'95/10/31',2975,null,20);
insert into emp values (7698,'BLAKE','MANAGER',7839,'92/6/11',2850,null,30);
insert into emp values (7782,'CLARK','MANAGER',7839,'93/5/14',2450,null,10);
insert into emp values (7788,'SCOTT','ANALYST',7566,'96/3/5',3000,null,20);
insert into emp values (7839,'KING','PRESIDENT',null,'90/6/9',5000,0,10);
insert into emp values (7844,'TURNER','SALESMAN',7698,'95/6/4',1500,0,30);
insert into emp values (7876,'ADAMS','CLERK',7788,'99/6/4',1100,null,20);
insert into emp values (7900,'JAMES','CLERK',7698,'00/6/23',950,null,30);
insert into emp values (7934,'MILLER','CLERK',7782,'00/1/21',1300,null,10);
insert into emp values (7902,'FORD','ANALYST',7566,'97/12/5',3000,null,20);
insert into emp values (7654,'MARTIN','SALESMAN',7698,'98/12/5',1250,1400,30);
insert into salgrade values (1,700,1200);
insert into salgrade values (2,1201,1400);
insert into salgrade values (3,1401,2000);
insert into salgrade values (4,2001,3000);
insert into salgrade values (5,3001,99999);


```

### SQL Test

**1. **emp 테이블에서 sal이 가장 높은 상위 5명을 순서대로 출력하기

```sql
SELECT	*, rank() over (ORDER BY sal DESC) AS rownum
FROM 	 emp
ORDER BY sal desc
LIMIT 5
```

**2. **emp 테이블에서 각 row의 SAL이 높은 순서대로 순위를 부여 했을 때 6등~10등인 사람을 순위대로 아래 예제처럼 출력하세요.

```sql
SELECT	*, row_number() over (ORDER BY sal DESC) AS rownum
FROM 	 emp
ORDER BY sal desc
LIMIT 5 OFFSET 5
```

**8. **emp 테이블에서 SAL값을 누계(SAL_CUMULATIVE) 값으로 EMPNO을 오름차순 정렬하여 출력하기

```sql
SELECT	empno, ename, sal, MAX(sal) AS SAL_CUMULATIVE
FROM 		emp
GROUP BY empno
ORDER BY empno
```

**9. ** 사원 테이블에서 job이 ‘SALESMAN’ 인 row 중 SAL이 낮은 순서대로 순위(RANK)를 출력하기

```sql
SELECT	job, empno, ename, sal, ROW_NUMBER() OVER (ORDER BY sal) AS rank
from		emp
WHERE		job = 'SALESMAN'
GROUP BY empno
ORDER BY rank
```

**10. ** 사원 테이블에서 직업이 ‘SALESMAN’ 사원 중에 급여(SAL) 낮은 순서대로 순위(RANK)를 출력하기




**11. ** 사원 테이블에서 직업이 ‘SALESMAN’ 사원 중에 급여(SAL) 낮은 순서대로 순위(RANK)를 출력하기



**12. ** EMP테이블을 백업 하기 위하여(복제하기 위하여) 한 sql문장으로 데이터를 EMP_BAK TABLE을 생성하여 넣는 문장을 작성하시오


```sql
CREATE TABLE EMP_BAK SELECT * FROM emp
```

**13. ** 사원(EMP이름)테이블에서 직업(JOB)이 ‘SALESMAN’ 인 사원 급여(SAL)에 400 더하는 수정(UPDATE) 구문을 구하세요.





