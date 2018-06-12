---
layout: post
title:  "[C] scanf 함수 "
subtitle:   "C"
categories: reference
tags: CRefer
comments: false
---

## scanf 함수에서의 & 사용

### &

> C언에서 ``&``는 & 오른쪽의 변수의 주소를 가르킴 

### scanf 함수의 사용

```
#include <stdio.h>
int main(void){
    int val;
    scanf("%d", &val);
    return 0;
}
```

- scanf 함수는 내부적으로 사용자로부터 정수를 입력받은 뒤 변수 val에 접근해 대입해야 함

- scanf 함수 내에서 main 함수에서 선언된 지역 변수에 접근하기 위해 해당 변수의 주소 알아야 함

- scanf 함수를 호출하면서 값이 채워질 지역 변수 val의 주소 값을 인자로 전달하는 것

- 결국 Call-By-Reference에 해당

### scanf 함수와char형의 배열

```
#include <stdio.h>
int main(void){
    char str[100];
    printf("문자열 입력 : ");
    scanf("%s", str);
    return 0;
}
```

- char형의 배열로 문자열을 입력받을 때는 &연산자를 사용하지 않음

- 배열 이름 str은 배열의 주소를 나타냄

- 그러므로 & 필요 없음

<br>