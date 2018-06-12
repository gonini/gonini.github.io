---
layout: post
title:  "[알고리즘 문제] 숫자의 표현 "
subtitle:   "알고리즘 문제"
categories: study
tags: algorithmproblem
comments: false
---

## 사용언어: JAVA

### 문제

> 수학을 공부하던 민지는 재미있는 사실을 발견하였습니다. 그 사실은 바로 연속된 자연수의 합으로 어떤 숫자를 표현하는 방법이 여러 가지라는 것입니다. 예를 들어, 15를 표현하는 방법은<br/>
(1+2+3+4+5)<br/>
(4+5+6)<br/>
(7+8)<br/>
(15)<br/>
로 총 4가지가 존재합니다. 숫자를 입력받아 연속된 수로 표현하는 방법을 반환하는 expressions 함수를 만들어 민지를 도와주세요. 예를 들어 15가 입력된다면 4를 반환해 주면 됩니다.

### 해결 방법

- 연속된 2개의 숫자 -> 2n + 1

- 연속된 3개의 숫자 -> 3n + 3

- 연속된 4개의 숫자 -> 4n + 6

- 연속된 5개의 숫자 -> 5n + 10

- 연속된 6개의 숫자 -> 6n + 21

- 위와 같은 법칙임을 알 수 있다.

- 실수 k는 n-1번째의 k에 n-1번째의 n앞의 실수를 더한다.

- 입력 받은 num에서 실수를 빼고 연속된 갯수로 나눠서 나머지가 없다면 연속된 수들의 합으로 이뤄진 num이 존재하는 것이다.

- 1개의 숫자로 이뤄진 경우까지 더해줘야하므로 answer + 1을 반환해준다.

### 해결

```
public class Expressions {

	public int expressions(int num) {

    int answer = 0;
    int i = 2;
    int j = 1;

    while(true){
      if(i + j > num){
      	break;
      }
      int temp = (num - j) % i;
      if(temp == 0){
      	answer ++;
      }
      j += i;
      i++;
    }

		return answer + 1;
	}

	public static void main(String args[]) {
		Expressions expressions = new Expressions();
		System.out.println(expressions.expressions(15));
	}
}

```
<br>
출처: <a href="https://programmers.co.kr/">프로그래머스</a>