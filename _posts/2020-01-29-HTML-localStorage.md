---
layout: article
title: HTML | HTML5 localStorage는 무엇인가?
tags: HTML

---

## **Today What I Learend**  

예전에 Javascript를 활용한 ToDoList 따라만들기에서 처음 localStorage라는 개념을 접했는데, 이해가 되지 않아서 미지의 영역으로 남겨두었다가.. 이제서야 보이지 않던 것들이 보이기 시작했다.. 
새롭게 알게 된 것들과 이해되지 않던 부분들이 명확해졌다는 사실이 기쁘다.

---
**Today I Think**
- localStorage


---


### localStorage

[참고 - MDN Web Storage API](https://developer.mozilla.org/ko/docs/Web/API/Web_Storage_API/Using_the_Web_Storage_API)

> Web Storage API는 브라우저에서 쿠키를 사용하는 것보다 훨씬 직관적으로 key/value 데이터를 안전하게 저장할 수 있는 메커니즘을 제공합니다.


Storage 객체는 단순한 key/value만을 저장하는 저장소이며, 객체와 비슷하다. 다만 중요한 점은 이 데이터들이 페이지 로딩 이후에도 온전히 유지된다는 점이다.


`localStorage`에 저장하는 `key`와 `value`는 문자열로 변환된다. boolean이나 정수 같은 기본형 타입의 데이터를 저장한다고 해도 자동으로 string으로 변경된다



| 속성 | 설명 |
|---|---|
| Storage.setItem() | 인자로 key, value를 전달해 Storage에 저장 |
| Storage.getItem() | 인자로 key를 전달하여 Storage에 저장된 값을 조회 |
| Storage.removeItem() | 인자로 key을 전달하면 해당 키가 Storage에서 지워짐 |
| Storage.clear() | Storage 전체를 비움 |









