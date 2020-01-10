---
layout: article
title: JAVA | JAVA 수업내용 정리 
tags: javascript
comments: true

---

## **Today What I Learend**  



자바는 강한 규칙을 가지고 있고, 프로그래머가 전해지는 책임이 크다.
대신 그만큼 강한 통제를 가지고 있는 것 같다.




---
**Today I Learend**

- JAVA
- 동작원리
- Attribute
- Method




---




### Java 

1. 수업형태: 번호, 
1. jdk: jdk8+(1.8), jdk13(option)
1. 자료:
1. 첫날: 환경 설정
1. IDE(Intergration Development Environment) - Eclipse, VSCode, 
    - https://www.eclipse.org/downloads/download.php?file=/oomph/epp/2019-12/R/eclipse-inst-win64.exe
1. download
    - openjdk: 무료,  
    https://jdk.java.net/java-se-ri/8  
    https://github.com/ojdkbuild/ojdkbuild  
    - oraclejdk: 무료, 특정 API를 사용하면 유로
1. 테마
    - http://www.eclipsecolorthemes.org/?view=theme&id=14105
1. 자바 동작원리
  - One Souce multiuse
  - 하나의 소스를 만들면 플랫폼에 상관없이 똑같은 결과를 얻을 수 있다. 
  - 플랫폼(Operating System, os)
  - 컨셉: 가전기기 통합 oak, 코드명으로 제작이 되었음
  - 플랫폼 독립적인 프로그래밍

  

1. 함수형 프로그래밍 지원[JDK8/jDK1.8]
  - 람다식
    - 필터링
    - 매핑
    - 집계
  - 변수 값이 변하지 않고 처리됨
  - 한 방향으로 진행된다. 
  - 대용량 데이터 처리를 하기 위해서
  - multi threading 을 사용할 수 있다. 
  - http://preview.hanbit.co.kr/1967/sample_ebook.pdf
1. jvm, jre, jdk
  - jdk: 자바개발할 때 필요한 API
  - jre: 자바 실행할 때 필요한 프로그램
  - jvm: 자바 가상 머신
  - jre를 설치하면 jvm은 자동으로 설치가 되고, java를 개발하고 싶으면 jdk를 설치하면 됨
1. 프로그래밍이란 
  - data + logic 
  - 사람이 컴퓨터에 명령을 내려서 동작하게 하는 것..
  - 언어선택할 때는 기준을 정해야 함..
    - 웹: Java, Javascript
    - 데이터분석: python, R
    - 게임: C, C++
1. OOP(Object Oriented Programming)
  - 객체 지향 프로그래밍
  - 객체
      - 행위와 속성을 갖는 모든 것
  - 컴포넌트 단위(객체)로 클래스를 만들어서 필요한 시점에 조합해서 사용할 수 있도록 하는 것
  - 각 클래스는 자신의 기능이나 역할을 하도록 구현되며 계층 구조를 구성함에 따라서 기능이 실행이 될 수도 있고 안 될 수도 있다. 
  - 구현된 클래스는 필요한 시점에 호출할 수 있다.
  - attribute (속성, member field)
  - method(행위, member method)
  - member : member field, member method 
1. 명명법, 프로그램을 구현하면서 지켜야 할 규칙. 
  - 파스칼
  - 카멜
  - 헝가리언
1. 패키지
  - 비슷한 클래스들의 묶음(모음)
    - www.sk.co.kr
    - kr.co.sk.sales
      - 영업파트 관련 코드들이 들어감
    - kr.co.sk.common
      - 공통으로 사용하는 코드들이 들어감
    - com.medici.java01
  - 파일 맨 상단에 작성을 한다. 
  - 패키지는 .밑으로 하나씩 폴더를 구성한다.
  

 ### 데이터 타입(type)
 **기본 타입(primitive)** : **값을 저장하는 타입**
 
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


- **참조타입(reference type)**: reference를 저장하는 타입
- 배열타입
- User define(개발자가 정의한 타입)
  - API Document 에 정의된 클래스
	  


### 변수
  - 데이터나 주소값을 저장하는 저장소
  - 기본타입은 값을 저장하고, 참조타입은 주소를 저장한다. 
  - 사용할 용도에 맞는 명칭을 정하면 그게 변수명이 된다. 

### main method
  - 순수 자바 애플리케이션을 실행할 때 제일 먼저 호출되는 메서드 
  - public static void main(String[] args) { }
  - 대소문자 구분을 하고, 반드시 위와 똑같이 쓰지 않으면 오류가 발생한다.
  - 만들어진 클래스를 실행하고 싶으면 위의 메소드에 객체를 생성해서 실행해야 한다. 


#### new 키워드
  - 객체를 생성할 때 사용하는 키워드
  - 객체를 생성하는 이유? 객체를 사용하기 위해서 
  - 객체를 생성하는 법
  - 참조변수는 그 자체가 값이 아니므로 어떤 식으로든 가공을 해야 한다.  
  - 예를 들면, cm.coffeeMake(); 처럼 만들어진 메소드를 호출해야 내가 작성한 메시지가 출력된다. 


#### method
  - 데이터를 가지고 어떤 로직을 만들어서 데이터를 출력하거나 넣을 때 사용
  - return O


```JAVA
int count() {
  int cup = 1000/100;
  return cup;
}
```

- return X
  - void 넣는 순간 리턴을 받지 않겠다고 답함..!  
  
```JAVA
void isSarangOk() {
  System.out.println(man > woman && money > 10 ? "짝짝짝! 사랑이 어루어졌어요..!": "ㅠㅠ 이별했음.. 그때 사랑 ㄸㅁㅇ");
}

```

참조타입은 그 자체로 무엇도 표현할 수 없으므로
. 연산자를 통해서 값에 접근해야 한다. 



#### Eclipse 단축명령

| 명령어 | 설명 | 
|---|---|
| `ctrl + n` | 파일생성하는 단축키 | 
| `ctrl + m` | 화면 확대 | 
| `ctrl + F11` | Run 입력 | 


```JAVA
public class helloworld {
	public static void main(String[] args) {
		System.out.println("밥 먹으러 갈 시간이다.");
	}
}
```

#### void
void 를 쓰지 않으면 값을 사용하고 끝낸다. 


#### 자바의 기술을 분석해보면 기술의 흐름이 보인다.
주요 기술들이 자바 안으로 계속해서 들어왔다. 