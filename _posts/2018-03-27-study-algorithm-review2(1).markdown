---
layout: post
title:  "[알고리즘&자료구조] 기수 변환 "
subtitle:   "알고리즘&자료구조"
categories: study
tags: algorithmANDdatastructure
comments: false
---

## 사용언어: C

### 문제

> 기수 변환 과정을 상세히 출력하는 프로그램 작성

### 해결

```
#include <stdio.h>
#include <stdlib.h>

//요소 자리 바꾸는 매크로
#define swap(type, x, y) do{type t = x; x = y; y = t;} while(0)

//기수 변환
int card_conv(unsigned x, int n, char d[]){
    int digits = 0;
    char dchar[] = "0123456789ABCDEFGHIJKLMNOPQRSTUVWZYZ";
    
    if(x == 0)  //0을 기수변환하는 경우
        d[digits++] = dchar[0];
    else{
        while(x){
            d[digits++] = dchar[x % n];
            printf("%d|     %d ... %d\n", n, x, x % n);
            printf(" +-------\n");
            x /= n;
        }
        printf("       0\n");
    }
    
    //기수 변환된 배열은 아랫자리부터 들어가있으므로 배열을 역순으로 재정렬
    for(int i = 0; i < digits / 2; i++){
        swap(int, d[i], d[digits - i -1]);
    }
    
    return digits;  //자릿수 반환
}

//배열 출력 함수
void print(char d[], int size){
    for(int i = 0; i < size; i++){
        printf("%c",d[i]);
    }
    printf("\n");
}

int main(void) {
    
    unsigned num;
    int cno;
    int cd;
    char no[512];
    
    puts("10진수를 기수 변환합니다.");
    printf("변환하는 음이 아닌 정수: ");
    scanf("%d", &num);
    printf("어떤 진수로 변환할까요?(2-36): ");
    scanf("%d", &cno);
    
    cd = card_conv(num, cno, no);
    
    printf("%d진수로 ", cno);
    
    print(no, cd);
    
    return 0;
}

```

### 결과

```
10진수를 기수 변환합니다.
변환하는 음이 아닌 정수: 58
어떤 진수로 변환할까요?(2-36): 2
2|     58 ... 0
 +-------
2|     29 ... 1
 +-------
2|     14 ... 0
 +-------
2|     7 ... 1
 +-------
2|     3 ... 1
 +-------
2|     1 ... 1
 +-------
       0
2진수로 111010
```

<br>