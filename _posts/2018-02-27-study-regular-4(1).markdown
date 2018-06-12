---
layout: post
title:  "[정규표현식] 고르기  "
subtitle:   "정규표현식"
categories: study
tags: regular
comments: false
---

## 몇 개 중에 고르기

### 알파벳 중에 소문자 모음만 고르기

> 알파벳 소문자 모음(a,e,i,o,u)만 고르기 위해 ``[aeiou]``라고 적는다. 정규표현식의 대괄호[ ]안에 글자를 넣으면 텍스트에 나오는 그 글자들은 모두 선택한다. 

### 코드

```
// 따옴표(')로 둘러쌓인 부분에 원하는 정규표현식을 적습니다.
regex = r'[aeiou]'

search_target = '''Luke Skywarker 02-123-4567 luke@daum.net
다스베이더 070-9999-9999 darth_vader@gmail.com
princess leia 010 2454 3457 leia@gmail.com'''

// 정규표현식과 일치하는 부분을 모두 찾아주는 파이썬 코드입니다.
import re
result = re.findall(regex, search_target)
print("\n".join(result))
```

### 결과

```
['02-123-4567', '070-9999-9999', '010 2454 3457']
```

<br>
출처: <a href="https://programmers.co.kr/">프로그래머스</a>