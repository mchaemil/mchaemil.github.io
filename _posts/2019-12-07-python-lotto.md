---
layout: article
title: Python Lotto Generator
mathjax: true
tags: python
---

## 파이썬으로 로또 생성기를 만드는 방법

---

- 기본적인 구문을 사용해서 생성하는 방법
- 조금은 개선된 방법? shuffle 사용?
- set 자료형을 사용한 방법?
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


