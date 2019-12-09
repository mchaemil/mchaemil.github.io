---
layout: article
title: Python/Web Crawling - Crawling을 위한 기본 세팅, 네이버 날씨, 웹툰, 정부부처 사이트 Crawling - 부제: 이게 프로그래밍의 힘인가?
tags: python

---

## **Today What I Learend**  
파이썬이라는 프로그래밍 언어를 가지고 크롤링을 위한 세팅부터 시작해서 간단한 세팅, 실제 사이트에서 다양한 데이터를 수집하는 과정을 진행했다.

말로만 그리고 커뮤니티 게시판으로만 전해들었던 크롤링을 실제로 직접해보니 놀랍다. 새삼 잊고 지냈던 프로그래밍 언어의 위력을 다시금 느낄 수 있었다. 


---
**Today I Learend**
- Web Crawling을 시작하기 위한 세팅
- 본격적인 Crawling 시작에 앞서 간단한 맛보기
- Crawling - 네이버 날씨 
- Crawling - 네이버 웹툰
- Crawling - 정부부처 사이트 게시판 읽어오기

---



```mermaid
graph TB;
    A[인자를 개수 제한 없이 받을 수 있는 함수를 생성]
    B[max 지역변수에 첫번째 값을 담고, for문을 통해 다른 값들과 순차적으로 비교]
    C[비교값 보다 크다면 max지역변수에 대입]
    D[가장 큰 값을 return]
    A--yes-->B;
    B--yes-->C;
    C--no-->B;	
    C--yes-->D;
```


