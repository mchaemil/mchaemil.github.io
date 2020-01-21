---
layout: article
title: JAVA | JAVA의 함수형 프로그래밍..!  
tags: JAVA
comments: true

---


## **Today What I Learend**  

함수형 프로그래밍의 특징은 실행흐름을 한 방향으로 흐르게 한다는 점이다! 아직은 이 말이 크게 와닿지 않지만..! 리액트를 학습할 때를 떠올려보면 화살표 함수를 사용했을 때 실행흐름을 쭉 이어나갈 수 있었던 코드가 있었던! 기억이 난다.

현대 프로그래밍 기법은 객체지향과 함수형을 짝꿍으로 사용하는데 이러한 설명이 더 와닿도록 코드를 통해 다양한 경험을 할 수 있기를..! 

> CPU와 VGA의 성능향상으로 인해 함수형 프로그래밍의 패러다임이 열리는 시대가 왔다.


---
**Today I Learend**

- 함수형 프로그래밍에 대한 이해
- 람다식
- 제네릭(Generics) 


---




### 함수형 프로그래밍(functional programming)

- y = f(x) 형태의 함수로 구성된 프로그래밍 기법
- 데이터를 파라미터로 전달하고, 결과를 받는 코드로 구성
- 객체지향 프로그래밍보다 효율적인 경우
    - 대용량 데이터 처리에 유리하다. 
        - 1) 데이터를 포장해서 객체를 생성하는 것보다 데이터를 바로 처리하는 것이 속도에 유리하다. 
        - 2) 멀티코어 CPU에서 데이터를 병렬처리하고, 취합할 때 객체보다는 함수가 유리하다. 
    - 이벤트 지향 프로그래밍
        - 반복적인 이벤트 처리는 핸들러 객체보다는 핸들러 함수가 적합함
    - 현대 프로그래밍 기법
        - 객체지향 프로그래밍 + 함수형 프로그래밍



### Java8에서 함수형 프로그래밍 지원
- 람다식(Lamda Expressions)을 언어차원에서 제공
    - 람다 계산법에서 사용된 식을 프로그래밍 언어에 접목
    - 익명함수()를 생성하기 위한 식
    - (타입 매개변수) -> {실행문;}
- 자바에서 람다식을 수용한 이유
    - 코드가 매우 간결하다.
    - 컬렉션 요소를 필터링 또는 매핑해서 쉽게 집계할 수 있다.


- 하둡이 병렬처리로 쪼개서..! 구성한다. 
- 하둡같은 아키텍쳐..! CPU의 성능향상, 그래픽 카드의 성능 향상 이 세 가지가 맞물리면서 인공지능의 성능이 크게 향상했다. 


### 람다식(Lambda Expressions)

람다식은 익명 함수를 생성하기 위한 식으로 함수형 언어이다. 람다식은 `y = f(x)` 형태의 프로그래밍 기법이다. JAVA에서는 람다식을 통해서 다양한 장점을 얻을 수 있게 되었다. 

- Java는 람다식을 함수적 인터페이스의 익명 구현 객체로 취급
- 함수적 인터페이스: 한 개의 메소드를 가지고 있는 인터페이스를 말한다. 
- 람다식 -> 파라미터를 가진 코드 블록 -> 익명객체 구현

```java
Runnable runnable = () => {}

Runnable runnable = new Runnable() {
  public void run() {
		System.out.println("마방진을 만들 수 없는 숫자입니다.");
    }
}
```

#### 람다식 기본문법

- 함수적 스타일의 람다식을 작성하는 방법
    - (타입 + 파라미터 변수) -> {실행문;}

```java
(int a) -> {System.out.println(a);}

Runnable runnable = new Runnable(){
    public void run(int a){
    System.out.println(a);
    }
}
```

- 파라미터 타입은 런타임시에 대입값에 따라 자동으로 인식하므로 생략 가능

```
(a) -> {System.out.println(a);}
```
- 하나의 파라미터만 있다면 괄호() 생략가능
a -> {System.out.println(a);}

- 하나의 실행문만 있다면 중괄호({}) 생략 가능
a -> System.out.println(a);

- 파라미터 변수가 없으면 괄호()를 생략할 수 없음
() -> {System.out.println();}

- 리턴값이 있는 경우, return 문을 사용



#### 함수형 인터페이스..!

추상 메소드는 바디가 하나만 존재하는 메소드!


```java
public interface MyFuncInterface {
  public void print();
}

MyFuncInterface mfi = () -> {...;}
mfi.print();
```



이클립스에서 우클릭 `refactor` -> `rename` 


- 한 개의 추상메소드를 가지는 인터페이스는 모두 람다식 사용이 가능하다. 


### 제네릭(Generics)

-1) 전용타입

```java
ArrayList list = new ArrayList(); 
list.add(Object o);
Object o = list.get(i); 
String card = ((Card)list.get(i)).getCard();

ArrayList<Card> list = new ArrayList<Card>();
// ArrayList<Card> list = new ArrayList<>();
list.add(Card o);
String card2 = list.get(i).getCard();
```

소쿠리에 들어가야 하는 타입이 무슨 타입인지 모르니
오브젝트로 해놓다가 나중에 캐시팅할 때 복잡할 수도 있으니
타입만 지정해놓고..!! 
맞는 타입만..! 



2) 타입을 파라미터화 해서 컴파일시 구체적인 타입이 결정되도록 하는 방법 
java5부터 새로 추가된 내용
컬렉션, 람다식(함수형 인터페이스), 스트림, NIO에서 널리 사용됨.


3) 제네릭을 사용해서 얻는 이점
- 미리 타입을 지정해서 casting을 하지 않고 사용할 수 있다.
- 컴파일시 강한 타입체크를 할 수 있다.
- 실행시 타입 에러가 나는 것보다 컴파일시에 미리 타입을 체크해서 에러를 사전에 방지한다.


78. 지네릭 타입(Generic Type)
- 타입을 파라미터로 가지는 클래스와 인터페이스로 말한다.
    - 선언시 클래스 또는 인터페이스 이름 뒤에 "<>" 기호가 붙는다.
    - "<>" 사이에는 타입 파라미터가 위치한다.

- 타입 파라미터
    - 일반적으로 대문자 알파벳 한문자로 표현한다.
    - 개발 코드에서는 타입 파라미터 자리에 구체적인 타입을 지정해야 한다.

- 제네릭 타입을 사용할 때

```java
public void class Box {
    private Object object;
    public void set(Object object) {
        this.object = object;
    }
    public get(){
        return object;
    }

}



Box box = new Box();
box.set("hi");
String str = (String) box.get();
```







- 제네릭 타입을 사용하지 않을 때





- 없었다.
- 바

코드가 없았다. 
코드리뷰 하시네 

사람들을 끌고갈 마음의 준비..!

자료에 대한 신뢰성..!
자료에 대해 신뢰성..!

발표자료는 물흐르듯이 잘 흘러가느냐
기승전결을 만들 수 있느냐..!

디테일한 건 사람마다 다르다..! 
개인적으로 여쭈어..!

제네럴한.. 

어..! 는 나인가.

중요한 스킬이 참 많구나...

- 제네릭 타입을 사용할 때 

```java
public class Box<T>{
    private T t; 
    public T get(){
        return t;
    } 
    public void set(T t){
        this.t = t;
    }
}

Box<String> box = new Box<String>(); 
public class Box<String>{
    private String t;
    public void set(String t){
        this.t = t;
    }
    public String get(){
        return t;
    }
}

Box<String> box = new Box<String>(); 
box.set("hi~");
String str = box.get();
```


