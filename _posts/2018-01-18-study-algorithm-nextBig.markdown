---
layout: post
title:  "[알고리즘 문제] 다음 큰 숫자 "
subtitle:   "알고리즘 문제"
categories: study
tags: algorithmproblem
comments: false
---

## 사용언어: JAVA

### 문제

> 어떤 수 N(1≤N≤1,000,000) 이 주어졌을 때, N의 다음 큰 숫자는 다음과 같습니다.<br/>
- N의 다음 큰 숫자는 N을 2진수로 바꾸었을 때의 1의 개수와 같은 개수로 이루어진 수입니다.<br/>
- 1번째 조건을 만족하는 숫자들 중 N보다 큰 수 중에서 가장 작은 숫자를 찾아야 합니다.<br/>
예를 들어, 78을 2진수로 바꾸면 1001110 이며, 78의 다음 큰 숫자는 83으로 2진수는 1010011 입니다.<br/>
N이 주어질 때, N의 다음 큰 숫자를 찾는 nextBigNumber 함수를 완성하세요.

### 해결 방법

- 이진수를 구한 후 1의 갯수를 카운트하는 oneCount()를 구현했다.

- 입력 받은 수에 1씩 더하여 oneCount()를 통해 입력 받은 수와 1의 갯수를 비교한다.

### 해결

```
class TryHelloWorld
{
  
  	int oneCount(int n){
  		int count = 0;
      while( n != 0){
      	count = (n % 2 == 1) ? ++count : count;
        n /= 2;
      }
      return count;
    }
  
    public int nextBigNumber(int n)
    {
        int answer = n;
      	int nOne = oneCount(n);
				while(true){
        	++answer;
          if(oneCount(answer) == nOne)
            break;
        }
        return answer;
    }
    public static void main(String[] args)
    {
        TryHelloWorld test = new TryHelloWorld();
        int n = 78;
        System.out.println(test.nextBigNumber(n));
    }
}

```
<br>
출처: <a href="https://programmers.co.kr/">프로그래머스</a>