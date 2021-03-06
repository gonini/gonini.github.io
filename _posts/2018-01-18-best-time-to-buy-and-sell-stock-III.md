---
layout: post
title:  "Best Time to Buy and Sell Stock III"
subtitle: 
categories: algorithm
tags: dp
comments: true
---  
[Best Time to Buy and Sell Stock III - LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/description/)  
* 정수형 주가 리스트가 주어진다. 최대 이익을 계산하라.  2번의 트렌젝션을 발생 시킬 수 있다.  
* 거래 규칙
	* 거래는 하루에 1번 할 수 있다.
	* 구매 - 주식을 구매한다.  새로운 주식을 구매하려면 보유한 주식을 판매하여야한다.
	즉 동시에 여러 거래를 할 수 없다.
	* 판매 - 주식을 판매한다.  
	* 트렌젝션 - 구매 + 판매를  한번의 트렌젝션으로 본다.
		* 최대 2번의 발생시킬 수 있다.

**Example 1**
```
Input: [3,3,5,0,0,3,1,4]
Output: 6
Explanation: Buy on day 4 (price = 0) and sell on day 6 (price = 3), profit = 3-0 = 3.
             Then buy on day 7 (price = 1) and sell on day 8 (price = 4), profit = 4-1 = 3.
```

**Example 2**
```
Input: [1,2,3,4,5]
Output: 4
Explanation: Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
             Note that you cannot buy on day 1, buy on day 2 and sell them later, as you are
             engaging multiple transactions at the same time. You must sell before buying again.
```

**Example 3**
```
Input: [7,6,4,3,1]
Output: 0
Explanation: In this case, no transaction is done, i.e. max profit = 0.
```

**Code**
```
int maxProfit(vector<int>& prices) {
        
}
```

- - - -

**Solution**
> minPrice : 이전 거래까지 가장 저렴한 주식의 가격  
> buy[i] : `buy[0] ~ buy[i]`  중 두번째 구매일 때 최대 이익  
> sell[i][0] :  `sell[0][0] ~ sell[i][0]`  중 첫 판매일 때  최대 이익  
> sell[i][1] :   `sell[0][1] ~ sell[i][1]` 중  두번째 판매일 때  최대 이익  

**minPrice**    
첫 판매일 때 최대 이익 `sell[i][0]` 을 구하기 위해서 사용된다. 판매를 위해서는 구매가 발생해야한다. 물건이 있어야 장사를 한다.  잠시 문제를 변경하자.  트렌젝션을 한번 발생시켜 최대의 이익을 내야한다. 가장 낮은 가격에 구매하여 가장 높은 가격에 판매하면 최대 이익을 낼 것이다.  0 ~ k 에서 최대 이익은 `FOR 0..k -> 최대값(price[k]-minPrice)` 이다.  트렌젝션 한번으로 최대 이익을 구하는 방법은 트렌젝션 두 번으로 최대 이익을 구하는 방법과 연결된다.

**sell[i][0]**  
1. i 번째 주식 가격에 판매하지 않는 경우 : sell[i-1][0]  
2. i 번째 주식 가격에 판매하는 경우 : price[i] - minPrice  
`sell[i][0] = max(sell[i-1][0], prices[i] - minPrice);`  
처음 주식을 판매하는 경우, 가장 낮은 가격에 구매한뒤 판매하는게 최대 이익을 낸다.  

**buy[i]**  
1. i 번째 주식 가격에 구매하지 않는 경우 : buy[i-1]  
2. i 번째 주식 가격에 구매하는 경우 : sell[i-1][0] - price[i]   
`buy[i] = max(buy[i-1], sell[i-1][0] - prices[i])`  
두번째 구매시 최대 이익 = MAX(현재 주식 구매 안하는 경우,  첫 판매시 최대 이익 - 현재 주식가) 

**sell[i][1]**  
1. i 번째 주식 가격에 판매하지 않는 경우 : sell[i-1][1]  
2. i 번째 주식 가격에 판매하는 경우 : buy[i-1] + price[i]  
`sell[i][1] = max(sell[i-1][1], buy[i-1] + prices[i])`  
두번째 판매시 최대 이익 = MAX(현재 주식 판매 안하는 경우, 두 번째 구매시 최대 이익 + 현재 주식가)


```
#define MAX 50002
#define NONE (1<<31)

class Solution {
public:
int buy[MAX];
int sell[MAX][2];
int maxProfit(vector<int>& prices) {
        int ret = 0;
        if(prices.empty()) return ret;
        memset(sell, 0, sizeof(sell));
        int minPrice = prices.front();
        for(int i = 0; i < MAX; i++)
            buy[i] = NONE;
        for(int i = 1; i < prices.size(); i++)
        {
            sell[i][0] = max(sell[i-1][0], prices[i] - minPrice);
            if(i > 1)
                buy[i] = max(buy[i-1], sell[i-1][0] - prices[i]);
            if(i > 2 && buy[i-1] != NONE)
                sell[i][1] = max(sell[i-1][1], buy[i-1] + prices[i]);
            minPrice = min(minPrice, prices[i]);
            ret = max(ret, max(sell[i][0], sell[i][1]));
        }
    return ret;
}
};
```
**time complexity O(n)**  
**space complexity O(n)**

- - - -

전일 거래 결과를 통해 당일 최대 수익을 계산하기 때문에, 모든 거래 결과를 유지하지 않아도된다. 전일 거래 결과만 유지하도록 변경한다.

```
#define NONE (1<<31)
class Solution {
public:
int maxProfit(vector<int>& prices) {
        int ret = 0;
        if(prices.empty()) return ret;
        int buy = NONE, sell1 = 0, sell2 = 0;
        int prevSell1, prevBuy;
        int minPrice = prices.front();

        for(int i = 1; i < prices.size(); i++)
        {
            prevSell1 = sell1;
            prevBuy = buy;
            sell1 = max(sell1, prices[i] - minPrice);
            if(i > 1)
            {
                buy = max(buy, prevSell1 - prices[i]);
            }
            if(i > 2 && prevBuy != NONE)
            {
                sell2 = max(sell2, prevBuy + prices[i]);
            }
            minPrice = min(minPrice, prices[i]);
            ret = max(ret, max(sell1, sell2));
        }
    return ret;
}
};
```
**time complexity O(n)**  
**space complexity O(1)**

- - - -

**Looking back**  
buy 배열의 초기값을 -1로 두었다. 두번째 구매시 최대 수익을 업데이트 하는 과정에서 이 초기 값으로 인하여 잘못된 결과가 계산되었다. 현재 주식을 구매한 가격 `sell[i-1][0] - prices[i]` 이 초깃값(-1)보다 더 작은 음수가 나오는 것을 고려하지 못하였기 때문이다.    `buy[i] = max(buy[i-1], sell[i-1][0] -prices[i])`   이 부분에서 초기값으로 인하여 buy [i]가 -1로 업데이트되면서 최대 수익에 대한 계산도 자연히 틀리게 되었다. 초기값을 INT_MIN으로 설정하여 해결하였다.




















