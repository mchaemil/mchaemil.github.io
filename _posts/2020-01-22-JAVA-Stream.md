---
layout: article
title: JAVA | JAVA의 스트림 정리..!  
tags: JAVA
comments: true

---


## **Today What I Learend**  

스트림에 대한 간단한 이해를 얻는 시간을 가졌다!

---
**Today I Learend**

- 두 개 이상의 파라미터를 선언!
- 제네릭 메소드
- 와일드 카드
- 와일드 카드의 세 가지 타입
- 스트림
- 스트림 파이프라인
- 필터링

---


### 자바는 두 개 이상의 타입 파라미터를 선언할 수도 있다.

```java
class A<K,V, ...> {}
interface IB<K,V,...> {}
```

```java
public class Product<T, M> {
	private T kind;
	private M model;

	public T getKind() {return this.kind;}
	public M getModel() {return this.model;}

	public void setKind(T kind) {
		this.kind = kind
	}
	public void setModel(M model) {
		this.model = model
	}
}


Product<Tv, String> product = new Product<Tv, String>();
Product<Tv, String> product = new Product<>();
```


#### 제네릭 메소드 
- 파라미터 변수 타입과 리턴 타입으로 타입 파라미터를 갖는 메소드를 말한다.
- 제네릭 메소드 선언방법
    - 리턴 타입 앞에 `<>`기호를 추가하고 타입 파라미터를 기술한다.
    - 타입 파라미터를 리턴타입과 파라미터 변수에 사용한다.
    - public <타입 파라미터, ...> 리턴타입 메소드명(파라미터 변수, ...){}
    - public <T> Box<T> boxing(T t) {...}

- 제네릭 메소드를 호출하는 두 가지 방법
    - 리턴타입 변수 = <구체적 타입> 메소드명(파라미터 값) // 명시적으로 궻적인 타입을 지정
    - 리턴타입 변수 = 메소드명(파라미터 값); // 파라미터 값을 보고 구체적 타입을 추정

    - Box<Integer> box = <Integer>boxing(100); // 타입파라미터를 명시적으로 Integer로 지정
    - Box<Integer> box = boxing(100); // 타입파라미터를 Integer로 추정
    

```java
public class Box<T> {
	
	private T t;
	public T get() {
		return t;
	}
	
	public void set(T t) {
		this.t = t;
	}

}

public class Util {
    public static <T> Box<T> boxing(T t) {
        Box<T> box = new Box<T>();
        box.set(t);
        return box;
    }
}


```


### 타입 파라미터에 지정되는 구체적인 타입을 제한할 필요가 있을 경우
- 상속 및 구현 관계를 이용해서 타입을 제한할 수 있다. 

```java
public <T extends 상위타입> 리턴타입 메소드명(파라미터 변수, ...){}
```

- 상위타입은 클래스뿐만 아니라 인터페이스도 가능하다.
- 인터페이스라고 해서 implements를 사용하지 않고, extends로 사용한다.
- 타입 파라미터를 대체할 구체적인 타입
    - 상위타입이거나 하위 또는 구현 클래스만 지정할 수 있다. 

- 주의할 사항
	- 메소드의 중괄{} 안에서 타입 파라미터 변수로 사용가능한 것은 상위 타입의 멤버(필드, 메소드)로 제한된다. 
    - 하위타입에만 있는 필드와 메소드는 사용할 수 없다. 

```java
public <T extends Number> int compare(T t1, T t2) {
    double v1 = t1.doubleValue();
    double v2 = t2.doubleValue();
    return Double.compare(v1, v2);
    // Double.compare라는 게 이미 구현되어 있다.
    // 상속을 통해서 제한을 둘 수 있다. 
    // 문자는 들어오면 안될때 타입을 지정할 수 있다.
    // 타입과 타입의 계층구조로, 즉 Number의 계층으로 이루어진 것만 사용할 수 있다.
} 
```

```java
public <T extends P> int compare(){...}
```

### 와일드 카드 타입
- 제네릭 타입을 파라미터 변수나 리턴타입으로 사용할 때 파라미터를 제한할 목적으로 사용
- <T extends 상위타입 or 인터페이스>는 제네릭 타입과 제네릭 메소드를 선언할 때 제한을 한다. 
- public static void registerCourse(Course<?> course){}
- public static void registerCourseStudent(Course<? extends Student> course){}
- public static void registerCourseWorker(Course<? super Worker> course){}

> `<?>`를 사용한 코스는 아무타입이나 다올 수 있다.
나의 것을 기준으로 위의 것을 쓸 거냐 아래것을 쓸거냐를 정할 수 있다.

### 와일드 카드(?)의 세 가지 타입 
- 제네릭 타입<?> : Unbounded Wildcards(제한 없음)
    - 타입 파라미터를 대치하는 구체적인 타입으로 모든 클래스나 인터페이스 타입이 올 수 있다. 
- 제네릭 타입<? extends 상위타입> : Upper Bounded Wildcards(상위 클래스 제한)
    - 타입 파라미터를 대치하는 구체적인 타입으로 상위타입(현재)이나 하위타입만 올 수 있다. 
    - 상위타입 = B > C,D,E
- 제네릭 타입<? super 하위타입> : Lower Bounded Wildcards(하위 클래스 제한)
    - 타입 파라미터를 대치하는 구체적인 타입으로 하위 타입이나 상위 타입이 올 수 있다. 
    - 하위타입 = B > B, A


```
    A
    |
    B
    |
---------
|       |
C       E
|
D
```

### 스트림(stream)

- 스트림은 반복자다.
- 컬렉션(배열 포함)의 요소를 하나씩 참조해서 람다식을 처리할 수 있는 반복자다. 

#### Java7에서의 스트림

```
List <String> list = Array.asList("", "", "");
Iterator<String> iterator = list.iterator();
while(iterator.hasNext()) {
    String name = iterator.next();
    System.out.println(name);
}
```

#### Java8에서의 스트림

```
List<String> list = Array.asList("이민지", "이득규","고은경");
Stream<String> stream = list.stream();
stream.forEach(name -> System.out.println(name))
```

#### 파라미터가 한 방향으로 흐르고 나서 끝나고 나면 클리어가 된다. 


#### 스트림의 특징
- 람다식으로 요소 처리 코드를 제공한다.
    - 스트림이 제공하는 대부분의 요소처리 메소드는 함수형 인터페이스의 파라미터 타입을 가진다. 
    - 파라미터 값으로 람다식 또는 메소드 참조를 대입할 수 있다. 

```java
public class StreamTestMain {
	public static void main(String[] args) {
		List<Student> list = Array.asList(
				new Student("수지", 10),
				new Student("설현", 20)
		);

		Stream<Student> stream = list.stream();
		stream.forEach(s -> {
				String name = s.getName();
				int score = s.getScore();
				System.out.println(name + "_"+score)
		})
	}
}
```

#### 스트림을 쓰면 내부 반복자를 사용하게 되어 병렬처리가 쉬워진다. 
- 외부 반복자: 개발자가 코드로 직접 컬렉션 요소를 반복해서 요청하고 가져오는 코드 패턴
- 내부 반복지: 컬렉션 내부에서 요소들을 반복시키고 개발자는 요소당 처리해야 할 코드만 제공하는 패턴 
- 내부 반복자의 이점: 개발자는 요소 처리 코드에만 집중하게 한다.
- 멀티코어 CPU를 최대한 활용하기 위해 요소들을 분배시켜 병렬처리 작업을 할 수 있다. 
- **병렬처리(parallel)**
	- 한 가지 작업을 서브 작업으로 나누고, 서브 작업들을 분리된 스레드에서 병렬적으로 처리한 후, 서브 작업들의 결과들을 최종 결합하는 방법
	- 자바는 ForkJoinPool이라는 프레임 워크를 이용해서 병렬처리를 한다(JAVA API)


### 스트림 파이프라인(스트림은 데이터 통로)
- 중간처리와 최종처리
- 리덕션(Reduction)
    - 대량의 데이터를 가공해서 축소하는 것을 말한다.
    - 요소가 리덕션의 결과물로 바로 집계할 수 없을 경우 중간처리가 필요하다. 
    - 중간처리한 요소를 최종처리해서 리뎍션 결과물을 산출한다.
- 스트림은 중간 처리와 최종 처리를 파이프라인으로 해결한다.
    - 파이프라인: 스트림을 파이프처럼 이어놓은 것을 말한다.
        - 중간 처리 메소드(필터링, 매핑, 정렬)는 중간 처리된 스트림을 리턴하고
        - 이 스트림에서 다시 중간 처리 메소드를 호출해서 파이프 라인을 형성하게 된다.
        - 스트림소스(컬렉션, 배열, 파일) -> 오리지널(중간) -> 필터로 처리(중간) -> 매핑처리 -> 집계처리(최종)


- 중간처리 메소드와 최종처리 메소드로 분류할 수 있다. 
    - 중간처리 메소드: 필터링, 매핑, 정렬
    - 최종처리 메소드: 합계, 평균, 최소값, 최대값
    - 중간처리 메소드인지 최종처리 메소드인지는 구별을 해야 한다.
    - 둘의 구분은 리턴을 보면 구분할 수 있다.
        - 중간처리 메소드 - 리턴타입이 스트림
        - 최종처리 메소드 - 리턴타입이 기본타입이거나 OptionalXXX


### 필터링 
- 중간처리 기능으로 요소를 걸러내는 역할을 한다.
- distinct()
    - Stream: equals() 메소드가 true로 나오면 동일한 객체로 판단하고 중복을 제거
    - IntStream, LongStream, DoubleStream: 동일값일 경우 중복을 제거
- filter()
    - 파라미터 값으로 주어진 Predicate(비교했는데 값이 맞으면 필더링하는 것)가 true를 리턴하는 요소만!! 필터링!







