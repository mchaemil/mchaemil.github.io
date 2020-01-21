---
layout: article
title: JAVA | JAVA 학습한 내용 정리 
tags: JAVA
comments: true

---

## **Today What I Learend**  



자바는 강한 규칙을 가지고 있어서 프로그래머가 짊어지는 책임이 크다. 대신 그만큼 프로그래머가 강한 통제를 가지고 있는 것 같다. 강한 통제를 가지고 있는데 이러한 지점이 가져다 주는 이점은 무엇일가 고민해본다..! 


#### 자바의 기술이 변화하는 흐름을 분석해보면 기술의 흐름이 보인다.
> 자바 안으로 주요한 기술들이 계속해서 들어왔다. 자바 1.8 부터 함수형 프로그래밍이 들어왔다. 이렇게 자바 안으로 들어온 기술들을 따라 들어가보는 것도 재밌는 일일 것 같다.


---
**Today I Learend**

- JAVA
- Java의 특징
- OOP
- Java 환경설정
- 변수
- 데이터타입
- main method
- new 키워드
- method


---


프로그래밍이란 data + logic 을 말한다. 사람이 컴퓨터에 명령을 내려서 동작하게 하는 것을 말한다.

### Java 



#### jvm, jre, jdk
- jdk: 자바개발할 때 필요한 API
- jre: 자바 실행할 때 필요한 프로그램
- jvm: 자바 가상 머신
- jre를 설치하면 jvm은 자동으로 설치가 되고, java를 개발하고 싶으면 jdk를 설치하면 됨


### Java의 특징

- Write once, run anywhere(One Souce multiuse)
- 하나의 소스를 만들면 플랫폼(Operating System, os) 상관없이 똑같은 결과를 얻을 수 있다, 플랫폼 독립적인 프로그래밍
- 객체지향 프로그래밍 언어로서 상속, 캡슐화, 다형성과 같은 특징이 있다. 
- 재사용과 유지보수의 용이성
- 가비지컬렉터가 자동으로 메모리를 관리해준다. 프로그래밍에만 집중할 수 있음.
- 네트워크 분산처리 지원
- 멀티쓰레드를 지원함
- 동적 로딩(dynamic loading)을 지원한다. 모든 클래스가 로딩되지 않고, 필요한 시점에만 클래스를 로딩하여 사용한다.



### Object Oriented Programming

현실 세계와 유사한 가상의 세계를 컴퓨터 세계 속에 표현하기 위해서 객체지향이론이 등장하였다. 프로그램의 규모가 커지고 절차적 언어로는 극복하기 어려우므로 객체지향언어를 이용한 개발 패러다임이 등장 

객체지향은 재사용성과 유지보수, 중복된 코드제거를 집중하는 관점에서 이해하면 쉽게 접근할 수 있다.  

- 객체: 행위와 속성을 갖는 모든 것
- 컴포넌트 단위(객체)로 클래스를 만들어서 필요한 시점에 조합해서 사용할 수 있도록 하는 것
- 각 클래스는 자신의 기능이나 역할을 하도록 구현되며 계층 구조를 구성함에 따라서 기능이 실행이 될 수도 있고 안 될 수도 있다. 
- 구현된 클래스는 필요한 시점에 호출할 수 있다.
- attribute (속성, member field)
- method(행위, member method)
- member : member field, member method 

#### Object 


### Java 환경설정

jdk: jdk8+(1.8)을 메인으로 사용, jdk13(option)  

#### JDK Download

| 종류 | 설명 | 링크 | 
|---|---|---|
| `openjdk` | 무료 | [openjdk link](https://github.com/ojdkbuild/ojdkbuild) |
| `oraclejdk` | 무료, 특정 API를 사용하면 유로 | [oraclejdk link](https://jdk.java.net/java-se-ri/8) |

1. `openjdk`링크에서 Micro soft install version 을 설치한다. 
	- java-1.8.0-openjdk-1.8.0.232-2.b09.ojdkbuild.windows.x86_64.msi (sha256)
1. 환경 변수가 설정된 것을 확인하기

#### 환경 변수 설정하는 또 다른 방법, JAVA_HOME

시스템 변수에 `JAVA_HOME` 을 만들어서 path에 연결하는 방법도 있다.

`C:\Program Files\ojdkbuild\java-1.8.0-openjdk-1.8.0.232-2` 을 시스템 변수 JAVA_HOME으로 설정

> JAVA_HOME을 시스템 변수로 설정하면 더 간편하게 버전을 바꿀 수 있다는데 아직은 잘..! 모르겠다.


```
C:\Program Files\ojdkbuild\java-1.8.0-openjdk-1.8.0.232-2\bin
C:\Program Files\ojdkbuild\java-1.8.0-openjdk-1.8.0.232-2\jre\bin
```

위의 주소를 아래처럼 변경

```
C:\Program Files\ojdkbuild\java-1.8.0-openjdk-1.8.0.232-2

%JAVA_HOME%\bin
%JAVA_HOME%\jre\bin
```

![주석 2020-01-13 190024](https://user-images.githubusercontent.com/40027211/72247069-773fea00-3637-11ea-8ea3-988590f33446.png)
![주석 2020-01-13 190324](https://user-images.githubusercontent.com/40027211/72247070-773fea00-3637-11ea-885f-002869309fe3.png)


#### IDE(Intergration Development Environment)

자바를 사용할 때 가장 많이 사용되는 IDE 
- **[이클립스 다운로드링크](https://www.eclipse.org/downloads/download.php?file=/oomph/epp/2019-12/R/eclipse-inst-win64.exe)**

이클립스 드라큘라 테마, 인텔리제이와 가장 비슷한 느낌을 준다고 함  
- **[이클립스 드라큘라 테마 링크](http://www.eclipsecolorthemes.org/?view=theme&id=14105)**

1. Eclipse를 다운로드 받고 실행 
1. 타입에서 -> `Eclipse IDE for Enterprise Java Developers` 를 선택
1. 나오는 체크박스들을 모두 선택


#### Eclipse 단축명령

| 명령어 | 설명 | 
|---|---|
| `ctrl + n` | 파일생성하는 단축키 | 
| `ctrl + m` | 화면 확대 | 
| `ctrl + F11` | Run 입력 | 
| `F3` | 마우스 오버를 하고 `F3` 누르면 원본 메서드로 넘어간다.  | 



#### 자바에서 프로그래밍 코드를 표기하는 약속(명명법)
- 프로그램을 구현하면서 지켜야 할 규칙이나, 오류가 발생하지는 않는다.
- 하지만 프로그래머들의 규약이라서 반드시 지키지 않으면 혼난다!
- 파스칼(pascal) : 처음에 시작할 때 대문자 그다음 소문자 의미 바뀌면 대문자 소문자
 ex) class CoffeeMachine 클래스, 인터페이스
- 카멜(camel) : 처음에 시작할 때 소문자 의미 바뀔때 첫글자 대문자 소문자
	- 메소드, 변수명

```java
public void makeCoffee(); //메소드, 변수명
```

- 헝가리언(hungarian) : 타입 축약 + 이름
	- 타입을 줄여서 이름과 붙여사용, GUI(Swing)
```java
txtName, lblNumber 
```

- 전체 대문자 : 상수, 변하지 않는 값을 지정할 때

```java
final String ROLE = "Manager";
Math.PI = 3.14 // PI는 상수
System.out.println(Math.PI); //3.14가 나온다.
```

- 전체 소문자 : 예약어, 키워드, 패키지

```java
public, new, void, class // 예약어
ham.study.java.play369 // 패키지 이름
```
  
  

#### 패키지
- 비슷한 클래스들의 묶음(모음)
- www.sk.co.kr
- kr.co.sk.sales
  - 영업파트 관련 코드들이 들어감
- kr.co.sk.common
  - 공통으로 사용하는 코드들이 들어감
- com.medici.java01
- 파일 맨 상단에 작성을 한다. 
- 패키지는 `.`밑으로 하나씩 폴더를 구성한다.
- 패키지는 클래스를 묶어주기 위해 사용한다.

### 변수

- 데이터나 주소값을 저장하는 메모리 공간
- 기본타입은 값을 저장하고, 참조타입은 주소를 저장한다. 
- 사용할 용도에 맞는 명칭을 정하면 그게 변수명이 된다. 

```java
int age;
age = 25;

```  

### 데이터 타입(type)
 
프로그래밍에서 사용하는 값은 문자와 숫자로 나눌 수 있으며, 숫자는 정수, 실수로 나눌 수 있다. 데이터 타입은 기본형과 참조형으로 구분된다. 


#### 기본 타입(primitive type) : 값을 저장하는 타입

`char` 는 내부적으로 정수(유니코드로)로 저장하므로 정수 또는 실수형과 연산이 가능하다. boolean은 다른 기본 자료형과 연산이 불가능하다. 또한 숫자는 가장 많이 사용되므로 타입을 4가지나 제공한다.  

| 명령어 | 설명 | 
|---|---|
| `byte` | 정수(1Byte) | 
| `short` | 정수(2Byte) | 
| `int` | 정수(4Byte) | 
| `long` | 정수(8Byte) |
| `float` | 실수(4Byte) |
| `double` | 실수(8Byte) |
| `boolean` | 논리값(1Byte) |
| `char` | 캐릭터(2Byte) |
| `enum` | 열거형 |


#### 참조타입(reference type): reference를 저장하는 타입

참조타입은 어떤 값이 저장되어 있는 주소를 값으로 가짐. 연산자 new를 통해서 객체의 주소가 만들어진다.

- 배열타입
- User define(개발자가 정의한 타입)
- API Document 에 정의된 클래스
	  

### main method
- 순수 자바 애플리케이션을 실행할 때 제일 먼저 호출되는 메서드 
- 만들어진 클래스를 실행하고 싶으면 main 메소드에 객체를 생성해서 실행해야 한다. `java.exe`에 의해 호출될 수 있도록 미리 약속된 부분이므로 항상 똑같이 적어야 한다. 
- 대소문자 구분을 하고, 반드시 아래와 똑같이 쓰지 않으면 오류가 발생한다.


```java
public class helloworld {
	public static void main(String[] args) {
	// 시행될 문장을 적는다.			
	System.out.println("밥 먹으러 갈 시간이다.");
	}
}
```


모든 클래스가 main 메서드를 가지고 있어야 하는 것은 아니지만 하나의 JAVA 애플리케이션에는 main 메서드를 포함한 클래스가 꼭 한 개는 있어야 한다. 

소스파일의 이름은 `public class`의 이름과 일치해야 한다. `public class`가 없다면 어떠한 class 의 이름으로 해도 상관 없다. 

### new 키워드
 
**new는 클래스로부터 객체를 생성할 때 사용하는 키워드이다.**
- 객체를 생성하는 이유? 객체를 사용하기 위해서 

`new`연산자 뒤에는 생성자(객체 생성시 초기화)가 오는데, 생성자는 `클래스의 이름`과 `()` 호출 연산자의 형태로 되어 있다. 물건이 어디 있는지 모르면 필요할 때 사용할 수 없는 것처럼 객체를 사용하기 위해서는 생성한 객체의 주소를 누군가가 알려주어야 하는데, `new`연산자는 힙(Heap) 영역에 객체를 생성시킨 후, 주소를 리턴하도록 되어 있다.  
이렇게 리턴 받은 주소를 참조 타입인 클래스 변수에 저장해두면, 변수를 통해 객체를 사용할 수 있다.

> 생성자를 호출해서 객체를 생성시킨다. 클래스에 오버로딩된 생성자가 한 개라도 있다면, `컴파일러`는 `Default 생성자`를 추가하지 않음! 생성자 오버로딩(명시적 생성자)을 하는 이유는 객체를 다양하게 초기화하기 위해서이다. 

```java
People p;
p = new People();

// 객체를 생성하는 코드를 한 줄로 작성
People p2 = new People();
``` 

```java
```

#### 객체를 사용하는 방법
- 참조변수는 그 자체가 값이 아니므로 어떤 식으로든 가공을 해야 한다. 
- 멤버를 참조할 때는 멤버참조연산자(`.`)를 사용한다
- 예를 들면, `cm.coffeeMake();` 처럼 메소드를 호출해야 사용자가 정의한 메소드가 수행된다. 

```java
CoffeeMachine cm = new CoffeeMachine()
cm.coffeeMake()

```

참조타입은 그 자체로 무엇도 표현할 수 없으므로
`.` 연산자를 통해서 값에 접근해야 한다. 


### method
- method는 필드를 읽고 수정하기도 하지만 다른 객체를 생성해서 다양한 기능을 수행하는 역할도 한다.
- 메소드는 객체간의 **데이터를 전달하기 위한 수단**으로 사용된다. 외부로부터 매개값을 받을 수도 있고, 실행 후 어떤 값을 리턴할 수도 있다.
- 데이터를 가지고 어떤 로직을 만들어서 데이터를 출력하거나 넣을 때 사용


#### method return type

리모컨에서 파워버튼과 음량 조절 버튼이 있을 때, 파워버튼은 전원만 끄거나 켜면 되므로 따로 결과를 되돌려줄 필요가 없다. 반면 음량조절 버튼은 음량을 줄이거나 높였을 때 얼만큼 줄이고 높였는지, 그래서 현재 상태(값)은 어떠한지 결과를 되돌려줄 필요가 있다. 이를 메소드의 리턴 타입에 비추어본다면 파워버튼을 `void` 타입, 음량조절 버튼을 `return type`으로 생각해볼 수 있지 않을까

메소드 실행의 결과값을 호출한 곳으로 전달해야 하는 경우에는 리턴값이 필요하다. 이 때는 리턴값의 `type`이 와야하며, 메소드의 실행 이후 바로 종료되어 리턴값이 필요 없다면 `void`가 와야 한다. 

```
returnType methodName(parameter) {
	// Context
}
```

- return O
- add() 메소드는 리턴값이 있으므로 저장할 변수가 있어야 한다.
- 다만! 리턴값을 받을 필요가 없고, 메소드가 실행되는 것이 중요하다면 변수 선언이 필요하지 않을 수 있다.

```java
int add(int a, int b) {
  int result = a + b;
  return result;
}
```

```java
int sum = add(3, 5)
```

- return X, 반환하는 자료형이 없으면 void를 명시한다.
- void 넣는 순간 리턴값이 없다고 답하는 것이므로 변수에 저장할 내용이 없다.

```java
void isSarangOk() {
  System.out.println(man > woman && money > 10 ? "짝짝짝! 사랑이 어루어졌어요..!": "ㅠㅠ 이별했음.. 그때 사랑 ㄸㅁㅇ");
}

```





