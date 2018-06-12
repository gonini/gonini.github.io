---
layout: post
title:  "[정규표현식] 정규표현식 사용해보기 "
subtitle:   "정규표현식"
categories: study
tags: regular
comments: false
---

## intro

### 정규표현식 사용

> 정규표현식은 문자열에서 특정 패턴을 만족하는 부분을 찾아내고 싶을 때 사용하면 좋습니다.

### 예시

- 스타워즈 주인공들의 주소록에서 전화번호 찾기

- 코드 5번째 줄에 있는 search_target이라는 변수에 전화번호 저장

- 주소록에서 전화번호를 찾아주는 정규표현식은<br>
```
0\d{1,2}[ -]?\d{3,4}[ -]?\d{3,4}
```

- 코드 2번째 줄에 있는 변수 regex에 정규표현식 저장

### 코드

```
// 따옴표(')로 둘러쌓인 부분에 원하는 정규표현식을 적습니다.
regex = r'0\d{1,2}[ -]?\d{3,4}[ -]?\d{3,4}'  # 전화번호를 찾는 정규표현식

// 주소록입니다. 이후 강의에서 모두 이 search_target을 사용합니다.
search_target = '''Luke Skywarker 02-123-4567 luke@daum.net
다스베이더 070-9999-9999 darth_vader@gmail.com
princess leia 010 2454 3457 leia@gmail.com'''

// 정규표현식과 일치하는 부분을 모두 찾아주는 파이썬 코드입니다.
import re
result = re.findall(regex, search_target)
print("\n".join(result))

```
<br>
출처: <a href="https://programmers.co.kr/">프로그래머스</a>