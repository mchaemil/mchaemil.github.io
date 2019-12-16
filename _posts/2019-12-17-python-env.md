---
layout: article
title: Python/가상환경 | virtualenv
tags: Python

---

## **Today What I Learend**  

독립된 환경을 구축하기 위해서


---
**Today I Learend**


- virtualenv








---
Pyenv로 파이썬 버전 관리하기

http://jeonghwan-kim.github.io/2016/08/11/pyenv.html



pip3 install virtualenv   
virtualenv &lt;project name&gt;
source &lt;project name&gt;/bin/activate => 앞에 이 환경을 쓰고 있다는 문자열이 생긴다. 윈도우 사용자는 source는 빼고 입력

가상환경을 만든 후 그 속에 
pip3 install django를 설치


django-admin startproject &lt;project name&gt; => config 같은 느낌의 폴더, 프로젝트 디렉토리 네임이랑 프로젝트 이름이랑 같게 하니.. 헷갈...

cd &lt;project name&gt;

django-admin startapp &lt;app name&gt;

