---
layout: post
title:  "[정규표현식] 대표문자(Meta sequence) "
subtitle:   "정규표현식"
categories: study
tags: regular
comments: false
---

## 숫자 대표문자

### 정규표현식

> 숫자를 대표하는 정규표현식은 `\d` 입니다. digit을 줄여서 \d로 씁니다.

### 코드

```
// 따옴표(')로 둘러쌓인 부분에 원하는 정규표현식을 적습니다.
regex = r'\d'

// 주소록입니다. 이후 강의에서 모두 이 search_target을 사용합니다.
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
Output에서 search_target에 들어 있는 모든 숫자가 한 줄씩 나오는 걸 확인 가능
```
<br>
출처: <a href="https://programmers.co.kr/">프로그래머스</a>