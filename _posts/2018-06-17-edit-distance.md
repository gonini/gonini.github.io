---
layout: post
title:  "Edit Distance"
subtitle: "Wagner–Fischer Algorithm"
categories: algorithm
tags: dp
comments: true
---

* 두 단어가 주어진다. 이 둘을 각각 word1, word2 이라 부른다. 교체, 삭제, 삽입 연산을 사용하여 word1을 word2로 변환할 수 있다. 이 때 최소 연산 횟수를 반환하라.   
* 각 연산은 한 문자에만 적용할 수 있다.  

**Example 1**  
```
Input: word1 = "horse", word2 = "ros"
Output: 3
Explanation: 
horse -> rorse (replace 'h' with 'r')
rorse -> rose (remove 'r')
rose -> ros (remove 'e')
```

**Example 2**  
```
Input: word1 = "intention", word2 = "execution"
Output: 5
Explanation: 
intention -> inention (remove 't')
inention -> enention (replace 'i' with 'e')
enention -> exention (replace 'n' with 'x')
exention -> exection (replace 'n' with 'c')
exection -> execution (insert 'u')
```

**Code**  
```
class Solution {
public:
int minDistance(string word1, string word2) {

}
};
```

---

**Solution**  
Wagner–Fischer 알고리즘은 교체, 삭제, 삽입의 연산을 기반으로 서로 다른 두 문자열 이 동일해 질 수 있는 최소 거리를 계산한다. 이러한 최소 거리를 편집 거리라 부른다. 주로 NLP(자연어처리) 프로그램에서 자연어와 사전의 단어간 유사도를 측정하여 맞춤법 교정 후보를 선출하는데 이용된다.  

> kitten → sitten ( “k” -> “s”  교체 )   
> sitten → sittin ("e" -> “i” 교체  )  
> sittin → sitting ( "g" 마지막 위치에 삽입 )  
> 
> kitten과 sitting의 Edit distance는 3이다.   

알고리즘의 핵심은 첫 번째 문자열의 모든 접두사와 두 번째 문자열의 모든 접두사 간 편집거리를 행렬에 채워가며 현재 편집 거리를 계산하는데 이용하는 것이다.  점화식은 아래와 같다.  

![](/assets/img/edit_distance.png)  


> 삭제 -> `m[i-1][j] + 1`  
> 삽입 -> `m[i][j-1] + 1`  
> 교체 -> `m[i-1][j-1] + (word1[j] != word2[i])`   

이를 염두해두고  “inte” 와 “exec” 의 편집거리를 구해보자.  ‘  ’ 는 공백이다. 공백으로부터  두 문자열의 모든 접두사까지의 편집거리는 접두사의 길이와 같다.  공백과 모든 접두사의 편집거리를 구하는 것은 가장 작은 문제이다.   

|    | '' | e | x | e | c |
|:--:|:--:|:-:|:-:|:-:|:-:|
| '' |  0 | 1 | 2 | 3 | 4 |
|  i |  1 |   |   |   |   |
|  n |  2 |   |   |   |   |
|  t |  3 |   |   |   |   |
|  e |  4 |   |   |   |   |

> 공백과 ‘exec’ 의 편집거리는  4이다 -> `m[0][4]`   
> 공백과  ‘int’ 의 편집거리는 3이다 ->  `m[3][0]`   

남은 칸을 채워나가게 되면 `m[word1.size()][word2.size()]` 에  ‘inte’ -> ‘exec’ 의 편집거리가 채워질 것이다.  이해를 돕기 위해 작은 문제들을 미리 풀어두었다.

|    | '' | e | x | e | c |
|:--:|:--:|:-:|:-:|:-:|:-:|
| '' |  0 | 1 | 2 | 3 | 4 |
|  i |  1 | 1 | 2 | 3 | 4 |
|  n |  2 | 2 | 2 | 3 | 4 |
|  t |  3 | 3 | 3 | 3 | 4 |
|  e |  4 | 3 | 4 |   |   |

채워야할 칸은   `m[4][3]` ,  `m[4][4]`  이다.  `m[4][4]` 를 구하기 위해서는 `m[4][3]`이 필요하다. `m[4][3]`이 의미하는 것은  ‘inte’ -> ‘exe’ 의 편집거리이다.  

**‘inte’ -> ‘exe’ 의 편집거리**  

* 수정  
‘inte’ 에서 e를 e로 수정하여 ‘exe’ 가 되는 편집 거리를 계산해야한다. 그렇다.  이미 수정하려는 문자와 동일하기 때문에 수정할 필요가 없다.  수정에 대한 비용은 고려하지 않아도 된다.  ‘e’ 는 원하는 단어다. 이제 ‘e’를 제외한 ‘int’ 와 ‘ex’ 의 편집 거리를 구하면 되지 않을까? ‘int’ 와 ‘ex’ 의 편집 거리 + 수정 연산은 ‘inte’ 에서 e를 e로 수정하여 ‘exe’ 가 되는 편집 거리가 된다. 물론   ‘int’ -> ‘ex’   `m[3][2]` 는 이미 구해져 있다.  수정할 필요가 없었으니 `m[3][2] + 0` 이 된다.

* 삭제   
‘inte’ 에서 e를 삭제하여 ‘exe’ 가 되는 편집 거리를 계산해야한다. ‘e’ 를 삭제했으니 삭제에 대한 연산 횟수도 포함해야한다. ‘inte’ 에서 ‘e’를 삭제하면 ‘int’ 이다. ‘int’ -> ‘exe’ 의 편집거리를 구하고 삭제한 연산 횟수를 포함해주면  *‘inte’ 에서 e를 삭제하여 ‘exe’ 가 되는 편집 거리가 된다.*  ‘int’ -> ‘exe’ `m[3][3]` 은 이미 구해져 있다. 삭제 연산 수를 포함 시켜줘야하니 `m[3][3] + 1` 이 된다.

* 삽입  
‘inte’ 에서  ‘ex’ 가 되는 편집거리를 계산해야한다.  왜  ‘exe’ 와의 편집 거리를 계산하는게 아닐까? ‘inte’ -> ‘ex’ 의 편집 거리는 이미 구해져 있으며 여기에 ‘e’ 를 삽입하면 ‘exe’ 가 되기 때문이다.  삽입 연산 수를 포함 시켜줘야하니  `m[4][2] + 1` 이 된다.

> 위의 수정, 삭제 , 삽입 연산을 수행한뒤 가장 작은 수가 편집거리가 된다.  
> 현재 편집 거리  = min(수정, 삭제, 삽입)   
> `m[4][3]` = min( `m[3][2] + 0`,  `m[3][3] + 1`,  `m[4][2] + 1`)  


|    | '' | e | x | e | c |
|:--:|:--:|:-:|:-:|:-:|:-:|
| '' |  0 | 1 | 2 | 3 | 4 |
|  i |  1 | 1 | 2 | 3 | 4 |
|  n |  2 | 2 | 2 | 3 | 4 |
|  t |  3 | 3 | 3 | 3 | 4 |
|  e |  4 | 3 | 4 | 3 |   |

**‘inte’ -> ‘exec’ 의 편집거리**  

위와 동일한 방일하게 m[4][4] 를 구할 수 있다.    `m[4][4]` = min( `m[3][3] + 1`,  `m[3][4] + 1`,  `m[4][3] + 1`)    가장 작은 수는 4이며, 편집거리가 된다.   

|    | '' | e | x | e | c |
|:--:|:--:|:-:|:-:|:-:|:-:|
| '' |  0 | 1 | 2 | 3 | 4 |
|  i |  1 | 1 | 2 | 3 | 4 |
|  n |  2 | 2 | 2 | 3 | 4 |
|  t |  3 | 3 | 3 | 3 | 4 |
|  e |  4 | 3 | 4 | 3 | 4 |

‘exec’ 와  ‘inte’ 의 편집거리는 4가 된다.   


```
class Solution {
public:
    int minDistance(string word1, string word2) {
      const int N = (int) word1.size() > word2.size() ? word1.size() : word2.size();
      vector<vector<int>> dp(N+1, vector<int>(N+1, 0) );

      for(int i = 0; i <= N; i++)
      {
          dp[0][i] = i;
          dp[i][0] = i;
      }

      for(int i = 1; i <= word1.size(); i++)
      {
          for(int j = 1; j <= word2.size(); j++)
          {

              int replace = dp[i-1][j-1] + (word1[i-1] != word2[j-1]);
              int insert = dp[i-1][j] + 1;
              int remove = dp[i][j-1] + 1;

              dp[i][j] = min(replace, min(insert, remove));
          }
      }    
    return dp[word1.size()][word2.size()];
  }
};
```  



**footnote**  
[Wagner–Fischer algorithm - Wikipedia](https://en.wikipedia.org/wiki/Wagner%E2%80%93Fischer_algorithm)  
[Levenshtein distance - Wikipedia](https://en.wikipedia.org/wiki/Levenshtein_distance)  
[Edit distance - Wikipedia](https://en.wikipedia.org/wiki/Edit_distance)  















