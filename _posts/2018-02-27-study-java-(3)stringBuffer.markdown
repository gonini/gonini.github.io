---
layout: post
title:  "[JAVA] java.lang 패키지 "
subtitle:   "JAVA"
categories: study
tags: java
comments: false
---

## 스트링버퍼

### 아무 값도 가지고 있지 않은 StringBuffer객체 생성

```
StringBuffer sb = new StringBuffer();

//  StringBuffer에 "Hello, 공백, world"를 차례로 추가
sb.append("Hello");
sb.append(" ");
sb.append("world");

//  StringBuffer에 추가된 값ㅇ르 toString()메소드를 이용하여 반환
String str = sb.toString();
```

### 출력

```
Hello world
```

### StringBuffer 메소드들은 대부분 자기 자신, this 반환

```
StringBuffer sb2 = new StringBuffer();
StringBuffer sb3 = sb2.append("hello");
if(sb2==sb3){
    System.out.println("sb2==sb3");
}
```

- StringBuffer클래스는 메소드 체인 방식으로 사용할 수 있다.

### 출력
```
sb2==sb3
```

### StringBuffer 메소드 체인

```
String str = new StringBuffer().append("hello").append(" ").append("world);
System.out.println(str);
```

### 출력

```
hello world
```

<br>
출처: <a href="https://programmers.co.kr/">프로그래머스</a>