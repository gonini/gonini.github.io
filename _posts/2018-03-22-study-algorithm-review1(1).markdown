---
layout: post
title:  "[알고리즘&자료구조] 이등변삼각형 출력 "
subtitle:   "알고리즘&자료구조"
categories: study
tags: algorithmANDdatastructure
comments: false
---

## 사용언어: C

### 문제

> 네 가지의 이등변 삼각형을 출력

### 해결 방법

- 이중 for문을 통해 해결

- 양수를 입력하도록 점검 필요

### 해결

```
#include <stdio.h>

void triangleLD (int n)
{
    for(int i = 1; i <= n; i++)
    {
        for(int j =1; j <= i; j++)
        {
            putchar('*');
        }
        putchar('\n');
    }
}

void triangleLU (int n)
{
    for(int i = 1; i <= n; i++)
    {
        for(int j = 1; j <= n - i + 1; j++)
        {
            putchar('*');
        }
        putchar('\n');
    }
}

void triangleRU (int n)
{
    for(int i = 1; i <= n; i++)
    {
        for(int j = 1; j < i; j++)
        {
            putchar(' ');
        }
        for(int k = 1; k <= n - i + 1; k++)
        {
            putchar('*');
        }
        putchar('\n');
    }
}

void triangleRD (int n)
{
    for(int i = 1; i <= n; i++)
    {
        for(int j = 1; j <= n - i; j++)
        {
            putchar(' ');
        }
        for(int k = 1; k <= i; k++){
            putchar('*');
        }
        putchar('\n');
    }
}

int main(void) {
    int a;
    
    do{
        printf("몇 단: ");
        scanf("%d", &a);
    }while(a <= 0);
    
    triangleLD(a);
    putchar('\n');
    triangleLU(a);
    putchar('\n');
    triangleRU(a);
    putchar('\n');
    triangleRD(a);
    
    return 0;
}

```

### 결과

```
몇 단: 4
*
**
***
****

****
***
**
*

****
 ***
  **
   *

   *
  **
 ***
****
```

<br>