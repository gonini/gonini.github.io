---
layout: post
title:  "[알고리즘&자료구조] 소수 구하기 "
subtitle:   "알고리즘&자료구조"
categories: study
tags: algorithmANDdatastructure
comments: false
---

## 사용언어: C

### 문제

> 1,000 이하의 소수를 구할때 나눗셈의 횟수 개선

### 코드

```
#include <stdio.h>
#include <stdlib.h>

int main(void) {
    int i, n;
    int count = 0;    //나누기한 횟수
    int prime[500];   //얻은 소수를 저장하는 배열
    int ptr = 0;          //얻은 소수의 갯수
    
    //첫번째
    for(n = 2; n <= 1000; n++){
        for(i = 2; i < n; i++){
            count++;
            if(n % i == 0)
                break;
        }
    }
    printf("나눗셈한 횟수는(1): %d\n", count);
    
    count = 0;
    
    //두번째
    prime[ptr++] = 2;   //2는 유일한 짝수 소수
    for(n = 3; n <= 1000; n += 2){
        for(i = 1; i < ptr; i++){
            count++;
            if(n % prime[i] == 0)
                break;
        }
        if(ptr == i)
            prime[ptr++] = n;
    }
    printf("나눗셈한 횟수는(1): %d\n", count);
    
    return 0;
}

```

### 결과

```
나눗셈한 횟수는(1): 78022
나눗셈한 횟수는(1): 14622
```

- 첫번째: 1,000 이하의 모든 수 n을 순회하며 n이하의 수로 나누는 방법

- 두번째: 발견한 소수를 삽입하는 prime 배열 생성 후 2를 제외한 짝수는 소수가 될 수 없으므로 2를 prime에 삽입

- 두번째: 소수는 어떤 소수로도 나누어 떨어지지 않으므로 prime에 삽입된 소수들로만 나눗셈을 진행하여 발견한 소수를 prime에 삽입

- 세번째: 소수 n의 조건은 n의 제곱근 이하의 어떤 소수로도 나누어떨어지지 않음

<br>