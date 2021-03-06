---
layout: article
title: Django/hello world | 시작은 언제나 hello world~
tags: Django

---

## **Today What I Learend**  

장고를 사용해 내딛는 첫걸음을 위해 알아야 할 요소들에 대해서 학습했다. 물론.. 아직도 익혀야 할 부분은 훨씬 더 많지만..! 
거대한 작업을 수행할 수 있는 장고라는 도구에 익숙해지기 위한 내딘 첫걸음에 만족해야지! 첫술에 배부를 수는 없다. 

**장고 학습방법**
- 따라 만들어보고, 안 보고 생각하며 만들면서 숙련해보고, 이후 또 다른 기능 추가해보기
- 그리고 현업에서 경험하는 것이 제일 좋은 학습법이므로 면접 계속 다녀보기


---
**Today I Learend**
- 프레임워크 장고의 특징 및 장점
- MVC vs MTV
- MTV에 대한 정리...!(준비중)
- Hello World 실습에 도움을 주는 지식
- Hello World 실습 코드

---

### 프레임워크 장고의 특징
파이썬으로 만들어진 웹 애플리케이션 프레임워크로 널리 사용되며, 사이트를 신속하게 개발할 수 있고, 보안과 유지보수를 편리하게 할 수 있으며, 많은 참고 자료와 커뮤니티가 있다. 

#### 장고의 장점
- 풀스택
- 보안
- 유지보수
- 확장성
- 다양한 용도


### MVC vs MTV 

프로그램의 복잡도가 높아지면 로직이건 디비건 섞여서 있어서 스파게티처럼 엉키게 되는데, 이를 스파게티 코드라고도 불린다. 스파게티 코드는 누가 쓰는지 모를정도로 뒤엉켜 있는 코드이므로 함부로 못 건드리는 코드가 되어 유지보수 측면에서 문제를 발생시킨다. 

이러한 문제를 해결하기 위해서 MVC 패턴을 통해서 모델, 뷰, 콘트롤러로 다 나누어서 스파게티 코드를 통해 겪던 어려움을 해소하는 개발을 할 수 있다.
- 웹은 아직까지 MVC가 대세인 것 같다.
- 뷰는 사용자에게 어떠한 화면을 보여줄지, 콘트롤러는 어떤 비즈니스 로직을 처리할 것인지만 정하면 된다. 

```


# MTV 패턴
# 모델은 똑같지만 뷰가 템플릿, 콘트롤러가 뷰...?
# 2년차 까지는..? 패턴에 대한 이해가 없을 수 있지만 경험이 생기면..~
# 개발 방법론 철학(디자인 패턴)에 대한 이해가 생긴다.

# 장고의 동작 원리
# 하얀색 영역은 건드릴 수 없는 것.
# 초록색만 건들 수 있는 것...!



```


#### 라이브러리와 프레임워크의 차이

라이브러리는 사용하는 주체가 '나'이다. 반대로 프레임워크는 내가 호출되는 것이다.
라이브러리와 프레임워크의 차이는 돌아가는 로직내에서 호출 주체에 의해서 결정되는데, 실행 흐름내에서 부품으로 존재하느냐 아니냐가 이 둘을 가르는 중요한 지점이다. 
가령 BeautifulSoup4은 내가 가져다 썼지만 장고는 로직의 처리에 껴서 가야 한다.
??프레임워크가 나를 호출하는 시점은 프레임워크가 결정한다.


### Hello World 실습

#### 프로젝트 구조 살펴보기
config 에는 프로젝트를 위한 설정 파일과 웹 서비스 실행을 위한 파일이 들어있다. 기본적인 문서구조가 잘못되면 에러를 만나게 됨..!! 

```

├── config
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
├── hello
├── venv
├── db.sqlite3
└── manage.py
```

#### manage.py 의 명령어
manage.py 의 명령어를 통해서 프로젝트를 관리할 수 있다.


| 명령어 | 설명 | 
|---|:---:|---:|
| `startapp` | 애플리케이션을 새로 만듦 |
| `makemigrations` | 앱의 모델 변경 사항을 정리 |  
| `migrate` | 디비에 모델의 변경사항을 적용, 이후에 admin 계정 생성가능 |  
| `runserver` | 테스트 서버를 실행 | 
| `createsuperuser` | 관리자 계정을 생성 |  


#### Hello World 앱 디렉토리 구조 살펴보기
Django 프레임워크를 사용해서 hello_world를 띄우기 위한 준비
hello 폴더에 urls.py 파일을 생성하여, URL Dispatcher가 hello_world/ 이후의 경로에 대해서 분석하도록 설정 

```
hello
├── admin.py
├── models.py
├── views.py
└── urls.py

```

### Hello World 실습 코드

#### hello/views.py

URL Dispatcher가 URL을 분석하여 어떠한 함수를 호출할지 결정하고, return 할 HttpResponse의 인자에 데이터를 넘겨준다.

```python

from django.http import HttpResponse

# Create your views here.
def hello_world(request):
    return HttpResponse('Hello World')
def hello_haemil(request):
    return HttpResponse('Hello haemil~!')
	
```

#### config/urls.py
request를 통해 사용자 요청이 들어왔을 때 URL Dispatcher가 URL을 분석하여 어떠한 함수를 호출할지 결정하고, 특정 URL 경로에 대한 처리로직을 설정한다. 

hello_world 와 같은 URL 패턴이 전달되면 URL 패턴처리에 대한 관리를 hello/urls.py 에게 위임한다.

```python

from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('hello_world/', include('hello.urls')),
]

```

#### hello/urls.py

계층이 깊어질 수도 있지만 hello_world의 / 이후로 계속 페이지를 표현할 수 있다. url 주소에 보여주고 싶은 데이터를 담은 함수를 맵핑하여 url 주소로 넘어오는 경로에 대해서 처리하는 화면을 제작할 수 있다. 우선은 hello_world까지만..! 



```python

urlpatterns = [
    path('', views.hello_world, name="hello_world"),
    path('hello_haemil', views.hello_haemil, name="hello_haemil"),
]

```

#### 결과 화면

![hello-world](https://user-images.githubusercontent.com/40027211/70628194-0f2e6a80-1c6b-11ea-8ca0-4e04c857ac62.PNG)



#### 이해에 도움을 얻은 코드

https://docs.djangoproject.com/en/3.0/topics/http/urls/

```python

from django.urls import path

from . import views
# articles/ 이후로 구조가 깊어질 수 있다.!!
urlpatterns = [
    path('articles/2003/', views.special_case_2003),
    path('articles/<int:year>/', views.year_archive),
    path('articles/<int:year>/<int:month>/', views.month_archive),
    path('articles/<int:year>/<int:month>/<slug:slug>/', views.article_detail),
]

```


