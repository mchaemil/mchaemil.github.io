---
layout: article
title: Algorithm/javascript | Level_1 - 가운데 글자 가져오기
tags: algorithm
comments: true

---

## **Today What I Learend**  

내게는 익숙한 Javascript를 활용해서 
알고리즘 문제를 풀어보았다...! 
예전에는 손도 못대던 것들이... 이제는 어렴풋이 감이 잡히는 것 같기도...

아직은 level 1이지만.. 시간이 지나면 조금은 더 나아질 수 있겠지! 



---
**Today I Learend**
- 주어진 문제
- 나의 풀이1 - 20191219



---

### 주어진 문제

- 문제에 대한 설명

> 주어진 단어 string의 가운데 글자를 반환하는 함수, solution을 만들어 보세요. 단어의 길이가 짝수라면 가운데 두글자를 반환하면 됩니다.

**제한 사항**  
- 주어진 단어 string은 길이가 1 이상, 100이하인 스트링입니다.


입출력 예시

| string | return | 
|---|:---:|---:|
| "abcde" | "c" |
| "qwer" | "we" |  


### 나의 첫 번째 풀이 - 20191219


```javascript
function solution(s) {
    var answer = '';
    var data
    var calc = Number(s.length % 2)        
    var div = Number(s.length / 2) // 2.5
    
    if(calc === 0) {
       answer = s[div - 1] + s[div]        
    } else if(calc === 1) {
       data = Math.floor(div) 
       answer = s[data]
       console.log(answer)
    }    
    return answer;
}

```

#### 나의 첫 번째 풀이 사고의 과정

1. 주어진 단어 string을 변수로 넘겨 받을 때, 나머지 연산자를 사용해서 2로 나눈 후 그 값을 통해 문자열의 길이가 짝수인지, 홀수인지 확인
1. 문자열의 길이를 확인 후 나누기 연산자로 잘라야겠다고 생각
1. 나누기 연산자로 글자를 자른 후 짝수라면, 자른 글자와 자른 글자의 index - 1의 글자를 return 
1. 홀수라면, string의 인덱스에 floor(), 즉 내림한 값을 대입하고 return



_posts/2019-12-18-DB-sql-second-day.md



