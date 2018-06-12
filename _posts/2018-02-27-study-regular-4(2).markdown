---
layout: post
title:  "[정규표현식] 고르기  "
subtitle:   "정규표현식"
categories: study
tags: regular
comments: false
---

## 범위에서 고르기

### 알파벳 중에 소문자만 고르기

> 영어 소문자만 고르고 싶다면 ``[abcdefghijklmnopqrlstuvwxyz]``와 같이 대괄호 안에 영어 소문자 모두를 적어주는 것도 가능하다. 하지만 이걸 줄여서 ``[a-z]``라고 쓸 수도 있다.

### 코드(1)

```
// 따옴표(')로 둘러쌓인 부분에 원하는 정규표현식을 적습니다.
regex = r'[a-z]'

search_target = '''Luke Skywarker 02-123-4567 luke@daum.net
다스베이더 070-9999-9999 darth_vader@gmail.com
princess leia 010 2454 3457 leia@gmail.com'''

// 정규표현식과 일치하는 부분을 모두 찾아주는 파이썬 코드입니다.
import re
result = re.findall(regex, search_target)
print("\n".join(result))

```

### 결과(1)

```
search_target에서 찾을 수 있는 영어 모음이 순서대로 한 줄씩 나오는것을 확인할 수 있습니다.
```

### 연속된 알파벳 소문자 고르기

> 연속된 영어 소문자를 찾을때는 ``[a-z]``에 반복횟수를 정해주는 +를 붙여서 ``[a-z]+``라고 한다.

### 코드(2)

```
// 따옴표(')로 둘러쌓인 부분에 원하는 정규표현식을 적습니다.
regex = r'[a-z]+'

search_target = '''Luke Skywarker 02-123-4567 luke@daum.net
다스베이더 070-9999-9999 darth_vader@gmail.com
princess leia 010 2454 3457 leia@gmail.com'''

// 정규표현식과 일치하는 부분을 모두 찾아주는 파이썬 코드입니다.
import re
result = re.findall(regex, search_target)
print("\n".join(result))
```

### 결과(2)

```
uke<br>
kywarker<br>
luke<br>
daum<br>
net<br>
darth<br>
vader<br>
gmail<br>
com<br>
princess<br>
leia<br>
leia<br>
gmail<br>
com<br>
```

<br>
출처: <a href="https://programmers.co.kr/">프로그래머스</a>