---
layout: post
title:  "[C] 배열의 요소 개수 구하기"
subtitle:   "C"
categories: reference
tags: CRefer
comments: false
---

## sizeof 함수를 통해 배열의 요소 개수 구하기

### sizeof 함수

> 자료형의 크기를 얻을 수 있음

### sizeof의 사용

- ``sizeof(int)`` 통해 int형이 몇 바이트인지 알 수 있음

- 배열 arr은``sizeof(arr)`` 통해 배열의 크기도 알 수 있음

- siezeof 함수는 CPU가 계산해서 바꾸는 것이 아닌 컴파일러가 컴파일할때 크기를 인식해서 상수로 바꿈

- CPU가 32비트든, 64비트든, 운영체제가 32비트든 64비트든 간에 컴파일러가 32비트 컴파일러면 sizeof(int)는 모두 4로 처리됨

- 32비트 CPU를 쓰고, 32비트 운영체제를 쓴다해도 16비트 컴파일러를 사용하면 sizeof(int)는 2로 처리됨

### sizeof와 배열의 요소 개수

배열 a의 요소 개수는

```
sizeof(a) / sizeof(a[0])
```
를 통해 구할 수 있음

- a배열의 전체 크기를 구한 뒤 배열의 요소 1개의 크기를 나눠줌

### 주의-(1)
```
int *p;
p = malloc(16);
printf("%d",sizeof(p));
```
- 이때 sizeof(p)는 4임

- int형 포인터이므로 4임

- malloc은 c언어 함수

- p = malloc(16)은 "malloc 함수 인자로 16을 주고, 리턴값을 p에 넣는다"라는 뜻

- sizeof()는 c언어 문법장치

- sizeof(p)는 "p의 바이트크기 상수값"이라는 의미

- 배열일 때는 c언어 문법장치인 char arr[24];를 고려해서 sizeof값을 정함

- 포인터일 때는 c언어 문법장치인 int *p;를 고려해서 sizeof값을 정함

### 주의-(2)
```
int *p;
int i;
scanf("%d",&i)
p = malloc(i);
printf("%d",sizeof(p));
```
- sizeof는 컴파일 될때 그 값이 결정되서 상수값으로 치환되어 컴파일 됨

- 만약 malloc으로 동적할당한 값을 sizeof하려 한다면 컴파일 할때 i의 값을 알 수 없으므로 sizeof 처리 불가능

<br>