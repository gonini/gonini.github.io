---
layout: post
title:  "[C] puts 함수"
subtitle:   "C"
categories: reference
tags: CRefer
comments: false
---

## puts 함수와 putchar

### puts 함수

> 자동으로 개행 문자('\n') 추가하여 출력

### puts의 사용

```
#include <stdio.h>
int main()
{
    char str[] = "Hello, World!";
    puts(str);
    return 0;
}
```
```
#include <stdio.h>
int main()
{
    puts("Hello, World!");
    return 0;
}
```

- puts는 형식제어문자 사용 불가

- puts는 특수문자 사용 가능

### putchar의 사용

```
#include <stdio.h>
int main(void){
    putchar(90);
    return 0;
}
```

- putchar는 문자코드를 이용

- puts와는 다르게 개행 문자 추가되지 않음

<br>