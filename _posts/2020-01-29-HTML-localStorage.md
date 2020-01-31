---
layout: article
title: HTML | HTML5 localStorage는 무엇인가?
tags: HTML

---

## **Today What I Learend**  

예전에 Javascript를 활용한 ToDoList 따라만들기에서 처음 localStorage라는 개념을 접했는데, 이해가 되지 않아서 미지의 영역으로 남겨두었던 적이 있었다.. 시간이 지나니 이제서야 보이지 않던 것들이 보이기 시작했고, 어렵게 느껴지지 않기 시작했다.

새롭게 알게 된 것들과 이해되지 않던 부분들이 명확해졌다는 사실이 기쁘다.

---
**Today I Think**
- localStorage


---

### Storage

> Web Storage API는 브라우저에서 쿠키를 사용하는 것보다 훨씬 직관적으로 key/value 데이터를 안전하게 저장할 수 있는 메커니즘을 제공합니다.   
[참고 - MDN Web Storage API](https://developer.mozilla.org/ko/docs/Web/API/Web_Storage_API/Using_the_Web_Storage_API)

window객체 안에는 `localStorage`와 `sessionStorage`라는 저장소가 있다. 두 스토리지는 HTML5에서 추가된 저장소이며, key/value형태로 데이터를 저장하는 Storage이다.

#### localStorage와 sessionStorage
`localStorage`와 `sessionStorage`는 `Storage`객체를 상속받으므로 메소드가 공통적으로 존재한다. 이 둘은 데이터를 영구적으로 보존하는지 아닌지에 따라서 차이를 가지게 되는데, `localStorage`는 사용자가 데이터를 제거하지 않는 이상 영구적으로 남는 반면, `sessionStorage`의 경우 윈도우를 종료하거나 브라우저 탭을 닫을 경우 데이터가 제거된다. 


### localStorage
`localStorage` 객체는 단순한 key/value만을 저장하는 저장소이며, 객체와 비슷하다. 다만 중요한 점은 이 데이터들이 페이지 로딩 이후에도 온전히 유지된다는 점이다.

`localStorage`에 저장하는 `key`와 `value`는 문자열로 변환된다. boolean이나 정수 같은 기본형 타입의 데이터를 저장한다고 해도 자동으로 string으로 변경된다

### Storage 메서드

| 속성 | 설명 |
|---|---|
| Storage.setItem() | 인자로 key, value를 전달해 Storage에 저장 |
| Storage.getItem() | 인자로 key를 전달하여 Storage에 저장된 값을 조회 |
| Storage.removeItem() | 인자로 key을 전달하면 해당 키가 Storage에서 지워짐 |
| Storage.clear() | Storage 전체를 비움 |


### localStorage에 데이터 넣어보기
`localStorage`에 데이터를 저장할 때 key/value 형식으로 저장할 수도 있지만, 객체 형태로 저장하려면 `JSON.stringify()`를 통해 객체 타입을 문자열 타입으로 변환하여 저장해야 한다. 또한 반대로 `localStorage`의 데이터를 가져올 때는 `JSON.parse()`를 통해 문자열을 객체 타입으로 변환하여 가져와야 합니다. 

```javascript
const TODOS_LS = "toDos";
const toDos = [];

for (let i = 0; i < 5; i++) {
  const toDoObj = {
    text:"안녕하세요",
    id: i + 1
  }
  toDos.push(toDoObj);  
}

localStorage.setItem(TODOS_LS, JSON.stringify(toDos))
```


### localStorage 활용

#### JSON.stringify

`localStorage.setItem(TODOS_LS, toDos)`처럼 `setItem()`메소드의 인자에 자바스크립트 데이터를 직접 넣으면 `LocalStorage`에는 `[object Object]`처럼 데이터가 들어간다.

왜냐하면 `LocalStorage`에는 자바스크립트의 data를 저장할 수 없기 때문이다. `LocalStorage`는 모든 데이터를 `string`으로 저장한다. 그래서 자바스크립트 `object`가 `string`이 되도록 바꾸고 저장해야 한다. 이를 위해서 `JSON.stringify()`메소드를 사용해야 하는데, `JSON.stringify()`는 인자로 전달된 자바스크립트 `object`를 `string`으로 바꿔준다.

```javascript
function saveToDos(){
  localStorage.setItem(TODOS_LS, JSON.stringify(toDos));
}
```

#### JSON.parse

null이 아닐 때만 해주면 된다.

`localStorage.getItem()`으로 데이터를 불러온 경우 불러온 데이터가 `string`이라는 문제가 생긴다! 이를 자바스크립트에서 활용하기 위해서는 `JSON(Javascript Object Notation)`을 사용해야 한다! JSON을 통해 string을 object로, object를 string으로 변경할 수 있다.

`JSON.parse()`를 사용하면 데이터를 가져올 때 자바스크립트가 다룰 수 있도록 `string`을 `object`로 바꿔준다!


```javascript
function loadToDos() {
  const loadedToDos = localStorage.getItem(TODOS_LS);
  if(loadedToDos !== null) {
    const parsedToDos = JSON.parse(loadedToDos);

    parsedToDos.forEach(toDo => {
      paintToDo(toDo.text);
    });
  } 
}
```











