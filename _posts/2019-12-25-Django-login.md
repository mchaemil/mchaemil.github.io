---
layout: article
title: Django/Login | 장고로 로그인 기능 만들어보기
tags: Django

---

## **Today What I Learend**  

회원가입 기능과 더불어서 늘 만들어보고 싶었던 로그인 기능을 만들어 보았다. 
단순히 따라 만든 것이므로 이것은 아직 나의 것이 아닌 코드이다.
나의 코드로 소화하기 위한 노력을 부단히 하자! 이렇게 조금씩 조금씩 다양한 기능들을 익혀서 거대한 웹 프로젝트를 만들 수 있는 날이 오기를 기대하며! 


---
**Today I Learend**
- 프로젝트 진행 순서, MVT 코딩 순서
- Model coding
- View coding
- Template coding

---


### 프로젝트 진행 순서, MVT 코딩 순서

데이터베이스 테이블 설계는 독립적이므로 Model(모델)을 먼저 코딩하고, 그 다음 서로 연결되어 있는 뷰와 템플릿 중에서는 템플릿을 먼저 코딩하는 방식으로 진행했다!


```mermaid
graph TB;
    A[프로젝트 구조 만들기]
    B[Model 클래스를 작성하고 데이터베이스에 반영]
	C[클라이언트의 요청을 분석하는 URLconf를 코딩, URL과 View를 매핑하는 작업]    
	D[애플리케이션을 컨트롤하는 View 로직을 코딩]
    E[템플릿 문법을 통해 사용자에게 보여질 화면 코딩]	
    A--yes-->B;
    B--yes-->C;
    C--yes-->D;	
    D--yes-->E;
	
```


### 파일 구조 설정

```
<Root folder>
│
├<community_project>
│ ├── config
│ ├── user
│ │   ├── migrations
│ │   ├── templates
│ │   ├── __init__.py
│ │   ├── admin.py
│ │   ├── apps.py
│ │   ├── models.py
│ │   ├── tests.py
│ │   ├── urls.py
│ │   ├── views.py
│ ├── db.sqlite3
│ ├── manage.py
└venv (가상환경 설정)


```


### Model coding

모델은 따로 코딩하는 것이 없다. 




#### 페이지를 분기하는 코드를 만든다. 
단순 로그인화면과 로그인을 통해 사용자 정보를 저장한 화면을 나누는 작업을 처리한다. 

로그인 기능이 요청되었다면 
Input 을 통해 넘어온 값을 변수에 저장하고

### View coding

#### Login view

```python
def login(request):
    if request.method == 'GET':
        return render(request, 'login.html')
    elif request.method == 'POST':
        username = request.POST.get('username', None)
        password = request.POST.get('password', None)
		
	return render(request, 'login.html', res_data)
	
```

데이터가 모두 입력되었는지 검증하는 절차를 가진다. 

데이터가 모두 입력되었을 경우 DB의 값과 비교하기 위해서
데이터를 저장한 모델로부터 가지고 와야 한다.  
이 아이디를 사용한 유저 모델을 가지고 와서 사용자가 입력한 비밀번호와 username을 사용한 fcuser 모델을 가지고 온다.  

입력받은 비밀번호와 Model 안에 있는 비밀번호가 일치하는지 확인해야 한다.

확인을 위해서 fcuser 변수에 username에 대한 정보를 가지고 온다.

**2.** check_password 메서드의 첫 번째 인자에는 현재 입력된 비밀번호, 두 번째 인자에는 모델로부터 가져온 비밀번호를 넣으면 이 둘이 같다면 로그인 처리를 진행하는 코드를 작성하고, 틀렸다면 안내문구를 처리하는 코드를 작성한다. 

여기서부터 Session에 대해서 다루게 되는 데, 세션에 대한 처리를 진행 후, 홈으로 가게 하기 위해서 리다이렉트를 거는 작업을 한다. 


세션은 각 키마다 값을 가지고 있는 딕셔너리와 비슷한 형태이먀, 유저라는 키에 아이디값을 저장했는데, 이렇게 넣은 것만으로 저장과 세션에 대한 처리가 끝난다.


```python  
res_data = {}
if not (username and password):
	res_data['info_error'] = '아이디와 비밀번호가 입력되지 않았습니다.'
else:
	user = User.objects.get(username=username) 
	# 앞은 필드명, 뒤는 입력을 저장한 변수 username
	
	# 2.번 설명
	# 입력받은 비밀번호, 모델로부터 가져온 값
	if check_password(password, fcuser.password):
		res_data['password_valid'] = '아이디와 비밀번호가 올바릅니다.'
		# 비밀번호가 일치, 로그인 처리를 진행!
		# 1. 세션에다가 저장하기
		request.session['user'] = fcuser.id

		# 2. Root로 redirect 
		return redirect('/')
	else:
	# 비밀번호 불일치,
	res_data['password_error'] = '비밀번호가 틀렸습니다.'

return render(request, 'login.html', res_data)

```

#### Home view

Login 진행 후 home으로 리다이렉트 되었을 때, user가 session내에 있다면 사용자 정보를 user_id 라는 변수에 할당한다.

user_id가 존재한다면 세션의 유저키(`request.session['user']`)에 넣어놓은 아이디를 가져온다.
user_id를 pk로 해서 모델을 가져오고!!

가져온 정보를 화면에 보여주기 위해 HttpResponse 의 인자에 넣는다. 

```python
def home(request):
    user_id = request.session.get('user')
    if user_id:
        user = User.objects.get(pk=user_id)
        return HttpResponse(user.username)

    return HttpResponse('Home')

```


### Template coding

템플릿 코드는 회원가입과 다를바가 없다.

`submit` 버튼의 벨류값과 태그내 값들만 바꾸어주고
아이디와 비밀번호만 입력할 수 있는 input tag만 남겨주면 된다. 

\{\{ \}\} 와 \{\% 을 <>로 표현

```python
<form method="post" action=".">
  < csrf_token >
  <div class="form-group">
	<label for="username">사용자 이름</label>
	<input type="text" class="form-control" id="username" name="username" placeholder="사용자 이름">
  </div>
  <div class="form-group">
	<label for="password">비밀번호</label>
	<input type="password" class="form-control" placeholder="비밀번호" id="password" name="password">
	 < password_error >
  </div>


  <button type="submit" class="btn btn-primary">로그인</button>
</form>


```



