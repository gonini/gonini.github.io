---
layout: post
title:  "[알고리즘 문제] 멀리뛰기 "
subtitle:   "알고리즘 문제"
categories: study
tags: algorithmproblem
comments: false
---

## 사용언어: JAVA

### 문제

> 효진이는 멀리 뛰기를 연습하고 있습니다. 효진이는 한번에 1칸, 또는 2칸을 뛸 수 있습니다. 칸이 총 4개 있을 때, 효진이는 <br/>
(1칸, 1칸, 1칸, 1칸) <br/>
(1칸, 2칸, 1칸) <br/>
(1칸, 1칸, 2칸) <br/>
(2칸, 1칸, 1칸) <br/>
(2칸, 2칸) <br/>
의 5가지 방법으로 맨 끝 칸에 도달할 수 있습니다. 멀리뛰기에 사용될 칸의 수 n이 주어질 때, 효진이가 끝에 도달하는 방법이 몇 가지인지 출력하는 jumpCase 함수를 완성하세요. 예를 들어 4가 입력된다면, 5를 반환해 주면 됩니다.

### 해결 방법

- 1 입력 -> [1] -> 1가지

- 2 입력 -> [1,1 / 2] -> 2가지

- 3 입력 -> [1,2 / 2,1 / 1,1,1] -> 3가지

- 4 입력 -> [1,1,1,1 / 1,2,1 / 1,1,2 / 2,1,1 / 2,2] -> 5가지

- 5 입력 -> [1,1,1,1,1 / 2,1,1,1 / 1,2,1,1 / 1,1,2,1 / 1,1,1,2 / 2,2,1 / 2,1,2 / 1,2,2] -> 8가지

- 피보나치 수열임을 알 수 있다.

### 피보나치 수열

> 피보나치 수는 0과 1로 시작, 다음 피보나치 수는 바로 앞의 두 피보나치 수의 합이 된다.

### 해결

```
class JumpCase {

    public int jumpCase(int num) {
        int answer = 0;
      	int fibo1 = 1, fibo2 = 1;

      	for(int i = 1; i<num; i++){
        	answer = fibo1 + fibo2;
          fibo1 = fibo2;
          fibo2 = answer;
        }

        return answer;
    }

    public static void main(String[] args) {
        JumpCase c = new JumpCase();
        int testCase = 4;
        //아래는 테스트로 출력해 보기 위한 코드입니다.
        System.out.println(c.jumpCase(testCase));
    }
}

```
<br>
출처: <a href="https://programmers.co.kr/">프로그래머스</a>