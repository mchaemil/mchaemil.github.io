# Vue.js

Vue.js는 가볍고 단순한 구조를 가지고 있어서 기존의 프로젝트에도 쉽게 적용할 수 있다. 또한 재사용이 가능한 컴포넌트 기반이므로 이를 이용하거나 ES6를 이용할 수도 있다. 그리고 routing, vuex를 사용해 한 곳에서 애플리케이션 전체에서 사용하는 데이터를 효과적으로 관리할 수도 있다. 

양방향 데이터 바인딩을 이용해 UI와 데이터 모델간의 reactivity 기능을 만들 수 있다는 장점이 있다.



## Table of Contents

1. [뷰 인스턴스](#뷰-인스턴스)
1. [컴포넌트를 사용한 작성방법](#컴포넌트를 사용한 작성방법)
1. [선언적 렌더링](#선언적-렌더링)
1. [조건문과 반복문](#조건문과-반복문)
1. [사용자 입력 핸들링](#사용자-입력-핸들링)
1. 
1. 
1. [Reference Docs](#Reference-Docs)

---

## Vue.js 시작을 위한 script

```html
<!-- 개발버전, 도움되는 콘솔 경고를 포함. -->
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>

<!-- 상용버전, 속도와 용량이 최적화됨. -->
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
```



## 뷰 인스턴스

1. new Vue() 생성자를 통해 뷰 인스턴스 생성
2. el 속성으로 뷰 인스턴스가 그려질 지점 지정!
3. data 속성에 key-value 형식의 데이터를 정의
4. `{{ }}`를 통해 화면에 뷰인스턴스의 데이터 속성 값과 연결 혹은 대체됨

```html
<div id="app">
  {{ message }} <!-- 4. 화면에 뷰인스턴스의 데이터를 연결 -->  
</div>
```

```javascript
new Vue({ // 1. new Vue() 생성자를 통해 뷰 인스턴스 생성
  el:'#app', // 2. el 속성으로 뷰 인스턴스가 그려질 지점 지정!
  data: {
    message: "Hello Vue.js!" // 3. data 속성에 key-value 형식의 데이터를 정의
  }
})
```

### 뷰 인스턴스 옵션 속성

#### el 속성

`el` 속성은 통해 뷰로 만든 화면이 그려지는 시작점을 의미하며, `el`속성에 의해 선택될 선택자는 `CSS 선택자 규칙`과 같다.

```html
<div class="selected-by-css">
  {{ message }}
</div>
```

```javascript
new Vue({
  el:'.selected-by-css'
})
```

**[⬆ back to top](#table-of-contents)**



## 컴포넌트를 사용한 작성방법

컴포넌트 시스템은 Vue의 중요한 개념인데, 조합하여 화면을 구성할 수 있는 블록을 의미한다. 컴포넌트는 작고 독립적이므로 재사용할 수 있기 때문에 대규모 애플리케이션을 구축할 수 있게 해준다.

컴포넌트를 통해 아래와 같은 이점을 얻을 수 있다.

1. 화면을 일괄적인 패턴으로 구조화하여 개발할 수 있음
2. 재사용이 편리함

Vue에서 컴포넌트는 **미리 정의된 옵션을 가진 Vue 인스턴스**이다. Vue에서 컴포넌트를 등록하는 방법은 간단하다.

```javascript
// todo-item 엘리먼트는 app안에 child으로  작성되어야 함
Vue.component('todo-item', {
  template: '<li>This is a todo</li>'
})

var app = new Vue({el:'#app', data: {...}})
```

```html
<div id="app">
  <ol>
    <todo-item></todo-item>
  </ol>
</div>
```

### HTML 사용자 정의 태그 스펙

HTML 사용자 정의 태그 스펙은 `케밥 케이스`와 `모두 소문자`를 강제하는데, 뷰에서는 이를 따르지 않아도 되지만 가급적 지키는 게 좋다.

### 컴포넌트의 유효 범위

전역 컴포넌트와 지역 컴포넌트는 유효 범위가 다르다.  

#### 전역 컴포넌트 

전역 컴포넌트는 한 번 등록하면 어느 인스턴스에서나 사용할 수 있으며, Vue 생성자에서 `component()`를 호출해야 한다. 

```javascript
Vue.component('global-component', {
  template: '<div>전역 컴포넌트임</div>'
})
```

#### 지역 컴포넌트 

지역 컴포넌트는 새 인스턴스를 생성할 때 마다 등록해야 하며, 유효 범위는 지역 컴포넌트가 등록된 인스턴스를 벗어날 수 없다. 사용하기 위해선 인스턴스의 속성으로 `components`를 추가하고 등록할 컴포넌트의 이름과 내용을 정의하면 된다.

```javascript
new Vue({
  components: {
    'local-component' : {
      template: '<div>지역 컴포넌트입니다.</div>'
    }
  }
})
```

**[⬆ back to top](#table-of-contents)**



## 선언적 렌더링

Vue.js는 간단한 템플릿 구문을 사용해 DOM에서 데이터를 선언적으로 렌더링(**Declarative Rendering**)할 수 있는 시스템이 있다.

### {{ }} - 콧수염 괄호

`{{}}`는 뷰 인스턴스의 데이터를 HTML 태그에 연결하는 가장 기본적인 텍스트 삽입 방식이다.  뷰 인스턴의 데이터를 HTML에서 표현하기 위해 사용한다. 

> double mustaches, mustache tag, 콧수염 괄호, 이중 중괄호

```html
<div id="app">
  {{ message }}
</div>
```

```javascript
var app = new Vue({
	el: '#app',
  data: {
    message: 'hello Vue! thx'
  }
})
```

위의 코드는  웹 페이지 상에서는 아래처럼 표현된다!

---

hello Vue! thx

---

`Vue 인스턴스`의 `data`속성이 바뀌면 뷰 반응성에 의해 자동으로 갱신되는데, 이를 막고 싶다면 아래의 코드처럼, div 태그의 속성으로 `v-once`를 사용한다. 

```html
<div id="app" v-once>
  {{ message }}
</div>
```

**[⬆ back to top](#table-of-contents)**









## 조건문과 반복문

### 조건문

`v-if`를 통해 엘리먼트의 표시여부를 제어할 수 있다. 브라우저의 console에 `app.seen = false`를 입력하면 엘리먼트의 표시를 숨길 수 있다. 

```html
<div id="app">
  <p v-if="seen">You can see me!</p>
</div>
```

```javascript
var app = new Vue({
  el: '#app',
  data: {
    seen: true,
  }
})
```

### 반복문

```html
<div id="app">
  <ul>
    <li v-for="todo in todos">{{ todo.text }}</li>
  </ul>
</div>
```

```javascript
var app = new Vue({
  el:'#app',
  data: {
    todos: [
      {text: "재미있는 Javascript!"},
      {text: "디자인을 만드는 CSS~"},
      {text: "구조를 만드는 HTML!"},
    ]
  }
})
```

**[⬆ back to top](#table-of-contents)**

## 사용자 입력 핸들링

사용자와 앱의 상호작용을 위해 `v-on`디렉티브를 사용하여 `Vue 인스턴스`에서 메소드를 호출하는 이벤트 리스너를 추가할 수 있다. 

이 방법은 DOM을 건드리지 않고, 앱의 상태만을 업데이트한다. **모든 DOM의 조작은 Vue에 의해 처리되며 작성한 코드는 기본 로직에만 초점을 맞춘다.** 

```html
<div id="app">
  <p>{{ message }}</p>
  <button v-on:click="reverseMessage">메시지 뒤집기</button>
</div>
```

```javascript
var app = Vue({
  el:'#app',
  data: {
    message: "hello Vue.js!"
  }, //end data
  methods: {
    reverseMessage: function() {
			this.message = this.message.split('').reverse().join('');
    }
  }
})
```

Vue는 입력과 앱의 상태를 양방향으로 바인딩하는 `v-model`디렉티브(directive)를 제공한다.

> Vue also provides the `v-model` directive that makes two-way binding between form input and app state a breeze:

**[⬆ back to top](#table-of-contents)**




## Reference Docs

- [Vue.js Tutorial](https://kr.vuejs.org/v2/guide/index.html)
- [OOD - 커플링이란 무엇이며, 어떻게 줄일 수 있을까?](https://vandbt.tistory.com/13)



## 라이프 사이클

created 에서 돔에서 접근하면 안 된다. 

화면이 만들어지지 않았는데, 뿌리려고 하면..! 문제가 생긴다..!

화면에 대한 접근이 되지 않기 때문에..! 

### created, mounted가 중요한 두 개!!

화면이 생성되었을 때, 

beforeUpdate 실제 업데이트가 변경되었을 때

### 라이프 싸이클은 



데이터를 해제해서 누수를 막기 위해서 쓰인다...



### components

  템플릿은 데이터를 표현하고 싶은게 아니라 

  태그를 만들고 싶은 것이다. 





## 뷰 컴포넌트 통신

컴포넌트는 각각 고유한 유효 범위를 가지므로 직접 다른 컴포넌트의 값을 참조할 수 없다. 따라서 Vue 프레임 워크가 정의한 컴포넌트 데이터 전달 방법을 따라야 한다. 

### 상위 - 하위 컴포넌트 관계

`상위 - 하위 컴포넌트`란 트리 구조에서 부모 노드, 자식 노드처럼 컴포넌트 간의 관계가 부모, 자식으로 이루어진 컴포넌트를 의미하는데, 상위에서 하위로는 `props`라는 특별한 속성을 전달한다. 

### props 

props 속성을 사용하려면, 먼저 아래처럼 **하위 컴포넌트**의 속성에 `props`를 정의해야 한다. 

```javascript
Vue.component('child-component', {
  props: ["props 속성이름"]
})
```

그리고 **상위 컴포넌트** HTML 태그의 자

```html
<child-component v-bind:props 속성이름="상위 컴포넌트의 data 속성"></child-component>
```

### props 속성을 사용한 데이터 전달 예제

```html
<div id="app">
  <child-component v-bind:propsdata="message"></child-component>
</div>
```

```javascript
Vue.component('child-component', {
  props:['propsdata'],
  template: '<div>부모 컴포넌트로 부터 전달받는 값은.. {{ propsdata }}</div>'
})

var app = new Vue({
  el:'#app',
  data: {
    message: "hello Vue nice to meet you! i am fine thx"
  }
})
```


### 커플링(Coupling)

어떤 모듈을 변경할 때 다른 모듈의 변경이 요구된다면 **커플링(Coupling)이 존재**한다

[OOD - 커플링이란 무엇이며, 어떻게 줄일 수 있을까?](https://vandbt.tistory.com/13)


### 테스트

```

  <div id="app">

    <div >

      <my-components1 v-bind:aa="value"></my-components1>
      <my-components2 v-bind:aa="value"></my-components2>

    </div>

  </div>


  <script>


    var cmp1 = {
      props: ["aa"],
      template: '<div>첫 번째 지역 컴포넌트: {{ aa }}</div>',
    }
    var cmp2 = {
      props: ["aa"],
      template: '<div>두 번째 지역 컴포넌트: {{ aa }}</div>',
    }

    var app = new Vue({
      el:'#app',
      data: {
        value: 100,
      },
      components: {
        "my-components1": cmp1,
        "my-components2": cmp2,
      }
    })

    //1. cmp1Data 상위로 이동

    //2. my-components1, my-components2에게 이동한 데이터를 주면 된다.

  </script>

```


