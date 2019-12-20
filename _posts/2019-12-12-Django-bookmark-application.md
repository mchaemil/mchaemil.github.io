---
layout: article
title: Django/Bookmark | 장고로 만드는 작은 애플리케이션 두 번째 
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


### 만든 애플리케이션
http://devhaemil.pythonanywhere.com/bookmark/git 






```
# 모델 생성
모델을 먼저 생성
데이터 베이스에 넣어보기 위해서
어드민에서 모델을 확인해보도록 하겠다. 

- 모델에서 클래스 생성을 디비를 만들고
- 세팅 INSTALLED_APPS에 넣는다. 넣기전까지는 연동이 되지 않으므로, 오류가 생긴다면 새로 만들어도 상관 없다. 
- makemigrations => 앱의 모델 변경 사항을 정리
- migrate 디비에 모델의 변경사항을 적용

```


3. 어드민 파일에 등록을 해야 한다. 
-	임포트를 하고 
- 모델에서 작성한 내용을 어드민으로 불러와야 한다. 

1. 세팅가서 북마크를 추가한다. 
디비에 쓸 준비를 한다.
마이그레이션 이후 마이그레이트 

1. 디비에 데이터를 써보는 작업을 한다. 
관리자 이름을 맵핑한다. 


1. 뷰를 만들고 임포트를한다.
from django.views.generic import ListView
from .models import Bookmark

- 북마크에서 URL 만든다.
- 뷰에서 패스랑 뷰를 임포트한다. 


1. config를 가서 
url을 받아오면 bookmark에서 처리할 수 있도록 처리한다.

1. 이름은 object_list가 디폴트이다. 
2. 바꾸어주려면 context_object_name를 해야 한다. 


포스트를 하면 토큰을 붙여줘야 한다



크리에이트를 상속받았기 때문에 
따로 기능을 만들어주지 않아도
제네릭뷰를 사용하면 다 만들어준다...

어떤 값을 가져올지 알아야 한다.
수정할 때는 그래서 피케이 값을 가져와야 한다!!


피케이는 데이터가 하나기 대문에 오브젝트이다. 굉장히 직관적인 측면이 있다. 


---


```

class BookmarkDetailView(DetailView):
    model = Bookmark

# Bookmark 가 소문자로 바뀌고 뒤에는 디폴트 값으로 계속해서 파일 구조의 경로가 붙는다.


```




