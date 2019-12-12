---
layout: article
title: Django/Bookmark | 장고로 만드는 작은 애플리케이션 두번째 
tags: Django

---

## **Today What I Learend**  

파이썬의 장고, 부트스트랩을 이용해 북마크 앱을 만들고, pythonanywhere 에 배포하는 과정을 통해 하나의 애플리케이션이 완성되는 과정을 경험해보았다.
지금은 단순히 따라 만들며 애플리케이션이 완성되는 흐름을 따르는 것이지만, 장고가 제공하는 다양한 기능들을 체험하며! 다음에는 내가 기획하고 설계한 하나의 서비스를 만들어보고 싶다. 





---
**Today I Learend**
- 프로젝트의 구조
- 장고에서 디비를 생성해서 마이그레이션 하는 방법
- 
-  

**부록**
- HTML 이 사용되는 방법
- 내가 생각하는 HTML에 대하여
- 생활코딩 HTML에서 많이 사용되는 태그의 순위

- 예전에 만든 결과물을 소개하면서, 이런 것을 만들었는데, 이렇게 바뀌어 간다. 
- HTML -> CSS -> JS -> Bootstrap 이런 식으로 옮겨가는 방향에 대해서 설명한다. - 아니면 말고... 

- 

- 포트폴리오 페이지를 문서에서 하나씩 더해가며 보여준다. 
- 이렇게 하는 방향이 좋겠다.
- HTML, CSS, JS에 대한 그림을 보여주는 방법

- 우리가 배운 수업에서 HTML이 활용될 수 있는 방법
	- 저는 크롤링을 할 때 요소를 쉽게 찾았어요
	- HTMl에 대한 이해가 있다보니 Template을 작성할 때 어떠한 내용이 보여질지에 대한 이해를 금방 얻을 수 있었어요
	- 지금 태그에 넣는 데이터가 어떠한 역할을 하는지 쉽게 이해했어요
	



웹의 본질은 문서이다. 
HTML은 웹이라는 공간에 정보를 나타내기 위한 그릇이다. 

HTML은 더 중요한 것과 덜 중요한 것을 구분하게 해주고 
정보의 형식을 담는 그릇이 됩니다. 

이 때문에 어떠한 형식인지 이해하게 된다면...!
단순히 데이터를 보는 것보다 더 많은 것을 마주할 수 있게 됩니다.


---




### 프로젝트의 구조

```

Bookmark
├── config
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
├── bookmark
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
├── hello
├── venv
├── db.sqlite3
└── manage.py
```


http://devhaemil.pythonanywhere.com/bookmark/git 







