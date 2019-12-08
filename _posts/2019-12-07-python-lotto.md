---
layout: article
title: Python/Lotto Generator
mathjax: true
tags: python
---


## Python으로 Lotto Generator 만드는 법

프로그래밍 언어를 사용해 로또 생성기를 만드는 방법을 구현하는데 있어서 아직까지는 어려움을 느낀다. 어서 이러한 어려움에 익숙해져서 논리적인 사고력에 익숙해져야겠다..!
다만 파이썬의 몇가지 문법을 사용하면 조금 더 쉽게 구현할 수 있는 방법이 있는 것 같다.!


---

**Lotto Generator 만드는 방법**

- 기본적인 구문을 사용하는 방법
- in연산자를 활용한 파이썬스러운 문법
- 조금은 개선된 방법 shuffle 함수 사용(더 나은 랜덤을 위해서)
- set 자료형을 사용한 방법(중복을 허용하지 않는 자료형)을 고민해보는 중...

---

### 기본적인 문법으로 생성하는 법

```python

import random

lottoNumbers = [0 for i in range(6)]
lottoNumberIndex = 0

while lottoNumberIndex < len(lottoNumbers):
  lottoNumbers[lottoNumberIndex] = random.randint(1, 46)
  has_duplicate = False

  for i in range(lottoNumberIndex):
    if lottoNumbers[lottoNumberIndex] == lottoNumbers[i]:
      has_duplicate = True
      break
  if not has_duplicate:
    lottoNumberIndex += 1

print('=== Lotto Numbers ===')
for i in lottoNumbers:
  print(i, end=', ')

# 13, 34, 1, 5, 45, 21,
```

### in연산자를 활용한 파이썬스러운 문법

```python
import random

lotto = []
while True:
	if len(lotto) == 6:
		break
	num = random.randint(1, 45)
	if num in lotto:
		continue
	else:
		lotto.append(num)

print(lotto) # [13, 34, 1, 5, 45, 21]
```

### random 모듈의 shuffle 함수를 사용한 방법
shuffle은 리스트내의 요소를 무작위로 섞는 함수이다. 

```python
import random

lotto = [x for x in range(1, 46)]
random.shuffle(lotto)
for i in range(6):
	print(lotto.pop(), end=' ') # 9 24 14 10 26 44
```



