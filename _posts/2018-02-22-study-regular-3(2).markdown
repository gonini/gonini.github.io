---
layout: post
title:  "[정규표현식] 횟수 정하기(Quantifier)  "
subtitle:   "정규표현식"
categories: study
tags: regular
comments: false
---

## 0개 이상

### 0개 이상의 숫자를 찾고 싶을때

> 0개 이상은 `*`으로 표현한다.<br>
숫자가 0개 이상 나타난다는건 `\d*`로 표현한다.<br>
자연수는 첫번째 자리에서 무조건 1-9 사이의 숫자가 나온다. 그 뒤로는 숫자가 나오지 않을 수도 있으므로, 이를 이용하여 자연수는 `[1-9]\d*`로 표현한다.

### 코드

```
//따옴표(')로 둘러쌓인 부분에 원하는 정규표현식을 적습니다.
regex = r'[1-9]\d*'

search_target = '''Luke Skywarker 02-123-4567 luke@daum.net
다스베이더 070-9999-9999 darth_vader@gmail.com
princess leia 010 2454 3457 leia@gmail.com'''

//정규표현식과 일치하는 부분을 모두 찾아주는 파이썬 코드입니다.
import re
result = re.findall(regex, search_target)
print("\n".join(result))
```

### 결과

```
자연수가 Output에 출력되는 것을 확인할 수 있다.
```
<br>
출처: <a href="https://programmers.co.kr/">프로그래머스</a>