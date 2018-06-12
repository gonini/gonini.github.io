---
layout: post
title:  "[정규표현식] 횟수 정하기(Quantifier)  "
subtitle:   "정규표현식"
categories: study
tags: regular
comments: false
---

## 하나 이상

### 연결된 숫자를 찾고 싶을때 

> `\d`를 이용하면 숫자를 한글자 한글자 찾아준다.<br>
연결된 숫자를 찾고 싶을때는 `+`를 이용한다.<br>
`\d+`라고 쓰면 하나 혹은 그 이상 연결된 숫자를 의미한다.

### 코드

```
//regex에는 넣는 값 중, 따옴표(')로 둘러쌓인 부분에 원하는 정규표현식을 적습니다.
regex = r'\d+'

search_target = '''Luke Skywarker 02-123-4567 luke@daum.net
다스베이더 070-9999-9999 darth_vader@gmail.com
princess leia 010 2454 3457 leia@gmail.com'''

//아래 부분은 본 강의에서 다루지 않습니다.
import re
result=re.findall(regex,search_target)
print(result)
```

### 결과

```
['02', '123', '4567', '070', '9999', '9999', '010', '2454', '3457']
```
<br>
출처: <a href="https://programmers.co.kr/">프로그래머스</a>