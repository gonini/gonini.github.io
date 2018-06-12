---
layout: post
title:  "[정규표현식] 고르기  "
subtitle:   "정규표현식"
categories: study
tags: regular
comments: false
---

## 한글 고르기

### 연속된 한글 고르기

> 한글의 첫번째 글자는 ``가``이고 마지막 글자는 ``힣``이다.
그래서 ``[가-힣]``은 모든 한글을 선택하게 됩니다. 단 ``ㄱㄴㄷ``이나 ``ㅏㅑㅓㅕ``같은 낱글자는 포함이 안된다.

### 코드

```
// 따옴표(')로 둘러쌓인 부분에 원하는 정규표현식을 적습니다.
regex = r'[가-힣]+'

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
다스베이더
```

<br>
출처: <a href="https://programmers.co.kr/">프로그래머스</a>