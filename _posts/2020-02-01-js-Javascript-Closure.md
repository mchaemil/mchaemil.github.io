---
layout: article
title: javascript | Javascript Closure
tags: javascript

---

## **Today What I Learend**  

Javascript를 이해하기 위해선 Closure를 꼭 이해해야 한다고 들었다.

클로저는 자바스크립트 문법이 아니라 테크닉이며 기법이다라는 이야기를 강의 때 들었는데, 아직까지 이 말을 온전히 이해하기에는 이해가 부족하다. 클로저를 학습하면서 계속 포스트를 추가하고, 이를 통해 익숙해지는 시간을 가져야겠다. 

> MDN과 Crockford의 글도 읽어보면서 익숙해지기!

---
**Today I Learend**



---

### Closure

클로저는 함수 내부에서 생성한 데이터와 그 유효범위로 인해 발생하는 특수한 현상/상태라고 할 수 있다.  


### Closure 정의

MDN에는 클로저를 아래처럼 정의하고 있다.

> A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment). In other words, a closure gives you access to an outer function’s scope from an inner function. In JavaScript, closures are created every time a function is created, at function creation time.


위의 내용을 풀이하면 
- 클로저는 함수와 그 함수가 선언되던 당시의 정보를 담은 lexical environment(사전적 환경, 어휘적 환경)의 구성으로 이루어져 있다.
- 클로저는 '함수'와 '그 함수가 선언되던 당시의 정보를 담은 사전적 환경'의 조합이다.
- 클로저는 선언 당시의 환경에 대한 정보를 담는 객체(구성 환경)이다
- 클로저는 함수와 구성환경의 조합이다. 
- 클로저는 스코프와 밀접한 관련이 있다. 스코프는 변수의 유효범위, 클로저는 그 유효범위로 인한 상태이다.

그래서! 핵심은 이 부분인 것 같다.

**클로저를 이해하려면 자바스크립트가 어떻게 변수의 유효범위를 지정하는지(Lexical scoping)를 먼저 이해해야 한다.**

### 코드로 살펴본 Closure

출처: [MDN - Closure](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Closures)  


```javascript
function init() {
  var name = "Mozilla"; // name은 init에 의해 생성된 지역 변수이다.
  function displayName() { // displayName() 은 내부 함수이며, 클로저다.
    alert(name); // 부모 함수에서 선언된 변수를 사용한다.
  }
  displayName();
}
init();
```






#### 참고자료

**[MDN - Closure](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Closures)**  
**[Douglas Crockford's JavaScript - Private Members in JavaScript](https://www.crockford.com/javascript/private.html)**




