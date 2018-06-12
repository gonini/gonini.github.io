---
layout: post
title:  "[정규표현식] 횟수 정하기(Quantifier)  "
subtitle:   "정규표현식"
categories: study
tags: regular
comments: false
---

## n번

### 반복

> `\d+[- ]?\d+[- ]?\d+`는 공백과 -롤 구분되는 전화번호는 찾아낼 수 있지만 숫자의 자릿수는 정의할 수 없다.<br>
중괄호를 사용하여 그 안에 숫자를 지정하면 정확히 몇 번 반복해서 나타나야 하는지 지정할 수 있다.<br>
`\d{2}`이면 정확히 2번의 숫자가 나타나는 것을 의미한다.

### 코드

```
regex = r'\d{2}[- ]?\d{3}[- ]?\d{4}'

search_target = '''이상한 전화번호 0030589-5-95826
Luke Skywarker 02-123-4567 luke@daum.net
다스베이더 070-9999-9999 darth_vader@gmail.com
princess leia 010 2454 3457 leia@gmail.com'''

//아래 부분은 본 강의에서 다루지 않습니다.
import re
result=re.findall(regex,search_target)
print(result)
```

### 결과

```
['02-123-4567']
```

<br>
출처: <a href="https://programmers.co.kr/">프로그래머스</a>