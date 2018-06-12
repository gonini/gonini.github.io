---
layout: post
title:  "[알고리즘 문제] 가장 큰 정사각형 찾기 "
subtitle:   "알고리즘 문제"
categories: study
tags: algorithmproblem
comments: false
---

## 사용언어: JAVA

### 문제

> O와 X로 채워진 표가 있습니다. 표 1칸은 1 x 1 의 정사각형으로 이루어져 있습니다. 표에서 O로 이루어진 가장 큰 정사각형을 찾아 넓이를 반환하는 findLargestSquare 함수를 완성하세요. 예를 들어<br/>
<table>
    <tr>
        <th>1</th>
        <th>2</th>
        <th>3</th>
        <th>4</th>
        <th>5</th>
    </tr>
    <tr>
        <td>X</td>
        <td>O</td>
        <td>O</td>
        <td>O</td>
        <td>X</td>
    </tr>
    <tr>
        <td>X</td>
        <td>O</td>
        <td>O</td>
        <td>O</td>
        <td>O</td>
    </tr>
    <tr>
        <td>X</td>
        <td>X</td>
        <td>O</td>
        <td>O</td>
        <td>O</td>
    </tr>
    <tr>
        <td>X</td>
        <td>X</td>
        <td>O</td>
        <td>O</td>
        <td>O</td>
    </tr>
    <tr>
        <td>X</td>
        <td>X</td>
        <td>X</td>
        <td>X</td>
        <td>X</td>
    </tr>
</table>
가 있다면 정답은 넓이가 9가 되므로 9를 반환해 주면 됩니다.

### 해결 방법

- 문자열 배열을 정수형 이차원 배열로 변환

- 1을 만나면 해당 위치의 왼쪽, 왼쪽 아래 대각선, 아래 위치의 수를 비교

- 최소 사각형이 될 조건이 된다면 해당 위치의 수를 증가

### 해결

```
class TryHelloWorld
{
    public int findLargestSquare(char [][]board)
    {
        int answer = 0;
      	int row = board.length;
      	int col = board[0].length;
      	int [][] arr = new int[row][col];
      	for(int i = 0; i < row; i++){
        	for(int j = 0; j < col; j++){
          	if(board[i][j] == 'X')
              arr[i][j] = 0;
            else
              arr[i][j] = 1;
          }
        }
      int max = 0;
      for(int i =1; i < row; i++){
      	for(int j = 1; j < col; j++){
        	if(arr[i][j] == 0)
            continue;
          if(arr[i-1][j] >= 1 && arr[i][j-1] >= 1 && arr[i-1][j-1] >= 1){
          	arr[i][j] = Math.min(Math.min(arr[i-1][j],arr[i][j-1]),arr[i-1][j-1]) + 1;
          }
          answer = Math.max(answer, arr[i][j]);
        }
      }

        return answer * answer;
    }
    public static void main(String[] args)
    {
        TryHelloWorld test = new TryHelloWorld();
				char [][]board ={
				{'X','O','O','O','X'},
				{'X','O','O','O','O'},
				{'X','X','O','O','O'},
				{'X','X','O','O','O'},
				{'X','X','X','X','X'}};

        System.out.println(test.findLargestSquare(board));
    }
}

```
<br>
출처: <a href="https://programmers.co.kr/">프로그래머스</a>