---
layout: article
title: Python/가상환경 | python 프로그래밍을 위한 가상환경 설정하기(feat. virtualenv, VSCode, Python, Django )
tags: python

---

## **Today What I Learend**  

하나의 운영체제에서 다양한 버전의 프로그래밍 언어를 사용해야 할 경우 발생할 수 있는 문제들을 해결하는 데 도움을 주는 기술인 가상환경에 대해서 학습했다.  
아직은 다양한 버전의 파이썬을 사용하지 않으므로 이 가상환경이란 기법에서 어떠한 위력을 느껴지는 못했지만 운영체제의 폴더 구조에서 독립된 환경을 구축하기 위해서 조금씩 꾸준히 사용해서 익숙해지는 연습을 하자!


---
**Today I Learend**

- VSCode 에 python 설치, Windows 설정
- VSCode 에 python 설치, Mac 설정
- venv로 프로젝트 생성하는 법
- virtualenv 로 프로젝트 생성하는 법


---


### VSCode 에 Python 설치 
#### Windows 에서 설치
1. Python 설치 후 Path 연결 
1. VSCode 도 가능하면 같은 폴더 구조에서 설치하기  
1. VSCode 실행 후 Extension에서 Python 설치
4. 설정(톱니바퀴 모양)에서 Command Palette를 클릭하고, Python: Select Interpreter
1. task runner 를 설치
	1. Command Palette 입력창에 Tasks: Configure Task 
	1. Create tasks.json file from template => Ohters
	2. 아래의 코드를 복사해서 붙여넣기
	3. ctrl + shifr + B 단축키를 통해서 파이썬 실행
	3. Executing task: 실행 파일 이름과 출력 내용이 간단하게 실행됨
	


```
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "label": "Project Label",
            "type": "shell",
            "command": "python", // Mac에서는 python3으로 변경하기!!
            "args": [
                "${file}" // 내가 실행하는 파일이 실행될 수 있도록
            ],
            "presentation": {
                "reveal": "always",
                "panel": "new"
            },
            "options": {
                "env": {
                    "PYTHONIOENCODING": "UTF-8" // 한글 출력을 위해서 UTF-8로 설정
                }
            },
            "group": {
                "kind": "build",
                "isDefault": true
            }
        }
    ]
}

```

#### Mac 에서 설치

1. Python 설치 후 
1. VSCode 를 실행하여, Shell Command: Install 'code'command in PATH 를 연결
1. VSCode 실행 후 Extension에서 Python 설치
4. 코드를 실행하고 가상환경을 설정!! 
	1. 작업 환경으로 이동하여
	1. python3 -m venv `python_basic` => 폴더이름 설정
	1. 그리고 bin으로 이동후 
	1. source ./activate => 이를 통해 가상환경 활성화됨
	1. `deactivate` 를 실행하면 가상환경 해제
	1. 
1. 앞으로는 Terminal을 통해서 가상환경을 실행하고 code 명령어 입력을 통해서 VSCode 를 실행하고 코드를 작성
4. 설정(톱니바퀴 모양)에서 Command Palette를 클릭하고, Python: Select Interpreter, 가상환경으로 잡아둔 버전을 설정
1. task runner 를 설치 - 단축키 설정, console창 정리
1.  Command Palette에서 configure task 클릭

**더욱 빠르게 단축키로 실행할 수 있음**  
`commnad + shift + B`
```
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "label": "Project Label",
            "type": "shell",
            "command": "python3", // Mac에서는 python3으로 변경하기!!
            "args": [
                "${file}" // 내가 실행하는 파일이 실행될 수 있도록
            ],
            "presentation": {
                "reveal": "always",
                "panel": "new"
            },
            "options": {
                "env": {
                    "PYTHONIOENCODING": "UTF-8" // 한글 출력을 위해서 UTF-8로 설정
                }
            },
            "group": {
                "kind": "build",
                "isDefault": true
            }
        }
    ]
}

```


의문을 가지고 해결을 해야 실력이 향상될 수 있다. 

### 파이썬 가상환경 설정  

#### 파이썬 가상환경을 사용해야 하는 이유
한 운영체제에 다양한 버전의 파이썬을 설치해서 사용하다보면 문제가 발생할 수도 있다. 가령 특정 어플리케이션은 파이썬 3.6버전이 필요한데, 현재 운영체제에서 이를 사용하지 못하는 상황이 생긴다면 곤란한 일이 발생한다! 

#### 파이썬 가상환경이 주는 이점

| 가상환경A | 가상환경B | 가상환경C |
|---|:---:|---:|
| Python 3.5 | Python 2.7 | Python 3.4 |
| Django | Numpy, Tensorflow | PyQT5 |
| Web |  Data 분석 | Gui Application |


프로젝트를 위한 가상환경은 A, B, C 로 구분하고 각각 장고, 넘파이, 파이큐티를 활용해 목적에 따른 작업을 진행한다고 한다고 할 때!, **가상환경을 사용할 때는 프로젝트가 끝나면 폴더만 지우면 된다!** 가상환경은 별개의 모듈을 사용하므로써 파이썬의 버전이 엉키는 일 없는 환경을 구축하게 해준다. 

**프로젝트가 끝나면 그저 폴더만 지우면 된다!** 이러한 이유가 가상환경이 주는 가장 큰 이점이라고 한다.!


### venv, 가상환경을 만드는 첫 번째 방법

**가상환경을 작업하는 순서**

---

1. `python -m venv python_workspace`
2. cd python_workspace
3. 윈도우는 `Scripts` | Mac은 `bin` 으로 이동
4. 윈도우는 `activate` | Mac은 `source ./activate`
5. 가상환경을 빠져나가고 싶을 때는 `deactivate`

---

여기까지 했다면 매우 잘했음!
개발을 하다가 무언가가 꼬였다면
코드 파일은 그대로 두고 `include`, 'bin', 'Scripts'만 지우고 다시 설치하면 됨


### 파이썬 가상환경에 패키지 설치해보기
#### 기억해야 할 명령어

`pip search simplejson` => 특정 패키지 검색
`pip search simple*` => simple이라는 단어가 들어간 패키지 검색, 내가 필요한 게 있는지 구글링, 깃허브 검색을 해서 사용해보기를 추천


`pip show simplejson` => 특정 패키지에 대한 내용정보를 요청할 떄!


`pip install simplejson` => 패키지 설치

`pip install --upgrade simplejson` => 간단한 명령어로 버전을 업그레이드를 진행할 수 있음

`pip list` => 현재 어떤 패키지가 설치되었는지 확인


#### Test!
1. simplejson 설치해보기
1. 아래 `Test code`를 실행해보기
1. simplejson 삭제해보기

**Test code**
```python

# import simplejson as json 이게 아니고...
import json as simplejson # 여기처럼 작성
test_dict = {
    '1': 95,
    '4': 66,
    '2': 16,
    '3': 76,
}

print(simplejson.dumps(test_dict, sort_keys=True, indent=4 * ' '))

```




### virtualenv, 가상환경을 만드는 두 번째 방법  
**virtualenv** 사용하기  
`pip install virtualenv` 명령으로 virtualenv가 설치되었다면
`virtualenv env` 와 같은 virtualenv + <가상환경 폴더이름>으로 가상환경을 구축할 수 있다. 



`pip3 install virtualenv`  => Mac에서는 `pip3` 명령을 사용해야 함
[파이썬 가상환경 설정시 Errno 13, Permission denied 오류 발생할 때](https://github.com/googlesamples/assistant-sdk-python/issues/236)


**첫 번째 구축 순서와 같음, 명령어만 다름**
1. `pip install virtualenv` 명령으로 virtualenv 설치 (Mac에서는 pip3)
1. 설치되었다면 `virtualenv env` 와 같은 virtualenv + <가상환경 폴더이름> 으로 가상환경을 구축할 수 있다. 
1. 가상환경을 구축하고 프로젝트 생성 순서는 위와 같음

**Tip.**  
맥의 경우는 가상환경으로 진입해 activate를 실행할 때 source를 입력해야 하고, 윈도우는 그냥 activate를 입력하면 된다. 


---

### 가상환경 설정 후 장고 프로젝트 실행하는 법

#### 장고 프로젝트 구축 순서
1. 가상환경 폴더로 이동 후 `activate`! 
1. `activate` 실행 후 Root folder로 빠져나오기
1. `pip install django`
1. `django-admin startproject <project_name>`
1. `cd <project_name>` 
1. `django-admin startapp <app_name>`

```
<Root Folder>
|
<project_name>
└──<project_name>
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
├── <app_name>
├── db.sqlite3
└── manage.py
```



**장고 프로젝트 구축을 virtualenv를 사용했을 경우의 순서**
1. virtualenv &lt;project name&gt;
2. source &lt;project name&gt;/bin/activate => 앞에 이 환경을 쓰고 있다는 문자열이 생긴다. 윈도우 사용자는 source는 빼고 입력
3. 가상환경을 만든 후 그 속에 pip3 install django를 설치
4. django-admin startproject &lt;project name&gt; => config 같은 느낌의 폴더, 프로젝트 디렉토리 네임이랑 프로젝트 이름이랑 같게 하니.. 헷갈...리지만 일단 생성!
5. cd &lt;project name&gt;
6. django-admin startapp &lt;app name&gt; # 애플리케이션의 이름



#### 참고자료

**[PYENV로 파이썬 버전 관리하기 - 링크](http://jeonghwan-kim.github.io/2016/08/11/pyenv.html)**
