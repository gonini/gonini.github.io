---
layout: post
title:  "[정규표현식] 횟수 정하기(Quantifier)  "
subtitle:   "정규표현식"
categories: study
tags: regular
comments: false
---

## 있거나 없거나

### or(1)

> 있거나 없거나 or은 `?`으로 표현한다.<br>
전화번호는 연속된 숫자 그룹 사이에 `-`가 있거나 없을 수 있다.<br>
`-`가 있거나 없는건 `-?`로 표현한다.<br>
그리고 숫자 그룹은 `\d+`으로 표현한다.<br>
위와 같은 사실들을 통해 전화번호는 `\d+-?\d+-?\d+`로 표현한다.

### 코드(1)

```
regex = r'\d+-?\d+-?\d+'

search_target = '''Luke Skywarker 02-123-4567 luke@daum.net
다스베이더 070-9999-9999 darth_vader@gmail.com
princess leia 010 2454 3457 leia@gmail.com'''

//아래 부분은 본 강의에서 다루지 않습니다.
import re
result=re.findall(regex,search_target)
print(result)
```

### 결과(1)

```
['02-123-4567', '070-9999-9999', '010', '2454', '3457']
```

### or(2)

> `-?`을 이용하면 공백을 찾을 수 없다.<br>
전화번호를 찾을 경우,<br>
- `-`가 있거나 없다는 조건보다<br>
- `-` 또는 `(공백)`이 있거나 없다는 조건이 정확하다.<br>
`-` 또는 `(공백)`이 있거나 없다는 조건은 `[- ]`로 표현한다.

### 코드(2)
```
regex = r'\d+[- ]?\d+[- ]?\d+'

search_target = '''Luke Skywarker 02-123-4567 luke@daum.net
다스베이더 070-9999-9999 darth_vader@gmail.com
princess leia 010 2454 3457 leia@gmail.com'''

//아래 부분은 본 강의에서 다루지 않습니다.
import re
result=re.findall(regex,search_target)
print(result)
```

### 결과(2)
```
['02-123-4567', '070-9999-9999', '010 2454 3457']
```

<br>
출처: <a href="https://programmers.co.kr/">프로그래머스</a>