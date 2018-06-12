---
layout: post
title:  "[정규표현식] 횟수 정하기(Quantifier)  "
subtitle:   "정규표현식"
categories: study
tags: regular
comments: false
---

## n~m번

### 범위 안에서의 반복

> 숫자가 2~3번 반복해서 나오는 것은 `\d{2,3}`으로 표현할 수 있다.<br>
전화번호는 `\d{2,3}[- ]?\d{3,4}[- ]?\d{4}`으로 표현할 수 있다.

### 코드

```
regex = r'\d{2,3}[- ]?\d{3,4}[- ]?\d{4}'

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
['02-123-4567', '070-9999-9999', '010 2454 3457']
```

<br>
출처: <a href="https://programmers.co.kr/">프로그래머스</a>