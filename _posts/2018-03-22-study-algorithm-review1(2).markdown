---
layout: post
title:  "[알고리즘&자료구조] 피라미드 출력 "
subtitle:   "알고리즘&자료구조"
categories: study
tags: algorithmANDdatastructure
comments: false
---

## 사용언어: C

### 문제

> 두 가지의 피라미드를 출력

### 해결 방법

- 이중 for문을 통해 해결

- 양수를 입력하도록 점검 필요


### 풀이 과정

```
n이 4일때 (정피라미드)
   *   
  ***  
 ***** 
*******

공백과 *의 갯수를 본다면
3 1 3
2 3 2
1 5 1
0 7 0

1열 첫번째 공백의 갯수는 'n-1'임을 알 수 있다.
i열 첫번째 공백의 갯수는 'n-i'임을 알 수 있다.
i열 *의 갯수는 '(i-1)*2+1'임을 알 수 있다.

n이 4일때 (역피라미드)
*******
 ***** 
  ***
   *

공백과 *의 갯수를 본다면
0 7 0
1 5 1
2 3 2
3 1 3

i열 첫번째 공백의 갯수는 'i-1'임을 알 수 있다.
i열 *의 갯수는 '(n-i)*2+1'임을 알 수 있다.
```

### 해결

```
#include <stdio.h>

void piramid (int n)
{
    for (int i = 1; i <= n; i++)
    {
        for(int j = 1; j <= n - i; j++)
        {
            putchar(' ');
        }
        for(int k = 1; k <= (i - 1) * 2 + 1; k++)
        {
            putchar('*');
        }
        putchar('\n');
    }
}

void npiramid (int n)
{
    for (int i = 1; i <= n; i++)
    {
        for(int j = 1; j <= i - 1; j++)
        {
            putchar(' ');
        }
        for(int k = 1; k <= (n - i) * 2 + 1; k++)
        {
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
    
    piramid(a);
    putchar('\n');
    npiramid(a);
    
    return 0;
}
```

### 결과

```
몇 단: 4
   *
  ***
 *****
*******

*******
 *****
  ***
   *
```

<br>