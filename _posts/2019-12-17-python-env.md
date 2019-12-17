---
layout: article
title: Python/가상환경 | python 프로그래밍을 위한 가상환경 설정하기(feat. virtualenv, VSCode, Python, Django )
tags: Python

---

## **Today What I Learend**  

독립된 환경을 구축하기 위해서


---
**Today I Learend**

- VSCode 에 python 설치, Windows 설정
- VSCode 에 python 설치, Mac 설정

- virtualenv 로 프로젝트 시작








---


### VSCode 에 Python 설치 
#### Windows
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
            "command": "python",
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

#### Mac

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





### 파이썬 가상환경 설정






### Pyenv로 파이썬 버전 관리하기
[PYENV로 파이썬 버전 관리하기](http://jeonghwan-kim.github.io/2016/08/11/pyenv.html)




### 장고 가상환경 설정
pip3 install virtualenv  
[파이썬 가상환경 설정시 Errno 13, Permission denied 오류 발생할 때](https://github.com/googlesamples/assistant-sdk-python/issues/236)


---
**오류 발생시**  
- python3 -m venv env => (가상환경 파일을 생성?)
- source ./env/bin/activate   
- python -m pip install google-assistant-sdk[samples] 

---


virtualenv &lt;project name&gt;
source &lt;project name&gt;/bin/activate => 앞에 이 환경을 쓰고 있다는 문자열이 생긴다. 윈도우 사용자는 source는 빼고 입력

가상환경을 만든 후 그 속에 pip3 install django를 설치


django-admin startproject &lt;project name&gt; => config 같은 느낌의 폴더, 프로젝트 디렉토리 네임이랑 프로젝트 이름이랑 같게 하니.. 헷갈...

cd &lt;project name&gt;

django-admin startapp &lt;app name&gt; # 애플리케이션의 이름

