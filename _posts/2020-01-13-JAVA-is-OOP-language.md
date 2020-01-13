---
layout: article
title: JAVA | JAVA is OOP 
tags: JAVA
comments: true

---

## **Today What I Learend**  

자바가 가지는 객체지향프로그래밍 언어이므로 이해해야 하는 규칙들이 있는데, 이에 대해 이해해보는 시간을 가졌다. 
이를 학습하면서 자바에 대해 더 가까워지는 시간을 갖자!


---
**Today I Learend**

- Pass by Value VS Pass by Reference
- Parameter/Arguement 를 작성하는 규칙
- access modifier
- OOP의 3대 특징


---

### Pass by Value VS Pass by Reference
기본타입은 value을 주고 value를 받고, 참조타입은 reference를 주고 reference를 받는다.

#### Pass by Value
- pass by value 
- assign by value
- immutable 

```java
int a = 10; 
int b = a;  // a-> b
c = a+20;
System.out.println(a); // 10, a의 값이 변하지 않는다.
					   // a값이 변하려면 재할당을 해야한다.
```

#### Pass by Reference
- pass by reference 
- assign by reference 
- mutable

```java
int[] c = {1,2,3,4,5};
int[] d = new int[5];
d = c;
c[2] = 100;
System.out.println(d[2]); // 100
```

	
	

### Parameter/Arguement 를 작성하는 규칙
class의 public setter 메소드 인자로 전달받을 값을 `DataType Var`(타입 변수명)형태로 지정한다. 

```java
p.setName(String name);

People p = new People();
p.setName("ham")
```



### 접근제한자(access modifier)

private   - : 같은 클래스 내에서만 접근 가능
(default)   : 같은 패키지 내에서만 접근 가능
protected # : 상속 O public, 상속 X default
public    + : 모든 곳에서 접근이 가능



```java
package com.medici.testa;
public class A {
  private int money=10;  
  public void sendMoney() {
    System.out.println("돈을 보냅니다.");
  }

}
```

같은 패키지가 아니므로 default는 접근이 허락 안됨!!

```java
package com.medici.testb;
public class B {
  int money2 = 20;
  void getMoney() {
    System.out.println("돈을 받습니다.");
  }
}
```

### OOP의 3대 특징
- 은닉성(encapsulation)
	- member field private, member method private
- 상속성(inheritance)
	- 부모에 있는 member를 물려 받는 것
	- extends 를 통해 상속을 받게 되는데, 부모와 is의 관계이다. 
- 다형성(polymorphism)
	- 다양한 형태를 나타내는 성질
  	- 부모에 있는 메소드가 자식에 형태에 따라 다양하게 호출되는 것


#### 멤버필드에 값을 선언하지 않으면
참조타입은 null로 초기화가 되고,
기본타입은 기본타입의 기본값으로 초기화가 된다.

```java
class A {
  int sum;
  // sum = 0; // member field, 전역변수 같은 개념으로 동작할 수도 있다..!
}
```

### 은닉성(Encapsulation)
: member field private, member method private

주민등록번호, 비밀번호는 직접 접근하면 안되므로 필드에 접근제한자로 private을 걸어놓는다. 그리고 public 메소드를 통해서 private 필드에 접근할 수 있도록 설정해준다. 이렇게 private 필드를 숨겨놓는 게 은닉성이다.

```java
class People {
  private int age;
  public void setAge(int age) {
    this.age = age;
  }
  public int getAge() {
    return age;
  }
}

public class Main {
  public static void main(String[] args) {
	People p = new People();
	p.age = 10; // private 에 접근할 수 없으므로 에러	
	// public method 를 통해서만 접근 가능
	System.out.println(p.getAge()); 
		
	}
}
```

### 상속성(Inheritance)
- 부모에 있는 member(field, method)를 물려 받는 것
- 상속이 되는 의미는 is 관계이다. 
  Student is People 이 ture인 관계이다. 
  (자식)     (부모)


```java
public class People {	
	private int age;
	private String name;
	public int getAge() {
		return age;
	}
	public void setAge(int age) {
		this.age = age;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
		// 바깥에서 가져오면 내거에 저장한다는 뜻
	}
}

```

```java
class Student extends People {
	private int sId;
	private String subject;
	public int getsId() {
		return sId;
	}
	public void setsId(int sId) {
		this.sId = sId;
	}
	public String getSubject() {
		return subject;
	}
	public void setSubject(String subject) {
		this.subject = subject;
	}
}

```

```java
public class Main {
	public static void main(String[] args) {
		// 부모의 멤버를 사용할 수 있음
		Student s = new Student();
		s.setName("이득규");
		s.getName();
		
		s.setsId(20010001);
		s.getsId();
	}
}



```

### 다형성(polymorphism)
- 다양한 형태를 나타내는 성질
- 부모에 있는 메소드가 자식에 형태에 따라 다양하게 호출되는 것






26. class(클래스)
- 속성(attribute)과 행위(method)가 들어있는 설계도
- 설계도, 붕어빵 틀
- 블루프린트(청사진) 
- .java


27. Object(.class)
  - instance, 오브젝트
  - 붕어빵
  - .class



### 메모리 4대 특징

1. 자식이 생성되면 부모가 생성된다.
2. 자식이 설계도에 올라가면 부모도 설계도에 올라간다.
3. 생성된 주소는 부모의 주소를 가리킨다. 
4. 설계도에 공개된 메소드만 사용이 가능하다. 





#### local variable(지역 변수)는 초기값을 설정해야 한다.

```java
public void localVar(){
 int a; 
 int b = 10;
 int c = b + a; // a는 오류가 발생한다.
				// a에 초기값을 지정해 줘야한다.
}
```


### String class(문자열 클래스)
- 문자열을 받을때 사용하는 참조타입 클래스
- 참조타입이지만 기본타입의 성질을 갖고 있는 클래스

#### Immutable
immutable: 값을 다시 할당하기 전까지는 값이 변하지 않는다.

```java
String s = new String("음동하"); // 참조타입
String s1 = "음동하"; // 기본타입
System.out.println(s==s1); // false
System.out.println(s.equals(s1)); // true
System.out.println(s.equalsIgnoreCase(s1)); // true

immutable, 다시 할당할 때 까지
String str = "배새연";   // int a = 10
str.repace("배","임");   // int c = a+20;
System.out.println(str); // System.out.println(a);
// 배새연, 할당을 하지 않으면 값이 변하지 않는다.

```

#### Concatenation
String타입을 만나는 순간 String 타입이 된다.
	   
```java
System.out.println(1+2+3+"유창용"); // 6유창용
System.out.println("유창용"+1+2);   // 유창용12
System.out.println("유창용"+1+(2+3)); // 유창용15    
System.out.println(1+"유창용"+2+3);   // 1유창용23
System.out.println((1+2)+3+"유창용"); // 6유창용
```



