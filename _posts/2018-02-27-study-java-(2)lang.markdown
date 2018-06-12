---
layout: post
title:  "[JAVA] java.lang 패키지 "
subtitle:   "JAVA"
categories: study
tags: java
comments: false
---

## java.lang 패키지/오토박싱

### Object

- java.lang패키지의 클래스는 import하지 않고 사용 가능

- java.lang패키지에는 기본형타입을 객체로 변환시킬때 사용하는 Wrapper클래스 존재 (Boolean, Byte, Short, Integer, Long, Float, Double 클래스)

- 모든 클래스의 최상위 클래스인 Object도 java.lang패키지

- 문자열과 관련된 String, StringBuffer, StringBuilder도 모두 java.lang패키지

- 화면에 값을 출력할때 사용하는 System클래스도 java.lang패키지

- 수학 관련 Math클래스도 java.lang패키지

- Thread와 관련된 중요 클래스들도 java.lang패키지

- 이외의 다양한 클래스와 인터페이스 java.lang패키지에 속해 있다.

### 오토박싱(Auto Boxing)과 오토 언박싱(Auto unboxing)

- 박싱(boxing)이란 기본형을 참조형으로 변환

- 언박싱(unboxint)이란 반대로 참조형을 기본으로 변환

- JAVA 5부터 지원한다. 이때 내부적으로 Wrapper클래스들이 사용된다.

```
public class WrapperExam {
    public static void main(String[] args) {
        int i = 5;
        Integer i2 = new Integer(5);
        Integer i3 = 5; //오토박싱
        int i4 = i2.intValue();
        int i5 = i2;    //오토언박싱
    }
}
```

- Integer i3 = 5; 숫자 5는 기본형이지만 자동으로 Integer 형태로 변환

- int i5 = i2; Integer객체타입의 값을 기본형 int로 자동으로 변환되어 값을 할당

<br>
출처: <a href="https://programmers.co.kr/">프로그래머스</a>