---
layout: article
title: JAVA | JAVA 는 계층 구조를 가진 언어이다!  
tags: JAVA
comments: true

---

## **Today What I Learend**  

자바는 계층이 있는 언어이다..!
음...!  그래서 verbose 하며..! 큰 구조에 좋은 프로그래밍 언어인 것일까?


ps. **[Write in Go](https://www.youtube.com/watch?v=LJvEIjRBSDA)** 링크의 동영상에서는 JAVA is verbose, Python's too slow.. ㅋㅋㅋ 그러면서 Write in Go 를 외치는데 시사하는 점도 있고, 재미도 있는 것 같다. 이러한 작은 고민과 생각들이 모여서 프로그래밍에 대한 이해를 더욱 키울 수 있을 것 같다. 충분히 해볼 법한 고민..!

---
**Today I Learend**

- 다형성
- 추상클래스 


---



### JAVA를 이용해서 369 게임 만들기
#### 요구사항
3,6,9 게임을 만들어보는 데 3,6,9가 들어간 숫자에서는 갯수만큼 
*를 출력하는 프로그램을 작성해보기
1~100까지 출력하면서 369개수에 따라서 *를 찍어보기 

[결과화면]  
```
1  2   *  4  5  *  7  8  * 10
11 12  * 14 15  * 17 18  * 20
21 22  * 24 25  * 27 28  *  *
...
*  *  ** *   * **  *  * ** 100  
```

1~100을 출력한다
10으로 나누어서 떨어지면 한 줄 개행한다.
숫자사이의 간격을 띄어주기 위해 \t을 추가한다. 
12 

```
String s = "12";
char c = s.charAt(0); // 1
char d = s.charAt(1); // 2
```


### 깔끔하게 가져오려면..!

jar로 만든다음에 import해서 가져온다. 
`App Client JAR file`
로 만든다..! 


### 다형성 발생원리 3가지

- 부모의 이름으로 자식을 생성할 수 있다.

```java
P p = new S();
```

- 부모의 이름으로 자식을 받을 수 있다. 

```java
P p1 = new P();
S s = new S();
P p1 = s
```

- 부모의 메소드로 자식의 메소드를 호출할 수 있다. (단, 상속과 오버라이딩이 되어있을 경우 가능하다.)
- 들고는 있지만 설계도가 없었다. 그래서 설계도에 올리면 쓸 수 있
다.

```java

Student s = new Student();
People p2 = s2;
Student s3 = (Student)p2;

```

(참고)
다형성
- 다양한 형태를 나타내는 성질
- 부모의 메소드가 자식의 형태에 따라 다양하게 호출되는 것

```java
public class Car {
  Tire t1 = new HamTire();
  Tire t2 = new FriendTire();
}

```

### 추상클래스 
- 용도: 공통적인 것을 구현하고, 상속받은 곳에서 다시 구현해야 하는 메소드는 추상 메소드로 선언할 때 사용한다. 

#### 추상 클래스를 만드는 이유는 무엇일까?

클래스들의 공통적인 field, method를 뽑아내 추상클래스를 만드는 이유는   
1. 동일한 데이터를 다루며 기능이 같더라도 이름이 다름으로 인해 발생하는 오차, 즉 객체마다 사용방법이 달라질 수 있는 문제를 해결하기 위해 사용한다.
1. 공통적인 field, method를 뽑아내면 클래스를 작성할 때 시간을 아낄 수 있다.

#### 추상 클래스 선언

```java
public abstract class MakeCoffee {
  // field
  // constructor
  // method
}
```


#### 추상 클래스의 특징
- 연관이 있는 클래스들끼리의 상속관계 
- 추상 메소드가 1개 이상 있는 클래스
- 추상 메소드는 body({}) 가 없는 메소드를 추상 메소드라고 한다 
- 추상메소드도 메소드 앞에 abstract 라는 키워드를 붙인다. 

```java
public abstract void make();
```

- 추상 클래스의 상속 키워드도 extends 이다. 
- 상속을 강요한다. 상속을 강요한다는 것은 반드시 구현해야 한다는 뜻!!!


- 추상 클래스에서 선언된 추상 메소드는 상속된 클래스에서 반드시 구현되어야 한다. 그렇지 않으면 오류가 발생한다. 오류가 발생되지 않게 하려면 상속받은 클래스도 추상 클래스로 만들어야 한다. 
- 추상 클래스는 추상클래스의 이름으로 생성할 수 없다.
- 추상 클래스는 new 연산자를 통해서 객체를 직접 생성하지 못한다. 



// 오버라이드를 위해서 접근제어자를 퍼블릭으로 준다.
// 공통적인 것은 위에서 구현을 하고..!
// COUNT 는 추상메소드로만 구현

다형성 부모의 이름으로 자식의 메소드를 호출할 수 있다. 


학생, 교수, 직원 등의 User로 추상 클래스를 만들고 여기서 분기를 하여 타입이ㅔ 맞는 User에 


### final 키워드 

```java
final int a = 10;
a = 5;
```
final 키워드로 선언된 변수의 값을 변경하려고 하면 발생하는 메시지

```
The final local variable a cannot be assigned. It must be blank and not using a compound assignment
```

#### class  : 상속 금지, 내 클래스가 마지막이야
```java
public final class Customer {

}
```

class에서 사용된 `final`키워드로 인해 `extends Customer` 를 할 수 없다. 상속 불가! 

```java
public class VeryImportantPerson extends Customer {

}
```

```java
public class Car {
  private int speed;
	public final int stop() {
		speed = 0;
		return speed;
	}
}
```


- method : 오버라이딩 금지, 내가 마지막 메소드니까 덮어 쓰지마가 된다. 


final 키워드는 위의 3가지 경우에서 사용할 수 있다

한 번에 만들지 않고
요구조건에 따라서 프로그램을 하나씩 만들어 간다...!
요구조건을 맞춰서 하나씩..!




### 계층


| AbstractMagicSquare | 
|---|
| +magic:int |
| +top:int | 
| `---------` | 
| +init(n:int):void |
| +make():void | 
| +print():void | 
| +print():void | 
| +isCheck():boolean |


| OddMagicSquare | 
|---|
| +make():void | 


| FourMagicSquare | 
|---|
| +make():void | 
| +makeRight():void | 
| +makeLeft():void | 



### 0117 JAVA REVIEW


팀별로 오늘의 규칙을 조사해서 정리해서 간단하게 텍스트로 발표하기
조사되는 상태까지 해보고 마무리한다. 



63. JCF(Java Collection Framework)

- 자료구조
- 데이터를 구조적으로 정리하는 방법



Collection
 
- 순서

| Set | List | Map | 
|---|---|---|
| 순서X | 순서O | 순서X, key,value가 쌍으로 존재 | 
| 중복X | 중복O | key 중복X | 
| iter pattern | index | key*value | 


HasSet    ArrayList     HashMap
XXXSet    LinkedList    XxxMap
          Vector




### CardGame

Card 게임 만들기
num: A, 2,3,4,5,6,7,8,9,T,J,Q,K


```
[S4][C5][SA][CJ][T6][CJ][CK][H5][H9][H9]
[C5][C7][H7][TJ][S4][CT][T5][H4][CQ][C9]
[H5][H3][H7][C6][H4][H5][SJ][C2][HQ][HJ]
[T2][C7][T2][H4][H3][CJ][T3][S9][C8][C2]
[S2][C9][SQ][S8][C4][H6][T5][C7][HK][TT]
[S5][ST]
```


음..! 
요구사항을 찾아라..!



64. Vector/ ArrayList

- Vector는 동기화되어있는 list 자료구조 
- ArrayList 는 비동기화 되어있는 list 자료구조

동기화는 Vector 라는 그릇에 데이터를 저장할 때 다른 사람이 접근 못하게 막고 데이터를 처리하는 형태
비동기는 ArrayList 라는 그릇에 데이터를 저장할 때 다른 사람이 접근해서 데이터가 깨질 수도 있음. 동시에 여러 사람이 하나의 데이터에 접근할 수 있는 경우가 생기면 Vector를 사용하는 것이 더 좋음

65. 콘솔에서 입력받는 방법

```java
import java.util.Scanner;
Scanner scan = new Scanner(System.in);
int num = scan.nextInt();
```

## [팀별 미니 프로젝트]  
카드 게임 만들기 
1) ArrayList or 배열중에 어떤 클래스를 사용할 것인지 팀별로 정하고
2) 어떤 카드게임을 할지 게임을 해보면서 규칙을 찾아내기 
3) 오늘 찾아낸 규칙을 5시에 텍스트나 ppt로 발표할것
4) 만들어진 게임은 다음주 화요일 4시에 발표할것!!







