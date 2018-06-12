---
layout: post
title:  "[JAVA] java.lang 패키지 "
subtitle:   "JAVA"
categories: study
tags: java
comments: false
---

## 스트링 클래스의 문제점

### String클래스는 불변클래스

```
String str1 = "hello world";
String str2 = str1.substring(5);
System.out.println(str1);
System.out.println(str2);
```

- 기존의 str1은 변화 없다.

- substring메소드는 5번째부터 문자열을 잘라 새로운 문자열을 반환하는 메소드

### 출력

```
hello world
world
```

### String클래스 사용시 문제 코드

```
String str3 = str1 + str2;
System.out.println(str3);
```

### 문제 코드의 출력
```
hello world world
```

### 문제 코드의 내부적 실행 코드

```
String str4 = new StringBuffer().append(str1).append(sstr2).toString();
System.out.println(str4);
```

- 문자열을 반복문 안에서 더하는 것은 성능상 문제 생길 수 있다.

<br>
출처: <a href="https://programmers.co.kr/">프로그래머스</a>